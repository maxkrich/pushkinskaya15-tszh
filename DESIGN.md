---
name: ТСЖ «Пушкинская 15»
description: Обезличенный справочник нормы закона против факта в доме, подан как официальный реестр
colors:
  paper: "#F7F7F5"
  paper-alt: "#EFEFEC"
  ink: "#1E2328"
  ink-soft: "#383F47"
  navy: "#24344D"
  navy-hover: "#1A2637"
  slate: "#5B6472"
  slate-line: "#D8D9D4"
  confirmed: "#3E6259"
  confirmed-bg: "#E7EEEB"
  needs-check: "#7A5C31"
  needs-check-bg: "#F0E9DD"
  pending: "#5B6472"
  pending-bg: "#E7E7E4"
typography:
  display:
    fontFamily: "ui-serif, Georgia, 'Iowan Old Style', 'Times New Roman', serif"
    fontSize: "clamp(1.75rem, 5vw, 2.5rem)"
    fontWeight: 600
    lineHeight: 1.2
    letterSpacing: "normal"
  body:
    fontFamily: "-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif"
    fontSize: "17px"
    fontWeight: 400
    lineHeight: 1.6
    letterSpacing: "normal"
  label:
    fontFamily: "ui-monospace, 'SFMono-Regular', Menlo, Consolas, 'Liberation Mono', monospace"
    fontSize: "0.72rem"
    fontWeight: 400
    lineHeight: 1.2
    letterSpacing: "0.03em"
rounded:
  sm: "4px"
  pill: "999px"
spacing:
  xs: "8px"
  sm: "16px"
  md: "24px"
  lg: "32px"
  xl: "48px"
  xxl: "64px"
components:
  button-primary:
    backgroundColor: "{colors.navy}"
    textColor: "{colors.paper}"
    rounded: "{rounded.sm}"
    padding: "10px 20px"
    height: "44px"
  button-primary-hover:
    backgroundColor: "{colors.navy-hover}"
    textColor: "{colors.paper}"
  button-secondary:
    backgroundColor: "transparent"
    textColor: "{colors.navy}"
    rounded: "{rounded.sm}"
    padding: "10px 20px"
    height: "44px"
  status-tag-confirmed:
    backgroundColor: "{colors.confirmed-bg}"
    textColor: "{colors.confirmed}"
    rounded: "{rounded.pill}"
  status-tag-needs-check:
    backgroundColor: "{colors.needs-check-bg}"
    textColor: "{colors.needs-check}"
    rounded: "{rounded.pill}"
  status-tag-pending:
    backgroundColor: "{colors.pending-bg}"
    textColor: "{colors.pending}"
    rounded: "{rounded.pill}"
---

# Design System: ТСЖ «Пушкинская 15»

## 1. Overview

**Creative North Star: "The Registry Desk"**

Not a landing page and not a blog — a public records office. Every claim on this site behaves like a filed document: it has a status stamp, a source, and a place it can be checked against. The visual system is built to feel like an official reference desk, calm and procedural, the kind of place where nobody raises their voice because the paperwork speaks for itself. Colour is used the way a records office uses colour: sparingly, and only to carry a status code, never to persuade.

This system explicitly rejects the warm-cream AI-landing-page look (crema background, terracotta accent, serif hero) and rejects alarmism (red, exclamation marks, urgent iconography). Urgency here comes from the numbers themselves — a five-year gap, a nine-figure debt — never from the chrome around them.

**Key Characteristics:**
- Cool, neutral paper — not warm cream, not stark white
- One accent (navy) used for links, primary actions, and "this is the required norm" — nothing else competes with it
- Three muted status colors (confirmed / needs-check / pending) are the only other color in the system, and they never leave their lane (status pills, left-accent stripes, row tints)
- Mono type is the "this is data/a citation/a status" signal throughout — wherever it appears, it means "verifiable," not "technical"
- Zero decorative motion; the one animation in the system (hero card stagger) is gated behind `prefers-reduced-motion`

## 2. Colors

A cool, desaturated palette — paper is grey-white, not cream; the only saturation in the system lives in the three status colors, and even those are muted almost to the point of looking institutional rather than alarming.

### Primary
- **Navy** (`#24344D`, hover `#1A2637`): links, primary buttons, headings' accent role, the "norma" (legal-requirement) side of every norm-vs-fact comparison. The one color allowed to mean "this is the standard."

