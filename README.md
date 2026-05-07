# Zendesk AI Slides Design System Guide

A three-page static guide mirroring the structure and quality bar of the Zendesk Brand Style Guide. Built for humans and machines.

## Structure

Three pages, sibling artifacts to the brand guide:

1. **Landing page** (`index.html`)  
   Hero with manifesto-style headline ("Built so every deck _ships_ on brand"), two cards linking to visual/skill references, metadata footer (System / Version / Audience / Built for)

2. **Visual reference** (`slides-visual-reference.html`)  
   Ten archetypes presented as a flowing deck. Numbered sections (01—10) with mono supertitles, prose treatments per archetype, full-fidelity renders from Figma. Real Zendesk content (Intelligence Assistant launch deck), not placeholder text.

3. **Skill reference** (`slides-skill-reference.html`)  
   Action-oriented. Installation instructions, worked example (starter prompt → draft output → common follow-ups), draft block format, full embedded skill content, token reference (color, typography, spacing).

## Visual Treatment

- **Typography**: Inter (sans), Monaco (mono)
- **Color**: Coconut/Licorice with Matcha used sparingly (brand mark, focus states, emphasis)
- **Section numbering**: NN — Section Title (mono supertitles)
- **Italic emphasis**: Load-bearing words in headlines (e.g., _ships_)
- **Spacing**: Generous whitespace, consistent hierarchy
- **Slide renders**: Full-fidelity at 16:9, inset on Sesame backing surface

Matches the brand guide's quality bar exactly.

## Content

**Deck story** (Visual reference):  
Internal launch announcement for Zendesk Intelligence Assistant. Ten slides walk through: problem → solution → product → proof → close. Cover with speaker, Agenda with 8 sections, Section divider ("The support gap"), Statement ("Every support interaction should feel effortless"), Quote (customer testimonial), Content (3 principles), Product plate (assistant UI), Data display (6 metrics), Timeline (rollout plan), Closing (wordmark).

**Skill content** (Skill reference):  
Complete `zendesk-slides-skill.md` embedded with installation instructions, worked example, draft block format explanation, and full token reference. Action-oriented tone: how to use the skill, not what it is.

## Files

```
zendesk-slides-guide-v2/
  index.html                        # Landing page
  slides-visual-reference.html      # Ten archetypes, numbered sections
  slides-skill-reference.html       # Installation, examples, tokens
  README.md                         # This file

  assets/
    renders/
      cover--canonical.png          # Exported from Figma
      agenda--canonical.png
      section-divider--canonical.png
      statement--canonical.png
      quote--canonical.png
      content--cols5-none.png
      product-plate--canonical.png
      data-display--callouts.png
      timeline--canonical.png
      closing--canonical.png
```

## How to View

Open `index.html` in any browser. Static site, no server required.

```bash
cd zendesk-slides-guide-v2
open index.html
```

## Relationship to the Brand Guide

This guide is a sibling artifact to the [Zendesk Brand Style Guide](https://zendesk-brand-style-guide.vercel.app/). Same structure: landing page with two parallel reading modes (Visual / Skill vs. Visual / Code), same typography treatment (Inter + Monaco, section numbering, italic emphasis), same restraint with color, same metadata footer pattern.

The brand guide covers the visual language system. This guide covers the slides design system. Both built for humans and machines.

## Design Decisions

1. **No toggle**: The split into two parallel documents (Visual / Skill) replaces the toggle pattern. Each page is self-contained and linked from the other.

2. **Real content, not placeholders**: The ten slides in the Visual reference tell a coherent story (Intelligence Assistant launch). No Lorem Ipsum, no generic "Slide title here."

3. **Action-oriented skill reference**: Installation → worked example → full content. Structured for someone wiring up the skill, not reading documentation.

4. **Static HTML**: Plain HTML, CSS, minimal vanilla JS. No build step, no framework. Viewable from `file://` URLs or simple static hosting.

5. **Manifesto-style hero**: "Built so every deck _ships_ on brand" with italic on the load-bearing word. Confident, practical, brand-forward.

6. **Prose treatments**: Each archetype in the Visual reference includes "When to use," "What pairs with it," "What to avoid" — actionable guidance, not descriptions.

## Token Reference

Full color, typography, and spacing tokens embedded in the Skill reference page. Pulled from Figma via MCP during build. Includes semantic names, literal values (hex, px, pt), and usage notes.

**Color tokens**: Coconut, Licorice, Matcha (400, bright, 600), Sesame (100, 200), Fern, Shamrock  
**Typography tokens**: Inter (Medium 14pt → Semi Bold 160pt), eight styles with weights and line heights  
**Spacing tokens**: 30px, 32px, 40px, 64px (horizontal padding, column gap, callout padding, major section gap)

## How to Regenerate

The guide is generated from the Figma design system. To regenerate after template changes:

1. **Export screenshots**: Use Figma MCP `get_design_context` on each archetype node ID. Save to `assets/renders/`.
2. **Update token reference**: Use `get_variable_defs` to pull latest tokens. Update Skill reference page.
3. **Rebuild prose**: If archetype structure changes (new parameters, different usage), update the Visual reference prose treatments.

The guide is hand-editable HTML — no build tool, readable as source.

## License

Internal Zendesk tool. Not for external distribution.
