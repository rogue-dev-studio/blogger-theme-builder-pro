# Blogger Theme Builder Pro

A single-file visual builder for Blogger (Blogspot) themes. Drag gadgets onto a canvas, style them, preview every Blogger page type, and export a native Blogger XML theme — all from one `index.html`, no build step, no backend.

![status](https://img.shields.io/badge/status-beta-orange) ![license](https://img.shields.io/badge/license-MIT-blue) ![single file](https://img.shields.io/badge/build-none-success)

## Why

Editing Blogger XML by hand is slow and error-prone: layout sections, gadget IDs, `<b:skin>` CSS, and page-type conditionals all have to stay in sync. This tool keeps a single schema as the source of truth and renders both the live preview and the exported XML from it, so what you see is what Blogger receives.

## Features

- **1:1 schema-synchronized preview** — the canvas renders from the same schema that produces the XML.
- **Add tab** — gadget palette (header, blog posts, labels, popular posts, link list, profile, and more) with per-widget defaults.
- **Layout tab** — Blogger-style layout view: sections, gadgets, reorder arrows, and "Add a Gadget" per section.
- **Theme tab** — colors, typography, spacing, and page background compiled into the exported `<b:skin>` block.
- **XML tab** — live canonical XML output with **Copy XML** and **Export XML** actions.
- **Import XML** — load an existing Blogger theme into the builder.
- **Validate** — checks duplicate widget IDs, unbalanced references, and common theme mistakes before export.
- **Page-type preview** — Homepage, Post Detail, Archive, Static Page.
- **Viewport preview** — desktop, tablet, and mobile widths.
- **Undo / redo** and a properties inspector for the selected gadget.
- **Three-column grid** — left sidebar 20% / post 60% / right sidebar 20%, each sidebar width adjustable; empty sidebars collapse so the post fills the row.

## Quick start

1. Clone the repository.
2. Open `index.html` directly in a browser, or serve the folder with any static server (e.g. VS Code Live Server, `npx serve`).
3. Build your theme, then **Export XML**.
4. In Blogger: **Theme → Edit HTML**, replace the whole file with the exported XML, and save.

No install, no bundler, no Node dependency at runtime. Tailwind, Font Awesome, and the web fonts load from CDNs.

## How it works

```
schema  ──►  preview renderer  ──►  canvas (WYSIWYG)
   └────►  XML compiler      ──►  Blogger theme XML (b:section / b:widget / b:skin)
```

- The schema describes sections, gadgets, and theme tokens.
- The preview renderer turns the schema into DOM for the selected page type.
- The XML compiler turns the same schema into Blogger-compatible XML, including widget IDs and skin CSS.
- Importing XML parses the theme back into the schema so editing stays round-trip safe.

## Compatibility

- Modern browsers (Chrome, Edge, Firefox, Safari).
- Blogger's current theme format (`b:section`, `b:widget`, `b:skin`, `b:if` page-type conditionals).
- Legacy left/right sidebar widget types remain supported and are placed on the right.

## Project status

Beta. The builder is feature-complete for layout, theming, and export, and is still being hardened against edge cases in imported third-party themes.

## License

MIT — see [LICENSE](LICENSE). Redistribution must keep the author credit below.

## Attribution

Built by **Rogue Development (Rogue Dev Studio)** — <https://github.com/rogue-dev-studio>.

This project was produced with the AI Agents Rogue workflow catalog. Credit and link must remain in `README.md` and `NOTICE`.

Third-party assets loaded via CDN keep their own licenses: Tailwind CSS (MIT), Font Awesome Free (icons CC BY 4.0, fonts SIL OFL 1.1, code MIT), Google Fonts (SIL OFL 1.1).
