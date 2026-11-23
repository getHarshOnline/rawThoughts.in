Title: Your first publication

[Read HTML](https://rawthoughts.in/gazette/first-publication/)

Rights holder: RawThoughts Enterprises Private Limited

<a id="your-first-publication"></a>

# Your first publication

Start **Field Notes**, a small site with two articles. Edit the first in Markdown, then open the result in your browser. You can keep the site and continue writing when you finish.

<a id="before-you-start"></a>

## Before you start

**Important**

**You need Python 3 and a local Gazette executable.** If you need to build it, follow [Build Gazette from source](https://docs.rawthoughts.in/gazette/install#what-a-build-needs). Keep the terminal where you set `GAZETTE_SOURCE`, your checkout of Gazette's own code, and `GAZETTE`, the executable.

<a id="start-the-publication"></a>

## Start the publication

Create your publication in a new folder:

```sh
export GAZETTE_PUBLICATION="$HOME/gazette-notes"
cd "$GAZETTE_SOURCE"
python3 examples/first-publication/create.py "$GAZETTE_PUBLICATION"
cd "$GAZETTE_PUBLICATION"
export GAZETTE_REQUEST="$GAZETTE_PUBLICATION/preview-request.json"
```

Choose another folder if `gazette-notes` already exists. The script leaves existing folders alone. Your articles are in `content/`, a **source**: a folder the workspace declares as holding writing. `gazette.toml` is the **workspace**, the configuration Gazette reads, and it connects that source to the theme. `preview-request.json` tells Gazette which site to open. These guides call the folder holding all three your publication folder.

Start the preview:

```sh
cat "$GAZETTE_REQUEST" - | "$GAZETTE" preview-sites \
  --local --allow-listeners --local-urls --watch \
  --listen site:field-notes=127.0.0.1:0
```

Keep the terminal open. When Gazette reports `ready`, open the `url` for `site:field-notes`. It will look like this, with a port chosen for your session:

```text
"url":"http://127.0.0.1:3908/"
```

On the **Field Notes** home page, open **Keep the observation with its context**.

<a id="make-your-first-edit"></a>

## Make your first edit

Open the new `gazette-notes` folder in your editor, then open `content/keep-the-context/index.md`.

The block between `+++` markers describes the article. Update its `title` and `description` inside `[content]`. Use your own note, or try this example:

```toml
title = 'After the rain'
description = 'Which garden paths stayed wet after an overnight shower.'
```

Replace the heading and text after the closing `+++` with:

```markdown
# After the rain

The path under the apple tree was still wet at noon. The open path beside the shed had already dried. I will check both again after the next shower.

[[id:content:review-a-note|Read the next note]].
```

Save and wait for the terminal to report a successful rebuild, then refresh. You should see **After the rain** and your new observation. Follow **Read the next note** to open the second article, then choose **Field Notes** in the header. The home page should show the new title and description.

Your article still lives at `/keep-the-context/`, its address on the site. You changed its title, leaving its slug and place in the home collection intact. The link to the second note uses that note’s identity, so Gazette can still find it if its address changes later. [Articles, collections and journeys](https://rawthoughts.in/gazette/organize-your-writing/) follows those changes through a larger publication.

<a id="stop-and-continue-later"></a>

## Stop and continue later

Press **Ctrl+D** in the preview terminal to stop. To resume there, run the preview command again.

In a new terminal, open your Gazette checkout and repeat the variable assignments in the [build setup](https://docs.rawthoughts.in/gazette/install#what-a-build-needs). You can reuse the executable you built. Then set your publication paths:

```sh
export GAZETTE_PUBLICATION="$HOME/gazette-notes"
export GAZETTE_REQUEST="$GAZETTE_PUBLICATION/preview-request.json"
cd "$GAZETTE_PUBLICATION"
```

Use the folder and request file you last previewed. Run the preview command and open the newly reported URL.

<a id="recover-from-a-writing-error"></a>

## If your edit does not appear

If the terminal reports a failed rebuild, fix the error it names, save and refresh. Gazette serves the last good build in the meantime. Restart the preview after editing `gazette.toml`.

Next, [Write in VS Code](https://rawthoughts.in/gazette/write-with-feedback/) or [Articles, collections and journeys](https://rawthoughts.in/gazette/organize-your-writing/).


Reading path: [Gazette](https://rawthoughts.in/gazette/) > [Your first publication](https://rawthoughts.in/gazette/first-publication/)
