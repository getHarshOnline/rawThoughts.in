Title: Work with an agent

[Read HTML](https://rawthoughts.in/gazette/work-with-an-agent/)

Rights holder: RawThoughts Enterprises Private Limited

<a id="work-with-an-agent"></a>

# Work with an agent

An agent arrives at Gazette over a local MCP server, and one call gives it the same account of your publication that the command line and the editor use: its pages, their addresses, how they belong to collections or journeys and where each one is edited. The [VS Code extension](https://rawthoughts.in/gazette/write-with-feedback/) gives you that account as you type.

Ask your agent why a note appears where it does, then have it rename the note and check the result. Use the publication folder from [Your first publication](https://rawthoughts.in/gazette/first-publication/).

<a id="connect-the-local-server"></a>

## Connect the local server

If your agent already shows Gazette in its MCP server list, skip this step. Otherwise open a terminal in your publication directory:

```sh
cd "$GAZETTE_PUBLICATION"
```

For Codex:

```sh
codex mcp add gazette -- "$GAZETTE" mcp
```

For Claude Code:

```sh
claude mcp add --transport stdio gazette -- "$GAZETTE" mcp
```

Use `/mcp` in the terminal client to check that Gazette is connected. If you replace the Gazette executable, reconnect to use the new build. For another setup, see the [Codex connection guide](https://developers.openai.com/codex/mcp/) or [Claude Code connection guide](https://code.claude.com/docs/en/mcp#option-3-add-a-local-stdio-server). A manual configuration needs the absolute executable path and the argument `mcp` over standard input and output. Your client starts and stops the local server. This setup works without a publishing account. If you are writing your own client, [connect it to Gazette and run a first check](https://docs.rawthoughts.in/gazette/mcp-quickstart).

<a id="ask-about-the-publication-you-made"></a>

## Ask about the publication you made

Give the agent the absolute path to your `gazette-notes` directory and ask:

> Use Gazette to review `gazette.toml` in this directory for `site:field-notes`. Read its local sources. Show the pages, their current addresses, how they belong to collections or journeys, and where I edit each one. Do not change files or start a release.

If the agent needs a tool name, ask for `review_publication`. Check that the answer finds both notes and any reading paths you added. Ask it to show the first note's title and address in the source. If you moved the note into a journey, look for its current address and the old ones you kept as aliases.

<a id="make-a-bounded-change"></a>

## Make a change

> Rename the first note to “Record the context” in its declaration and heading. Keep its identity, current address, body and reading relationships. Save the change in the existing source, then inspect the publication again.

If you already chose that title in [Write in VS Code](https://rawthoughts.in/gazette/write-with-feedback/), ask for another and use it below.

A title change is safe because the identity and address stay put; a change to an identity, slug or route is not, and Gazette's check does not say what else points at the old one. Ask the agent to list the references to it with `authoring_references` before it edits. The agent edits the file and asks Gazette to check it. Review the edit, then refresh after the preview rebuilds. The new title should appear in the article and its collection or journey at the same address.

<a id="use-the-current-editor-context-when-it-matters"></a>

## Use the current editor context when it matters

If the question concerns an unsaved passage, use **Gazette: Inspect Current Editor with MCP** in the connected [editor](https://rawthoughts.in/gazette/write-with-feedback/). It shares the current editor text, including unsaved changes.

**Caution**

**To take that context to a separate client**, use **Export Current Editor Context**. The export can include your sources and unsaved writing. Share it only with the client you want to read it. Save first if you want the preview to use the same text.

<a id="ask-the-agent-to-preview-then-close-it"></a>

## Ask the agent to preview, then close it

Give the agent the current saved request path named by `GAZETTE_REQUEST`, then ask:

> Start a local preview of this saved publication, keeping its current sites and enabled math. Read its local sources, use local addresses and free loopback ports, and show me the ready address. Stop that preview when I finish and tell me if it fails to close.

Open the reported address and ask the agent to stop its preview when you finish. Your files stay where you edited them. For a client integration, see [how a preview starts and stops](https://docs.rawthoughts.in/gazette/mcp#preview-lifetime). To share a build, see [Review and export a publication](https://rawthoughts.in/gazette/review-and-deliver/).


Reading path: [Gazette](https://rawthoughts.in/gazette/) > [Work with an agent](https://rawthoughts.in/gazette/work-with-an-agent/)
