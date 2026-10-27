---
version: alpha
name: Expense Tracker
description: Mobile-first visual system for a Vietnamese student expense tracker.
---

# Expense Tracker — Design System

This document describes the existing visual identity of the "Sổ chi tiêu" expense
tracker app, extracted from its live source code. Use it to generate new screens in
Google Stitch that match the current product exactly. Do not restyle, re-theme, or
"improve" anything — replicate what is documented here.

## Overview

A calm, mobile-first money app for Vietnamese students. The interface is a single
centered phone-width column (max 420 px) on a warm off-white background. One deep
emerald/teal carries all primary actions and the home hero; one amber carries all
budget warnings; one red carries destructive and over-budget states. Money figures
are the heroes of every screen: they are large, extra-bold, and set in a display
font with tabular numerals so digits align. Surfaces are soft and rounded (16–36 px
radii), shadows are low and tinted green, and motion is gentle (rise-in animations,
slowly filling progress rings).

Design principles to preserve:

- **Remaining money first.** Every budget view leads with "how much is left", not
  "how much was spent".
- **One accent per meaning.** Teal = primary/healthy, amber = approaching limit,
  red = over limit or destructive. Never recolor these meanings.
- **Soft, tactile surfaces.** Large radii, soft tinted shadows, press-down feedback
  on every tappable element.
- **Vietnamese language, Vietnamese formats.** UI copy is Vietnamese; numbers use
  `vi-VN` grouping (dots as thousand separators) and the ₫ symbol.

## Colors

All colors are defined as oklch CSS custom properties; the token values below are
the canonical CSS color strings.

```yaml
colors:
  background: "oklch(0.976 0.009 85)"
  foreground: "oklch(0.26 0.012 160)"
  card: "oklch(0.995 0.004 85)"
  primary: "oklch(0.43 0.085 163)"
  primary-foreground: "oklch(0.985 0.01 160)"
  primary-deep: "oklch(0.33 0.07 165)"
  primary-soft: "oklch(0.93 0.045 163)"
  mint: "oklch(0.86 0.1 165)"
  mint-soft: "oklch(0.95 0.035 165)"
  secondary: "oklch(0.945 0.01 85)"
  muted-foreground: "oklch(0.5 0.012 160)"
  warning: "oklch(0.77 0.14 62)"
  warning-soft: "oklch(0.955 0.04 70)"
  warning-foreground: "oklch(0.45 0.11 50)"
  destructive: "oklch(0.56 0.17 28)"
  destructive-foreground: "oklch(0.99 0 0)"
  border: "oklch(0.92 0.01 85)"
  track: "oklch(0.92 0.012 85)"
```

Usage and rendered hex approximations:

