Title: Write in VS Code

[Read HTML](https://rawthoughts.in/gazette/write-with-feedback/)

Rights holder: RawThoughts Enterprises Private Limited

<a id="write-in-vs-code"></a>

# Write in VS Code

You reach Gazette from the editor through its language server, which gives you the same account of the publication that the command line and a connected agent use: a diagnostic on the page you are typing, and a way to jump to the source behind a result. Your agent has the same account through its own connection, [Work with an agent](https://rawthoughts.in/gazette/work-with-an-agent/).

Use VS Code to catch a mistake before it reaches your preview. Keep the [Field Notes preview](https://rawthoughts.in/gazette/first-publication/) open so you can compare the saved page with what you are typing.

<a id="open-your-publication-with-the-extension"></a>

## Open your publication with the extension

You need VS Code 1.96 or later. If you have not set up Gazette in VS Code, follow [Open the local extension from a source checkout](https://docs.rawthoughts.in/gazette/vscode#open-the-local-extension-from-a-source-checkout). Return here with the Field Notes folder open in that window.

<a id="correct-a-declaration-in-the-publication"></a>

## Change a title and repair a broken link

Open `content/keep-the-context/index.md`. If VS Code opens a preview, choose **Reopen Editor With → Text Editor**. Whatever its title is now, change it to this one:

```toml
title = 'Record the context'
```

Change the heading to match:

```markdown
# Record the context
```

Check that the new heading appears in **Outline**. Then find the link to the second note. Its label is **separate the observation from the claim** in the starter, or **Read the next note** if you followed the garden example. Change only its identity from `id:content:review-a-note` to `id:content:missing-note`, keeping the label. Open **Problems** to inspect the unresolved destination.

Open the second note, `content/review-a-note/index.md`, and find its `[content].id`: `content:review-a-note`. Restore the first note’s destination to `id:content:review-a-note`. Once the error clears, use **Open Link** or **Go to Definition** on the repaired link to open the second note's source.

If you already moved that note by following [Select content sources](https://rawthoughts.in/gazette/select-owned-sources/), look in `research/review-a-note/index.md`. Its identity remains the same when you move it into a journey or change its slug, so the repaired link can still find it.

Save the first note, wait for the preview to rebuild and refresh. The article and its collection or journey entry should now read **Record the context** at its current address. Follow the repaired link to the second note.

<a id="inspect-the-page-you-are-writing"></a>

## Inspect the page you are writing

- **Gazette: Page Details** shows where this page comes from and where it sits in the publication. Before you change a page's identity or slug, use **Find All References** on it to see what links to it; Problems reports a broken link only after the change.
- In `gazette.toml`, **Go to Definition** on `'owner:field-notes'` opens the author's declaration.
- **Gazette: Inspect Current Editor with MCP** reads unsaved text from the active editor. The ordinary preview reads your saved files. See [Work with an agent](https://rawthoughts.in/gazette/work-with-an-agent/) for the next task.

<a id="if-feedback-is-missing"></a>

## If feedback is missing

The current Field Notes starter finds its pages through `gazette.toml`. Adding or moving a page beneath `content/` requires no per-page editor list: open the page to get feedback. A file outside that folder must belong to another configured content source; opening an unrelated folder does not add its files.

Open **Output → Gazette**. Check that you trust the publication folder, **Gazette: Server Path** in User settings points to your executable, and `gazette.workspace.configuration` selects its `gazette.toml`. Check any reported configuration error and that the page belongs to a configured content source, then open the page again. For an older workspace using explicit file lists, check that its selection includes the page. After correcting the setup, use **Gazette: Restart Server** if feedback is still missing.

An older workspace may still use explicit file lists. Those keep it in that mode even when `gazette.workspace.discovery` is true. If you want automatic discovery, follow the [migration instructions](https://docs.rawthoughts.in/gazette/editor-discovery) to preserve selected content and manual support. Removing only one list can leave other explicit selections active.

If the extension never loads, return to the [local extension setup](https://docs.rawthoughts.in/gazette/vscode#open-the-local-extension-from-a-source-checkout). To integrate a different editor, see the [language server guide](https://docs.rawthoughts.in/gazette/lsp).

<a id="reopen-this-editor"></a>

## Reopen this editor

Reopen the same Gazette-enabled window or profile and the publication in `GAZETTE_PUBLICATION`. If you deleted the profile, repeat the extension setup and point it at the same files.


Reading path: [Gazette](https://rawthoughts.in/gazette/) > [Write in VS Code](https://rawthoughts.in/gazette/write-with-feedback/)


Source code for [Gazette](https://github.com/getHarshOnline/gazette) is credited to [Harsh Joshi](https://getharsh.in/about/).
