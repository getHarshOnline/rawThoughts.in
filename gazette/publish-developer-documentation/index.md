Title: Publish developer documentation

[Read HTML](https://rawthoughts.in/gazette/publish-developer-documentation/)

Rights holder: RawThoughts Enterprises Private Limited

<a id="publish-developer-documentation"></a>

# Publish developer documentation

Open a repository guide in Mintlify, then follow a link from Field Notes to that guide and back. Keep editing product help in your publication and developer guides in the code repository.

<a id="configure-the-documentation-site"></a>

## Configure the documentation site

Start with [your Field Notes publication](https://rawthoughts.in/gazette/first-publication/). Follow [Add a manual to Field Notes](https://docs.rawthoughts.in/gazette/mintlify#configured-local-assembly). Return here when your publication has the **Notes tooling** guide and the settings check passes.

The sample guide links back to `https://field-notes.example/keep-the-context/`. If you moved the note into a journey, update that link in the guide before you assemble it.

<a id="build-and-open-the-preview"></a>

## Build and open the preview

This walkthrough uses port `3908` for Field Notes and `3909` for Mintlify. You will restart Field Notes on `3908` in the next section. If either port is in use, choose another and change the corresponding map and listener below.

Leave your Field Notes terminal open. In a second terminal, [restore the Gazette and publication paths](https://rawthoughts.in/gazette/first-publication/#stop-and-continue-later), then run this in the Field Notes directory. Replace `/absolute/path/to/your/publication` with its full path:

```sh
mkdir -p "$HOME/gazette-doc-builds"
"$GAZETTE" assemble-docs --local --workspace-json --site site:field-notes \
  --output-parent "$HOME/gazette-doc-builds" \
  --preview-link-bases-json '{"https://field-notes.example/":"http://127.0.0.1:3908/"}' <<'JSON'
{"kind":"local","root":"/absolute/path/to/your/publication","workspace":"gazette.toml"}
JSON
```

Open the `directory` printed in the result and start [Mintlify’s CLI](https://www.mintlify.com/docs/cli/install):

```sh
cd /directory/printed/in/the/result
npx mint dev --classic --port 3909 --no-open --telemetry=false
```

Open the address Mintlify prints. In the sidebar, choose **Build an integration → Notes tooling**. If you edit the original guide, assemble again and start Mintlify from the new output folder.

<a id="follow-links-between-the-two-previews"></a>

## Follow links between the two previews

In the first Field Notes article, add `[Developer guide](https://docs.field-notes.example/notes-tool/overview)`. If you chose a different address for the guide, use it in this link.

Keep the Mintlify terminal running. In the Field Notes terminal, press **Ctrl+D** to stop the earlier preview, then restart it on the port you put in the Mintlify build's map. In this command, use the address Mintlify reported. The example uses IPv6 (`http://[::1]:3909/`). If it listens on IPv4, use `http://127.0.0.1:3909/`.

```sh
cat "$GAZETTE_REQUEST" - | "$GAZETTE" preview-sites --local --allow-listeners --local-urls --watch \
  --listen site:field-notes=127.0.0.1:3908 \
  --preview-link-bases-json '{"https://docs.field-notes.example/":"http://[::1]:3909/"}'
```

If your current request also includes the workbook, add `--listen site:workbook=127.0.0.1:0`. Keep both previews running. Open the note in Field Notes, follow **Developer guide**, then follow **Return to the note** in Mintlify. If either link opens an `.example` host, check the map on the build that produced that link.

Use your own public domains for another project. Leave the public links in the sources. Omit the two preview maps when you build for public addresses. To include API reference from your code, see [Run a documentation generator](https://docs.rawthoughts.in/gazette/documentation-generators).


Reading path: [Gazette](https://rawthoughts.in/gazette/) > [Publish developer documentation](https://rawthoughts.in/gazette/publish-developer-documentation/)
