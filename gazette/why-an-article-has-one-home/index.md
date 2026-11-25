Title: Why an article has one home

[Read HTML](https://rawthoughts.in/gazette/why-an-article-has-one-home/)

Rights holder: RawThoughts Enterprises Private Limited

<a id="why-an-article-has-one-home"></a>

# Why an article has one home

An article can answer more than one reader's question without becoming several copies. The challenge is to represent its different contexts without making each context another authority over its words. Take an article about the cost of a completed inference request. A reader comparing infrastructure suppliers might encounter it in a collection about procurement. A reader learning how serving works might reach the same article after pieces on batching and latency. Its argument is unchanged, but the route through it is different.

<a id="one-placement-more-than-one-way-to-arrive"></a>

## One placement, more than one way to arrive

In Gazette's editorial model, an article has one structural placement. It can stand alone, belong directly to a collection or subcollection, or occupy a step in a journey within one of those collections. That choice says where its argument is developed, not every place where its argument might be useful.

A collection gathers work around a shared question. Subcollections give a deeper inquiry room to develop without losing its relationship to the larger one. A journey within that inquiry makes an authored reading order explicit. Membership and order have different jobs: grouping related arguments does not, by itself, tell a reader which premise comes first.

The procurement journey might begin with the workload, move to the capacity promise and end with accepted output. If our cost article belongs to that journey, a serving discussion can still refer readers to it after explaining batching and latency. The reference creates another way to arrive, not a second membership. The serving discussion can explain why the detour matters and where to resume.

That is why a journey is not just a collection sorted by date. The order carries an editorial argument. A later article can supply a premise that the reader needs first; an older article can become the final comparison. When order is meaningful, it deserves an authored decision rather than a filename convention.

An independent blog article also remains legitimate. Not every useful thought needs a series, and a collection should not exist merely to surround one short page with navigation. The structure should express the work's actual depth.

There is an example in this publication. [Serving tokens is a service problem](https://rawthoughts.in/blog/serving-tokens-is-a-service-problem/) stands alone. [Useful compute](https://rawthoughts.in/collections/useful-compute/) refers to it because request arrivals and accepted outputs affect a compute purchase. The article about [runtime portability](https://rawthoughts.in/blog/a-portable-model-needs-a-runtime/) reaches it through a different question: what happens to live memory and scheduling when the backend changes? Neither reference turns the serving article into a chapter of another container. Its argument stays at one address, while the surrounding questions give the arrival different meaning.

<a id="a-page-has-one-home"></a>

## A page has one home

Copying the article into every collection would make navigation easy at first. Later, a correction might reach one copy but not the others. Citations, discussion and publication dates could diverge. Readers would no longer know whether they were seeing the same argument. One source, one publication home and one structural placement prevent that drift. An index can list the page, another article can cite it and another journey can offer it as a detour. A correction then reaches the same argument wherever a reader arrives from, while the surrounding discussion explains why it matters in that context.

The source bundle and the published address are separate decisions too. This guide occupies `blog/one-article-several-reading-paths/index.md` in Gazette's selected content source. Its declaration names the identity `content:gazette-reading-paths`, membership in Gazette’s help and the slug `why-an-article-has-one-home`. Gazette combines that placement and slug with RawThoughts’ routing rules to derive `/gazette/why-an-article-has-one-home/`. Membership gives the page its reading context; the slug supplies its own part of the address. Both can change while the source folder stays in place. One file is enough for its argument. [Figures, notes and notebooks](https://rawthoughts.in/gazette/figures-notes-and-math/) shows a fuller bundle in the same publication: its source folder, `rich-documents/`, keeps the guide beside the notebook it displays and the small browser program that lets a reader compare image sizes:

```text
rich-documents/
  index.md
  analysis.ipynb
  compare-resources.mjs
```

| Part of the guide | Meaning |
| --- | --- |
| `index.md` | The explanation, `content:gazette-rich-documents` identity and membership in Gazette's introduction |
| `analysis.ipynb` | The saved file-size calculation, attached to that article |
| `compare-resources.mjs` | The article's optional browser comparison, compiled as a page resource |
| Workspace selection | Gazette's content source is composed into the RawThoughts publication |
| `/gazette/figures-notes-and-math/` | The guide's reader-facing address, independent of its source-folder name |

Gazette brings the saved notebook and declared resource into the same article. A reader can study the complete calculation or change the selected subset without arriving at a competing version of the guide. The controls leave the saved result intact, and the table remains readable without them. A `notes.md` companion can similarly extend an article with a longer derivation under the same identity. These files have different jobs within one authored work; their presence does not create additional articles or collection memberships.

The pattern also works across publications. A personal essay can lead into a formal treatment of a question; a technical account can lead into its economic consequences. Each publication can frame the connection in its own voice, while the destination gives the other argument room to develop. A useful crossing tells the reader what they will find there, not merely that the two pages mention similar things.

<a id="the-structure-must-reach-every-reader"></a>

## The structure must reach every reader

If the human page shows a journey but the machine-readable representation only sees isolated text, the publication tells two different stories. If search invents a relationship that the page does not declare, it creates a third. Gazette’s compiler resolves the publication once, giving navigation, search, feeds and structured data the same articles, relationships and canonical destinations to express. A theme can then give each publication a different experience without reconstructing where the argument belongs. A reader following the collection and a machine inspecting the page should encounter the same explanation of where the argument belongs.

To apply this to your own writing, choose the home in which each argument develops, put dependent explanations in a deliberate order and link to useful detours where the reader needs them. [Articles, collections and journeys](https://rawthoughts.in/gazette/organize-your-writing/) takes you through those declarations in Field Notes. Gazette can detect a missing journey member; you decide why that member belongs in the sequence.


Reading path: [Gazette](https://rawthoughts.in/gazette/) > [Why an article has one home](https://rawthoughts.in/gazette/why-an-article-has-one-home/)


Source code for [Gazette](https://github.com/getHarshOnline/gazette) is credited to [Harsh Joshi](https://getharsh.in/about/).
