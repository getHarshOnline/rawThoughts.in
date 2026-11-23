Title: Typeset mathematics

[Read HTML](https://rawthoughts.in/gazette/typeset-mathematics/)

Rights holder: RawThoughts Enterprises Private Limited

<a id="typeset-mathematics"></a>

# Typeset mathematics

Add an inline equation and a displayed fraction to [Field Notes](https://rawthoughts.in/gazette/first-publication/).

**Important**

**You need Python 3, Node 20 or later, and `GAZETTE` and `GAZETTE_SOURCE` from the starter setup.** Gazette includes KaTeX in `adapters/math/`. It runs locally without an npm install or a typesetting service.

<a id="select-the-local-interpreter-and-producer"></a>

## Choose the Node executable

Stop the preview. In your `gazette-notes` directory, check which Node executable your shell uses:

```sh
node --version
export GAZETTE_MATH_NODE="$(node -p 'process.execPath')"
```

Run the setup with the source checkout you built and the request you last used. It creates two files and leaves existing files alone:

```sh
python3 "$GAZETTE_SOURCE/examples/first-publication/configure_math.py" \
  --gazette-source "$GAZETTE_SOURCE" \
  --request "$GAZETTE_REQUEST" \
  --node "$GAZETTE_MATH_NODE"
```

`math-runtime.toml` records the executable and renderer. `preview-math-request.json` keeps your current sites and enables math, with limits of 32 expressions, 64 KiB input, ten seconds and 1 MiB output.

<a id="enable-math-for-this-content-source"></a>

## Enable math for this content source

In `gazette.toml`, add this at the very beginning, before `[composition]`:

```toml
includes = ['math-runtime.toml']
```

If `includes` already exists, add `math-runtime.toml` to the existing array. Keep the settings file beside `gazette.toml`.

In the Field Notes publication's existing `authored` array, find the record whose `source` is `source:field-notes` and whose `target` is `content`. Set `markdown_profile = 'publication-math'` inside that record. For the original, single-source starter, the complete array then reads:

```toml
authored = [{ source = 'source:field-notes', target = 'content', markdown_profile = 'publication-math' }]
```

Keep the other settings and source entries. This profile applies to Markdown in this source, including Markdown in attached notebooks. It leaves other sources alone and does not run notebook code.

<a id="write-and-preview-the-calculation"></a>

## Write and preview the calculation

Use the equation to support the note's explanation; readers still need to know what was counted and under which conditions. Add this section to `content/keep-the-context/index.md`, after its existing text:

````markdown
## A count over a fixed interval

For a fixed observation window, the mean rate is $r = n/t$.

```math
r = \frac{n}{t}
```

Here, n is the count and t is the duration. State the duration's unit beside the calculation.
````

Save the article. Start a preview using the new single-line request:

```sh
export GAZETTE_REQUEST="$GAZETTE_PUBLICATION/preview-math-request.json"
cat "$GAZETTE_REQUEST" - | "$GAZETTE" preview-sites \
  --local --allow-listeners --local-urls --watch \
  --listen site:field-notes=127.0.0.1:0
```

If your request also includes the workbook, add `--listen site:workbook=127.0.0.1:0`. When Gazette reports `ready`, open the URL for `site:field-notes`, then open your first note. Look for the inline equation and a displayed fraction with n above t. Gazette writes MathML into the article, so this theme needs no extra component or browser script for the example.

Keep using the math request as you edit. Save, wait for the rebuild and refresh the tab. Press **Ctrl+D** to stop the preview. Restart it after changing the workspace, Node or the renderer.

<a id="correct-the-particular-failure"></a>

## Correct the particular failure

| What happens | What to check |
| --- | --- |
| Dollar expressions remain ordinary text | Check that the article's source uses `publication-math`, then restart the preview |
| Preview refuses the request before rendering | Keep `preview-math-request.json` as the single compact JSON line generated above; preview reads its initial request from one line |
| Gazette reports a different Node executable | [Update the math renderer](https://rawthoughts.in/gazette/update-math-renderer/) to use the intended Node version |
| Typesetting fails | Check the TeX expression and the renderer files. Gazette stops if the renderer rejects a command |
| Gazette reports a formula, time or size limit | Check the files in that source before raising the limit |

Use backticks to show dollar expressions as text. See [supported math notation](https://docs.rawthoughts.in/gazette/markdown) or [configure a renderer](https://docs.rawthoughts.in/gazette/local-rendering#select-native-math-or-diagram-generation) for another setup. You can also [add a figure or notebook](https://rawthoughts.in/gazette/figures-notes-and-math/) to the same article.


Reading path: [Gazette](https://rawthoughts.in/gazette/) > [Typeset mathematics](https://rawthoughts.in/gazette/typeset-mathematics/)
