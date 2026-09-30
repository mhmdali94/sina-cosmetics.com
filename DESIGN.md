---
name: Sina Cosmetics
description: A grayscale-first Arabic cosmetics catalog with one signal-pink accent for wayfinding
colors:
  ink: "#212121"
  muted: "#a0a0a0"
  border-light: "#eee"
  border: "#ccc"
  surface: "#ffffff"
  signal-pink: "#ff3aa0"
  sale-red: "#f70d28"
typography:
  headline:
    fontFamily: "Cairo, Helvetica, Arial, sans-serif"
    fontWeight: 700
    lineHeight: 1.4
  label:
    fontFamily: "Cairo, Helvetica, Arial, sans-serif"
    fontWeight: 400
  body:
    fontFamily: "Lora, Helvetica, Arial, sans-serif"
    textColor: "{colors.ink}"
rounded:
  sm: "2px"
  md: "5px"
  none: "0px"
  pill: "100%"
components:
  button-primary:
    backgroundColor: "{colors.border-light}"
    textColor: "{colors.ink}"
    rounded: "{rounded.md}"
    padding: "0 15px"
  button-primary-hover:
    backgroundColor: "{colors.border}"
  nav-link-active:
    textColor: "{colors.signal-pink}"
  sale-badge:
    backgroundColor: "{colors.sale-red}"
    textColor: "{colors.surface}"
    rounded: "{rounded.none}"
    padding: "5px 10px"
---

# Design System: Sina Cosmetics

## 1. Overview

**Creative North Star: "The Neighborhood Counter"**

