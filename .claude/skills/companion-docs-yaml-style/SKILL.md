---
name: companion-docs-yaml-style
description: Use this when writing or editing YAML, JSON, or Jinja2 template code examples in the companion app docs — notification payloads, actionable notification configs, action (service) calls, automations, and sensor definitions.
---

# Companion docs YAML and example style

The companion app docs contain many code examples: notification payloads, actionable notification configs, action (service) calls, automations, and sensor definitions. Most are YAML. Keep them consistent, minimal, and easy to copy.

For prose and tone, use `companion-docs-writing-style`. For fenced-code and MDX rules, use `companion-docs-docusaurus-style`.

## Formatting rules

- Use 2 spaces for indentation. Never use tabs.
- Use `true` and `false` for booleans, not `yes`, `no`, `on`, or `off`.
- Prefer block style over flow (JSON-like) style for sequences and mappings.
- Keep lines inside a code fence readable. Wrap long values across multiple lines where the format allows.
- Declare the language on the fence: ` ```yaml `, ` ```json `, or ` ```jinja `.

## Strings and placeholders

- Values like entity IDs, action names, and device classes do not need quotes. Quote other strings with double quotes when quoting aids clarity or is required.
- Use capital letters and underscores for values the reader must replace, for example `token: YOUR_LONG_LIVED_TOKEN` or `notify.mobile_app_<your_phone_name>`.
- Put comments on their own line above the code they describe, indented to match:

  ```yaml
  # Send only to this phone
  action: notify.mobile_app_iphone
  ```

## Actions (service calls)

- Put `entity_id`, `area_id`, and `device_id` under a `target:` block, not at the action level or inside `data:`.
- Keep companion-specific options (such as `push`, `actions`, and `data`) under `data:`.
- Write lists in block style, one item per line, rather than comma-separated inline lists.

Example of a notification action with data:

```yaml
action: notify.mobile_app_iphone
data:
  title: "Front door"
  message: "Motion detected"
  data:
    push:
      sound: default
    actions:
      - action: OPEN_DOOR
        title: "Open door"
```

## Templates

- Keep Jinja2 templates readable by splitting long expressions across multiple lines.
- Prefer helper methods such as `states('sensor.example')` over direct object access.
- A template inside a YAML example stays in the YAML fence. A standalone template example uses a ` ```jinja ` fence.
- Because `.mdx` parses `{{ }}` and `{% %}` as JSX, templates must always live inside a code fence. See `companion-docs-docusaurus-style`.

```yaml
message: >-
  {{ states('sensor.living_room_temperature') }} degrees right now
```

## Keep examples minimal

- Omit default values and empty sections so the example shows only what matters.
- Show the smallest example that works first, then build up if more detail is needed.
- Do not invent new automation, notification, or sensor examples unless explicitly asked. Improving an existing example — clarifying it, adding comments, or removing defaults and unnecessary code — is fine.
