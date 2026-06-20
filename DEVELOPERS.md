# Seudrim — Engineering & Brand System

How everything fits together across the org, so it's clear for everyone. (The
public-facing brand copy lives in `profile/README.md`; this is the team reference.)

## The chain: design → package → products

```
Claude Design  →  @seudrim/brand  →  consumers (site, products…)
 (design is born)   (versioned artifact)   (npm/git install)
```

1. **Design source of truth — Claude Design.** The project **"Seudrim"** (start at
   `Index.dc.html`) holds the brand guidelines, the public site design, the
   internal product registry, the mark, and the asset/media kits. All design is
   born here — never invented in code. Read it via the **claude_design MCP**
   (`/design-login` grants `user:design:read/write`).

2. **Distribution — [`@seudrim/brand`](https://github.com/seudrim/brand).** The
   versioned package compiled from Claude Design: design **tokens** (Tailwind v4
   `@theme` + CSS vars + JSON + preset), the framework-agnostic compass **`Seal`**,
   the full **asset kit**, and per-product brands under `products/<name>/`
   (Job Whisper is the first). Private, GitHub Packages. See its README to consume.

3. **Consumers.** [`seudrim/site`](https://github.com/seudrim/site) (the public
   **seudrim.com**) installs `@seudrim/brand` and consumes its tokens + Seal.
   Future product front-ends consume the same package. Change a token or the
   mark **in the package**, bump it, then bump the consumer's dependency.

## House rules

- **Internal stays internal.** `Seudrim Products` / the product registry and
  product *pages* are internal — never published. A product's *logo + card* on
  the public site (e.g. Job Whisper) is fine.
- **The public site is static, zero client-side JS.** Keep it that way (the mark
  is a static SVG; the only `<script>` is JSON-LD metadata).
- **One source of truth.** Don't fork tokens or the Seal into a consumer — fix it
  in `@seudrim/brand` so every project inherits it.

## Naming conventions (from the Claude Design `Index`)

| Thing | Convention | Example |
|---|---|---|
| Pages | `Seudrim <Thing>.dc.html` (Title Case) | `Seudrim Site` |
| Components | `PascalCase.dc.html` | `SeudrimSeal` |
| Brand assets | `seudrim-<thing>-<variant>.svg` (kebab) | `seudrim-mark-gold.svg` |
| Products | `products/<name>/` + `<initials>-<thing>.svg` | `jw-badge.svg` |
| Colors / years | named colors · Roman years | Gilt · `MMXXVI` |

Source of truth at brand and per-product level is a `DESIGN.md` (Google format).

## Where to look

- **Consuming the brand** → [`seudrim/brand` README](https://github.com/seudrim/brand)
- **Site specifics / agent guide** → [`seudrim/site` `CLAUDE.md`](https://github.com/seudrim/site/blob/main/CLAUDE.md)
- **Design** → Claude Design project "Seudrim" → `Index.dc.html`

© MMXXVI Seudrim, Inc. · _Ad Astra · Per Machinam_