This is the visual system of an existing, live JNews-theme storefront (شركة سيناء لمستحضرات التجميل), scanned as-is rather than designed fresh. Its character is almost entirely grayscale: near-white surfaces, dark-ink text, light hairline borders, and plain gray buttons. Against that quiet field, exactly one accent color appears — Signal Pink (#ff3aa0) — and it is reserved for navigation state, not decoration. The effect reads like a shop counter you already trust: nothing shouts, the products carry the visual weight, and the one spot of color exists purely to tell you where you are, not to sell you something.

This matches PRODUCT.md's "trustworthy and affordable" personality closely, and explicitly rejects the cluttered, banner-heavy marketplace look PRODUCT.md names as an anti-reference — there is no gradient hero, no discount-badge confetti, no stacked promotional color.

**Key Characteristics:**
- Grayscale-dominant surface; color is the exception, not the rule
- One accent (Signal Pink) restricted to navigation wayfinding
- Flat by default; shadows appear only as ambient lift on overlays and popups
- Small, consistent corner rounding (2–5px) on interactive elements; sale badges are hard-cornered (0px)

## 2. Colors

The palette is Restrained by strategy: tinted grayscale neutrals carry the surface, and Signal Pink is the sole named accent, used on well under 10% of any given screen.

### Primary
- **Signal Pink** (`#ff3aa0`): Navigation-only wayfinding color. Marks the active/hovered menu item and the underline beneath it. Not used on buttons, prices, or badges — its rarity is what makes it legible as a signal rather than decoration.

### Secondary
- **Sale Red** (`#f70d28`): Reserved for the WooCommerce "on sale" badge only. A hard, saturated alert color that stands apart from Signal Pink so the two are never confused — one means "you are here," the other means "this is discounted."

### Neutral
- **Ink** (`#212121`): Primary text color, headings, and button labels.
- **Muted Gray** (`#a0a0a0`): Secondary text — prices, breadcrumbs, quantity labels. Signals "supporting information," not "disabled."
- **Border Light** (`#eee`): Hairline dividers, default button background, card separators.
- **Border** (`#ccc`): Slightly stronger border for buttons and input outlines.
- **Surface White** (`#ffffff`): Page and card background.

### Named Rules
**The Signal-Only Rule.** Signal Pink appears in navigation state only — never on a button, a price, or a product card. The moment it shows up anywhere else, it stops meaning "you are here" and starts meaning nothing.

## 3. Typography

**Display/Headline Font:** Cairo, Helvetica, Arial, sans-serif
**Body Font:** Lora, Helvetica, Arial, sans-serif

**Character:** A sans-serif carries the structural elements (headings, navigation, post/product titles) while a serif carries body copy — the inverse of the usual serif-heading/sans-body pairing, which gives headings a plainer, more utilitarian voice and lets body paragraphs feel slightly warmer and more read-friendly.

### Hierarchy
- **Headline** (700 weight, page/section and product-listing titles, line-height 1.4): Cairo. Used for `jeg_post_title` and category/product headings.
- **Label** (400 weight): Cairo. Navigation links, menu items, UI labels.
- **Body** (Lora, color `{colors.ink}`): Paragraph copy inside content blocks and excerpts.

### Named Rules
**The Latin-Serif Gap Rule.** Lora has no Arabic glyphs. Since every page on this site is Arabic (`lang="ar" dir="rtl"`), body text set in Lora silently falls back to the Helvetica/Arial sans stack in practice — the serif declaration only has visible effect on any stray Latin text (SKUs, brand names in English, numerals). Don't treat "Lora" as the real rendered Arabic body font; the sans fallback is what users actually see for Arabic copy.

## 4. Elevation

Flat by default. The overwhelming majority of surfaces (cards, buttons, nav) carry `box-shadow:none`. Depth is reserved for two specific situations: a very light ambient lift on small floating elements (dropdowns, tooltips), and a much larger, deliberately dramatic shadow on full overlays (lightboxes, modal popups) to visually separate them from the page behind.

### Shadow Vocabulary
- **Ambient low** (`box-shadow: 0 1px 3px rgba(0,0,0,.1)`): Small floating UI — dropdowns, small popovers.
- **Ambient card** (`box-shadow: 0 1px 4px rgba(0,0,0,.09)`): Subtle separation for card-like elements that need to lift barely off the page.
- **Overlay lift** (`box-shadow: 0 1px 3px rgba(0,0,0,.1), 0 32px 60px rgba(0,0,0,.1)`): Modals and lightbox overlays — a soft near shadow plus a large diffuse far shadow to read as "floating above everything."

### Named Rules
**The Flat-Until-Floating Rule.** Nothing at rest on the page casts a shadow. Shadows only appear once an element leaves the document flow entirely (dropdown, modal, lightbox) — shadow presence itself communicates "this is temporarily on top of the page," not "this is a card."

## 5. Components

**Feel: quietly confident, no CTA flash.** Buttons are treated as plain utility rather than a branding surface — the accent color is deliberately withheld from them so that no single button competes visually with the product photography or the navigation's pink wayfinding cue.

### Buttons
- **Shape:** 2–5px radius (`{rounded.sm}` / `{rounded.md}`) depending on button size variant; never fully square, never pill-shaped except the "on sale" flag treatment described below.
- **Primary/default:** background `{colors.border-light}` (#eee), text `{colors.ink}` (#212121), 1px `{colors.border}` (#ccc) border, radius `{rounded.md}` (5px), horizontal padding 15px, line-height 35px.
- **Compact variant:** height 26px, font-size 11px, letter-spacing 0.5px, weight 500 — used inline within cart widgets and dense listings.
- **Hover/Focus:** background shifts one step darker toward `{colors.border}`; no color-accent hover treatment on buttons themselves.

### Cards / Containers
- **Corner Style:** none by default on catalog cards; small radius only on discrete UI chrome (buttons, badges).
- **Background:** `{colors.surface}` white.
- **Shadow Strategy:** flat at rest (see Elevation); a light ambient shadow (`0 1px 4px rgba(0,0,0,.09)`) appears only where a card genuinely floats above other content.
- **Border:** `{colors.border-light}` hairlines separate list items rather than card shadows.

### Navigation
- **Style:** Cairo label typography, flat background, no shadow.
- **Default state:** `{colors.ink}` text.
- **Hover/Active state:** text and underline switch to `{colors.signal-pink}` (#ff3aa0) — the only place this color is allowed to appear (see The Signal-Only Rule).

### Sale Badge (signature component)
- Hard-cornered rectangle (`{rounded.none}`, 0px), background `{colors.sale-red}` (#f70d28), white text, uppercase, bold, small padding (5px 10px). Positioned as a corner flag on discounted products. Its squared-off shape and saturated red deliberately contrast with the soft-rounded, muted-gray default button, so a shopper's eye catches "discount" before anything else on the card.

## 6. Do's and Don'ts

### Do:
- **Do** keep Signal Pink (#ff3aa0) exclusive to navigation hover/active state (The Signal-Only Rule).
- **Do** keep buttons neutral gray (#eee background, #212121 text) — quiet, confident, no CTA-flash color.
- **Do** keep shadows flat-at-rest; only apply shadow when an element leaves the page flow (dropdown, modal, lightbox).
- **Do** treat Muted Gray (#a0a0a0) as "supporting information" (prices, breadcrumbs), not as a disabled/inactive signal.
- **Do** verify any new Arabic body copy actually renders in a font with Arabic glyph coverage — don't rely on the Lora declaration.

### Don't:
- **Don't** introduce the cluttered, low-trust AliExpress-style marketplace look named in PRODUCT.md's anti-references — no stacked promotional banners, no cramped repetitive grids, no stock-placeholder padding-out of the catalog.
- **Don't** put Signal Pink on a button, price, or product card. It reads as "you are here," not "buy this" — reusing it elsewhere breaks the one visual signal this system has.
- **Don't** add a drop shadow to elements that sit at rest in the normal page flow (product cards, list items). Shadow means "floating," not "here's a card."
- **Don't** assume Lora is rendering as a serif for Arabic users — it silently falls back to the sans stack, so don't design typography decisions around a serif/sans contrast that Arabic readers won't actually see.
