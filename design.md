# Buoyancy Elite Yacht Management — Design System

This document describes the design language, architecture, and content
principles behind the Buoyancy Elite website. The site ships in three
distinct editions, each a complete creative interpretation of the same
company, cross-linked through global navigation.

- **Classic Edition** — `/` (`index.html`)
- **Fable Edition** — `/fable` (`fable.html`)
- **Harbor Edition** — `/harbor` (`harbor.html`)

All three are static single-page HTML/CSS/vanilla-JS documents with no build
step, deployed on Vercel (`cleanUrls: true`, `trailingSlash: false`).

---

## 1. The Company

**Buoyancy Elite Yacht Management** is a premium yacht management and
stewardship firm headquartered in Chicago, operating across all nine Chicago
Park District harbors on Lake Michigan. It serves owners of high-value motor
yachts and sailing vessels, typically 35–70 feet.

**Positioning.** Buoyancy Elite is not a boat-cleaning service, a marine
contractor, a SaaS startup, or a luxury lifestyle brand. It is a professional
vessel management firm that operates like a private estate manager — but for
boats. The team includes USCG-licensed captains.

**Core promise.** Yacht ownership should give back more time than it takes.
Buoyancy Elite removes the friction, worry, and logistics of ownership. The
owner arrives Friday evening to a vessel that is spotless, provisioned,
inspected, and ready to cast off. Everything else is already handled.

**Harbors served.** Montrose, Belmont, Diversey, DuSable, Monroe, Burnham,
31st Street, Jackson Park, 59th Street.

---

## 2. Shared Foundations

These hold across all three editions regardless of visual treatment:

- **Single-page architecture** — anchored sections, in-page navigation.
- **Live Lake Michigan conditions** — NOAA NDBC Buoy 45198 via the
  corsproxy.io CORS proxy, with Open-Meteo marine API as fallback. Renders
  wind, waves, water temp, air temp.
- **Microsoft Clarity** analytics (ID `x2eyivxcmg`) in every `<head>`.
- **Design tokens** expressed as CSS custom properties.
- **IntersectionObserver** for scroll reveals, active-nav tracking, and
  animated counters.
- **Graceful image fallbacks** — every `<img>` degrades to a neutral block
  on load failure rather than showing a broken-image icon.
- **No custom cursor, no parallax, no toast notifications, no carousels on
  desktop.** Dignified, restrained motion only.
- **Editions switcher** — each edition links to the other two in nav, mobile
  menu, and footer.

### Content tone (all editions)

- Confident, factual, operational — never aspirational filler.
- Short sentences, active voice.
- Real marine vocabulary: brightwork, gelcoat, through-hulls, impellers,
  zincs, shrink-wrap, haul-out, lay-up, shakedown, sea trial, chafe gear,
  fender, dock line, bilge, shore power, isinglass.
- Numbers carry authority: 9 harbors, 180 boating days, 48-hour captain
  notice, 24-hour storm response, photographs every visit.
- Banned phrases: "game-changing," "best-in-class," "seamless," "world-class."

---

## 3. Classic Edition (`/`)

The original, broadly appealing interpretation — refined, warm, traditional.

### Palette
| Token | Value | Use |
|---|---|---|
| Navy | `#0B1F33` | Primary dark, headers, footer |
| Gold | `#C2A24C` / `#D4B96A` | Accent, dividers, emphasis |
| Off-white | `#F7F5F0` | Page background |

### Typography
- **Serif:** Cormorant Garamond — headlines.
- **Sans:** Inter — body and UI.

### Notable structure
- Marquee, NOAA conditions strip, about section with accent image.
- **Services grid:** 10 cards laid out `repeat(5, 1fr)` on desktop (two full
  rows, no orphans), `repeat(2, 1fr)` ≤1024px, `1fr` ≤768px.
- Booking modal.
- Content swap markers (`<!-- SWAP: -->`) for phone, email, photos,
  testimonial names, stat numbers, social URLs.

---

## 4. Fable Edition (`/fable`)

A "Quiet Luxury" editorial interpretation, built from first principles.
Sparse, confident, gallery-like.

### Palette
| Token | Value | Use |
|---|---|---|
| Linen | `#F4EFE4` / `#EDE8DC` | Backgrounds |
| Ink | `#18180E` | Text, dark sections |
| Brass | `#8C7856` / `#B09A6E` | Accent |
| Slate | `#2B4556` | Standards section |
| Mid | `#6B6254` | Secondary text |

### Typography
- **Serif:** Playfair Display — display headlines, light italic.
- **Sans:** DM Sans — body and UI.

### Notable structure
- **Fixed 64px left sidenav** (`--nw: 64px`) with dot navigation, hover
  tooltips, and a vertically-rotated "B·E" brand mark. Edition links at the
  foot of the rail.
