Title: Articles, collections and journeys

[Read HTML](https://rawthoughts.in/gazette/organize-your-writing/)

Rights holder: RawThoughts Enterprises Private Limited

<a id="articles-collections-and-journeys"></a>

# Articles, collections and journeys

A publication's reading structure decides where each piece lives and how a reader moves between pieces. You declare it on the pages themselves, and Gazette derives the listings, reading order and next links from those declarations.

Use a collection when several pieces develop a shared question. Use a journey when reading them in a particular order helps the argument unfold: a later explanation may depend on an earlier observation, or several pieces may tell one continuing story. Shared keywords alone do not establish either relationship. A self-contained article can stand on its own, with links from the discussions it helps.

In [Field Notes](https://rawthoughts.in/gazette/first-publication/), the two starter articles can be read on their own. Add a third, then put the original two in an order that takes the reader from observing something to interpreting it. You can stop after either task.

<a id="add-an-article-to-the-collection"></a>

## Add an article to the collection

Create `content/a-new-note/index.md` in your publication with this complete page:

```markdown
+++
collections = ['content:field-notes']

[content]
id = 'content:a-new-note'
title = 'A question worth returning to'
description = 'Keep a useful question beside the observations that prompted it.'
keywords = ['field notes', 'questions', 'observation']
schema_type = 'Article'
lifecycle = 'draft'
language = 'en'
slug = 'a-new-note'
attributions = [{ principal = 'owner:field-notes', role = 'author' }]
structure = { kind = 'page', family = { kind = 'article' } }
+++

# A question worth returning to

An observation can leave a better question than the one you started with. Write that question while the details are still close enough to examine.
```

Save and refresh after the preview rebuilds. The new title should appear in the collection and open `/a-new-note/`. Gazette builds that list from `collections`. The starter selects Field Notes as its home at `/`; the article’s slug supplies `a-new-note` beneath it. If the article should stand on its own, leave that field out and link to it where it helps. A file move alone does not change its collection.

<a id="use-a-journey-when-the-order-matters"></a>

## Use a journey when the order matters

A journey belongs in a collection because the sequence develops part of that collection's question. Field Notes can keep growing through independent observations while this journey provides a particular sequence from recording an observation to interpreting it. Other articles need not join that sequence to contribute to the collection.

Stop the preview while changing the reading order. Create `content/first-reading/index.md` with the original two notes as its steps:

```markdown
+++
[content]
id = 'journey:field-notes-first-reading'
title = 'From observation to interpretation'
description = 'Record the context, then examine what the observation supports.'
lifecycle = 'draft'
language = 'en'
slug = 'first-reading'
structure = { kind = 'journey', collection = 'content:field-notes', members = [{ content = 'content:keep-the-context', primary = true }, { content = 'content:review-a-note', primary = true }] }
+++

# From observation to interpretation

Begin with the circumstances of the observation. Then ask which explanation it supports and what you would need to distinguish another explanation.
```

Remove `collections` from both notes. They now belong to the journey. Leave the new question in Field Notes as an article someone can read on its own.

Keep both notes’ identities and slugs. Their membership now gives them addresses beneath the journey: `/first-reading/keep-the-context/` and `/first-reading/review-a-note/`. You do not need to write those paths into the notes. Their existing identity links, such as `[[id:content:review-a-note|separate the observation from the claim]]`, follow the new addresses. In the current Field Notes starter, open the new journey in VS Code to get Gazette feedback; it is discovered from the configured content source. For an older setup with explicit file lists, follow [Write in VS Code](https://rawthoughts.in/gazette/write-with-feedback/).

Restart the preview with your current request and listeners. Open the journey from Field Notes and follow both steps. Check the new addresses and follow a link between the notes. Old addresses do not become redirects automatically; the later section explains how to preserve an address readers already use. Your theme controls how the steps look. Gazette uses the order in `members`.

<a id="give-a-developing-branch-its-own-subcollection"></a>

## Give a developing branch its own subcollection

If Field Notes grows beyond observation, give that subject its own branch. Create `content/observation-practice/index.md`:

```markdown
+++
[content]
id = 'content:observation-practice'
title = 'Practising observation'
description = 'Keep the circumstances of an observation separate from the explanation it invites.'
lifecycle = 'draft'
language = 'en'
slug = 'observation-practice'
attributions = [{ principal = 'owner:field-notes', role = 'author' }]
structure = { kind = 'collection', parent = 'content:field-notes' }
+++

# Practising observation

Begin with the circumstances you can describe. Return to the question when a new observation changes what you think the first one supports.
```

The `parent` makes this a subcollection of Field Notes. In the question article, change its `collections` entry to `content:observation-practice`. Set the journey's `structure.collection` to the same value. Its notes still belong to the journey, so leave `collections` off those notes.

Keep the contributions’ existing slugs. Their new placement derives these addresses:

```text
Independent question:
  /observation-practice/a-new-note/
Reading journey:
  /observation-practice/first-reading/
First journey note:
  /observation-practice/first-reading/keep-the-context/
Second journey note:
  /observation-practice/first-reading/review-a-note/
```

Keep each identity and leave its existing identity links in place. Open the new collection in the Gazette-enabled VS Code window to get feedback through the starter’s source discovery.

Restart the preview. From Field Notes, open **Practising observation**. It should offer the question and the journey. Follow the two notes and check their addresses against the paths above.

<a id="preserve-an-address-readers-already-use"></a>

## Preserve an address readers already use

The starter’s notes have only been previewed locally. If you are reorganizing published writing, keep its released addresses working. Gazette does not report a released address that a move or slug change leaves without an alias: `gazette check` passes and the address stops working without a message, so keep a list of the addresses you have released and give each moved page an alias. Inside the note’s `[content]` block, the `route` field sets its address and can redirect earlier ones. Without it, Gazette derives the address from the article's collection and slug:

```toml
# In review-a-note/index.md, after the branch change above:
route = { path = '/observation-practice/first-reading/review-a-note/', aliases = ['/review-a-note/', '/first-reading/review-a-note/'] }
```

This is an address exception: the explicit `path` takes precedence over the derived address. Keep aliases for addresses you actually released, including any earlier aliases. If you later change this note’s placement, update its explicit path too. Its identity links still name the same note.

Check each retained old address in the preview. It should redirect directly to the current one. Apply the same care to the journey and collection if readers already used their earlier addresses; [the routing reference](https://docs.rawthoughts.in/gazette/routing#explicit-address-exceptions) explains the full declaration.

<a id="keep-product-documentation-separate-from-editorial-writing"></a>

## Keep product documentation separate from editorial writing

If you are organizing product help, give its root collection a documentation purpose:

```toml
[content.structure]
kind = 'collection'
purpose = 'documentation'
```

Keep the collection’s identity, title, slug and placement. If it has an explicit address exception, retain that declaration too. Its children still join a collection or journey as usual. They can appear in search and stay out of Blog and ordinary collection listings. Order them by what a reader needs to understand or do. For architecture and code reference, [publish developer documentation separately](https://rawthoughts.in/gazette/publish-developer-documentation/).

<a id="keep-a-useful-reference-without-claiming-membership"></a>

## Keep a useful reference without claiming membership

When a piece already has a home, link to it in context. [Useful compute](https://rawthoughts.in/collections/useful-compute/) leads to the [serving article](https://rawthoughts.in/blog/serving-tokens-is-a-service-problem/) through the cost of waiting. [Runtime portability](https://rawthoughts.in/blog/a-portable-model-needs-a-runtime/) leads to the same piece through memory and scheduling. See [Why an article has one home](https://rawthoughts.in/gazette/why-an-article-has-one-home/) for that editorial example. If you are writing a theme or integration, see [membership rules](https://docs.rawthoughts.in/gazette/content-model#identity-and-relationships) and [journey navigation](https://docs.rawthoughts.in/gazette/content-model#structural-breadcrumbs-and-journey-neighbors).

Taxonomies let you classify writing across those homes. An observation term could connect a Field Notes article with a piece in another collection without moving either or putting them in a reading order. Declare the taxonomy and its terms in the workspace, then assign the relevant pairs in each page's `[content].taxonomies`. A collection's classifications do not automatically apply to its articles. The workspace can also configure term listings for readers to browse. Follow [the taxonomy declarations](https://docs.rawthoughts.in/gazette/content-model#language-and-explicit-classifications) when you need that additional way into the work.


Reading path: [Gazette](https://rawthoughts.in/gazette/) > [Articles, collections and journeys](https://rawthoughts.in/gazette/organize-your-writing/)
