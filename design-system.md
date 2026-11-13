# Good Food Design System

Single source of truth for the look and feel of Good Food (mobile app and marketing site). If a screen and this file disagree, update one so they match.

## 1. Principles

1. **Black and white first.** The interface is white, black and grey. Color is rare so it means something.
2. **One accent.** Brand green is the only color. Use it for highlights, never for body text.
3. **Bold type, plain layout.** Large heavy headlines, generous space, one clear action per screen.
4. **Thumb friendly.** Every tappable element is at least 44 x 44 px.
5. **Placeholders are honest.** Nutrition numbers that are not yet real data are shown as `[kcal]`, `[g]`, `[min]`.

## 2. Design tokens

### 2.1 Color

| Token | Value | Use |
|---|---|---|
| `--ink` | `#000000` | Primary text, primary buttons, selected chips, active nav, filled icons |
| `--surface` | `#FFFFFF` | Screen background, nav bar, bottom sheets |
| `--surface-subtle` | `#F6F6F6` | Cards, thumbnails inside lists |
| `--surface-muted` | `#EEEEEE` | Inputs, secondary buttons, unselected chips |
| `--tag` | `#E8E8E8` | Default tag background |
| `--divider` | `#E2E2E2` | Nav top border, "or" dividers |
| `--text-secondary` | `#545454` | Meta text, inactive nav labels |
| `--handle` | `#CCCCCC` | Bottom sheet drag handle |
| `--icon-empty` | `#AFAFAF` | Empty rating stars |
| `--green` | `#06C167` | Brand accent (see rules below) |
| `--scrim` | `rgba(0,0,0,.5)` | Dim layer behind sheets |

**Green rules**

- Use green as a **background** with **black** text on top. Never use green text on white (low contrast).
- Allowed uses: the "Food" wordmark highlight, the "From video" tag, the "Approved" tag, the "Surprise me" button, the "meals need approval" banner, the "New collection" plus tile, calendar dots, and the landing page closing band.
- Do not use green for primary buttons. Primary buttons are black.

### 2.2 Typography

Font: **Inter** (weights 400, 500, 600, 700). Fallback: `system-ui, sans-serif`.

| Style | Size / line height | Weight | Tracking | Use |
|---|---|---|---|---|
| Display (landing) | 76 / 1.02 | 700 | -0.03em | Landing hero headline |
| Heading 1 (app) | 34 / 1.08 | 700 | -0.03em | Screen titles |
| Heading 1 (login) | 36 / 1.08 | 700 | -0.03em | Login headline |
| Section title (landing) | 40 | 700 | -0.02em | Landing section titles |
| Heading 2 | 17 | 700 | normal | Card titles, sheet titles (sheet title is 20) |
| Body | 16 | 400 / 500 | normal | Inputs, paragraphs |
| Label | 14 | 700 | normal | Field labels, section labels |
| Meta | 14 | 400 | normal | Secondary info (`--text-secondary`) |
| Tag | 12 | 700 | normal | Tags |
| Nav label | 12 | 600 | normal | Bottom tab labels |
| Button | 17 (ghost 16) | 700 | normal | Buttons |

### 2.3 Spacing

- Base unit: 4 px. Common steps: 4, 6, 8, 12, 16, 20, 24, 32.
- Mobile screen: **20 px** horizontal padding, **32 px** top padding (64 px on login), **16 px** gap between blocks (12 px on dense screens).
- Card padding: 16 px.
- Landing page: 80 px horizontal padding, sections have fixed vertical rhythm.
- Minimum touch target: 44 x 44 px.

### 2.4 Radius

| Element | Radius |
|---|---|
| Cards, thumbnails, collection covers | 16 / 12 px |
| Buttons, inputs | 12 px |
| Chips (pills), day circles | fully round (22 px at 44 px height) |
| Tags | 8 px |
| Small list thumbnails | 8 px |
| Bottom sheet (top corners) | 24 px |

### 2.5 Elevation

Flat by default. Only bottom sheets lift: `box-shadow: 0 -8px 24px rgba(0,0,0,.16)` with a `--scrim` behind the save sheet.

### 2.6 CSS variables

```css
:root {
  --ink: #000000;
  --surface: #ffffff;
  --surface-subtle: #f6f6f6;
  --surface-muted: #eeeeee;
  --tag: #e8e8e8;
  --divider: #e2e2e2;
  --text-secondary: #545454;
  --handle: #cccccc;
  --icon-empty: #afafaf;
  --green: #06c167;
  --scrim: rgba(0, 0, 0, 0.5);

  --font: "Inter", system-ui, sans-serif;

  --radius-card: 16px;
  --radius-control: 12px;
  --radius-tag: 8px;
  --radius-sheet: 24px;

  --space-screen-x: 20px;
  --touch-min: 44px;
}
```

## 3. Components

### Wordmark
"Good" in black plus "Food" on a `--green` background with black text. Inter 700, tracking -0.02em. "Food" has 1 px vertical and 6 px horizontal padding (8 px at large sizes), 4 px left margin, 6 px radius. Sizes: 20 (footer), 24 (login), 26 (site header).

