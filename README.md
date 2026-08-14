# Milo Sectional Spacing — Visual Reference

A design-engineering reference for the `.spacing-*` utility classes used in Milo sections. Each class applies responsive `padding-block` (top + bottom) to a page section using the S2A design token system.

Open `index.html` directly in a browser — no build step required.

---

## Token Source

| Field | Value |
| --- | --- |
| Package | `@adobecom/s2a-tokens` |
| Verified version | `0.0.20` (tarball: `adobecom-s2a-tokens-0.0.20.tgz`) |
| Repository | `github.com/adobecom/consonant` |
| Last verified | 2026-08-14 |

---

## Changelog

### 2026-08-14 — Synced to `0.0.20`, migrated onto official `--s2a-section-spacing-*`

- `s2a-tokens.css` brought from `0.0.17` to `0.0.20` (picks up the `0.0.18` `--s2a-spacing-128` primitive, the `0.0.19` border-radius refactor, and the `0.0.20` `--s2a-section-spacing-*` scale).
- `sectional-token-styles.css` no longer hand-rolls a 14-rung scale on top of `--s2a-viewport-vertical-padding-*`. That local extension has shipped upstream as the official `--s2a-section-spacing-*` tokens (v0.0.20), so `.spacing-*` classes now reference those directly. The redundant `:root` block re-declaring spacing/layout semantic aliases was also removed — `s2a-tokens.css` already provides them.
- One real value change from the migration: `.spacing-md` at Mobile now resolves to `--s2a-spacing-md` (16px), down from the local scale's `--s2a-spacing-xl` (32px). Every other rung was already an exact match with the official token.
- `.spacing-3xl` / `.spacing-4xl` values that route through `--s2a-layout-lg` move from 124px to 128px (the `0.0.18` primitive fix).

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
| `.spacing-md` | 16 | 40 | 48 |
| `.spacing-lg` | 24 | 40 | 64 |
| `.spacing-xl` | 32 | 64 | 80 |
| `.spacing-2xl` | 40 | 64 | 96 |
| `.spacing-3xl` | 40 | 80 | 128 |
| `.spacing-4xl` | 64 | 128 | 160 |
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
| `.spacing-3xl-static` | 128px |
| `.spacing-4xl-static` | 160px |
| `.spacing-5xl-static` | 240px |

---

## Token architecture

Three-layer resolution chain:

```text
.spacing-sm
  └── padding-block: var(--s2a-section-spacing-sm)
        └── var(--s2a-spacing-lg)          ← mobile base
            var(--s2a-spacing-xl)          ← ≥1024px override
            var(--s2a-spacing-2xl)         ← ≥1280px override
              └── var(--s2a-spacing-24)    ← primitive
                    └── 24px
```

**Layer 1 — Primitives** (`s2a-tokens.css`): raw values like `--s2a-spacing-24: 24px`.

**Layer 2 — Semantic aliases** (`s2a-tokens.css`): human-readable names like `--s2a-spacing-lg: var(--s2a-spacing-24)`.

**Layer 3 — Responsive section-spacing tokens** (`s2a-tokens.css` + media queries): `--s2a-section-spacing-*` redefined at each breakpoint. This is the official package token as of v0.0.20 — `sectional-token-styles.css` no longer redeclares it locally.

Static classes skip layer 3 and reference semantic aliases directly.

---

## Files

| File | Role |
| --- | --- |
| `index.html` | Visual reference page |
| `sectional-token-styles.css` | `.spacing-*` class declarations only — consumes tokens from `s2a-tokens.css` |
| `s2a-tokens.css` | Primitive, semantic, and responsive token source (includes `--s2a-section-spacing-*`) — read-only reference |
| `style.css` | Page chrome styles only |
