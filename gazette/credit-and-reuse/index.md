Title: Authorship, citation and reuse

[Read HTML](https://rawthoughts.in/gazette/credit-and-reuse/)

Rights holder: RawThoughts Enterprises Private Limited

<a id="authorship-citation-and-reuse"></a>

# Authorship, citation and reuse

Add a byline, citation and content licence to the first [Field Notes](https://rawthoughts.in/gazette/first-publication/) article, `content/keep-the-context/index.md`. Use its current title and address if you changed them in an earlier guide.

These fields answer different questions:

| You want to | Use |
| --- | --- |
| Credit the writer | An `author` attribution |
| Identify the copyright holder | A `rights-holder` attribution |
| Give readers a citation for this article | `citation` |
| Cite another work in your argument | A link or footnote in the article |
| State the article's reuse terms | `license` with the content licence's URL |

<a id="credit-the-writer"></a>

## Credit the writer

The starter already credits `owner:field-notes` as the article's author. In `gazette.toml`, find that principal and add your display name:

```toml
[[principals]]
id = 'owner:field-notes'
kind = 'person'
name = 'Your name'
```

Replace `Your name` with the byline name. Edit the existing `owner:field-notes` entry and keep its key. The key points to the same person even if you change the name later.

In the article's existing `[content]` table, keep its attribution:

```toml
attributions = [{ principal = 'owner:field-notes', role = 'author' }]
```

For several writers, declare each in the workspace and list their attributions in byline order. To credit a different copyright holder, declare them and give them the `rights-holder` role. If the writer also holds copyright, use their key for both roles. Enter the article's own credits. Gazette cannot fill in a missing author from the publisher or collection.

Restart the preview. Your name should appear under the heading. A named rights holder appears below the article. These credits also reach [structured data](https://rawthoughts.in/gazette/help-readers-find-the-work/).

<a id="supply-a-citation-for-the-article"></a>

## Supply a citation for the article

Write the citation readers should use. At the end of the article's frontmatter, before the closing `+++`, add:

```toml
[content.citation]
text = 'Keep the observation with its context. Field Notes. https://field-notes.example/keep-the-context/'
```

For your own publication, use the article's current title, public address and any real author or date details. Gazette displays the citation as you wrote it. If the title or address changes, update the citation too. Save and refresh after the rebuild, then open **Cite this article** to see it.

To offer a BibTeX download, save this as `content/keep-the-context/reference.bib`, adjusting the title and public address to the article you are publishing:

```bibtex
@misc{field_notes_context,
  title = {Keep the observation with its context},
  url = {https://field-notes.example/keep-the-context/}
}
```

Add `bibtex = 'reference.bib'` inside `[content.citation]`. After the rebuild, use **Cite this article → Download BibTeX** to check the file. This download works without `static_assets`. For a named format or a PDF, see [citation downloads](https://docs.rawthoughts.in/gazette/content-model#authored-citation-and-downloads). To cite work you used, put the reference in the body or in a [footnote](https://rawthoughts.in/gazette/figures-notes-and-math/#add-a-short-note-where-it-matters).

<a id="record-the-content-licence"></a>

## Record the content licence

Once the owner has chosen the article's reuse terms, record the licence's actual URL in the article's `[content]` table, above any `[content.citation]` table:

```toml
license = 'https://your-site.example/licenses/writing/'
```

**Important**

**Use the URL of the terms that apply to the article.** Leave `license` out if none were declared. The article has its own licence, independent of the collection, theme or Gazette's software.

Save and refresh. **Content licence** appears beneath the citation and Notes. Follow it to check the terms. Gazette also adds that URL to structured data. Confirm that you can publish any work you reuse, and put its required credit beside it. For example, use `Image: [creator's name], [work title], used under [licence](the-actual-licence-url).` The article's licence leaves the image's own terms in place.

See the [licence field rules](https://docs.rawthoughts.in/gazette/content-model#explicit-content-licence) or [Review and export a publication](https://rawthoughts.in/gazette/review-and-deliver/).


Reading path: [Gazette](https://rawthoughts.in/gazette/) > [Authorship, citation and reuse](https://rawthoughts.in/gazette/credit-and-reuse/)


Source code for [Gazette](https://github.com/getHarshOnline/gazette) is credited to [Harsh Joshi](https://getharsh.in/about/).
