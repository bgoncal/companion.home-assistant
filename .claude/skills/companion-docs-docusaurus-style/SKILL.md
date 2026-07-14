---
name: companion-docs-docusaurus-style
description: Use this when editing the Markdown or MDX syntax of the companion app docs — frontmatter, headings, admonitions, platform icons, images, internal and external links, beta flags, code fences, or MDX/JSX gotchas. This site is built with Docusaurus.
---

# Companion docs Docusaurus and Markdown style

The companion app documentation is built with [Docusaurus](https://docusaurus.io/). Pages live under `docs/` as `.md` or `.mdx` files and use GitHub-Flavored Markdown. Prefer Markdown over HTML wherever possible.

For writing tone and language rules, use `companion-docs-writing-style`. For formatting YAML and other code examples, use `companion-docs-yaml-style`.

## Frontmatter

Every page starts with YAML frontmatter. Match the conventions already used in `docs/`:

```markdown
---
title: Getting started
id: getting-started
---
```

- `title` is the page title and becomes the first-level heading. Use sentence-style capitalization.
- `id` is a stable identifier used for links and the sidebar. Use lowercase with hyphens.
- Add `sidebar_label` only when the sidebar entry should differ from the title.

## Headings and Markdown basics

- The frontmatter `title` is the H1, so page content starts at heading level 2 (`##`).
- Use ATX-style headings (`##`, `###`) and do not skip levels.
- Use sentence-style capitalization for headings.
- Use `-` for unordered lists and increasing numbers for ordered lists.
- Use `_italic_` for italics and `**bold**` for bold. Reserve bold for UI strings.
- Use backticks for file paths, file names, variable names, action names, and text the reader types into a field.
- Always declare a language on fenced code blocks (` ```yaml `, ` ```json `, ` ```jinja `, ` ```text `).
- There is no line-length limit for prose. Write in flowing text and do not hard-wrap paragraphs.

## Admonitions

Use Docusaurus admonitions to highlight important information, but do not overuse them:

```markdown
:::note
General information or a side note.
:::

:::tip
A recommendation or helpful shortcut.
:::

:::info
Helpful context or background information.
:::

:::caution
Advises against an action that may cause data loss or behavior that is hard to reverse.
:::

:::warning
Alerts the reader to a risk to the security or integrity of their system.
:::

:::danger
Critical information about potential data loss or security issues.
:::
```

Admonitions can contain other Markdown, including lists, links, and platform icons.

## Platform indicators

Use the platform icons to flag content that applies to only one platform:

```markdown
![iOS](/assets/iOS.svg)          <!-- iOS only -->
![Android](/assets/android.svg)  <!-- Android only -->
```

- Place the icon inline at the start of the sentence, table cell, or list item it applies to.
- When a feature applies to both platforms, do not add an icon.
- Both icons live at `static/assets/iOS.svg` and `static/assets/android.svg` and are referenced with the absolute paths above.

## Beta and Labs features

Flag features that are not yet in the stable release with a `beta` span in the heading or intro:

```markdown
## New feature name <span class="beta">BETA</span>

This feature is currently in beta and available only in the beta version of the app.
```

For Labs preview features, use the same span with `LABS` text:

```markdown
Kiosk mode is a <span class="beta">LABS</span> feature in the iOS Companion app.
```

## Images

- Store images in `static/assets/`.
- Reference images with absolute paths that start with `/assets/`.
- Always include descriptive `alt` text for accessibility.
- Use an HTML `<img>` tag with a `width` attribute when you need to control the display size:

  ```html
  <img alt="Notification settings screen" src="/assets/notification-settings.png" width="400" />
  ```

- When a step needs a screenshot you cannot add yet, leave a placeholder comment so it is easy to find later: `<!-- TODO: Add screenshot of the notification settings screen -->`.

## Links

### Internal links

Link between documentation pages with relative paths that keep the file extension:

```markdown
[Android flavors](../core/android-flavors.md)
[Getting started](./index.mdx)
```

If you move or rename a page, update the links that point to it so nothing breaks.

### External links

Use descriptive link text. Never use a bare URL in body text.

```markdown
<!-- Good -->
[Home Assistant installation](https://www.home-assistant.io/installation/)

<!-- Avoid -->
https://www.home-assistant.io/installation/
```

### Common external destinations

- Home Assistant documentation: `https://www.home-assistant.io/docs/...`
- Home Assistant Cloud (Nabu Casa): `https://support.nabucasa.com/...`
- iOS app issues: `https://github.com/home-assistant/iOS/issues/...`
- Android app issues: `https://github.com/home-assistant/android/issues/...`

## MDX gotchas

`.mdx` files are compiled as JSX, so a few characters behave differently than in plain `.md`:

- Curly braces `{ }` and angle brackets `< >` are parsed as JSX. Escape them or wrap them in an inline code span or code fence when they are literal content.
- Home Assistant Jinja2 templates (`{{ ... }}`, `{% ... %}`) must live inside a fenced code block so MDX does not try to interpret the braces. See `companion-docs-yaml-style` for template formatting.
- When in doubt, prefer a `.md` file. Use `.mdx` only when you need JSX, imported components, or Docusaurus-specific interactivity.

## Local development

- `npm start` — start the local dev server.
- `npm run build` — build the static site for production.
- `npm run serve` — serve the built site locally.
