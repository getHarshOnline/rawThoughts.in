Title: The sorting program that passed the wrong test

[Read HTML](https://rawthoughts.in/blog/checking-generated-code/)

Author: Harsh Joshi

<a id="the-sorting-program-that-passed-the-wrong-test"></a>

# The sorting program that passed the wrong test

For `[3, -1, 3]`, a sorting program returns `[0, 0, 0]`. Its output is in ascending order. Its length matches the input. Both tests pass, yet the program has discarded every value it was asked to sort.

We can construct that failure without a language model: the checker was never asked whether the program kept the input values. Model-written code makes the gap especially interesting because it can produce an implementation, tests and an explanation together. All three could agree that those zeros are a success. What did we actually ask them to check?

<a id="a-perfectly-checked-wrong-answer"></a>

## A perfectly checked wrong answer

The missing property is preservation of the values being sorted. No dishonest checker is necessary: a correct proof of order and length would still accept the zeros. The requirement has to connect the output to this input, rather than merely describe the shape of an acceptable-looking list.

Adding set equality is not enough either. The outputs `[-1, 3, 3]` and `[-1, -1, 3]` have the same set of values and the same length, but different multiplicities. The contract needs to preserve the count of each value, as well as establish order. Whether the input may be modified also needs an answer: returning a new list and sorting the caller's list in place are different promises.

The gap fits in a few lines of Python. This example checks the output of a function intended to return a new list of integers; it does not execute an unknown generated program.

```python
from collections import Counter

def looks_sorted(before, after):
    return len(before) == len(after) and all(
        left <= right for left, right in zip(after, after[1:])
    )

def preserves_sorting_contract(before, after):
    return looks_sorted(before, after) and Counter(before) == Counter(after)

values = [3, -1, 3]
assert looks_sorted(values, [0, 0, 0])
assert not preserves_sorting_contract(values, [0, 0, 0])
assert not preserves_sorting_contract(values, [-1, -1, 3])
assert preserves_sorting_contract(values, [-1, 3, 3])
```

The first assertion succeeds for the wrong reason: nothing in that check connects the returned values to the supplied values. `Counter` supplies the missing multiplicities. The second contract also accepts an empty input and handles repeated values, but it remains an executable check of a candidate output.

**Note**

**What this check leaves open.** It does not check that the caller's list stayed unchanged or that a fresh list was allocated; those promises need observations of the call itself. Nor is it a termination argument or a proof about every execution of the function that produced it.

The constructed example exposes a requirement problem before it becomes a tool choice. [Dafny's official guide](https://dafny.org/dafny/OnlineTutorial/guide) develops the same distinction through preconditions and postconditions: a nonnegative result alone does not sufficiently specify an absolute-value function. Verification establishes the written conditions, so those conditions have to capture the computation the caller actually needs.

<a id="five-greens-with-different-meanings"></a>

## Five greens with different meanings

A generated artifact can pass several checks without those checks answering the same question.

| Check | What its success can establish | What remains outside that result |
| --- | --- | --- |
| Schema validation | The artifact has the required representational shape | Whether that representation describes the intended computation |
| Compilation | The selected compiler accepts and translates the program | Whether the resulting behaviour meets the need |
| Tests | The checked cases produced their expected observations | The unchecked cases and the adequacy of those expectations |
| Formal verification | The declared properties hold within the selected semantics and proof assumptions | Whether those properties capture the actual requirement |
| Operational qualification | The selected system met its criteria in the observed setting | Other configurations, environments and future conditions |

These are not five grades on one confidence scale. They are different obligations. A compiler error cannot be dismissed because tests looked plausible; a proof cannot compensate for a requirement that permits the wrong result.

Even the word "verification" needs its object. LLVM's verifier checks that an LLVM module is well formed, including structural conditions beyond what its parser accepts.<sup><a id="fnref-note-6c6c766d"></a>[1](#fn-note-6c6c766d)</sup> That is valuable compiler infrastructure. It is not a proof that a user wanted this computation or that every memory access is safe.

<a id="independence-is-a-control-boundary"></a>

## Independence is a control boundary

The generator can help propose a specification. It can suggest an invariant, find an edge case or explain a failed proof. None of those contributions requires giving it the power to accept its own changes to the acceptance conditions.

For the sorting example, fixing a failure by replacing "preserve every value's multiplicity" with "preserve the length" would change the problem. So would adding a precondition that the input contains only zeros, or weakening the allowed input to already sorted lists without the caller's agreement. A successful result after either change says nothing about the original request.

Keeping the reviewed contract and the range of inputs it must handle outside the candidate's writable area preserves the question through repair. A repair attempt changes the candidate; a proposed contract change returns to requirement review and starts a different evaluation if accepted. Generated annotations can supply useful invariants, but unchecked assumptions or exemptions would remove the very property an independent judge is supposed to assess.

The independent judge need not be a single magical oracle. It can combine a type checker, executable reference behaviour, property tests, a solver and human review. What matters is which claim each component decides, which assumptions it relies on and who can alter its inputs. Another model is useful for criticism, but agreement between generators does not become a proof simply because the critics have different names.

This question already has a research setting. [Clover](https://theory.stanford.edu/~barrett/pubs/SSP%2B24.pdf), for example, checks consistency among generated code, documentation and formal annotations using verification tools and models. That can filter candidates within the study's conditions. The question here is whether a separately reviewed requirement survives the whole process: consistency among three generated descriptions cannot, by itself, show that they express what the caller needed.

<a id="the-arithmetic-has-a-world"></a>

## The arithmetic has a world

Mathematical integers and fixed-width machine integers obey different arithmetic rules. A specification that ignores overflow may be adequate for comparisons but inadequate for an implementation that subtracts two values to compare them. The translation into machine code must preserve the behaviour the proof establishes.

Likewise, proving a return-value property does not automatically establish termination, a memory bound, an acceptable runtime or harmless behaviour in surrounding code. A precondition may rule out inputs that a real caller still supplies. An external library or unchecked escape hatch may sit outside the verified fragment. Those boundaries are part of the result, not footnotes to remove after the badge turns green.

A small, explicitly supported fragment makes this approach testable. Its semantics can be stated, its failures inspected and its checks compared with ordinary development without executing unknown generated artifacts in an uncontrolled environment. Extending that fragment then becomes a concrete question about which new constructs the contract and checking system can faithfully handle.

<a id="a-rejected-candidate-is-information"></a>

## A rejected candidate is information

For this approach to be useful, the report must distinguish a counterexample from a tool failure, a resource limit from a proved property and an unsupported construct from an accepted one. "Could not establish" is not "established false", but neither is it permission to report success.

A finite repair budget also matters. Repeatedly regenerating until a weak checker passes can hide how often the system failed and how much review it consumed. The failures needed to understand that process belong in the evaluation, alongside the cost of obtaining a correctly checked result. A pipeline that saves typing but multiplies specification review may still be useful; the comparison with ordinary implementation needs to show where its benefit actually lies.

The ambition is to let candidate generation explore freely inside a question that survives its attempts. A rejected program can lead to a better implementation, a missing invariant or a proposed correction to the requirement. Those are different kinds of progress. Keeping them distinct lets cheap generation contribute without making the meaning of success equally cheap.

1. 
   
   <a id="fn-note-6c6c766d"></a>
   
   [LLVM's language reference](https://llvm.org/docs/LangRef.html#well-formedness). [↩](#fnref-note-6c6c766d)