### Neutral
- **Paper** (`#F7F7F5`): page background.
- **Paper Alt** (`#EFEFEC`): card/section background, one step darker than paper — the "this is a filed record" surface.
- **Ink** (`#1E2328`): body text, headings.
- **Ink Soft** (`#383F47`): secondary body text (ledes, card descriptions).
- **Slate** (`#5B6472`): captions, mono labels, the neutral/"pending" status color doing double duty.
- **Slate Line** (`#D8D9D4`): all hairline borders and dividers.

### Named Rules
**The Status-Only Color Rule.** Confirmed (teal `#3E6259`), Needs-Check (ochre `#7A5C31`), and Pending (slate `#5B6472`) are the only colors on the site besides navy and neutrals. They appear exactly three places: the left accent stripe on a card, the `.status-tag` pill, and (as of the row-tint pass) a faint full-row background on dense tables. They never appear as decoration and never as pure saturated red/green/amber — full-saturation status color is the alarmist look this system explicitly rejects.

**The Dark Mode Is Not an Afterthought Rule.** Every token has a `prefers-color-scheme: dark` counterpart already defined in `css/styles.css`; navy inverts to a lighter `#7C93B8` so it still reads as "the accent" against a dark paper, not as a random hue flip.

## 3. Typography

**Display Font:** ui-serif, Georgia, "Iowan Old Style", "Times New Roman", serif
**Body Font:** -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif
**Label/Mono Font:** ui-monospace, "SFMono-Regular", Menlo, Consolas, "Liberation Mono", monospace

**Character:** A restrained serif for headings only (never body text) reads as "official document," not "editorial" — deliberately scoped to feel like a letterhead, not a magazine. The mono face is the site's second voice: anywhere it appears, it's signaling "this is a citation, a status, or a filed reference number," which trains the reader to trust mono text as verifiable.

### Hierarchy
- **Display / H1** (600, `clamp(1.75rem, 5vw, 2.5rem)`, 1.2 line-height): page titles only.
- **Headline / H2** (600, `clamp(1.35rem, 3.5vw, 1.75rem)`, 1.2): section breaks.
- **Title / H3** (600, 1.15rem, 1.2): card and sub-section titles; inside `.registry-card`, right-margin-cleared to leave room for the stamp.
- **Body** (400, 17px, 1.6): all prose. `main` caps at 760px (712px after padding), which works out to roughly 76–84ch at this font's average character width — at or just past the 65–75ch guideline, not "well inside" it as an earlier draft of this file claimed. Not a real readability problem at this line-height, but worth knowing precisely rather than assuming.
- **Label** (400, 0.72rem, uppercase, 0.03–0.04em tracking): `registry-fields dt`, `.eyebrow`, table headers, status tags — always mono, always the "this is metadata" register.

### Named Rules
**The Serif-Never-Body Rule.** The display serif appears only in h1–h3 and `.site-title`. Body copy is always the system sans. Mixing them elsewhere would blur the "letterhead vs. letter" distinction the whole system depends on.

## 4. Elevation

Flat by default — no shadows anywhere in the current stylesheet. Depth is conveyed by background-tint layering (`--paper` vs `--paper-alt`) and by the left-accent-stripe status color, not by elevation. The one exception is the `.tip-content` hover popover, which uses a soft drop shadow (`0 6px 20px rgba(0,0,0,0.22)`) because it's genuinely floating above the page — the only element in the system that is.

### Shadow Vocabulary
- **Popover** (`box-shadow: 0 6px 20px rgba(0, 0, 0, 0.22)`): `.tip-content` only. Not reused elsewhere.

### Named Rules
**The Flat-By-Default Rule.** Everything at rest is flat. Shadow is reserved for the single element that is actually floating above the document flow (the citation-preview popover), never used to fake depth on cards or buttons.

## 5. Components

### Buttons
- **Shape:** 4px radius, 44px min-height (touch target floor).
- **Primary:** navy fill, paper text, 10px/20px padding, 1px navy border.
- **Hover:** darkens to `--navy-hover`.
- **Secondary:** transparent fill, navy text, navy border; hover fills with `--paper-alt`.
- Used sparingly — two buttons total, both on the homepage hero. This is a reference site, not a conversion funnel; buttons are not the primary interaction.

