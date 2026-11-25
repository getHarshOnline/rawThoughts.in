Title: Choose a reading form

[Read HTML](https://rawthoughts.in/gazette/change-presentation/)

Rights holder: RawThoughts Enterprises Private Limited

<a id="choose-a-reading-form"></a>

# Choose a reading form

Give the first [Field Notes](https://rawthoughts.in/gazette/first-publication/) article a narrower reading column and serif text. The starter theme has two page templates. You will use its reading template for one article and keep the default on the rest.

<a id="select-a-prepared-reading-form"></a>

## Select a prepared reading form

In `gazette.toml`, find the existing `[composition]` table. Keep its `theme` and add `page_templates` below it:

```toml
[composition]
theme = { package = 'theme:field-notes' }
page_templates = { 'content:keep-the-context' = 'field-notes/reading.html' }
```

Edit the existing `[composition]` table and keep any other entries in `page_templates`. `content:keep-the-context` is the article's ID. `field-notes/reading.html` is the template the theme supplies. Leave the article and its address as they are.

<a id="compare-the-two-pages"></a>

## Compare the two pages

Stop the preview with **Ctrl+D** and restart from the Field Notes directory. Gazette reads the template settings when the session starts. If your request includes the workbook, keep `--listen site:workbook=127.0.0.1:0` too.

```sh
cat "$GAZETTE_REQUEST" - | "$GAZETTE" preview-sites \
  --local --allow-listeners --local-urls --watch \
  --listen site:field-notes=127.0.0.1:0
```

Keep the request you last used, including the math request if you enabled it. In the new preview, open `/keep-the-context/` or its current journey address. Check the narrower column and serif text. The font depends on your computer. The article and its link to the next note still work at the same addresses.

Open **Review a note** from its collection or journey, then return to the collection at `/` to compare. To restore the default for the first note, remove just its entry from `page_templates` and restart the preview.

<a id="choose-the-publication-s-theme-separately"></a>

## Choose the publication's Theme separately

The theme supplies the reading form; the workspace selects it for the article. [From one site to many](https://rawthoughts.in/gazette/from-one-site-to-many/#keep-the-four-jobs-clear) explains how the writing, workspace, compiler and theme share the work.

Use `theme` to choose a package already declared in `theme_packages`, with its sources available. Field Notes includes only `theme:field-notes`. Its styles set light and dark appearance, and there are no named palettes to choose from. For another theme, use the palette and template names that package documents.

For a fuller publication, [Base](https://github.com/getHarshOnline/gazette-theme-base) supplies shared navigation, reading, search and controls. Each publication's world, the visual language its theme adds, brings its own type, material and light:

| World | Reading character |
| --- | --- |
| [Carrier](https://github.com/getHarshOnline/gazette-theme-carrier) | Applied systems and consulting |
| [Lattice](https://github.com/getHarshOnline/gazette-theme-lattice) | Research and exact notation |
| [Folio](https://github.com/getHarshOnline/gazette-theme-folio) | Institutional inquiry |
| [Chassis](https://github.com/getHarshOnline/gazette-theme-chassis) | A studio and its products |
| [Chronicle](https://github.com/getHarshOnline/gazette-theme-chronicle) | A personal publication |
| [Nocturne](https://github.com/getHarshOnline/gazette-theme-nocturne) | Atmosphere and narrative |

These themes have their own repositories and setup requirements; they are separate from the Field Notes starter.

`page_templates` overrides a template named in the article. When neither names one, Gazette uses the theme's default. For sites that share settings, see [template precedence and defaults](https://docs.rawthoughts.in/gazette/workspace-presentation#per-content-presentation-selection).

<a id="let-a-crossing-reveal-its-destination"></a>

## Let a crossing reveal its destination

In [How Pale fits together](https://rawthoughts.in/collections/systems/making-a-working-world-intelligible/architecture/), the link to [MONAD](https://causality.in/monad/) (on Causality) connects a system's working description with the research question of changing that description. RawThoughts' Carrier world owns the article's type and layout. The link borrows the small destination mark supplied by Causality's Lattice world. That mark gives the reader a glimpse of where the thought leads while leaving the sentence in the publication they are reading.

Gazette resolves the destination and gives those facts to the theme. Base's shared link treatment uses the destination world's configured signature; the author does not select a colour or draw a mark for each link. Field Notes' starter teaches the same [cross-site reference](https://rawthoughts.in/gazette/connect-publications/), but does not supply this visual treatment.

<a id="know-when-you-need-theme-development"></a>

## Know when you need Theme development

If Gazette reports a missing `reading.html`, check which templates your package includes or update an older starter. To create a template or component, see the [theme contract](https://docs.rawthoughts.in/gazette/theme-reference) and [Tera guide](https://docs.rawthoughts.in/gazette/tera). A search box also needs a theme that supplies it, even after you [generate search data](https://rawthoughts.in/gazette/help-readers-find-the-work/).


Reading path: [Gazette](https://rawthoughts.in/gazette/) > [Choose a reading form](https://rawthoughts.in/gazette/change-presentation/)


Source code for [Gazette](https://github.com/getHarshOnline/gazette) is credited to [Harsh Joshi](https://getharsh.in/about/).
