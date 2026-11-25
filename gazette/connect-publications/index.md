Title: Connect publications

[Read HTML](https://rawthoughts.in/gazette/connect-publications/)

Rights holder: RawThoughts Enterprises Private Limited

<a id="connect-publications"></a>

# Connect publications

Give readers a way from a [Field Notes](https://rawthoughts.in/gazette/first-publication/) article to a separate workbook and back. Both sites will run on your machine. If you moved the first note into a journey, use its current address in the example below.

<a id="add-the-workbook-source-and-publication"></a>

## Add the workbook source and publication

Stop the preview. In your publication directory, create `workbook/index.md`:

```markdown
+++
[content]
id = 'content:field-notes-workbook'
site = 'site:workbook'
title = 'The Field Notes workbook'
description = 'Bring an observation into the next question you want to explore.'
lifecycle = 'draft'
language = 'en'
route = { path = '/' }
attributions = [{ principal = 'owner:field-notes', role = 'author' }]
structure = { kind = 'page', family = { kind = 'article' } }
+++

# The Field Notes workbook

Begin with an observation whose context you can still explain. [[site:field-notes.example/keep-the-context/|Keep the observation with its context]] supplies the starting note; this workbook gives it another reason to be read.
```

Append these tables to `gazette.toml`, replacing the source root with the actual absolute path to your new `workbook` folder:

```toml
[[sites]]
id = 'site:workbook'
publisher = 'owner:field-notes'
deployable = false

[sites.composition]
page_templates = { 'content:field-notes-workbook' = 'field-notes/reading.html' }

[[brands.publications]]
site = 'site:workbook'
public_base_url = 'https://workbook.example/'
authored = [{ source = 'source:workbook', target = 'workbook' }]

[[sources]]
id = 'source:workbook'
location = { kind = 'filesystem', root = '/absolute/path/to/gazette-notes/workbook' }
```

The workbook uses the existing publisher and the theme's reading template. Each publication can use its own theme without changing the other site's articles.

In `content/keep-the-context/index.md`, add the return reference where it helps your reader:

```markdown
Continue in [[site:workbook.example/|the Field Notes workbook]].
```

This link gives readers another path to the work. Both pages keep their own addresses and memberships.

<a id="preview-both-sides-of-the-crossing"></a>

## Preview both sides of the crossing

Open the request named by `GAZETTE_REQUEST`. Replace `sites` with the two entries below. Keep the workspace and other settings, including `math_generation` if you enabled it:

```json
"sites": [
  {"site": "site:field-notes", "model_output": "model.json"},
  {"site": "site:workbook", "model_output": "model.json"}
]
```

Save the complete JSON request on one line. Preview reads the first line as its request.

Start with an explicit listener for each publication:

```sh
cat "$GAZETTE_REQUEST" - | "$GAZETTE" preview-sites \
  --local --allow-listeners --local-urls --watch \
  --listen site:field-notes=127.0.0.1:0 \
  --listen site:workbook=127.0.0.1:0
```

Use the two URLs Gazette reports. Open the first note, follow the workbook link and then follow **Keep the observation with its context** back. The workbook should use the reading template. The port numbers belong to this preview. Leave them out of the articles. A link to a configured site outside the request keeps that site's public address.

<a id="keep-the-public-destinations-in-the-sources"></a>

## Keep the public destinations in the sources

**Important**

**The `.example` hosts are placeholders.** The preview resolves them to the two local sites. A regular build uses the public addresses in `gazette.toml`. Set and verify your own addresses before delivery.

Field Notes shows the change of address and a different reading template. A theme can style cross-site links using the [destination information Gazette supplies](https://docs.rawthoughts.in/gazette/links-and-crossings). To link to a separate Mintlify site, see [Publish developer documentation](https://rawthoughts.in/gazette/publish-developer-documentation/).

[From one site to many](https://rawthoughts.in/gazette/from-one-site-to-many/) connects this starter to the publications you are reading, with writing, configuration and each site’s design kept distinct.


Reading path: [Gazette](https://rawthoughts.in/gazette/) > [Connect publications](https://rawthoughts.in/gazette/connect-publications/)


Source code for [Gazette](https://github.com/getHarshOnline/gazette) is credited to [Harsh Joshi](https://getharsh.in/about/).
