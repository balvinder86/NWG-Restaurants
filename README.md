# 🫐 NWG Restaurants — Bluebird Café & Diner

<div align="center">

![Version](https://img.shields.io/badge/version-1.0.0-4a9fd4?style=for-the-badge)
![Status](https://img.shields.io/badge/status-live-brightgreen?style=for-the-badge)
![HTML](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)

**A premium, high-end single-page restaurant website for Bluebird Café & Diner, Arlington WA.**
Built with zero dependencies — pure HTML, CSS, and vanilla JavaScript.

[Live Preview](#) · [Report Bug](https://github.com/balvinder86/NWG-Restaurants/issues) · [Request Feature](https://github.com/balvinder86/NWG-Restaurants/issues)

</div>

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Design System](#design-system)
- [Page Sections](#page-sections)
- [Animations & Effects](#animations--effects)
- [Breakfast Menu Architecture](#breakfast-menu-architecture)
- [Responsive Breakpoints](#responsive-breakpoints)
- [Getting Started](#getting-started)
- [Deployment](#deployment)
- [Roadmap](#roadmap)
- [Contributing](#contributing)

---

## Overview

**Bluebird Café & Diner** has been a family-owned institution in Arlington, Washington since 1958. This project delivers a modern, luxury-tier website that reflects the café's rich heritage while providing a world-class digital experience.

The site is intentionally built as a **zero-dependency, single-file** application — no frameworks, no build tools, no npm. It opens directly in any browser and can be hosted on any static file server.

```
Business:   Bluebird Café & Diner
Location:   308 N Olympic Ave, Arlington, WA 98223
Phone:      (360) 435-2724
Founded:    1958 by Merle & Florence Peper
```

---

## Features

### User Experience
- **Cinematic loader** — animated bluebird logo with progress bar on every page load
- **Custom cursor** — gold dot with lagged trailing ring (desktop only)
- **Smooth scroll** — native CSS scroll-behavior with parallax hero
- **Scroll-triggered reveals** — elements animate in from left, right, or below via `IntersectionObserver`

### Visual Design
- **3D hero dish** — CSS `rotateX/rotateY` rings that react to mouse position in real time
- **Floating food particles** — 10 food emojis drift upward continuously across the hero
- **3D flip cards** — CSS `perspective` + `rotateY(180deg)` specials cards reveal details on hover
- **Card tilt effect** — menu cards tilt in 3D on mouse movement using `rotateX/rotateY`
- **Animated counters** — statistics count up with an easing curve when scrolled into view
- **Marquee ticker** — infinite scrolling gold strip with brand phrases

### Content
- **Tabbed menu system** — Breakfast / Lunch / Drinks / Weekend Dinner
- **Exact breakfast menu** — two-column layout faithfully replicating the physical printed menu
- **Testimonials** — real guest review quotes
- **Hours & location** — full weekly schedule with online ordering link
- **Mobile hamburger menu** — full-screen overlay navigation

---

## Tech Stack

| Layer | Technology | Notes |
|---|---|---|
| Markup | HTML5 | Semantic, accessible |
| Styling | CSS3 | Custom properties, Grid, Flexbox, `clamp()` |
| Scripting | Vanilla JS (ES6+) | No frameworks or libraries |
| Fonts | Google Fonts | Cormorant Garamond, Inter, Playfair Display |
| Icons | Unicode Emoji | No icon library required |
| Hosting | Any static host | GitHub Pages, Netlify, Vercel, etc. |

---

## Project Structure

```
NWG-Restaurants/
└── bluebird-cafe/
    ├── index.html          # Entire site — HTML + CSS + JS in one file
    └── README.md           # This file
```

> **Why a single file?**
> Zero build steps, zero dependencies, instant load. The entire site — ~1,000 lines — ships in one HTTP request. Ideal for small business deployments where simplicity and reliability matter most.

---

## Design System

### Color Palette

```css
:root {
  --cream:    #eef5fc;   /* Page background — light blue-white      */
  --warm:     #daeaf8;   /* Section alternates — slightly deeper     */
  --gold:     #c8973a;   /* Accent — warm gold for badges & prices   */
  --gold-lt:  #e8bb6a;   /* Light gold — hover states                */
  --deep:     #0b2545;   /* Deep navy — dark section backgrounds      */
  --charcoal: #1a3a6e;   /* Navy charcoal — cards, overlays          */
  --muted:    #4a7fa8;   /* Muted blue — body text, labels           */
  --white:    #ffffff;   /* Pure white                               */
  --sky:      #4a9fd4;   /* Sky blue — primary interactive accent    */
  --sky-lt:   #b8d9f0;   /* Light sky — headings on dark bg          */
  --navy:     #1d3461;   /* Main navy — section headers, menu bars   */
}
```

### Typography

| Role | Font | Weight | Usage |
|---|---|---|---|
| Display / Hero | Cormorant Garamond | 300–600 | Page titles, section headings, prices |
| Body | Inter | 300–600 | Paragraphs, labels, navigation |
| Decorative | Playfair Display | 400, 700 | Pull quotes, specials |

### Spacing Scale
All spacing uses `clamp()` for fluid scaling between viewport sizes:
```css
/* Section padding */
padding: clamp(80px, 12vw, 160px) clamp(24px, 6vw, 100px);

/* Typography */
font-size: clamp(40px, 6vw, 72px);   /* Section titles */
font-size: clamp(52px, 10vw, 120px); /* Hero title     */
```

---

## Page Sections

| # | Section ID | Background | Description |
|---|---|---|---|
| 1 | `#hero` | `--deep` navy | Full-viewport hero with 3D dish, particles, parallax |
| — | `.marquee-strip` | `--navy` | Infinite scrolling brand ticker |
| 2 | `#about` | `--cream` | Founding story, floating logo, animated stats |
| 3 | `#menu` | `--deep` | Tabbed menu — Breakfast, Lunch, Drinks, Weekend |
| 4 | `#experience` | `--warm` | 5-card atmosphere gallery grid |
| 5 | `#specials` | `--cream` | 3D flip cards for signature dishes |
| — | `#cta-strip` | `--navy` | Full-width call-to-action with phone link |
| 6 | `#testimonials` | `--cream` | Guest review cards |
| 7 | `#visit` | `--deep` | Hours, location, contact info |
| — | `footer` | `--deep` | 4-column footer with social links |

---

## Animations & Effects

### CSS Animations

| Name | Element | Description |
|---|---|---|
| `birdFloat` | Loader, about emoji | Vertical float loop |
| `loaderFill` | Loader progress bar | Width 0→100% on load |
| `particleDrift` | Hero particles | Float upward with rotation, fade in/out |
| `dishFloat` | Hero 3D dish | Gentle vertical + Y-axis rotation loop |
| `ringRotate` | Dish orbit rings | Full 360° rotation at different speeds |
| `fadeSlideUp` | Hero content blocks | Opacity + translateY on mount |
| `aboutFloat` | About section emoji | Vertical float loop |
| `marqueeScroll` | Ticker strip | Continuous left scroll (duplicated content) |
| `scrollDrop` | Hero scroll indicator | Line drops down repeatedly |
| `expFloat` | Gallery card emojis | Vertical float with staggered delays |
| `specialFloat` | Flip card front emoji | Float + slight rotation |
| `ctaPulse` | CTA radial gradient | Scale pulse |
| `blink` | Hours "open" badge dot | Opacity pulse |
| `pinBounce` | Map pin | Vertical bounce |

### JavaScript Effects

```js
// Custom cursor — dot follows instantly, ring lags behind
rx += (mx - rx) * 0.12;  // 12% lerp per frame

// Scroll reveal — IntersectionObserver at 10% threshold
const obs = new IntersectionObserver(entries => { ... }, { threshold: 0.1 });

// Counter animation — cubic ease-out over 2000ms
const eased = 1 - Math.pow(1 - progress, 3);

// Hero parallax — content moves at 35% of scroll speed
heroContent.style.transform = `translateY(${scrollY * 0.35}px)`;

// 3D dish — rotates based on mouse distance from viewport center
dish.style.transform = `translateY(-50%) rotateX(${-dy*8}deg) rotateY(${dx*12}deg)`;

// Card tilt — ±5° on both axes based on mouse position within card
card.style.transform = `translateY(-2px) rotateX(${-y*5}deg) rotateY(${x*5}deg)`;
```

---

## Breakfast Menu Architecture

The breakfast tab replicates the physical printed menu with a **two-column layout**:

```
┌──────────────────────────────────────────────────────────────┐
│  HEADER: Logo circle  |  Founding story paragraph            │
├──────────────────────────────────────────────────────────────┤
│              🍳  Breakfast Menu  🫐                          │
├────────────────────────┬─────────────────────────────────────┤
│  LEFT COLUMN           │  RIGHT COLUMN                       │
│  ─────────────────     │  ──────────────────────────────     │
│  Breakfast Combos      │  Meat Combinations                  │
│    NO.1  …  $11.75     │    Chicken Fried Steak  …  $22.95   │
│    NO.2  …  $17.95     │    Pork Loin Chops  …   $22.95      │
│    NO.3  …  $16.50     │    Flat Iron Steak  …   $30.95      │
│    NO.4  …  $18.95     │    Hamburger Steak  …   $22.95      │
│    NO.5  …  $22.50     │    Homemade Hash  …     $17.95      │
│    NO.6  …  $12.50     │    Breakfast Burrito …  $17.95      │
│                        │    G.G. Special  …      $27.50      │
│  Biscuits & Gravy      │                                     │
│  Breakfast Sandwiches  │  Omelettes / Scrambles              │
│  Benedicts             │    Build Your Own  … from $15.95    │
│                        │    Add Meat  …  $2.25/meat          │
│                        │    Add Vegetable  …  $0.95/veg      │
│                        │    Remember The Aalmo  …  $18.95    │
│                        │                                     │
│                        │  🚜  Disclaimer notes               │
└────────────────────────┴─────────────────────────────────────┘
│  Footer: Split plate charge · GF note · Raw food warning     │
└──────────────────────────────────────────────────────────────┘
```

### Menu Item CSS Classes

```
.bfmenu-wrap          Outer container — wood-plank background texture
.bfmenu-header        Logo + story — 2-col grid
.bfmenu-title-row     "Breakfast Menu" navy title bar
.bfmenu-body          2-col grid (collapses to 1-col on mobile)
.bfms-head            Navy section header bar (e.g. "Breakfast Combos")
.bfms-note            Sub-header note row (italic notes)
.bfms-items           Padding wrapper for item rows
.bfmi-combo           Numbered combo row (NO.1–NO.6) — 2-col grid
.bfmi                 Standard menu item row — name + price + desc
.bfmenu-footer        Bottom navy bar with disclaimers
```

---

## Responsive Breakpoints

| Breakpoint | Layout Changes |
|---|---|
| `> 1024px` | Full layout — 3D dish visible, 2-col about, side-by-side visit |
| `≤ 1024px` | 3D dish hidden, about stacks vertically, visit stacks vertically |
| `≤ 900px` | Breakfast menu collapses to single column |
| `≤ 768px` | Nav links hidden → hamburger menu, experience grid adjusts |
| `≤ 480px` | Experience cards go full-width, stats grid to 2-col |
| `hover: none` | Custom cursor hidden, pointer cursors restored for touch |

---

## Getting Started

### Prerequisites
- Any modern browser (Chrome, Firefox, Safari, Edge)
- A local HTTP server (optional — the file works opened directly)

### Run Locally

**Option 1 — Open directly:**
```bash
open bluebird-cafe/index.html
```

**Option 2 — Serve with Python:**
```bash
cd bluebird-cafe
python3 -m http.server 8080
# → http://localhost:8080
```

**Option 3 — Serve with Node:**
```bash
npx serve bluebird-cafe
```

### Clone the Repo
```bash
git clone https://github.com/balvinder86/NWG-Restaurants.git
cd NWG-Restaurants/bluebird-cafe
open index.html
```

---

## Deployment

The site is a single static HTML file — it deploys anywhere in seconds.

### GitHub Pages
```bash
# From repo root
git checkout -b gh-pages
git push origin gh-pages
# Enable Pages in repo Settings → Pages → Branch: gh-pages
```

### Netlify (drag & drop)
1. Go to [app.netlify.com](https://app.netlify.com)
2. Drag the `bluebird-cafe/` folder onto the deploy zone
3. Done — live URL in under 10 seconds

### Vercel
```bash
npx vercel bluebird-cafe/
```

---

## Roadmap

- [ ] Add photo gallery with real food photography
- [ ] Integrate live Google Maps embed for location section
- [ ] Connect Toast Tab iframe for inline online ordering
- [ ] Add Lunch & Dinner menu tabs with full item lists
- [ ] Add seasonal specials banner system
- [ ] Implement contact / reservation form with email delivery
- [ ] Add additional restaurant pages under `NWG-Restaurants/`

---

## Contributing

This repo is maintained under the **NWG Restaurants** umbrella. To add a new restaurant:

```bash
# Create a new folder at the repo root
mkdir nwg-restaurants/<restaurant-name>

# Add your index.html following the same conventions
# Then commit and push
git add .
git commit -m "feat: add <restaurant-name> website"
git push origin master
```

Each restaurant lives in its own subfolder so the repo scales cleanly across multiple properties.

---

<div align="center">

Built with care for **Bluebird Café & Diner** · Arlington, WA · Est. 1958
© 2024 NWG Restaurants

</div>
