Title: Figures, notes and notebooks

[Read HTML](https://rawthoughts.in/gazette/figures-notes-and-math/)

Rights holder: RawThoughts Enterprises Private Limited

<a id="figures-notes-and-notebooks"></a>

# Figures, notes and notebooks

A reader may need to see where you stood, understand a measurement’s limit or check the calculation behind your note. Add the material that answers that question: a figure, a short qualification, a longer explanation or saved working. Use the first note from [Field Notes](https://rawthoughts.in/gazette/first-publication/), `content/keep-the-context/index.md`, and keep its supporting files beside it.

The figure and note examples can be used separately. The worked calculation follows a publishing question: how much do three image files add up to? It first saves the answer in a notebook, then lets readers compare combinations in the browser. Field Notes has only your one sketch, so the calculation counts three real figures from the Causality publication, recorded on a stated date. Swap in your own figures when you have them.

<a id="put-a-figure-beside-the-observation"></a>

## Put a figure beside the observation

Choose a sketch or photo that helps explain your observation, and save it beside the article. For this example, use your own PNG and name it `context-sketch.png`, giving you `content/keep-the-context/context-sketch.png`. If you choose a JPEG, keep its real extension and use that filename in the Markdown below and in the notebook calculation later in this guide.

To give images a URL, add `static_assets` to the `source:field-notes` entry in `gazette.toml`. For the original starter, the `authored` array becomes:

```toml
authored = [{ source = 'source:field-notes', target = 'content', static_assets = { route_prefix = '/media/field-notes/' } }]
```

Edit the existing array and keep any other source entries and settings, including `markdown_profile` if you enabled math.

Add the image to `content/keep-the-context/index.md` using a path relative to that article:

```markdown
![Sketch showing the observation point and the direction of the light](context-sketch.png)

Field sketch: the position and lighting that help explain the observation.
```

Describe what the image shows in its alt text. The following paragraph supplies context and credit; it remains ordinary explanatory text. To bind that text to the image as a caption, use a theme with the [figure components described below](https://rawthoughts.in/gazette/figures-notes-and-math/#keep-an-image-and-its-caption-together). Restart the preview after changing `gazette.toml`, following [Start the publication](https://rawthoughts.in/gazette/first-publication/#start-the-publication). Open the article and check the image and explanation. If the build stops, check the filename and the `static_assets` entry.

**Warning**

**Check the whole selected source.** This setting can publish supported files anywhere under that source, even if you never link to them. Move private exports out of the source. Gazette copies the images with their dimensions and metadata intact. Prepare them before publishing and check them at the widths readers will use.

For crops or thumbnails, see [image transformations](https://docs.rawthoughts.in/gazette/page-resources#captured-image-transformations). To publish vector artwork, see [static SVG images](https://docs.rawthoughts.in/gazette/page-resources#static-svg-images). Both use resource recipes in the workspace.

<a id="use-a-diagram-when-the-relationship-is-the-point"></a>

### Use a diagram when the relationship is the point

Export a diagram as PNG or JPEG and include it as above. Put the relationship it explains in the surrounding text too. To render a `.dot` file as PNG during the build, [configure and allow a local Graphviz renderer](https://docs.rawthoughts.in/gazette/local-rendering#select-native-math-or-diagram-generation).

Field Notes uses static figures. If your theme offers an interactive figure, use its documented options and keep the explanation readable without the interaction. See [Choose a reading form](https://rawthoughts.in/gazette/change-presentation/) for using what a theme already provides.

<a id="add-a-short-note-where-it-matters"></a>

## Add a short note where it matters

A footnote keeps a brief explanation close to the sentence it qualifies. Add this to the same article:

```markdown
Keep the instrument's resolution with the reading.[^resolution]

[^resolution]: Record both the unit and the smallest increment the instrument can distinguish.
```

Save and refresh after the rebuild. Follow the numbered link to the footnote, then use the return link. Gazette numbers the footnotes you reference. Keep any condition the reader needs to understand the claim in the sentence itself.

<a id="give-a-longer-tangent-its-own-space"></a>

## Give a longer tangent its own space

For a longer derivation or worked example, create `content/keep-the-context/notes.md`. Write ordinary Markdown without frontmatter:

```markdown
# Comparing two observations

Before interpreting a difference, compare the conditions under which each note was made.

## What to keep fixed

Record the instrument, units and observation window alongside the comparison.
```

Save, then open **Notes** beneath the article. You should see **Comparing two observations**. Gazette keeps these headings and anchors within the article's Notes. There is no new page or collection entry. If you build themes, see [how article Notes reach the template](https://docs.rawthoughts.in/gazette/content-model#article-notes-stay-with-their-article).

<a id="typeset-a-calculation-when-the-publication-is-ready-for-math"></a>

## Typeset a calculation when the publication is ready for math

Follow [Typeset mathematics](https://rawthoughts.in/gazette/typeset-mathematics/) to turn on the renderer, then [add an equation to this note](https://rawthoughts.in/gazette/typeset-mathematics/#write-and-preview-the-calculation). Give the symbols and units in the surrounding text. Keep using that guide's preview request after adding a figure or notebook.

<a id="bring-saved-notebook-results-into-the-article"></a>

## Bring saved notebook results into the article

Three figures can be individually modest and still add up. The calculation below records their byte counts, combined size and each figure’s share. The notebook at the end of this guide uses actual image files from Gazette's local draft publication output of 16 November 2026; their hashes identify the versions counted. It uses only Python's standard library.

<a id="reproduce-a-saved-calculation"></a>

### Reproduce a saved calculation

Create a Python 3 notebook in an editor that saves nbformat 4.5. Copy the four cells shown at the end of this guide in order: the context, the file records, the calculation and the interpretation. Use Markdown cells for prose and code cells for the two programs. Copy the code, not its printed results. Run all cells from the beginning and check the results, then save as `content/keep-the-context/analysis.ipynb`. Gazette publishes those saved results; it never runs the notebook. The second program should print:

```text
Total: 347,269 bytes (339.13 KiB)
admissible-paths.png: 33.92%
query-tree.png: 34.45%
retrodiction-horizon.png: 31.63%
```

The observations are included in the notebook, so reproducing this arithmetic needs no download. If your editor exports an older notebook or omits cell IDs, use an editor or export option that writes nbformat 4.5; renaming the file does not convert it. This calculation needs neither image configuration nor a math renderer.

For your own figures, collect the same fields before running the total. For example, with the notebook editor's working folder set to `content/keep-the-context/`, this code reads the `context-sketch.png` you added earlier:

```python
from pathlib import Path
from hashlib import sha256

figure = Path("context-sketch.png")
data = figure.read_bytes()
record = {
    "name": figure.name,
    "bytes": len(data),
    "sha256": sha256(data).hexdigest(),
}
print(record)
```

Replace the example's `resources` list with records for the figures you actually want to compare, then rerun and save. Use the exported file if you resized or transformed the original: that is the version the reader receives. Record the observation date in the notebook’s opening cell. Rerun and save whenever you change the code or input records.

<a id="attach-the-saved-result"></a>

### Attach the saved result

With `analysis.ipynb` saved beside the article, attach it to the page. At the top of the article's existing frontmatter, before `[content]`, add:

```toml
notebooks = ['keep-the-context/analysis.ipynb']
```

Start the path from `content/`, your source root. `analysis.ipynb` alone would look directly in that root, while `content/keep-the-context/analysis.ipynb` would repeat the root directory. Keep the rest of the frontmatter. Save and refresh after the rebuild. Gazette shows the notebook after the article today. As the article's evidence it belongs in the article's Notes, read on request, and that move is in front. Check that all four cells and both saved outputs appear, in the order you saved them. If you list several notebooks, they appear in the order you list them. They stay with the article without creating separate pages or downloads.

Gazette can show Markdown and code cells, saved streams and errors, and supported text, JSON, inert HTML, PNG and JPEG results. Remove widgets, raw cells, SVG and other unsupported outputs before attaching the notebook, even if a cell also has a supported result. Check for saved errors you did not mean to show.

If notebook Markdown links to `plot.png`, put that image beside the notebook and include it through the same `static_assets` setting. The [notebook reference](https://docs.rawthoughts.in/gazette/notebooks) covers attachments inside a cell and limits on saved results. For crediting the material, see [Authorship, citation and reuse](https://rawthoughts.in/gazette/credit-and-reuse/).

<a id="choose-between-a-component-an-island-and-a-page-program"></a>

## Decide whether readers need controls

The saved notebook lets readers inspect the calculation you checked. A table may be enough to show its result. Add browser controls if trying different inputs would help them answer another question; for these figures, that means seeing how much of the total remains when one is left out.

A *component* is a named reading form that a theme supplies, such as the `reading-comparison` and `process-path` of Base, Gazette's shared theme. An *island* is a component that also loads a small browser module so it can respond to the reader.

| Form | Choose it when | Example |
| --- | --- | --- |
| Static component | A recurring reading form needs consistent presentation, with no browser interaction. | Base's `reading-comparison` presents an ordinary Markdown table. |
| Component island | A reusable component needs its own interaction while keeping a readable starting form. | Base's `process-path` turns an ordered account into selectable steps. |
| Page module | The behavior belongs to one article's particular question or data. | This guide's image-size checkboxes sum selected files. |
| Saved notebook | Readers need to inspect the calculation and the results you checked. | This guide's notebook records the files, hashes, total and shares. |

<a id="compare-image-sizes"></a>

## Compare image sizes

The table gives each figure’s size and its share of the combined total.

| Figure | Bytes | Share |
| --- | --: | --: |
| Admissible paths | 117,797 | 33.92% |
| Query tree | 119,621 | 34.45% |
| Retrodiction horizon | 109,851 | 31.63% |
| **All three** | **347,269** | **100%** |

The largest accounts for roughly a third of the combined bytes. File size is one publishing consideration alongside the detail a reader needs to see.

<a id="add-the-readable-comparison-first"></a>

### Add the readable comparison first

Copy this section into `content/keep-the-context/index.md`. Keep the explicit heading anchor: the script uses it to place the controls. You can change the visible heading without changing that anchor.

```markdown
## Compare image sizes {#compare-image-sizes}

Three image files from Gazette's local draft publication output of 16 November 2026:

| Figure               |       Bytes |    Share |
| -------------------- | ----------: | -------: |
| Admissible paths     |     117,797 |   33.92% |
| Query tree           |     119,621 |   34.45% |
| Retrodiction horizon |     109,851 |   31.63% |
| **All three**        | **347,269** | **100%** |

The saved notebook below records the file names and hashes. One KiB is 1,024 bytes; all three total 339.13 KiB.
```

<a id="give-this-page-its-own-script"></a>

### Give this page its own script

Create `content/keep-the-context/compare-resources.mjs` with this complete program. Its values are local to the module; it needs no library, server request or variable supplied by another script. Checking a box changes the sum shown to the reader. It does not remove an image from the publication.

```javascript
const resources = [
  { name: "Admissible paths", bytes: 117797 },
  { name: "Query tree", bytes: 119621 },
  { name: "Retrodiction horizon", bytes: 109851 },
];

const heading = document.getElementById("compare-image-sizes");
if (heading) {
  const controls = document.createElement("fieldset");
  const legend = document.createElement("legend");
  legend.textContent = "Choose which figures to include in the sum";
  controls.append(legend);
  const checks = [];
  const result = document.createElement("p");
  result.setAttribute("role", "status");
  const fullSize = resources.reduce((total, item) => total + item.bytes, 0);
  function update() {
    const selected = resources.filter((item, i) => checks[i].checked);
    const bytes = selected.reduce((total, item) => total + item.bytes, 0);
    result.textContent = `${selected.length} files: ${bytes.toLocaleString("en-US")} bytes (${(bytes / 1024).toFixed(2)} KiB), ${((100 * bytes) / fullSize).toFixed(2)}% of all three.`;
  }
  for (const item of resources) {
    const paragraph = document.createElement("p");
    const label = document.createElement("label");
    const check = document.createElement("input");
    check.type = "checkbox";
    check.checked = true;
    check.addEventListener("change", update);
    checks.push(check);
    label.append(check, ` ${item.name}`);
    paragraph.append(label);
    controls.append(paragraph);
  }
  update();
  controls.append(result);
  heading.after(controls);
}
```

In the article's existing frontmatter, place this resource table after `notebooks` and before `[content]`. Keep collection and project declarations before any `[[resources]]` table too.

```toml
[[resources]]
inputs = ['keep-the-context/compare-resources.mjs']
build = { kind = 'browser-module', entry = 'keep-the-context/compare-resources.mjs' }
output = '/assets/field-notes/compare-resources.js'
```

Both `inputs` and `entry` start at the configured `content/` source root, just like the notebook attachment. `output` is the script's public address within the site. Give another page's script a different output address. This declaration compiles the module; the image `static_assets` setting is not needed for it.

<a id="let-field-notes-load-the-page-s-resources"></a>

### Let Field Notes load the page's resources

The current Field Notes starter does not include page scripts automatically. Open your publication's `theme/templates/page.html` and add this loop immediately before `</head>`. If you already added it, keep one copy. Leave the existing presentation block and other template content in place.

```jinja
{% for resource in presentation.resources %}
  {% if resource.kind == "stylesheet" %}
  <link rel="stylesheet" href="{{ resource.url }}">
  {% elif resource.kind == "browser-module" %}
  <script type="module" src="{{ resource.url }}"></script>
  {% endif %}
{% endfor %}
```

The loop loads resources declared by the current page. Gazette supplies their resolved URLs for the local preview or configured publication address. Module scripts run after the document has been parsed, when the comparison heading is available. The [page-resource reference](https://docs.rawthoughts.in/gazette/page-resources) explains the declaration and theme connection.

Restart the preview with the same request you used for Field Notes. Open the article and uncheck **Query tree**: the total should change from **347,269** to **227,648 bytes**. Tab to a checkbox and press Space. Uncheck all three and check that the total reaches zero. Disable JavaScript and reload: the complete table and saved notebook should remain readable, without inactive controls. Re-enable JavaScript afterwards.

If the controls are missing, check the heading anchor, the two source-root paths and the template loop. A successful compilation alone does not load a script into the page. When replacing the data, update the notebook records, the article's table and the module together, then rerun and save the notebook.

The notebook holds the dated calculation; the browser controls let readers explore subsets of the same figures. They work independently, so changing a checkbox leaves the saved result intact.

<a id="reuse-a-reading-form-across-articles"></a>

## Reuse a reading form across articles

When several articles need the same reading form or interaction, look for an existing theme component. If none fits, develop it with the theme and leave each article’s data and explanation beside that article. The one-page image calculation above can stay with its own page.

**Note**

**Check your theme's components.** The examples below use Gazette's Base theme. Use them only in a theme that provides those definitions and their resources. The Field Notes starter does not include Base; copying these blocks into that starter would produce an unknown-component error. Its notebook and page-module examples above work through the declarations and template loop already shown.

<a id="keep-an-image-and-its-caption-together"></a>

### Keep an image and its caption together

In a theme providing `figure` and `figure-caption`, put one image and its caption inside the same figure:

```text
::::figure

![Sketch showing the observation point and the direction of the light](context-sketch.png)

:::figure-caption

Field sketch: the position and lighting that help explain the observation.

:::

::::
```

The outer fence has four colons and the caption's fence has three. Alt text describes the image for someone who cannot see it; the visible caption supplies context or credit. Keep the article's continuing argument outside the figure. Gazette carries the bound caption into the image's metadata too, so the visible and machine-readable accounts use the same words. A paragraph beneath an ordinary image does not create that connection by itself.

Preview the figure at a narrow reading width and check that the caption stays with it. If you maintain a theme, [the figure contract](https://docs.rawthoughts.in/gazette/theme-reference#bind-an-image-to-its-authored-caption) explains how to declare these components.

<a id="present-a-comparison-without-adding-behavior"></a>

### Present a comparison without adding behavior

In a theme providing `reading-comparison`, give the comparison a meaningful label and keep the table as Markdown:

```markdown
:::reading-comparison {label = "What belongs beside an observation"}

| Detail              | Why keep it?                         |
| ------------------- | ------------------------------------ |
| Instrument and unit | Make the value interpretable.        |
| Observation window  | Establish which period it describes. |

:::
```

The component wraps the table in a labelled section. It has no browser module and adds no controls. The table still carries the comparison. You can see the same component comparing the guide's source files in [Why an article has one home](https://rawthoughts.in/gazette/why-an-article-has-one-home/).

<a id="let-readers-move-through-an-ordered-account"></a>

### Let readers move through an ordered account

Base's `process-path` keeps a complete ordered list before JavaScript runs. Each `process-step` needs a heading and its explanation:

```markdown
::::process-path {label = "From an observation to a checked note"}

:::process-step

### Record the conditions

Keep the instrument, unit and observation window with the reading.

:::

:::process-step

### Compare like with like

Check those conditions before interpreting a difference.

:::

:::process-step

### Keep the working

Save the calculation beside the explanation so another reader can follow it.

:::

::::
```

The outer fence has four colons so it can contain the three-colon step blocks. With the theme's interaction loaded, readers select step headings to open their explanations; keyboard users can activate the buttons and move among them with Up, Down, Home and End. Without JavaScript, all three explanations remain in order. Automatic progression is off by default. Use an ordinary numbered list when showing everything at once serves the reader better.

The theme declares an island's module and the function that mounts it; the article supplies the headings, explanations and component arguments. For `process-path`, Base declares the module and its `mount` function. The [component contract](https://docs.rawthoughts.in/gazette/markdown#component-islands) explains that connection for theme authors.

<a id="carry-the-method-into-a-real-article"></a>

## Carry the method into a real article

The three sample figures above come from Causality's articles on [endpoint-constrained paths](https://causality.in/blog/future-without-retrocausation/) (on Causality), [the cost of a query](https://causality.in/collections/changing-descriptions/from-summary-to-repair/the-price-of-another-question/) (on Causality) and [reconstructing from a noisy record](https://causality.in/blog/the-record-and-the-arrow/) (on Causality). In [What did selective memory buy?](https://causality.in/collections/evidence-and-evaluation/from-observation-to-evaluation/what-did-selective-memory-buy/) (on Causality), a saved notebook recomputes summaries from Reckon's retained evaluation results. The article keeps the workload, negative results and measurement costs beside those numbers. Its analysis uses the same saved-result form for a research comparison.

For an interaction that changes a model, [RawFish's opinion comparison](https://rawthoughts.in/collections/systems/rehearsal-and-evidence/how-opinions-move/) lets a reader vary a small illustrative influence model; its trajectories remain simulated possibilities. [What can you distinguish with one more move?](https://causality.in/collections/changing-descriptions/from-summary-to-repair/budgeted-questions/) (on Causality) spends an observation budget and shows which distinctions remain possible. Both keep the explanation readable alongside the controls, so the interaction helps readers examine the argument.


## Article notes



<a id="gazette-notebook-0f922ca1ac24394d9be9cd2608e2c1a2e337f8a4d61dfa483d80b323a48d5a77--cell-0-three-figures-and-their-combined-size"></a>

## Three figures and their combined size

These file sizes were recorded from Gazette’s local draft publication output on 16 November 2026. The figures accompany [endpoint-constrained paths](https://causality.in/blog/future-without-retrocausation/) (on Causality), [the price of another question](https://causality.in/collections/changing-descriptions/from-summary-to-repair/the-price-of-another-question/) (on Causality) and [the record and the arrow](https://causality.in/blog/the-record-and-the-arrow/) (on Causality). Each SHA-256 digest identifies the version counted.

Execution count: 1

```python
resources = [
    {
        "name": "admissible-paths.png",
        "bytes": 117797,
        "sha256": "087c366adfc4f63e60bdfd34c22caaf7bf044aa76ae921ed661e876581b26e1b",
    },
    {
        "name": "query-tree.png",
        "bytes": 119621,
        "sha256": "75e269a66ba8e7f239779ee984373ed55d070d32f4a3cd91e53ff95ee501f587",
    },
    {
        "name": "retrodiction-horizon.png",
        "bytes": 109851,
        "sha256": "c7717802086c244cee3ec96ac53fef118035fe99538a75ac3a0d9b5eb099ce72",
    },
]
for item in resources:
    print(f"{item['name']}: {item['bytes']:,} bytes")
```

stdout

```
admissible-paths.png: 117,797 bytes
query-tree.png: 119,621 bytes
retrodiction-horizon.png: 109,851 bytes
```

Execution count: 2

```python
total = sum(item["bytes"] for item in resources)
print(f"Total: {total:,} bytes ({total / 1024:.2f} KiB)")
for item in resources:
    share = 100 * item["bytes"] / total
    print(f"{item['name']}: {share:.2f}%")
```

stdout

```
Total: 347,269 bytes (339.13 KiB)
admissible-paths.png: 33.92%
query-tree.png: 34.45%
retrodiction-horizon.png: 31.63%
```

<a id="gazette-notebook-0f922ca1ac24394d9be9cd2608e2c1a2e337f8a4d61dfa483d80b323a48d5a77--cell-3-what-the-total-tells-us"></a>

### What the total tells us

The three images contain 347,269 bytes, or 339.13 KiB. Query tree is the largest at 34.45% of this selection. One KiB is 1,024 bytes.

This accounts for the selected image files. A page’s transfer size also depends on its other resources, delivery encoding and caching; elapsed loading time needs a separate measurement. Replacing an image calls for a new byte count and hash before comparing the totals again.





Reading path: [Gazette](https://rawthoughts.in/gazette/) > [Figures, notes and notebooks](https://rawthoughts.in/gazette/figures-notes-and-math/)


Source code for [Gazette](https://github.com/getHarshOnline/gazette) is credited to [Harsh Joshi](https://getharsh.in/about/).
