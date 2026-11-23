Title: Review a publication before release

[Read HTML](https://rawthoughts.in/gazette/review-a-publication/)

Rights holder: RawThoughts Enterprises Private Limited

<a id="review-a-publication-before-release"></a>

# Review a publication before release

Open the generated publication and follow the argument as a reader would. Are the words, figures and qualifications there? Can you reach the next part? Does the page reveal anything that should have stayed private? A successful build gives you something to review. The publisher decides whether that result is ready to release.

This guide covers review and the checks after delivery. Gazette prepares the output for the publisher’s review and explicit confirmation before it pushes the release to the host that serves it. That push has run against local repositories only, so a first public release also needs a hosted destination that its publisher has set up and checked. The [developer release guide](https://docs.rawthoughts.in/gazette/releasing) supplies the commands. You can keep writing and [previewing locally](https://rawthoughts.in/gazette/first-publication/) while preparing for release.

<a id="read-the-result-with-its-sources"></a>

## Read the result with its sources

Start with the exact output you intend to release. Read each changed page beside its source and inspect the presentation. An editor may have approved the words before a template change hid a qualification, cropped a figure or exposed private metadata. Check the words and what the reader actually sees together.

For example, [the serving article](https://rawthoughts.in/blog/serving-tokens-is-a-service-problem/) compares burst and spaced requests. Both schedules have equal throughput, but their response times differ. If the chart survives while the arrival conditions disappear, the page keeps the numbers and loses the explanation. Follow the same comparison through its machine-readable output: the conditions still matter there.

When a source or theme changes after review, inspect the affected output again. Approval should identify the result the publisher saw.

<a id="follow-the-complete-reading-path"></a>

## Follow the complete reading path

Compare the output's page addresses with those of your last release. Gazette does not list a released address that the new output no longer serves, so a moved page without an alias leaves readers' bookmarks broken with no diagnostic. Open collections and journeys from their entrances and follow their links. A journey promises an argument in a particular order. Leaving out an unapproved member can remove the premise its next step needs. Supply the approved members or deliberately revise the reading path before releasing it.

An external citation can remain external. The question is which pages your publication promises as its own reading path and which it cites elsewhere. [Why an article has one home](https://rawthoughts.in/gazette/why-an-article-has-one-home/) explains how membership and useful references serve different purposes.

Check privacy across the whole result, including metadata, downloadable files and attached resources. A private source may help you write a public explanation without belonging in the published output itself. The current preparation flow checks the selected content and assets, runs the configured disclosure and output checks, and retains the result for inspection. Its [preparation instructions](https://docs.rawthoughts.in/gazette/releasing#preparing) describe the inputs that flow requires.

<a id="agree-what-each-publisher-will-release"></a>

## Agree what each publisher will release

Keep the selected sites, reviewed output and destinations clear. Each publisher approves their own scope. One person may act for several publishers, but approval for one destination does not extend to another by association.

The confirmation applies to the reviewed output, sites and destinations, and is used once for that release. Changed output or scope needs another review. Follow [Reviewing and confirming](https://docs.rawthoughts.in/gazette/releasing#reviewing-and-confirming) with the person responsible for each site. [Signed authorisation](https://docs.rawthoughts.in/gazette/releasing#optional-signed-authorization) is optional; a local preview supplies no permission to publish.

<a id="check-the-destination-then-the-served-page"></a>

## Check the destination, then the served page

A successful push tells you that Git accepted a change. GitHub Pages or Mintlify may still need to build and serve it. Read back the destination, then open the public page and follow the changed reading path. Check every selected site; one working destination tells you nothing about whether another still serves an older result.

Keep those observations separate. If the remote holds the expected commit but the page is old, investigate the hosting build and delivery. If the push response was lost, first establish what the remote received. Repeating the push on the assumption that nothing happened would make the uncertainty harder to resolve.

The developer guide describes [reading back and settling a release](https://docs.rawthoughts.in/gazette/releasing#reading-back-and-settling), including the separate observations of the host build and served output. If those observations cannot settle what happened, stop and reconcile the recorded attempt before trying again.

<a id="continue-from-a-known-result"></a>

## Continue from a known result

If the released page needs a correction, identify the result to replace and prepare the change for review. If an earlier publication needs restoring, inspect what is available to restore and obtain the publisher’s approval for that result. Rebuilding old source may produce something different when its dependencies have changed; inspect it before treating it as the old publication.

Your local preview remains a place to experiment. At release, the practical question is more specific: did readers receive the connected work the publisher approved? The reviewed output, the destination’s state and the served pages let you answer it.


Reading path: [Gazette](https://rawthoughts.in/gazette/) > [Review a publication before release](https://rawthoughts.in/gazette/review-a-publication/)
