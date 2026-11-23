Title: Review and export a publication

[Read HTML](https://rawthoughts.in/gazette/review-and-deliver/)

Rights holder: RawThoughts Enterprises Private Limited

<a id="review-and-export-a-publication"></a>

# Review and export a publication

Read your [Field Notes publication](https://rawthoughts.in/gazette/first-publication/) as a visitor, then export the HTML and assets to a fresh folder. You can do both locally. The starter contains drafts and is set up for local use only.

<a id="read-the-publication-as-someone-arriving-for-the-first-time"></a>

## Read the publication as someone arriving for the first time

Open the URL Gazette reported for this preview.

1. From the home page, open each note and follow its links. Then open a note directly in a new tab. Check that its opening makes sense without the home page.
2. Read the page in a narrow window. Open its figures, equations and Notes. If your theme offers light, dark or reduced-motion settings, try the ones your readers will use.
3. If you changed a title, look for it in the article, the collection and your [discovery files](https://rawthoughts.in/gazette/help-readers-find-the-work/). If you [connected another publication](https://rawthoughts.in/gazette/connect-publications/), follow both directions.

<a id="decide-which-edition-you-are-reviewing"></a>

## Decide which edition you are reviewing

Each page declares its own `lifecycle` in `[content]`:

| State | What it means for your review |
| --- | --- |
| `draft` | Work still being prepared. You can read it in the local preview; a release candidate cannot include it. |
| `published` | Work marked for publication. It still needs to be selected for the release and approved by its publisher. |
| `archived` | Earlier work retained as an archive. It can remain available when deliberately included in a release. |

These values do not upload or delete files. A local export can contain all three states, so do not treat everything in its output folder as approved for public delivery. [Search and feed selections](https://rawthoughts.in/gazette/help-readers-find-the-work/) separately determine which pages appear in those reading paths; omitting a page from a feed does not make its address private.

<a id="review-a-collection-or-journey-together"></a>

## Review a collection or journey together

Read the collection's introduction alongside the articles you intend to release. Changing the introduction's state does not change the states of its articles. Check their links, Notes and required resources as part of the same selection.

For the [Field Notes journey](https://rawthoughts.in/gazette/organize-your-writing/), both the observation and interpretation steps need to be ready. A release candidate cannot silently omit one step or change their order. If the second step is still a draft, finish it or hold the journey; a successful preview of the first step does not establish a complete reading sequence. The [release guide](https://docs.rawthoughts.in/gazette/releasing#closed-candidates) explains how Gazette checks the selected pages and their dependencies.

<a id="retain-a-local-result"></a>

## Export the site files

Choose an existing output parent outside the publication's source folders. For example, create a new directory in your home folder:

```sh
mkdir "$HOME/gazette-output"
```

You can reuse that parent directory. From your publication folder, export the site with the workspace on standard input:

```sh
cd "$GAZETTE_PUBLICATION"
"$GAZETTE" render-site --local --site site:field-notes \
  --output-parent "$HOME/gazette-output" < gazette.toml
```

Gazette prints a result naming the `directory` it created, a fresh folder beneath the output parent that holds the HTML and resources. If you added the workbook, run the command again with `--site site:workbook`. The command reads `gazette.toml` alone, so it cannot follow the extra file that math adds with `includes`. If you enabled math, or prefer to work in conversation, use [Work with an agent](https://rawthoughts.in/gazette/work-with-an-agent/) and ask for an export:

> Keep a generated copy of my saved Field Notes publication in a fresh folder beneath this output parent. Keep its current settings and enabled math, use public addresses, and leave my sources, saved request and existing results unchanged. Tell me where the files were written or why the export failed.

Give the agent the saved request path and the full path to the output parent. The `stage_rendered_site` tool exports one publication per call, so ask for the workbook separately. For client integration, see [the tool inputs](https://docs.rawthoughts.in/gazette/mcp#fresh-source-staging).

**Note**

**The export and preview use different addresses.** Gazette reports the new folder holding the HTML and resources. Keep using the browser preview for review. The export uses the configured public addresses, including the starter's `.example` host, so opening `index.html` from disk cannot reproduce the preview's links. For using the files in another tool, see the [developer rendering guide](https://docs.rawthoughts.in/gazette/local-rendering).

<a id="prepare-a-real-publication-with-its-publisher"></a>

## Prepare a real publication with its publisher

For a public release, set up the destination and agree who can approve the publication. Gazette has pushed only to local repositories so far, so nothing it builds is live yet. The `deployable` flag alone does not set up hosting. [Review a publication before release](https://rawthoughts.in/gazette/review-a-publication/) follows the checks from the selected output to what readers receive. The [developer release guide](https://docs.rawthoughts.in/gazette/releasing) supplies the current release and recovery procedure. Once the site is public, repeat the reader checks there, including links between product help and developer docs.


Reading path: [Gazette](https://rawthoughts.in/gazette/) > [Review and export a publication](https://rawthoughts.in/gazette/review-and-deliver/)
