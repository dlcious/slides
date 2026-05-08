# Zendesk AI Slides — Session Start

Fetch these files in order before beginning any slide work.

## 1. Skill files

```
https://raw.githubusercontent.com/dlcious/slides/main/zendesk-slides-skill.md
https://raw.githubusercontent.com/dlcious/slides/main/slide-archetypes.md
https://raw.githubusercontent.com/dlcious/slides/main/voice-for-slides.md
https://raw.githubusercontent.com/dlcious/slides/main/zendesk-brand-skill.md
```

## 2. Token reference

```
https://raw.githubusercontent.com/dlcious/slides/main/slides-skill-reference.html
```

## 3. Archetype render index

```
https://raw.githubusercontent.com/dlcious/slides/main/assets/renders/index.json
```

## 4. Archetype renders

```
https://raw.githubusercontent.com/dlcious/slides/main/assets/renders/cover--canonical.png
https://raw.githubusercontent.com/dlcious/slides/main/assets/renders/agenda--canonical.png
https://raw.githubusercontent.com/dlcious/slides/main/assets/renders/section-divider--canonical.png
https://raw.githubusercontent.com/dlcious/slides/main/assets/renders/statement--canonical.png
https://raw.githubusercontent.com/dlcious/slides/main/assets/renders/quote--canonical.png
https://raw.githubusercontent.com/dlcious/slides/main/assets/renders/content--cols5-none.png
https://raw.githubusercontent.com/dlcious/slides/main/assets/renders/product-plate--canonical.png
https://raw.githubusercontent.com/dlcious/slides/main/assets/renders/data-display--callouts.png
https://raw.githubusercontent.com/dlcious/slides/main/assets/renders/timeline--canonical.png
https://raw.githubusercontent.com/dlcious/slides/main/assets/renders/closing--canonical.png
```

## How to start a session

Share this URL with Claude:

```
https://raw.githubusercontent.com/dlcious/slides/main/session-start.md
```

Claude will fetch this file, then fetch everything listed above, and confirm it is ready to build before asking for deck content.

## Notes

- Skill files govern copy rules, archetype selection, and voice
- Token reference provides exact hex values, font sizes, and spacing
- Renders are the visual ground truth — Claude samples these for pixel-accurate colors and layout proportions
- If a render cannot be fetched, fall back to uploading the corresponding PDF from `assets/pdfs/`