### Status Tag
- **Style:** pill (`border-radius: 999px`), mono 0.82rem, a small solid dot (`::before`) in `currentColor` leading the label.
- **Three states only:** confirmed (teal), needs-check (ochre), pending (slate) — see Colors § Named Rules. Always paired with a plain-language label (`подтверждено`, `требует проверки`, `на рассмотрении`), never color alone.

### Registry Card (signature component)
The system's one true signature element — a status record rendered as a physical filed document.
- **Shape:** 4px right-corner radius only (left corner square, where the accent stripe sits) — `border-radius: 0 4px 4px 0`.
- **Background:** `--paper-alt`, one step off the page background.
- **Left accent:** 4px solid stripe in the row's status color (confirmed/needs-check/pending) — see the Named Rule below on why this is a deliberate exception, not an oversight.
- **Stamp:** a small mono chip (`.registry-stamp`, e.g. `№А`) pinned top-right, `--paper` background, `--slate-line` border, 2px radius — reads as an actual case-file stamp, not a caption.
- **Fields:** a `dl`/`dt`/`dd` grid (`.registry-fields`), labels in uppercase mono, mimicking a paper form's field/value pairs rather than a paragraph.
- **Reused as:** the homepage's four hero stat cards (`.anomaly-item`) are a compact variant of this exact pattern — same accent-stripe + stamp language, smaller — so the homepage teaches the site's visual grammar before the reader ever reaches the full registry cards.

### Accent-Card Family (claim-box / verdict-box / callout)
Three siblings of the same shape as Registry Card, minus the stamp: `--paper-alt` background, 4px left accent (slate for a quoted claim, navy for a verdict, confirmed-teal for a source callout), `--space-3` padding. They currently duplicate the same four declarations independently in `css/styles.css` rather than sharing a base class — a known small inconsistency, not an intentional variant system.

### Details / Summary (FAQ, year-by-year breakdowns)
- Native `<details>` with the disclosure triangle replaced by a mono `+`/`−` (`summary::before`), consistent with the site's "mono = status/metadata" language.
- `.year-detail` variant wraps it in a full border for the denser per-year 290-постановление breakdowns.

### Tables
- Plain, hairline-bordered, mono uppercase headers. On the two data-dense pages (per-year expense breakdowns), rows carrying a `needs-check` or `pending` status tag get a faint full-row background tint (`table tr:has(> td .status-tag[data-status="..."])`) — the only place status color spreads beyond a stripe or a pill, added specifically so a 40-row table can be scanned by eye.

### Navigation
- Flat text links, `--ink-soft` default, underline + navy on hover/current. 44px min-height row for touch. No dropdown, no mobile hamburger — the nav is short enough (7 items) to always be visible.

## 6. Do's and Don'ts

### Do:
- **Do** keep the status vocabulary to exactly three colors (confirmed/needs-check/pending), always paired with a text label, never color alone.
- **Do** use the mono face as the "this is verifiable" signal — citations, statuses, field labels, document stamps — consistently, so readers learn to trust it.
- **Do** reuse the registry-card accent-stripe-plus-stamp language for any new "here is a filed fact" element, including compact variants (as the homepage hero cards already do), rather than inventing a new card shape.
- **Do** gate any new motion behind `prefers-reduced-motion: no-preference`, and keep it to one deliberate moment per page, not per-element hover flourish.

### Don't:
- **Don't** introduce warm-cream / terracotta / crema tones anywhere — PRODUCT.md names this explicitly as the rejected AI-lending-page look. Paper stays cool grey-white.
- **Don't** use full-saturation red, green, or amber for status, ever — even for a "critical" finding. The muted confirmed/needs-check/pending triad is the ceiling. PRODUCT.md is explicit that urgency comes from facts and numbers, never from alarmist styling.
- **Don't** treat the `border-left: 4px` accent stripe as impeccable's generic "side-stripe border" anti-pattern and "fix" it away. On this project it is the deliberate signature element (Registry Card), reviewed and confirmed earlier in this project's own design pass — not an unintentional default. Leave it.
- **Don't** add a hero-metric / big-number-plus-gradient block. The homepage's four stat cards intentionally use the registry-card language instead, precisely to avoid this SaaS cliché.
- **Don't** add shadows to cards or buttons to fake depth. Depth here is background-tint layering only (see Elevation § Flat-By-Default Rule).
- **Don't** add an uppercase tracked eyebrow above every section as decoration. The one eyebrow pattern in use (`.pointer .eyebrow`) carries real information (норма/действие/факт) — it labels a role, it isn't a kicker template.
