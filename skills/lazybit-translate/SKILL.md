---
name: lazybit-translate
description: Set up or change LazyBit Translate on a site — languages, translation instructions, the language switcher, and which parts of the pages are never translated. Use when the user asks to add or remove languages, change how the site is translated, or keep text untranslated.
---

# LazyBit Translate

1. `get_translation_settings` for the site first.
2. Languages: `set_languages`. On or off: `set_translation_enabled`.
3. How it translates: `update_translation_settings` — `instructions` (tone, terms to keep, glossary in plain
   words) and `automatic_translation`.
4. Text that must stay as it is (brand names, code, addresses, user content): mark it in the site's code with
   `data-i18n-ignore`, as `get_sdk_docs` with `translate` describes, and show the user the change.
5. Translate is designed for public pages. On pages behind a login, keep private content out with
   `data-i18n-ignore` or leave those pages without the tag.