### Buttons
| Variant | Height | Background | Text | Use |
|---|---|---|---|---|
| Primary | 56 | `--ink` | white, 17/700 | Main action (Find meals, Log in, Generate plan, Done) |
| Secondary (ghost) | 52 | `--surface-muted` | black, 16/700 | Not now, Continue with Google or Apple |
| Accent | 48 | `--green` | black | Surprise me |
| Compact | 44 | `--ink` or `--surface-muted` | 15/700 | Approve, Swap, Review (inside cards) |

Full width on mobile, 12 px radius. One primary button per screen.

### Chips
44 px tall pill, 16 px horizontal padding, 15/600. Selected: black background, white text. Unselected: `--surface-muted`, black text. Ingredient chips include a remove (x) button with an accessible label.

### Inputs
52 px tall, `--surface-muted` fill, no border, 12 px radius, 16/500 text. Always paired with a visible label (14/700 or 14 meta). Placeholder uses the browser default grey.

### Cards
`--surface-subtle` background, 16 px radius, 16 px padding, no border. Used for ingredient groups, targets, meals, recipe sections, calendar entries.

### Tags
12/700, 8 px radius, 5 x 10 px padding. Default `--tag` background. Green variants: "From video", "Approved".

### Meal result card
Thumbnail (72 px, white tile with bowl icon), title (Heading 2) with a heart button on the right, meta line ("Uses all 3 ingredients"), then tags for calories, protein, time.

### Heart (like) button
44 x 44 touch area, 24 px icon, black. Outline = not liked, filled = liked. Liking adds the meal to **Liked meals**. Label changes with state ("Save {meal}" / "Remove from liked meals").

### Rating
Five 40 px stars. Filled stars are black, empty stars are `--icon-empty` outline. Shown in the "How was it?" sheet. In lists, rating is a number plus a star ("4 ★").

### Bottom sheet
White, 24 px top radius, 12 px top padding, centered drag handle (40 x 4, `--handle`), 20 px side padding, `--scrim` behind. Used for **Save to collection** and **How was it?**.

### Collection list row (in sheet)
48 px cover, name (Label), count (Meta), and a 24 px checkbox with black accent. Row min height 56 px. The first collection is always **Liked meals** with a black cover and white heart.

### Collection cover
Square, 12 px radius. **Liked meals**: black with a white heart. Others: 2 x 2 mosaic of meal tiles on `--surface-muted`.

### Bottom navigation
76 px tall, white, 1 px `--divider` top border. Three tabs: **Find**, **Plan**, **Cookbook**. 24 px stroke icons (2 px, round caps), 12/600 labels. Active: black. Inactive: `--text-secondary`. Not shown on Login, Recipe or Save.

### Day selector
- Plan setup: seven 44 px circles (M T W T F S S). Selected black, unselected `--surface-muted`.
- Review: five equal-width 44 px pills (Mon to Fri), same colors.
- Calendar: weekday letter, 44 px date circle (today is black), and a 6 px green dot under days with planned meals.

### Calendar entry
Time column (52 px, meta) plus a card with meal slot (meta), meal name (Heading 2) and macros (meta).

### Banner
Full-width card with `--green` background, Label text and a compact black button. Used for "{n} meals need approval".

### Toggle row
Card with label, one-line helper text and a 24 px checkbox (black accent). Example: "Use my cookbook first".

## 4. Icons

- 24 px, 2 px stroke, round caps and joins, `currentColor`.
- Mark every decorative icon `aria-hidden="true"`; give icon-only buttons an `aria-label`.
- No emoji as icons. Brand logos (Google, Apple) must follow each company's brand guidelines if used on sign-in buttons.

## 5. Layout

| Context | Size |
|---|---|
| Mobile screen | 390 x 844 px |
| Landing page | 1280 px wide, sections 320 to 620 px tall |
| Spacing between screens on the design canvas | 80 px |

Landing page order: header, hero with phone mockup, How it works (3 cards), Features (black band, 3 columns), closing call to action (green band), footer.

## 6. Screen inventory (user flow)

1. Landing page
2. Login
3. Find (ingredients, targets, video link)
4. Results
5. Recipe and rating
6. Save to collection
7. Cookbook (collections grid)
8. Collection (meal list, Surprise me)
9. Plan your week
10. Review and approve
11. Calendar

## 7. Accessibility

- Text contrast: black on white and `--text-secondary` on white or `--surface-subtle` meet WCAG AA. Black text on `--green` also passes.
- All inputs have visible labels. Checkboxes and icon buttons have accessible names.
- Minimum touch target 44 x 44 px.
- Do not rely on color alone: selected chips also change text color, liked hearts change from outline to filled, approved meals carry a text tag.
- Add a visible focus ring when building for the web, for example `outline: 2px solid #000; outline-offset: 2px`.

## 8. Content conventions

- Voice: short, direct, friendly. Sentence case for all UI text.
- Button labels are verbs: Find meals, Generate plan, Approve, Save to collection.
- Use the typographic apostrophe in copy (’).
- Nutrition per serving is written `[kcal]`, `[g] protein`, `[min]` until real data is wired in.
- Use the same words everywhere: **meal** (not dish), **collection** (not playlist or folder), **cookbook** (the whole library).
