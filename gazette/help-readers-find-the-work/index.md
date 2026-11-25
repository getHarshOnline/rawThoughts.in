Title: Search, feeds and discovery

[Read HTML](https://rawthoughts.in/gazette/help-readers-find-the-work/)

Rights holder: RawThoughts Enterprises Private Limited

<a id="search-feeds-and-discovery"></a>

# Search, feeds and discovery

An article reached through search should make the same claim as the page a reader opens. Gazette derives the page, search record and structured data from the same title, description and relationships, so you can correct the writing in one place. Each output still has its own selection: a feed of published articles can omit a draft that appears in your local preview.

Add a sitemap, search data and structured data to [Field Notes](https://rawthoughts.in/gazette/first-publication/), then check them against the article a reader sees. You can also add a feed for new articles. The starter theme has no search box. This guide builds the data a search interface would use.

<a id="choose-the-outputs"></a>

## Choose the outputs

In `gazette.toml`, find the `[[brands.publications]]` block for `site:field-notes`. Add this table before the next brand or publication. If `machine` already exists for that site, add the entries to that table.

```toml
[brands.publications.machine]
sitemap = true
json_ld = true
search = { language = 'lexical', fields = ['title', 'description', 'body', 'keywords'] }
markdown_alternates = { enabled = true, directory_page = 'index.md', file_page = 'append-md', media_type = 'text/markdown', discovery_rel = 'alternate' }
llms = { enabled = true, coverage = 'all-pages', description_from = 'content:field-notes', representation = 'markdown-alternate', include_human_link = true }
```

| Output | What a reader or tool receives |
| --- | --- |
| `sitemap.xml` | The publication's canonical page addresses |
| `search.json` | Page records and the text fields enabled for search |
| `site.jsonld` | Structured descriptions of the pages and their declared relationships |
| Markdown counterparts | A Markdown representation beside each canonical page |
| `llms.txt` | A reading guide linking to those Markdown counterparts and, here, their HTML pages |

`description_from` uses the collection's description to introduce `llms.txt`. `all-pages` lists all eligible pages from the build. Give each included article a description a reader can use.

The `lexical` search profile indexes the listed fields without reducing words to English stems. Use `english` if you want English stemming. Choose the profile yourself. Neither detects the language.

<a id="inspect-the-result-in-your-preview"></a>

## Inspect the result in your preview

Stop the preview with **Ctrl+D** and restart it to load `gazette.toml`. If your current request includes the workbook, keep `--listen site:workbook=127.0.0.1:0` as well. Keep the math request if you enabled it.

```sh
cat "$GAZETTE_REQUEST" - | "$GAZETTE" preview-sites \
  --local --allow-listeners --local-urls --watch \
  --listen site:field-notes=127.0.0.1:0
```

Use the new Field Notes URL from the `ready` event.

1. Open `/search.json` and `/llms.txt`. Find the collection and both notes. For the first note's Markdown, open `/keep-the-context/index.md` or append `index.md` to its current journey address.
2. Open `/sitemap.xml` and follow one page address. `--local-urls` makes it open this preview. A regular build uses the configured public address. Replace `https://field-notes.example/` before publishing your own site.
3. Open `/site.jsonld` for the site-wide data. In the first article's page source, find `application/ld+json`. It should describe the same article and title. The starter embeds this data when you enable `json_ld`.
4. Edit the first note's description in `content/keep-the-context/index.md`. Save and refresh `search.json` after the rebuild. The entry should show the new description. An edit to the article body also changes its search text and Markdown counterpart.

Keep one main heading for the article and make it agree with the declared title. Use second- and third-level headings to develop the argument. The title supplies the article’s `name` and `headline` in structured data; the description supplies its `description`. Author, publisher and dates come from their own declarations. A heading cannot supply a missing author or publication date. Inspect these fields beside the rendered page so a machine receives the same claim a person reads.

**Warning**

**Discovery settings do not make a page private.** The local files include drafts. Check what your public build includes. Hiding a page from discovery leaves it accessible by URL if you still publish it.

<a id="add-a-feed-when-there-are-updates-to-follow"></a>

## Add a feed when there are updates to follow

Add a JSON Feed for dated, published articles. Put these tables in the Field Notes publication block before the next brand or publication:

```toml
[brands.publications.machine.feeds]
identity_base = 'https://field-notes.example/'
selection = { kind = 'articles', residence = 'all', lifecycle = ['published'], require_published_date = true }
omit_when_empty = true

[[brands.publications.machine.feeds.channels]]
id = 'feed:notes'
channel = 'content:field-notes'
path = '/updates.json'
format = 'json'
```

Restart the preview. `/updates.json` stays absent while the starter's articles are undated drafts because `omit_when_empty` is on. To add an eligible article, set `lifecycle` to `published` and put its publication date inside `[content]`. For example, `published = '2026-11-09'` means November 9, 2026. Save and wait for the rebuild, then open `/updates.json` and check for that article. This change only affects the local build.

Use a domain you control for `identity_base` and keep it stable. See the [feed format requirements](https://docs.rawthoughts.in/gazette/feeds) for Atom, RSS and JSON Feed. Atom needs named authors and modification timestamps. If you know only a calendar date, leave the time unspecified rather than using midnight as a guess.

<a id="check-the-reading-experience-as-well-as-the-files"></a>

## Check the reading experience as well as the files

Open an article directly and check that its title, description and opening explain what the reader found. Use keywords that describe the work. Search and answer systems decide for themselves what to index, rank and cite.

Try a missing page such as `/a-note-that-does-not-exist/` in the local preview. Gazette returns a 404 recovery page with a link home when the Home page was built, and a Search link when that page was built. Field Notes has no Search page. This lets you check the local recovery experience; the eventual host needs its own missing-page handling.

A theme can compose the publication’s home-page sharing card from its landing visual and H1, using an existing image or a frame from its film. Base includes the generated image in the page’s initial sharing metadata. Follow the [theme recipe](https://docs.rawthoughts.in/gazette/theme-reference#publication-home-social-card-recipe) and [local renderer setup](https://docs.rawthoughts.in/gazette/workspace#social-card-renderer); capture must be explicitly enabled when building.

An existing PNG or JPEG selected through `identity_assets.link_preview` takes precedence over generation. Keep that resource selected for the site. The generated recipe covers the publication’s home, not every article. The Field Notes starter has no sharing-card recipe; use a theme that supplies one, or configure an [existing preview image](https://docs.rawthoughts.in/gazette/workspace-discovery#machine-readable-publication-outputs) with a theme that presents it.

Before publishing, set the publisher’s crawler policy and inspect the generated `robots.txt` alongside the public sitemap and included pages. The [deployment guide](https://docs.rawthoughts.in/gazette/deployment-output#crawler-policy) explains workspace defaults and per-site overrides. Crawler rules request how bots use the site; they do not make a page private. Follow [Review and export a publication](https://rawthoughts.in/gazette/review-and-deliver/) to check what the build actually contains before handing it to the publisher.

If you are adding a search interface, see the [search record format](https://docs.rawthoughts.in/gazette/render-outputs#search-documents). For a theme integration, see [discovery files](https://docs.rawthoughts.in/gazette/render-outputs#site-discovery-outputs) and [embed page JSON-LD](https://docs.rawthoughts.in/gazette/json-ld#rendering-scope-and-failure).


Reading path: [Gazette](https://rawthoughts.in/gazette/) > [Search, feeds and discovery](https://rawthoughts.in/gazette/help-readers-find-the-work/)


Source code for [Gazette](https://github.com/getHarshOnline/gazette) is credited to [Harsh Joshi](https://getharsh.in/about/).
