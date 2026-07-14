---
name: companion-docs-writing-style
description: Use this when writing or editing prose for the Home Assistant companion app documentation — page introductions, step-by-step instructions, UI walkthroughs, troubleshooting text, or any user-facing writing. Covers tone, audience, dual-platform (iOS and Android) coverage, and language rules.
---

# Companion docs writing style

This repository holds the documentation for the Home Assistant companion apps (iOS, Android, and their extensions like Apple Watch, Wear OS, CarPlay, Android Auto, and Meta Quest). Write so that Home Assistant feels approachable, stable, and easy to use for a broad, non-technical audience.

Present the app's UI as the standard, recommended way to do things. Treat YAML, templates, and action calls as optional paths for readers who want more control, not as the normal path.

## Brand personality

Reflect Home Assistant's brand personality:

- **Welcoming**: Meet readers at their own level. Never talk down to them.
- **Candid**: Be direct and honest. Do not hide complexity behind false simplicity or marketing fluff.
- **Supportive**: Guide the reader forward in a practical, patient way.
- **Generous**: Give readers what they need without overwhelming or patronizing them.
- **Independent**: Be confident, direct, and human. Home Assistant does not need to sound like a corporate tech brand.

## Audience and tone

Always write as if the reader:

- Has never used Home Assistant before, and may not know what entities, automations, actions, or YAML are. Provide a brief inline definition or link to the [Home Assistant documentation](https://www.home-assistant.io/docs/) when a concept needs prior knowledge.
- Is not a developer and is not familiar with technical terminology.
- Needs step-by-step guidance with visual confirmation at each step.
- May be using either iOS or Android, so both must be covered.
- Speaks English as a second language. Write for a global audience and avoid idioms, cultural references, and region-specific terms.

Use an informational, friendly tone. Write directly to the reader with "you" and "your", not "the user". Avoid wording that makes the app or Home Assistant sound fragile, difficult, or easy to break. Do not label features as "advanced" unless the product itself uses that wording.

## Cover both platforms

This is the rule that most distinguishes companion documentation from the rest of Home Assistant.

- Every feature must document both iOS and Android.
- When a feature, setting, or path differs between platforms, describe each one explicitly.
- When a feature exists on only one platform, state clearly which platform supports it and which does not.
- Remember the platform extensions too (Apple Watch, Wear OS, CarPlay, Android Auto, Meta Quest) when they are relevant.

Use the platform icons to flag platform-specific content. See `companion-docs-docusaurus-style` for the exact syntax.

## Language rules

- Use American English (for example, "color", not "colour").
- Follow the [Microsoft Writing Style Guide](https://learn.microsoft.com/style-guide/welcome/).
- Use the serial (Oxford) comma before the conjunction in a list of three or more items. For example, "Home Assistant supports Zigbee, Z-Wave, and other protocols".
- Do not use "e.g.", "i.e.", "etc.", or "etcetera". Use "for example", "such as", or "like".
- Prefer "select" over "click" unless you specifically mean a mouse action, such as right-clicking or double-clicking.
- Use "Home Assistant" in full. Never use "HA" or "HASS".
- Do not use all caps for emphasis. Use _italics_ when emphasis is needed.
- Use **bold** for UI strings, not for emphasis. Write UI breadcrumbs as **Settings** > **Companion app** > **Notifications**.
- Do not use "master/slave". Use alternatives such as "client/server", "leader/follower", or "controller/device".
- Adopt inclusive language. For example, use "allowlist" instead of "whitelist". Keep content objective and free of gender-favoring, polarizing, race-related, or religion-inconsiderate wording.
- Match the official capitalization of brand names, services, protocols, and platforms. For example: "Z-Wave" (not "Zwave", "Z-wave", or "ZWave"), "CarPlay", "Android Auto", "Wear OS", "Meta Quest", and "Input Select" (not "input select").
- Do not put two spaces after a period.
- Proofread for grammar and spelling. End sentences with a period.

## Lists

- Use a numbered list for sequential steps or ordered items, and a bulleted list for unordered items.
- Keep list items parallel in structure.
- If at least one item is a complete sentence, end every item in that list with a period. If no item is a complete sentence, do not use end punctuation.
- Do not use semicolons, commas, or conjunctions such as "and" or "or" at the end of list items.

## Content structure

- Start each page with a brief overview that says what the feature is and why the reader would use it.
- Use progressive disclosure: basic information first, more complex details later.
- Break longer content into logical sections with clear, sentence-style headings.
- Avoid redundancy unless repetition adds clarity.
- Prefer lists over tables. Tables often render poorly on mobile. If a table is unavoidable, minimize the number of columns and keep the text short.

## Write for beginners: example

Good — defines the concept, gives numbered steps, covers both platforms, and confirms the result:

```markdown
## Sending a notification to your phone

A notification is a message that appears on your phone's lock screen or
notification center, similar to a text message alert.

1. In Home Assistant, go to **Developer tools** > **Actions**.
2. In the **Action** drop-down, search for and select
   `notify.mobile_app_<your_phone_name>`.

   ![iOS](/assets/iOS.svg) On iOS, the action might be called
   `notify.mobile_app_iphone`.

   ![Android](/assets/android.svg) On Android, it might be called
   `notify.mobile_app_pixel_7`.

3. In the **Action message** section, enter a message, such as
   `Hello from Home Assistant!`.
4. Select **Perform action**.
5. Check your phone. You should see a notification appear.
```

Bad — assumes expertise, skips the UI, and ignores platform differences:

```markdown
## Notifications

Perform the `notify.mobile_app_*` action with a message payload to send
notifications. See the HA docs for more info on action calls.
```

## Documenting requirements

When a feature has requirements, state them up front:

- Supported devices or operating systems, and minimum app or OS versions.
- Whether the feature is stable or in beta.
- Any required Home Assistant integration, configuration, or minimum Core version.

## Beta and Labs features

When a feature is not yet in the stable release, or is experimental and may change, flag it. See `companion-docs-docusaurus-style` for the exact markup. Use this when:

- The feature is only available in beta versions of the iOS or Android app.
- The feature is experimental and may change.
- The documentation is prepared ahead of a production release.

## Other rules

- Do not invent new automation, notification, or dashboard examples unless explicitly asked. Improving an existing example (clarifying it, adding comments, or removing defaults) is fine.
- If a feature or setting is renamed in the app, update the documentation to match.
- When you move or rename a page, keep internal links working. See `companion-docs-docusaurus-style`.
