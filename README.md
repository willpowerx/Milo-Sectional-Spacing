# Milo Sectional Spacing — Visual Reference

A design-engineering reference for the `.spacing-*` utility classes used in Milo sections. Each class applies responsive `padding-block` (top + bottom) to a page section using the S2A design token system.

Open `index.html` directly in a browser — no build step required.

---

## What it covers

| Section | Purpose |
| --- | --- |
| **Spacing Classes** | Live cards for every class — tinted padding zones resize with the viewport |
| **Token Chain** | Full resolution table: class → viewport token → primitive → px value per breakpoint |
| **Top / Bottom** | Reference list of `.spacing-*-top` and `.spacing-*-bottom` variants |
| **Static** | Fixed-value classes that bypass responsive tokens |

---

## The scale

### Responsive classes

Values listed as Mobile / Tablet / Desktop (px).

| Class | Mobile | Tablet | Desktop |
| --- | --- | --- | --- |
| `.spacing-none` | 0 | 0 | 0 |
| `.spacing-5xs` | 8 | 8 | 8 |
| `.spacing-4xs` | 12 | 12 | 12 |
| `.spacing-3xs` | 16 | 16 | 16 |
| `.spacing-2xs` | 16 | 24 | 24 |
| `.spacing-xs` | 16 | 24 | 32 |
| `.spacing-sm` | 24 | 32 | 40 |
| `.spacing-md` | 32 | 40 | 48 |
| `.spacing-lg` | 24 | 40 | 64 |
| `.spacing-xl` | 32 | 64 | 80 |
| `.spacing-2xl` | 40 | 64 | 96 |
| `.spacing-3xl` | 40 | 80 | 124 |
| `.spacing-4xl` | 64 | 124 | 160 |
| `.spacing-5xl` | 80 | 160 | 240 |

Breakpoints: Mobile `< 1024px` · Tablet `≥ 1024px` · Desktop `≥ 1280px`

### Static classes

Fixed value at all breakpoints — no responsive override.

| Class | Value |
| --- | --- |
| `.spacing-5xs-static` | 8px |
| `.spacing-4xs-static` | 12px |
| `.spacing-3xs-static` | 16px |
| `.spacing-2xs-static` | 24px |
| `.spacing-xs-static` | 32px |
| `.spacing-sm-static` | 40px |
| `.spacing-md-static` | 48px |
| `.spacing-lg-static` | 64px |
| `.spacing-xl-static` | 80px |
| `.spacing-2xl-static` | 96px |
| `.spacing-3xl-static` | 124px |
| `.spacing-4xl-static` | 160px |
| `.spacing-5xl-static` | 240px |

---

## Token architecture

Three-layer resolution chain:

```text
.spacing-sm
  └── padding-block: var(--s2a-viewport-vertical-padding-sm)
        └── var(--s2a-spacing-lg)          ← mobile base
            var(--s2a-spacing-xl)          ← ≥1024px override
            var(--s2a-spacing-2xl)         ← ≥1280px override
              └── var(--s2a-spacing-24)    ← primitive
                    └── 24px
```

**Layer 1 — Primitives** (`s2a-tokens.css`): raw values like `--s2a-spacing-24: 24px`.

**Layer 2 — Semantic aliases** (`sectional-token-styles.css :root`): human-readable names like `--s2a-spacing-lg: var(--s2a-spacing-24)`.

**Layer 3 — Viewport tokens** (`sectional-token-styles.css` + media queries): responsive tokens like `--s2a-viewport-vertical-padding-sm` redefined at each breakpoint.

Static classes skip layer 3 and reference semantic aliases directly.

---

## Files

| File | Role |
| --- | --- |
| `index.html` | Visual reference page |
| `sectional-token-styles.css` | Viewport token definitions + `.spacing-*` class declarations |
| `s2a-tokens.css` | Primitive and semantic token source — read-only reference |
| `style.css` | Page chrome styles only |
