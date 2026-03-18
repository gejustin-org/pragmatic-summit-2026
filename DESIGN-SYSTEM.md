# Design System Prompt — "Summit Dark"

*Extracted from [gejustin-org/pragmatic-summit-2026](https://gejustin-org.github.io/pragmatic-summit-2026/). Use this as the canonical design reference for all editorial/report pages.*

---

## Identity

**Name:** Summit Dark  
**Aesthetic:** GitHub-dark editorial. Magazine-quality, typography-first, zero-framework. Feels like a polished publication, not a developer README.  
**Tone:** Professional, confident, information-dense but breathable.

---

## Color Palette

```css
:root {
  --bg: #0d1117;          /* Page background — GitHub dark */
  --card: #161b22;        /* Card/section backgrounds */
  --card-alt: #1c2333;    /* Alternate card (e.g., "Connections" boxes) */
  --border: #30363d;      /* Borders, dividers, subtle lines */
  --text: #c9d1d9;        /* Body text */
  --text-muted: #8b949e;  /* Secondary/meta text */
  --heading: #f0f6fc;     /* Headings, emphasis */
  --accent: #58a6ff;      /* Primary accent — links, active states, highlights */
  --green: #7ee787;       /* Success, stats, data callouts, action items */
  --orange: #d29922;      /* Theme/category labels */
  --purple: #bc8cff;      /* "Connections" / cross-reference accent */
  --red: #f85149;         /* Warnings, critical callouts */
  --pink: #f778ba;        /* Spare accent (use sparingly) */
}
```

### When to use each color
- **Accent blue** (`--accent`): Links, active sidebar states, left-border on blockquotes, numbered insight badges, section-title bars
- **Green** (`--green`): Stat numbers in data boxes, action item numbers/borders, TL;DR left-border, positive implications
- **Orange** (`--orange`): Theme/category numbering labels, bullet markers in theme cards
- **Purple** (`--purple`): "Connections to Our Work" section accent, arrow markers in connection lists
- **Red/Pink**: Reserved for warnings or special emphasis. Don't overuse.

---

## Typography

```css
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica, Arial, sans-serif;
font-size: 17px;          /* Root — slightly larger than default for readability */
line-height: 1.7;         /* Generous for long-form reading */
-webkit-font-smoothing: antialiased;
```

### Scale
| Element | Size | Weight | Color |
|---------|------|--------|-------|
| Hero title | `clamp(2.4rem, 5vw, 4rem)` | 800 | `--heading` |
| Meta-narrative heading | `2rem` | 800 | `--heading` |
| Section heading (h2) | `1.6rem` | 700 | `--heading` |
| Talk/card title | `1.65rem` | 700 | `--heading` |
| Section title (h3 inside cards) | `1.05rem` | 600 | `--heading` |
| Body text | `1rem` (17px) | 400 | `--text` |
| TL;DR body | `.95rem` | 400 | `--text` |
| Small labels (TOC, categories) | `.7rem–.82rem` | 700 | `--text-muted` |
| Stat numbers | `1.4rem` | 800 | `--green` |
| Stat labels | `.75rem` | 400 | `--text-muted` |

### Rules
- **Headings** use `letter-spacing: -1px` at hero scale, `2–4px` letter-spacing for uppercase labels
- **Uppercase labels** only for: category/theme numbers, TOC header, TL;DR label, hero superlabel
- **Bold text** inside body uses `--heading` color, not just font-weight — makes it pop on dark bg
- **Italic** reserved for blockquotes and taglines

---

## Layout

### Page structure
```
┌────────────────────────────────────────────┐
│                  HERO                       │
│  label · title · subtitle · date · tagline │
├──────────┬─────────────────────────────────┤
│ SIDEBAR  │          CONTENT                │
│ (TOC)    │   max-width: 900px              │
│ 280px    │   padding: 3rem                 │
│ sticky   │                                 │
│ top: 0   │   [ talk cards ]                │
│ h: 100vh │   [ themes ]                    │
│          │   [ meta-narrative ]             │
│          │   [ action items ]               │
│          │   [ quote gallery ]              │
├──────────┴─────────────────────────────────┤
│                 FOOTER                      │
└────────────────────────────────────────────┘
```

- **Max layout width:** `1400px`, centered
- **Sidebar:** 280px, sticky, full viewport height, scrollable, right border
- **Content:** flex: 1, max-width 900px, generous padding (3rem sides, 6rem bottom)
- **Hero:** Full width, gradient bg (`#161b22` → `--bg`), centered text, bottom border

### Responsive (≤900px)
- Sidebar becomes fixed off-screen drawer (slides in from left)
- Floating TOC toggle button: fixed bottom-right, 48px circle, accent blue, shadow
- Content goes full-width with reduced padding (1.25rem)
- Hero padding shrinks

---

## Components

### 1. Hero Section
```
- Superlabel: uppercase, letter-spacing 4px, accent blue, .75rem
- Title: clamp responsive, weight 800, heading color
- Subtitle: 1.15rem, muted text
- Date: .95rem, muted text
- Tagline: 1.25rem, italic, green, max-width 650px centered
```

### 2. Talk Card
```
- 4rem bottom margin, scroll-margin-top 2rem
- Header: bottom border, talk number (uppercase label, accent blue),
  title (1.65rem, heading), speaker (muted with bold name)
- TL;DR callout: card bg, 3px green left border, rounded right corners,
  green uppercase label, .95rem body
- Section titles: 1.05rem, heading color, 3px accent-blue bar before text
```

### 3. Numbered Insights List
```
- No list-style, counter-reset
- Each item: left-padded 2.5rem, bottom border (subtle)
- Number badge: absolute left, 1.6rem circle, card bg + border,
  accent-blue number, .75rem, bold
- Bold text inside items uses heading color
```

### 4. Blockquotes
```
- 3px accent-blue left border
- Slight blue tinted background: rgba(88,166,255,.04)
- Rounded right corners (6px)
- Italic text
- Attribution: normal style, .8rem, muted, margin-top .25rem
- Gallery variant: 4px border, larger padding, 1.05rem font
```

### 5. Data Stat Boxes
```
- CSS grid: repeat(auto-fill, minmax(180px, 1fr)), .75rem gap
- Each box: card bg, 1px border, 8px radius, centered
- Stat number: 1.4rem, weight 800, green
- Label: .75rem, muted, tight line-height
```

### 6. Connections Box
```
- card-alt background (#1c2333), 8px radius, 1px border
- 1.5rem padding, margin-top 1.5rem
- Section title uses purple bar instead of blue
- List items: purple arrow (→) marker, .9rem, 1.25rem left pad
- Bold text uses heading color
```

### 7. Theme Cards
```
- card bg, 1px border, 10px radius, 2rem padding
- Theme number: orange, uppercase, .7rem, 2px letter-spacing
- Title: 1.2rem, heading color
- Bullet list: orange dot markers
- Implication footer: top border, muted text, bold uses green
```

### 8. Action Items
```
- Flex row: number badge + content
- Number badge: 2rem circle, card bg, 2px green border,
  green number, .85rem bold
- Body: .95rem, bold uses heading color
- Bottom border between items
```

### 9. Sidebar TOC
```
- Links: muted text, 2px transparent left border, 10px left padding
- Hover/active: accent blue text + accent blue left border
- Separator: 1px border between sections
- .82rem font size, thin scrollbar
```

### 10. Footer
```
- Centered, 3rem vertical padding, top border
- Muted text, .85rem
- Links: accent blue, underline on hover
```

---

## Spacing Rules

- **Between talk cards:** 4rem
- **Between sections within a card:** 2rem top margin on section titles
- **Between list items:** .75rem padding top/bottom
- **Card internal padding:** 1.5–2rem
- **Hero to content:** border + natural flow
- **Content bottom padding:** 6rem (breathing room before footer)

---

## Transitions & Effects

- Sidebar link hover: `all .15s` transition
- Mobile sidebar slide: `left .25s` transition
- No other animations. Keep it still and editorial.

---

## Constraints

- **No frameworks.** Pure HTML + CSS.
- **No JavaScript** except a tiny toggle for mobile TOC.
- **Single HTML file** preferred. Inline `<style>` in `<head>`.
- **Responsive** at ≤900px breakpoint.
- **Must feel like a published editorial piece** — not a docs page, not a dashboard, not a blog template.

---

## Usage

Feed this prompt to any agent building an HTML page in the Summit Dark system. Pair with content in markdown format. The agent should:

1. Apply the color palette and CSS variables exactly
2. Use the component patterns above for the content type (talks → talk cards, data → stat boxes, etc.)
3. Maintain the layout structure (hero → sidebar + content → footer)
4. Keep typography scale and spacing consistent
5. Adapt components as needed for new content types while preserving the visual language

---

*Design system extracted from `gejustin-org/pragmatic-summit-2026/index.html` — March 2026*
