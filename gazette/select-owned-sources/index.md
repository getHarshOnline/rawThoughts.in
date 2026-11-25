Title: Select content sources

[Read HTML](https://rawthoughts.in/gazette/select-owned-sources/)

Rights holder: RawThoughts Enterprises Private Limited

<a id="select-content-sources"></a>

# Select content sources

Move the second [Field Notes](https://rawthoughts.in/gazette/first-publication/) article into a `research/` folder. Readers can still find it in the same collection and at the same address. The same setup lets you publish a note from a separate project without copying it into this one; [Why an article has one home](https://rawthoughts.in/gazette/why-an-article-has-one-home/) explains how its reading paths can change while the article stays together.

<a id="give-the-second-note-its-own-source"></a>

## Give the second note its own source

Stop the preview. From your publication directory:

```sh
cd "$GAZETTE_PUBLICATION"
mkdir research
mv content/review-a-note research/
pwd -P
```

Use the directory printed by `pwd -P` plus `/research` as the new source path.

In `gazette.toml`, add the research binding to the existing publication's `authored` array. For an unchanged starter, the result is:

```toml
authored = [
  { source = 'source:field-notes', target = 'content' },
  { source = 'source:research-notes', target = 'research' }
]
```

Keep the options on your existing source records. If the moved note uses figures or math, give its new source the same `static_assets` or `markdown_profile` settings it needs.

Add the new source declaration, substituting the actual absolute path:

```toml
[[sources]]
id = 'source:research-notes'
location = { kind = 'filesystem', root = '/absolute/path/to/gazette-notes/research' }
```

Write the full path in TOML. Gazette does not expand `$HOME`. `target` names the folder within the build input. Keep the note’s identity, slug and membership as they are. Its new source is bound to the same publication, so the address stays the same. The first note’s `[[id:content:review-a-note|Read the next note]]` link still reaches it, including if you already placed it in a journey.

<a id="read-the-result"></a>

## Read the result

Restart with your current command and `GAZETTE_REQUEST`. Keep `preview-math-request.json` if you enabled math. In the preview, follow the first note into **Review a note before drawing a conclusion**. It should open at the same address, now built from `research/review-a-note/index.md`.

In the current Field Notes starter, open `research/review-a-note/index.md` in the Gazette-enabled VS Code window. The editor discovers it from the source you added to `gazette.toml`; there is no per-page list to update. If feedback is missing, follow [the editor recovery steps](https://rawthoughts.in/gazette/write-with-feedback/#if-feedback-is-missing). An older workspace using explicit file lists still needs its old entry replaced with the new path; follow the same guide before changing that discovery mode.

<a id="choose-a-source-deliberately"></a>

## Choose a source deliberately

**Important**

**Point each source at material you mean to include.** Use [filesystem exclusions](https://docs.rawthoughts.in/gazette/workspace-sources#explicit-filesystem-exclusions) for unrelated files. To build from a fixed revision, see the [Git source options](https://docs.rawthoughts.in/gazette/workspace-sources#publication-acquisition). Before delivery, check the pages and resources the build will expose.

With the sources in place, [Articles, collections and journeys](https://rawthoughts.in/gazette/organize-your-writing/) shows how to choose how the pieces read together.


Reading path: [Gazette](https://rawthoughts.in/gazette/) > [Select content sources](https://rawthoughts.in/gazette/select-owned-sources/)


Source code for [Gazette](https://github.com/getHarshOnline/gazette) is credited to [Harsh Joshi](https://getharsh.in/about/).