- Mobile: hidden sidenav, top bar with burger → full-screen ink nav.
- Sections: **Practice** (62/38 split, italic headline), **Conditions**
  (ink-dark NOAA strip), **Work** (Roman-numeral I–VIII service inventory),
  **Standard** (slate, 2×2 principles + pull quote), **Waters** (editorial
  prose + harbor index + seasonal acts), **Record** (full-bleed
  auto-advancing gallery, keyboard arrows), **Begin** (sparse
  bottom-border-only form).

---

## 5. Harbor Edition (`/harbor`)

The maritime-authentic interpretation — operational credibility over
lifestyle aspiration. This is the edition the Stitch prompt is modeled on.

### Palette
| Token | Value | Use |
|---|---|---|
| Navy / Deep | `#142A3D` / `#0C1D2C` | Masthead, dark sections |
| Harbor | `#1E3A52` | Mid-dark surfaces |
| Paper | `#F5F2EA` | Chart-paper background |
| Sand | `#E9E3D4` | Section alternation |
| Chart | `#EFEBDF` | Card surfaces |
| Signal red | `#A8442E` | Accent, CTAs — used sparingly |
| Rope | `#8A7349` | Teak/brass gold-brown |
| Text | `#22313D` | Body |
| Muted | `#5A6873` | Secondary text |

### Typography
- **Serif:** Libre Caslon Text — authoritative, traditional headlines.
- **Sans:** IBM Plex Sans (300–500) — body and UI.
- **Mono:** IBM Plex Mono — all data, timestamps, labels, harbor names,
  conditions. Signals precision.
- All-caps labels: wide tracking (0.16–0.28em), ~0.60rem, monospace.
- Maximum border-radius 2px on any element — no rounded pills.

### Logo / Mark
A **burgee** (swallowtail pennant): split diagonally, signal red left / cream
right, navy circle at center. Beside it "BUOYANCY ELITE" in serif, with
"YACHT MANAGEMENT · CHICAGO" in monospace small caps below.

### Section architecture
0. **Utility bar** — dark, live NOAA conditions ticker in mono + editions
   switcher.
1. **Masthead** (sticky) — burgee, wordmark, nav, phone + "Request a
   Walkthrough" red CTA. Mobile: inline dropdown drawer.
2. **Hero** — full-bleed photo, bottom-left text block, two CTAs, + a navy
   credential strake (Fully insured ◆ USCG-licensed captains ◆
   Photo-documented visits ◆ One dedicated crew).
3. **Services** — four 2×2 spec-sheet cards with "INCLUDED" diamond-bullet
   task lists (Routine Vessel Care, Maintenance & Restoration, Projects &
   Refit Oversight, Captains & On-Water Services).
4. **The Care Log** — copy left, a reproduced log-entry artifact right
   (vessel, berth, date, crew, 5 timestamped tasks, condition flag, photo
   count, send time) entirely in IBM Plex Mono.
5. **How It Works** — four CSS-counter steps (walkthrough → proposal → crew →
   weekly care).
6. **The Season** — navy ruled calendar: Commissioning (Apr–May), Active
   Season (May–Oct), Decommissioning (Oct–Nov), Winter Watch (Dec–Mar).
7. **Harbors** — nine-row data table + storm-check policy card (24-hour
   check after sustained winds top 25 knots).
8. **Owner Words** — three left-border blockquotes with mono vessel specs.
9. **Questions** — six `<details>` accordion items (Q.1–Q.6).
10. **Contact** — deep navy, phone-first left panel + walkthrough form
    (validates name + phone).

### Interaction
- Scroll reveals: opacity + ~16px translateY, no bounce.
- Accordion: smooth height transition, + rotates 45deg to ×.
- Mobile drawer slides down inline (not full-screen).
- Active nav: red bottom-border indicator.
- Hover: red bottom-border on nav links; warm tint on cards and calendar rows.

### What it should feel like
Walking into the office of a well-run boatyard — charts on the walls, a
vessel log on the clipboard, someone with a USCG ticket answering the phone
on the second ring. Not a hotel, not a startup, not an agency portfolio. A
company that has been on the dock since 6am and will still be there Friday
evening.

---

## 6. Responsive Behavior (all editions)

- **Desktop ≥1020px:** full multi-column layouts, horizontal/side nav, phone
  visible.
- **Tablet 768–1020px:** collapsed nav, 2-column services, adjusted tables.
- **Mobile <640px:** single column, dropdown/drawer nav, horizontally
  scrolling tables.

---

## 7. Outstanding Content Swaps

Real values to be supplied before launch (marked in source):

- Phone number, email address.
- Real photography: hero, about/approach, gallery.
- Testimonial names, vessels, harbors.
- Stat numbers.
- Form submission endpoint (email/CRM) — currently `SWAP` stubs.
- Google Analytics GA4 Measurement ID — not yet provided.