- `background` (#F7F5EE): app background; warm off-white with a slight cream tint.
- `foreground` (#303A34): primary text; very dark desaturated green-gray.
- `card` (#FDFCF9): cards, bottom nav pill, dialog sheet, chips on colored surfaces.
- `primary` (#2E6A5C): primary buttons, FAB, active chips, selected category tile,
  healthy progress bar fill.
- `primary-foreground` (#F5FBF7): text and icons on primary surfaces.
- `primary-deep` (#1F5043): hover state of primary buttons; emphasized teal text on
  soft surfaces.
- `primary-soft` (#DBEDE2): soft teal tint for subtle highlighted areas.
- `mint` (#B2E4CD): healthy ("ok") progress ring fill.
- `mint-soft` (#E9F4EC): category icon chip background; active bottom-nav item
  background.
- `secondary` (#EDEAE0): inactive chips, text inputs, secondary buttons; warm light
  gray.
- `muted-foreground` (#6F7A72): secondary text, dates, placeholders, inactive icons.
- `warning` (#D89A2C): near-limit progress fill; amber.
- `warning-soft` (#F8ECD6): warning card background and Budget Detail hero
  background; pale amber.
- `warning-foreground` (#8B5A0F): text and icons on warning surfaces; dark
  amber-brown.
- `destructive` (#BF4B32): over-budget progress, error messages, destructive
  buttons; muted red.
- `destructive-foreground` (#FCFCFC): text on destructive buttons.
- `border` (#E5E2D9): hairline borders and dividers.
- `track` (#E4E2D8): empty track of progress bars and rings.

Status color mapping (do not change):

- `ok` (under 80% of budget) → `mint` fill on `track`; `mint-soft` badge with
  `primary-deep` text.
- `near` (80–100%) → `warning` fill; `warning-soft` badge with `warning-foreground`
  text.
- `over` (above 100%) → `destructive` fill; `destructive` at 10% opacity badge
  background with `destructive` text.

## Typography

Two font families, loaded from Google Fonts: **Be Vietnam Pro** (400/500/600/700) is
the body font for all text, chosen for full Vietnamese diacritic support;
**Plus Jakarta Sans** (600/700/800) is the display font applied to every money
amount and percentage, always with tabular numerals.

```yaml
typography:
  display-amount:
    fontFamily: "Plus Jakarta Sans"
    fontSize: "38px"
    fontWeight: 800
    lineHeight: 1
    letterSpacing: "-0.02em"
  display-percentage:
    fontFamily: "Plus Jakarta Sans"
    fontSize: "46px"
    fontWeight: 800
    lineHeight: 1
    letterSpacing: "-0.02em"
  input-amount:
    fontFamily: "Plus Jakarta Sans"
    fontSize: "48px"
    fontWeight: 800
    lineHeight: 1
    letterSpacing: "-0.02em"
  financial-stat:
    fontFamily: "Plus Jakarta Sans"
    fontSize: "20px"
    fontWeight: 700
    lineHeight: 1.2
    letterSpacing: "-0.02em"
  screen-title:
    fontFamily: "Be Vietnam Pro"
    fontSize: "16px"
    fontWeight: 600
    lineHeight: 1.4
    letterSpacing: "0px"
  section-title:
    fontFamily: "Be Vietnam Pro"
    fontSize: "16px"
    fontWeight: 600
    lineHeight: 1.4
    letterSpacing: "0px"
  body:
    fontFamily: "Be Vietnam Pro"
    fontSize: "15px"
    fontWeight: 400
    lineHeight: 1.5
    letterSpacing: "0px"
  label:
    fontFamily: "Be Vietnam Pro"
    fontSize: "14px"
    fontWeight: 400
    lineHeight: 1.5
    letterSpacing: "0px"
  chip:
    fontFamily: "Be Vietnam Pro"
    fontSize: "14px"
    fontWeight: 600
    lineHeight: 1.4
    letterSpacing: "0px"
  category-label:
    fontFamily: "Be Vietnam Pro"
    fontSize: "13px"
    fontWeight: 500
    lineHeight: 1.4
    letterSpacing: "0px"
  navigation-label:
    fontFamily: "Be Vietnam Pro"
    fontSize: "11px"
    fontWeight: 500
    lineHeight: 1.4
    letterSpacing: "0px"
```

Usage rules:

- `display-amount`: the home hero "Còn lại" remaining amount.
- `display-percentage`: the Budget Detail ring percentage.
- `input-amount`: the Add Expense amount field; shrinks to 40px beyond 8 digits.
- `financial-stat`: spent/remaining figures on Budget Detail; also transaction
  amounts (15px bold variant of the same display font).
- `screen-title`: centered header titles. `section-title`: "Gần đây", "Chi nhiều
  nhất".
- `body`: transaction names, dialog body. `label`: dates, secondary lines, helper
  text.
- `chip`: date chips, badges, small buttons. `category-label`: labels under
  category selector tiles. `navigation-label`: bottom navigation labels.
- Every money amount and percentage uses the display font with tabular-nums.
- Amounts are formatted vi-VN: 1.550.000 ₫ (dot thousands separator, ₫ suffix).
- Percentages allow one decimal: 84,5% (comma decimal separator).

## Layout

Mobile-first single column; the app is a phone app and is never wider than a phone.

```yaml
spacing:
  xs: "4px"
  sm: "8px"
  md: "12px"
  lg: "16px"
  xl: "20px"
  section: "28px"
  page-gutter: "20px"
  hero-bottom: "32px"
  content-bottom-clearance: "176px"
```

Layout rules:

- **App shell:** max-width 420px, horizontally centered, min-height 100vh,
  `background` color.
- **Page padding:** 20px horizontal (`page-gutter`); the Budget Detail hero uses
  12px horizontal padding.
- **Section spacing:** 28px vertical between home sections (`section`).
- **Header:** 56px tall; icon button left, centered title, optional icon button
  right.
- **Home hero:** full-width block with 36px bottom corner radius; 16px top padding,
  32px bottom padding (`hero-bottom`), 20px sides; contains the title row, the
  248px progress ring, and the spent/limit caption.
- **Bottom navigation:** fixed to the bottom, centered, max-width 420px; 12px side
  padding; bottom padding is max(12px, safe-area-inset-bottom); the container is a
  card-colored pill with 28px radius, 6px inner padding, and the nav shadow.
- **FAB:** fixed 92px from the bottom, right-aligned within the 420px column.
- **Content clearance:** home content gets 176px bottom padding
  (`content-bottom-clearance`) so it clears the FAB and nav.
- **Responsive:** no breakpoints; the layout is fixed at ≤420px and centered on
  larger screens. The date chip row wraps to two lines on very narrow screens.
- **Safe area:** the bottom nav and the sticky submit bar use
  `env(safe-area-inset-bottom)`.

## Elevation & Depth

Shadows are soft, large-blur, and tinted with the deep teal of the palette — never
pure black. Most surfaces are flat; elevation is reserved for floating elements.

- **Card shadow:** `0 1px 2px oklch(0.3 0.03 160 / 5%), 0 8px 24px -8px oklch(0.3
  0.03 160 / 12%)` — subtle card lift (defined in the system; most cards are
  currently flat).
- **FAB shadow:** `0 10px 24px -8px oklch(0.33 0.07 165 / 60%)` — FAB, primary
  submit button, selected category tile, success checkmark.
- **Nav shadow:** `0 12px 32px -12px oklch(0.3 0.03 160 / 28%)` — bottom navigation
  pill.
- **Overlays:** the success overlay uses `background` at 90% opacity with backdrop
  blur; the confirm sheet uses a `foreground` (dark) scrim at 40% opacity, no blur.

## Shapes

Base radius is 16px; larger radii are built from it. Fully rounded pills are used
for all buttons, chips, and badges.

```yaml
rounded:
  base: "16px"
  icon-chip: "16px"
  category-tile: "20px"
  card: "28px"
  navigation: "28px"
  hero-bottom: "36px"
  sheet-top: "32px"
  pill: "9999px"
  full: "9999px"
```

Shape rules:

- Buttons are always pills (fully rounded), never rounded rectangles.
- Cards and the nav container use 28px (`card` / `navigation`).
- Hero sections bleed to the screen edges with a 36px bottom radius
  (`hero-bottom`).
- The confirm sheet is a bottom sheet with a 32px top radius (`sheet-top`).
- Icon chips and text inputs use 16px (`icon-chip` / `base`); category selector
  tiles use 20px (`category-tile`).
- Progress bars and rings have rounded line caps; icon buttons are 48px circles
  (`full`).

## Components

```yaml
components:
  home-hero:
    backgroundImage: "radial-gradient(120% 90% at 85% 0%, oklch(0.5 0.1 160) 0%, oklch(0.33 0.07 165) 62%)"
    textColor: "{colors.primary-foreground}"
    roundedBottom: "{rounded.hero-bottom}"
  progress-ring-home:
    size: "248px"
    strokeWidth: "14px"
    sweep: "250deg"
    trackColor: "oklch(0.985 0.01 160 / 15%)"
    fillColor: "{colors.mint}"
    rounded: "{rounded.full}"
  progress-ring-budget:
    size: "232px"
    strokeWidth: "20px"
    sweep: "360deg"
    trackColor: "{colors.card}"
    fillColor: "{colors.warning}"
    rounded: "{rounded.full}"
  progress-bar:
    height: "8px"
    trackColor: "{colors.track}"
    fillColor: "{colors.primary}"
    rounded: "{rounded.pill}"
  status-badge-safe:
    backgroundColor: "{colors.mint-soft}"
    textColor: "{colors.primary-deep}"
    typography: "{typography.chip}"
    rounded: "{rounded.pill}"
    paddingX: "12px"
    paddingY: "6px"
  status-badge-warning:
    backgroundColor: "{colors.warning-soft}"
    textColor: "{colors.warning-foreground}"
    typography: "{typography.chip}"
    rounded: "{rounded.pill}"
    paddingX: "12px"
    paddingY: "6px"
  status-badge-exceeded:
    backgroundColor: "oklch(0.56 0.17 28 / 10%)"
    textColor: "{colors.destructive}"
    typography: "{typography.chip}"
    rounded: "{rounded.pill}"
    paddingX: "12px"
    paddingY: "6px"
  transaction-row:
    minHeight: "64px"
    gap: "14px"
    titleTypography: "{typography.body}"
    dateTypography: "{typography.label}"
    amountColor: "{colors.foreground}"
  category-icon-chip:
    size: "44px"
    rounded: "{rounded.icon-chip}"
    backgroundColor: "{colors.mint-soft}"
    iconColor: "{colors.primary-deep}"
  category-selector-item:
    width: "72px"
    tileSize: "56px"
    rounded: "{rounded.category-tile}"
    backgroundColor: "{colors.mint-soft}"
    iconColor: "{colors.primary-deep}"
    labelTypography: "{typography.category-label}"
    labelColor: "{colors.muted-foreground}"
  category-selector-item-selected:
    width: "72px"
    tileSize: "56px"
    rounded: "{rounded.category-tile}"
    backgroundColor: "{colors.primary}"
    iconColor: "{colors.primary-foreground}"
    labelTypography: "{typography.category-label}"
    labelColor: "{colors.primary-deep}"
  bottom-navigation-item:
    minHeight: "56px"
    rounded: "{rounded.base}"
    textColor: "{colors.muted-foreground}"
    typography: "{typography.navigation-label}"
  bottom-navigation-item-active:
    minHeight: "56px"
    rounded: "{rounded.base}"
    backgroundColor: "{colors.mint-soft}"
    textColor: "{colors.primary-deep}"
    typography: "{typography.navigation-label}"
  button-primary:
    height: "56px"
    rounded: "{rounded.pill}"
    backgroundColor: "{colors.primary}"
    textColor: "{colors.primary-foreground}"
    typography: "{typography.screen-title}"
  button-primary-disabled:
    height: "56px"
    rounded: "{rounded.pill}"
    backgroundColor: "{colors.primary}"
    textColor: "{colors.primary-foreground}"
    typography: "{typography.screen-title}"
  button-secondary:
    height: "48px"
    rounded: "{rounded.pill}"
    backgroundColor: "{colors.secondary}"
    textColor: "{colors.foreground}"
    typography: "{typography.chip}"
  button-destructive:
    height: "48px"
    rounded: "{rounded.pill}"
    backgroundColor: "{colors.destructive}"
    textColor: "{colors.destructive-foreground}"
    typography: "{typography.chip}"
  icon-button:
    size: "48px"
    rounded: "{rounded.full}"
    backgroundColor: "transparent"
    iconColor: "{colors.foreground}"
  fab:
    height: "56px"
    rounded: "{rounded.pill}"
    backgroundColor: "{colors.primary}"
    textColor: "{colors.primary-foreground}"
    typography: "{typography.screen-title}"
  date-chip:
    minHeight: "48px"
    paddingX: "16px"
    rounded: "{rounded.pill}"
    backgroundColor: "{colors.secondary}"
    textColor: "{colors.foreground}"
    typography: "{typography.chip}"
  date-chip-active:
    minHeight: "48px"
    paddingX: "16px"
    rounded: "{rounded.pill}"
    backgroundColor: "{colors.primary}"
    textColor: "{colors.primary-foreground}"
    typography: "{typography.chip}"
  text-input:
    height: "48px"
    rounded: "{rounded.base}"
    backgroundColor: "{colors.secondary}"
    textColor: "{colors.foreground}"
    paddingX: "16px"
    typography: "{typography.body}"
  amount-input:
    backgroundColor: "transparent"
    textColor: "{colors.foreground}"
    typography: "{typography.input-amount}"
  error-hint:
    textColor: "{colors.destructive}"
    typography: "{typography.label}"
  warning-card:
    rounded: "{rounded.card}"
    backgroundColor: "{colors.warning-soft}"
    padding: "16px"
  success-overlay:
    backgroundColor: "oklch(0.976 0.009 85 / 90%)"
    iconBackgroundColor: "{colors.primary}"
    iconColor: "{colors.primary-foreground}"
  confirm-sheet:
    rounded: "{rounded.sheet-top}"
    backgroundColor: "{colors.card}"
    padding: "24px"
```

Component behavior notes:

- **Progress rings** are SVG rings with rounded caps showing budget usage; the fill
  animates over 1200ms ease-out on mount. The home variant is a 250° arc with the
  gap at the bottom, drawn on the gradient hero with a white 15% track; it contains
  the "Còn lại" label, the 38px remaining amount, and the "đã dùng X%" caption.
  The budget variant is a full 360° circle on the amber hero with a card-colored
  track; it contains the 46px percentage and the month label. Fill color follows
  status: `mint` (ok) / `warning` (near) / `destructive` (over).
- **Progress bar:** 8px rounded bar on a `track` background; width animates over
  1000ms ease-out; fill follows the same status colors.
- **Status badges** pair an icon with a fixed Vietnamese label: safe → check icon +
  "Ổn định"; warning → triangle icon + "Sắp chạm hạn mức"; exceeded → alert icon +
  "Vượt hạn mức".
- **Transaction row:** category icon chip | name (truncated) + date | right-aligned
  amount in the display font, bold, prefixed with −.
- **Category selector:** horizontally scrolling row of 7 items with the scrollbar
  hidden; the selected tile scales to 105% with the FAB shadow over 300ms.
- **Bottom navigation:** four items (Trang chủ, Giao dịch, Ngân sách, Hồ sơ) inside
  the floating pill container described in Layout.
- **Primary button:** full-width; hover darkens to `primary-deep`; while saving it
  shows a spinner and "Đang lưu…". The disabled state keeps the same colors and
  removes press scaling.
- **Icon button:** hover shows a `secondary` background wash; 20px icon.
- **FAB:** plus icon + "Thêm khoản chi", FAB shadow, fixed above the bottom nav.
- **Text input:** filled, borderless; focus shows a 2px `primary` ring at 40%
  opacity.
- **Amount input:** borderless, transparent, centered; grows with its content;
  placeholder "0" in `muted-foreground` at 40% opacity; ₫ suffix in 28px bold
  `muted-foreground`.
- **Error hint:** appears below the field with the rise animation; 16px alert icon.
- **Warning card:** home card for a category at ≥80% of budget: category chip +
  name + remaining amount, large amber percentage, progress bar, status badge,
  chevron right.
- **Success overlay:** full-screen blurred overlay; 80px `primary` circle with FAB
  shadow containing a white check (40px, strokeWidth 2.5) that pops in; "Đã lưu"
  label below.
- **Confirm sheet:** bottom sheet on the dark scrim; 18px semibold title, 15px
  muted body, destructive button above a secondary button.

Interaction states shared by all tappable elements (`pressable` utility):

- Press/active: scales down to 97% over 150ms.
- Hover: background darkens (e.g. primary → `primary-deep`) over 200ms.
- Disabled: press scaling is removed.

## Motion

| Motion | Keyframes | Duration | Easing |
| --- | --- | --- | --- |
| `rise` | opacity 0 → 1, translateY 12px → 0 | 500ms | cubic-bezier(0.2, 0.8, 0.2, 1) |
| `pop` | scale 0.96 → 1.03 → 1 | 250ms | cubic-bezier(0.2, 0.8, 0.2, 1) |
| `check` | opacity 0 → 1, scale 0.6 → 1 | 450ms | cubic-bezier(0.2, 0.9, 0.3, 1.3) |
| `ring-fill` | — | 1200ms | ease-out |
| `bar-fill` | — | 1000ms | ease-out |
| `press` | — | 150ms | ease |
| `color-transition` | — | 200ms | ease |

Motion rules:

- `rise` is the entrance animation for the hero, cards, sections, and overlays;
  staggered with 60–150ms delays.
- `check` is reserved for the success checkmark.
- `ring-fill` and `bar-fill` play once on mount as the progress visualizations fill.
- `press` is the scale-to-0.97 active state on every tappable element.
- `color-transition` covers chip and button background/color changes (200–300ms).
- The saving state uses a standard rotating spinner (Loader2).
- Under `prefers-reduced-motion`, all animation and transition durations collapse
  to ~0ms.

## Iconography

- Library: **Lucide** icons only.
- Default stroke width: **1.8** for decorative icons; 2.0 for badge icons; 2.4 for
  the FAB plus; 2.5 for the success check.
- Sizes: 16px (badges, hints, chevrons), 20px (header icon buttons, category
  chips), 22px (bottom nav), 24px (category selector tiles), 40px (success check).
- All decorative icons are `aria-hidden`; interactive icons always have a
  Vietnamese accessible label on their button.
- Category mapping: Ăn uống → utensils-crossed, Đi lại → bike, Học tập → book-open,
  Nhà ở → home, Hóa đơn → receipt, Mua sắm → shopping-bag, Giải trí → film.
- Navigation mapping: Trang chủ → house, Giao dịch → arrow-left-right,
  Ngân sách → pie-chart, Hồ sơ → user-round.
- Status mapping: ok → check-circle-2, near → alert-triangle, over → circle-alert.

## Content Style

- Language: **Vietnamese** throughout; `lang="vi"`.
- Tone: short, plain, friendly labels; no jargon. Examples: "Còn lại", "đã dùng
  84,5%", "Thêm khoản chi", "Lưu khoản chi", "Đã lưu", "Bỏ khoản chi này?".
- Numbers: `vi-VN` locale — 10.000.000 ₫, 84,5%. The ₫ symbol follows the amount
  with a thin space; in the hero the ₫ is smaller (about half the digit size) and
  semi-transparent.
- Dates: "Hôm nay" for today, otherwise dd/mm/yyyy (23/10/2026).
- Negative amounts in transaction lists are prefixed with a minus sign (−45.000 ₫).
- Status labels are fixed strings: "Ổn định" / "Sắp chạm hạn mức" / "Vượt hạn mức".
- Validation messages are polite and direct: "Nhập số tiền lớn hơn 0 ₫.", "Chọn một
  danh mục cho khoản chi.", "Ngày phát sinh không thể ở tương lai."

## Screen Patterns

### Home (`/`)

1. Emerald radial-gradient hero (36px bottom radius): "Trang chủ" title, month
   selector chip ("Tháng 10/2026" with chevron), the 248px partial progress ring
   with the remaining amount as the dominant figure, and a "spent / limit" caption
   below the ring.
2. Zero or more amber warning cards for categories at ≥80% of their budget,
   staggering in with rise animations.
3. "Gần đây" (Recent) section: title + "Tất cả" text action, then up to 3
   transaction rows.
4. Floating "Thêm khoản chi" FAB above the floating pill bottom navigation.

### Add Expense (`/add`)

1. Plain header: close (X) icon button left, centered "Khoản chi mới" title.
2. Large centered amount input (48px display font) with ₫ suffix.
3. Horizontal scrolling category selector (7 tiles).
4. Date chip group: "Hôm nay" / "Hôm qua" / "Chọn ngày" (custom date picker chip).
5. Collapsible "Thêm chi tiết" disclosure (chevron rotates 180°) revealing "Nơi
   chi" and "Ghi chú" filled inputs.
6. Sticky bottom save button (blurred background bar, safe-area padding):
   full-width primary button "Lưu khoản chi".
7. On save: spinner state → full-screen success overlay with animated check →
   returns Home. On close with unsaved content: unsaved-changes confirmation
   bottom sheet.

### Budget Detail (`/budget/:category`)

1. Pale amber hero (36px bottom radius): back button, centered category chip +
   name, insights (sparkles) icon button.
2. The 232px full-circle progress ring with the usage percentage as the dominant
   figure and the month label beneath; status badge below the ring.
3. Two-column financial stats row ("đã dùng" / "còn lại") separated by a hairline
   divider.
4. "Chi nhiều nhất" (Top expenses) list of up to 4 transaction rows, then a
   secondary pill button "Xem cả N giao dịch".

## Accessibility

- Touch targets are at least 48px (icon buttons, chips, nav items, list rows are
  56–64px).
- All icon-only buttons have Vietnamese `aria-label`s; decorative icons are
  `aria-hidden`.
- The category selector is a real `radiogroup` with `role="radio"` and
  `aria-checked`.
- Form fields are associated with error messages via `aria-describedby` and
  `aria-invalid`; on submit, focus moves to the first invalid field.
- The confirm dialog uses `role="alertdialog"` with `aria-modal` and a labelled
  title; the success overlay uses `role="status"`.
- Focus is visible: inputs get a 2px `primary` ring at 40% opacity.
- Color is never the only signal: budget status always pairs color with an icon
  and a text label.
- `prefers-reduced-motion` collapses all animations and transitions.
- The html element is `lang="vi"`.

## Do's and Don'ts

Do:

- Lead every budget view with the remaining amount in large display-font numerals.
- Use teal for primary actions and healthy states, amber for near-limit, red for
  over-limit and destructive actions — consistently, everywhere.
- Use fully rounded pill buttons and 28px cards on the warm off-white background.
- Format all money as vi-VN with the ₫ suffix and tabular numerals.
- Keep Vietnamese copy short and plain; pair every status color with an icon + label.
- Animate entrances with the soft rise animation and let rings/bars fill slowly.
- Respect the 420px centered column and safe-area insets.

Don't:

- Don't introduce additional gradients. The Home hero is the only approved gradient.
- Don't introduce new accent colors or a dark mode.
- Don't use square or lightly rounded (4–8px) buttons; buttons are always pills.
- Don't use heavy black shadows; shadows are soft and green-tinted.
- Don't render money in a body font or without tabular numerals.
- Don't mix English into UI copy, and don't reword the fixed status labels.
- Don't add visible borders to inputs; they are filled, borderless, and rounded.
- Don't widen the layout beyond 420px or add desktop multi-column layouts.
- Don't use icons from any library other than Lucide.
