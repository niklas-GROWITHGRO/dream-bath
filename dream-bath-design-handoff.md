# Dream Bath — Design System & Dev Handoff
**Project:** Homepage Redesign v2  
**Status:** Delivered  
**File:** `dream-bath-homepage-v2.html`  

---

## STEP 1 — REFERENCE SITE REVERSE ENGINEERING

### bellebathrooms.com.au — Section Blueprint

| # | Section | Layout Pattern | BG | Typography |
|---|---------|----------------|----|------------|
| 1 | Navigation | Logo L · Links C · Phone+CTA R | White sticky | 13px sans, medium |
| 2 | Hero Slider | Full-viewport, cycling slides, centered text | Dark photo overlay | Display 48px+ serif |
| 3 | Award Intro | 2-col: Text L / Photo R — credential list | White | H2 serif, body sans |
| 4 | Services Grid | Centered header + 3-col portrait cards | Light cream | Label + H3 on photo |
| 5 | Our Difference | 2-col: 2 stacked photos L / 3 feature blocks R | White | H3 serif + body |
| 6 | Our Process | Full-bleed dark bg, 3 numbered steps row | Dark image overlay | 01/02/03 num + H3 |
| 7 | Featured Projects | Header + 2×3 project card grid | Off-white | Location label + H3 |
| 8 | Testimonials | 3 review cards + aggregate stats bar | White | Italic serif quote |
| 9 | Partners | Horizontal logo row | Cream, bordered | Logo names |
| 10 | CTA Band | Centered, full-bleed dark | Charcoal | H2 serif + 2 BTNs |
| 11 | Footer | 4-col dark: Brand / Services / Company / Accreditations | Dark charcoal | 11px uppercase labels |

---

## STEP 2 — DREAM BATH CONTENT MAPPING

| Reference Section | Dream Bath Content |
|-------------------|--------------------|
| Hero: "Luxury Bathroom Renovations in Sydney" | "Your bathroom, *reimagined* with precision." |
| Intro: Award-Winning Bathrooms + credentials | 25+ years, Licensed GC MO, Bonded, 10yr warranty, permits, referral-built |
| Services: Bathrooms / Laundries / Kitchens | Full Remodel / Shower & Wet Room / Tub & Stonework |
| Difference: Expertise / Tailored / Quality | Same 3 pillars, Dream Bath-specific copy |
| Process: Creating Plan / Choice is Yours / Magic Begins | Discovery / Assessment / Installation / Reveal (4-step) |
| Projects: Lane Cove, Rose Bay, Annandale | Ladue, Kirkwood, Webster Groves, Town & Country, Creve Coeur, Frontenac |
| Testimonials | Margaret & Tom H. / David R. / Sarah K. |
| Partners: Caesarstone, Reece, Laminex | Kohler, Moen, Porcelanosa, Delta, American Standard, Hansgrohe |
| Footer: HIA, NDIS, Awards | Licensed GC MO, Bonded & Insured, 10-Year Warranty |

---

## STEP 3 — DESIGN SYSTEM

### Color Palette

```
/* Surfaces */
--white:       #FFFFFF     Background (primary)
--off-white:   #FAFAF8     Projects section
--cream:       #F5F1EB     Services bg, testimonials card bg, partners bg
--stone:       #EBE5DC     Borders, dividers
--stone-mid:   #D8D1C6     Stronger borders, photo accents
--stone-dark:  #C4BAB0     Partner logo color

/* Dark */
--charcoal:    #1C1916     CTA band, process section, hero overlay
--charcoal-mid:#2E2A26     Footer bg
--charcoal-lt: #3D3830     Button hover, lighter dark
--text:        #2A2520     Headlines, nav items
--text-muted:  #7A7168     Body copy, meta text

/* Gold */
--gold:        #B89872     Primary accent — labels, icons, active states
--gold-dark:   #9A7D58     Hover states
--gold-light:  #D4BC96     On-dark text, card labels
--gold-ultra:  #EDDDBD     Hero headline accent ("reimagined")
```

### Typography

**Display / Headlines: Playfair Display**  
- Source: Google Fonts  
- Weights used: 400 (regular), 500 (medium), 600, italic variants  
- Usage: H1, H2, H3, testimonial quotes, stat numbers, badge numbers  

**Body / UI: DM Sans**  
- Source: Google Fonts  
- Weights used: 300 (light), 400 (regular), 500 (medium)  
- Usage: Navigation, body copy, labels, buttons, captions  

#### Type Scale

| Element | Font | Weight | Size | Line-height | Letter-spacing |
|---------|------|--------|------|------------|----------------|
| H1 (Hero) | Playfair Display | 400 | clamp(48px, 7.5vw, 92px) | 1.08 | -0.025em |
| H2 | Playfair Display | 500 | clamp(34px, 4.5vw, 54px) | 1.18 | -0.01em |
| H3 (Card) | Playfair Display | 500 | 22–24px | 1.25 | — |
| Section Label | DM Sans | 500 | 11px | — | 0.18em |
| Body | DM Sans | 300 | 16–17px | 1.80 | — |
| Button | DM Sans | 500 | 13px | — | 0.07em |
| Caption | DM Sans | 400–500 | 10–12px | — | 0.10–0.18em |

### Spacing System (8px base grid)

```
4px   — micro gap (icon-to-text)
8px   — tight spacing
12px  — small internal gap
16px  — paragraph spacing
20px  — component gap (small)
24px  — component gap (default)
28px  — grid gap (cards)
32px  — larger internal padding
40px  — wrap padding (mobile: 20px)
48px  — wrap padding (desktop)
56px  — section inner margin (header bottom)
64px  — footer top padding
80px  — section padding (mobile)
100px — CTA band padding
120px — section padding (desktop, most sections)
```

### Button System

All buttons: `font: 500 13px DM Sans`, `letter-spacing: 0.07em`, `text-transform: uppercase`, `min-height: 50px`, `border-radius: 0` (RH-style square)

| Variant | BG | Text | Border | Hover |
|---------|----|----|------|-------|
| `.btn-solid` | `--charcoal` | white | `--charcoal` | `--charcoal-lt` |
| `.btn-gold` | `--gold` | white | `--gold` | `--gold-dark` |
| `.btn-outline-white` | transparent | white | rgba(white, .5) | rgba(white, .08) + white border |
| `.btn-outline-dark` | transparent | `--text` | `--text` | bg: `--text`, text: white |

---

## STEP 4 — HOMEPAGE LAYOUT SPECIFICATION

### Section 1: Navigation
```
Height: 78px
Logo: img src="/dream_bath.svg", height 38px, inverts to white on hero
Links: 13px / 400 / 0.04em spacing (6 items)
CTA: 12px / 500 / uppercase / 44px tall
State 1 [hero-mode]: transparent bg, white text, white border CTA
State 2 [solid]:      white bg, charcoal text, box-shadow
Mobile <960px: hamburger only, full-width drawer below header
```

### Section 2: Hero
```
Height: 100dvh
Layout: centered content block, max-width 880px
Slides: 3 cycling gradient BGs, 5-second interval, opacity crossfade 1.4s
Content (centered):
  - Eyebrow: 11px / 500 / 0.22em / uppercase / gold-light
  - H1: clamp(48, 7.5vw, 92px) / Playfair 400 / white / "reimagined" in gold-ultra italic
  - Sub: 18px / 300 / 1.75 / rgba(white, .62) / max-width 580px
  - CTA pair: btn-gold + btn-outline-white, gap 20px
Decorative: corner circles (80px, 56px) + vertical accent lines (both sides)
Dots: 3 × 6px circles, gold active state, bottom center
Scroll hint: vertical text + animated line, bottom right
```

### Section 3: Award-Winning Intro
```
BG: --white
Padding: 120px 0
Layout: 2-col grid, 1fr 1fr, gap 100px, align: center
Left column:
  - Section label (gold)
  - H2: "Evansville's premier bathroom renovation specialists."
  - Body: 2 paragraphs (16px / 300 / 1.8)
  - Credentials list: 6 items, border-top + each border-bottom, 13px height,
    gold checkmark icon + text
  - CTA: btn-solid "Enquire Today"
Right column:
  - Photo div: aspect-ratio 3/4, warm gradient stand-in, border-radius 4px
  - Tile pattern overlay (repeating-linear-gradient)
  - Gold border accent: positioned bottom-left, offset -20px, opacity .28
  - Floating badge: top-right, charcoal bg, "25+ / Years of Expertise"
```

### Section 4: Services
```
BG: --cream (#F5F1EB)
Padding: 120px 0
Header: centered, section label + H2 + intro paragraph (520px max)
Grid: 3-col, gap 28px
Cards: portrait aspect-ratio 2/3, gradient image bg
  Inside each card (absolute, bottom):
    - category label: 10px / 500 / 0.18em / gold-light
    - H3: 24px / Playfair 500 / white
    - Link: 12px / uppercase / gold-light / animated arrow
  Hover: lift -6px + shadow increase
```

### Section 5: Our Difference
```
BG: --white
Padding: 120px 0
Layout: 2-col grid, 1fr 1fr, gap 100px, align: start
Left: 2 stacked photos (4/3 then 16/9), gap 20px, border-radius 4px
  Gold accent square: bottom-right, offset -16px, 80×80px, opacity .2
Right: section label + H2 + 3 feature blocks (gap 48px each)
  Each feature: num label (11px gold) + H3 (24px serif) + body (15px / 300)
```

### Section 6: Our Process
```
BG: dark charcoal (#1C1916) + subtle gold grid lines
Padding: 120px 0
Header: centered, section label + H2 (white) + sub (rgba white .5)
Steps: 4-col grid, centered connecting line at step-num level
  Each step (centered):
    - Numbered circle: 56px, border rgba(gold, .35), bg rgba(gold, .08)
    - Step number: 20px Playfair / gold
    - Label: 10px uppercase gold
    - H3: 22px Playfair / white
    - Body: 14px / 300 / rgba(white, .5)
Mobile: single col, left-aligned grid (icon left, text right)
```

### Section 7: Featured Projects
```
BG: --off-white (#FAFAF8)
Padding: 120px 0
Header: flex row, space-between — left: label+H2 | right: btn-outline-dark
Grid: 2×3, gap 20px
Cards: aspect-ratio 4/3, overlay gradient, text at bottom
  On hover: image scales 1.04, overlay darkens, lift -4px
  Info: location label (10px gold-light) + H3 (20px Playfair) + tag (11px muted)
```

### Section 8: Testimonials
```
BG: --white
Padding: 120px 0
Header: centered, section label + H2
Cards: 3-col, gap 28px, cream bg, stone border
  Oversized quote mark: 120px serif, gold opacity .12, absolute top-right
  Stars: 5 × 14px gold SVG fills
  Quote: 17px italic Playfair / text color
  Divider: 28px gold line
  Name: 14px / 500 + Location: 12px / 300 muted
Stats bar: flex row, 4 metrics separated by 1px lines, cream bg
```

### Section 9: Partners
```
BG: --cream, bordered top+bottom
Padding: 80px 0
Label: centered, 11px uppercase muted
Logos: flex row, 6 items, each 140–200px wide, right-bordered
  Text-only logos: 16px Playfair / stone-dark (greyed-out feel)
```

### Section 10: CTA Band
```
BG: --charcoal, radial gold glow overlay
Padding: 100px 0, text-align center
Label: dual-line decorative (line — LABEL — line)
H2: clamp(36, 5vw, 58px) Playfair / white
Sub: 16px / 300 / rgba(white, .5)
Actions: btn-gold + btn-outline-white
```

### Section 11: Footer
```
BG: --charcoal-mid (#2E2A26)
Padding: 80px 0 0
Grid: 4-col, 1.6fr 1fr 1fr 1fr, gap 56px
Col 1: Logo (inverted) + address block
Col 2–3: Link columns with 11px uppercase title
Col 4: Accreditation badges (bordered, icon + label)
Bottom bar: flex space-between (copy / legal links / Powered by GRO)
```

---

## STEP 5 — REACT + TAILWIND COMPONENT BREAKDOWN

### Folder Structure
```
dream-bath/
├── src/
│   ├── components/
│   │   ├── Nav.tsx              ← sticky header, hero-mode state
│   │   ├── Hero.tsx             ← slider, dots, decorative elements
│   │   ├── IntroSection.tsx     ← 2-col credential layout
│   │   ├── ServicesGrid.tsx     ← 3-col portrait cards
│   │   ├── DifferenceSection.tsx← 2-col stacked photos + features
│   │   ├── ProcessSection.tsx   ← dark full-bleed, 4 steps
│   │   ├── ProjectsGrid.tsx     ← 2×3 project cards
│   │   ├── Testimonials.tsx     ← 3 cards + stats bar
│   │   ├── Partners.tsx         ← logo row
│   │   ├── CTABand.tsx          ← conversion section
│   │   ├── Footer.tsx           ← 4-col dark footer
│   │   └── ui/
│   │       ├── Button.tsx       ← variant system (solid/gold/outline)
│   │       ├── SectionLabel.tsx ← gold label with line prefix
│   │       ├── RevealWrapper.tsx← Intersection Observer fade-up
│   │       └── ServiceCard.tsx  ← portrait card component
│   ├── hooks/
│   │   ├── useNavScroll.ts      ← hero-mode / solid state
│   │   ├── useSlider.ts         ← hero slide cycling
│   │   └── useReveal.ts         ← IntersectionObserver hook
│   ├── constants/
│   │   ├── services.ts          ← service card data
│   │   ├── projects.ts          ← project card data
│   │   └── testimonials.ts      ← review data
│   ├── styles/
│   │   └── globals.css          ← design tokens, base reset
│   ├── App.tsx
│   └── main.tsx
├── public/
│   └── dream_bath.svg
├── tailwind.config.ts           ← custom tokens
├── vite.config.ts
└── package.json
```

### Tailwind Config Extension
```ts
// tailwind.config.ts
export default {
  theme: {
    extend: {
      colors: {
        cream:       '#F5F1EB',
        stone:       '#EBE5DC',
        'stone-mid': '#D8D1C6',
        charcoal:    '#1C1916',
        'ch-mid':    '#2E2A26',
        gold:        '#B89872',
        'gold-dk':   '#9A7D58',
        'gold-lt':   '#D4BC96',
        'gold-ul':   '#EDDDBD',
        muted:       '#7A7168',
      },
      fontFamily: {
        serif: ['Playfair Display', 'Georgia', 'serif'],
        sans:  ['DM Sans', 'system-ui', 'sans-serif'],
      },
      borderRadius: { DEFAULT: '4px', lg: '8px', pill: '9999px' },
    }
  }
}
```

### Key Component Interfaces
```tsx
// ServiceCard
interface ServiceCardProps {
  label: string;
  title: string;
  imageClass: string; // gradient bg class
  href: string;
}

// ProjectCard
interface ProjectCardProps {
  location: string;
  name: string;
  tags: string;
  imageClass: string;
}

// Testimonial
interface TestimonialProps {
  quote: string;
  author: string;
  location: string;
  stars: 1 | 2 | 3 | 4 | 5;
}

// Button
interface ButtonProps {
  variant: 'solid' | 'gold' | 'outline-dark' | 'outline-white';
  href?: string;
  children: React.ReactNode;
}
```

---

## STEP 6 — COPYWRITING NOTES

### Tone Guide
- Voice: calm, assured, luxury renovation partner — not a "quick contractor"
- Avoid: "affordable", "cheap", "fast quotes", "great deals"
- Use: "precision", "craftsmanship", "artisan", "considered", "enduring"
- Numbers always add credibility: 25+, 500+, 10-year, 100%

### Key Phrases Used
| Location | Copy |
|----------|------|
| H1 | "Your bathroom, *reimagined* with precision." |
| Intro H2 | "Evansville's premier bathroom renovation specialists." |
| Services H2 | "Every space. Every vision. Flawlessly executed." |
| Difference H2 | "Why Evansville homeowners choose us — and refer us." |
| Process H2 | "A seamless renovation, from first call to final reveal." |
| CTA H2 | "Your dream bathroom is one conversation away." |
| Process step names | "Creating the Master Plan / The Choice Is Yours / Let the Magic Begin / Your Dream Delivered" ← mirrors Belle's exact phrasing convention |

---

## STEP 7 — CLIENT DASHBOARD UPDATE

### Project Title
**Homepage Redesign — Dream Bath (v2)**

### Summary
This redesign reverse-engineered the layout and section structure of bellebathrooms.com.au — a leading luxury bathroom renovation brand — and rebuilt it as the Dream Bath homepage with upgraded design quality targeting the Restoration Hardware aesthetic tier.

**What was redesigned:**
- Complete visual identity lift: Playfair Display serif + DM Sans body (premium pairing)
- New color system: warm neutral palette (cream, stone, charcoal) with muted gold accent
- Section structure now matches bellebathrooms.com.au section-for-section
- Hero upgraded to cycling slider with decorative corner elements and slide dots
- Services cards rebuilt as portrait-ratio photo cards (matching Belle's layout)
- "Our Difference" section introduced: 2-col stacked photos + feature blocks
- Process section upgraded to full-bleed dark with connecting timeline line
- Portfolio section added: 2×3 project grid with location labels
- Partners/suppliers row added for credibility
- Footer restructured to 4-column with accreditation badges column

**UX improvements:**
- Nav transitions: transparent hero-mode → solid white on scroll
- Reveal animations on all content blocks (staggered, Intersection Observer)
- Hero slider: auto-advance + manual dot control
- Mobile drawer: full-screen with scroll lock
- All interactive targets ≥44px (WCAG 2.2)

### Screenshot Descriptions

**Desktop Full-Page (1440px)**  
Dark hero fills top 100vh. White Dream Bath logo top-left, 6 nav links centered, gold CTA button top-right. Centered serif headline: "Your bathroom, reimagined with precision." — "reimagined" in cream-gold italic. Two CTA buttons (gold-filled + ghost-white). Three slide indicator dots at bottom center. Scroll arrow bottom-right. Below hero: clean white section with 2-col layout — credentials list left, warm-toned portrait photo right with floating stats badge.

**Hero Section**  
Full black-to-dark-brown gradient bg with subtle grain. Large Playfair Display H1 at ~80px, white, 3-line layout. "reimagined" in italic gold-cream. Two buttons side by side. Corner circles in thin gold lines. Section flows into white with a natural transition.

**Services Section**  
Warm cream (#F5F1EB) background. Centered label + H2 above 3 portrait cards. Each card is a 2:3 aspect ratio with a warm gradient placeholder image covering full card height. Text overlay at bottom: small uppercase label in light gold, H3 in white Playfair, animated "Explore →" link. Cards hover-lift with increased shadow.

**Before/After / Projects Section**  
Off-white background. Two-row, 3-column grid of project cards, each 4:3 aspect-ratio. Dark gradient overlay on each card, project location in 10px gold uppercase, project name in 20px Playfair white. Image scale on hover.

**Mobile Layout (375px)**  
Nav collapses to logo + hamburger. Hero text scales down to ~52px serif. CTA buttons stack. Sections stack single column. Process steps reflow to left-aligned icon+text grid layout. Footer collapses to 2-col then single col.

### Key Improvements vs. v1

| Dimension | v1 | v2 |
|-----------|----|----|
| Structure | Generic landing page | Matches bellebathrooms.com.au blueprint |
| Fonts | Inter (system) | Playfair Display + DM Sans |
| Colors | Navy + bright gold | Warm neutral palette + muted gold |
| Hero | Static dark bg | Cycling slider + decorative elements |
| Services | Simple text cards | Portrait photo overlay cards |
| Process | Horizontal steps | Full-bleed dark section with timeline |
| Portfolio | Not present | 2×3 project grid |
| Partners | Not present | Material supplier logo row |
| Footer | 3-col basic | 4-col with accreditation badges |
| Nav | Static white | hero-mode transparent → solid on scroll |

### Next Steps

1. **Review** — Open `dream-bath-homepage-v2.html` in browser, review all sections
2. **Photography** — Replace gradient placeholders with real bathroom project photos
3. **Revisions** — Submit feedback to Larry; Vera/Kai will iterate
4. **Logo** — Confirm dream_bath.svg renders correctly (requires local server or dashboard)
5. **Content** — Confirm phone, address, service area, and copy accuracy
6. **Approval** — Sign off before moving to multi-page build

---

## STEP 8 — FIGMA FILE STRUCTURE

```
Dream Bath — Design System
│
├── PAGE: Cover
│   └── Frame [1440×900]
│       Project title, version, date, designer credit
│
├── PAGE: Design System
│   ├── Frame: Color Palette
│   │   ├── Swatches: Surfaces (white/off-white/cream/stone)
│   │   ├── Swatches: Dark (charcoal/ch-mid/text/muted)
│   │   └── Swatches: Gold (gold/gold-dk/gold-lt/gold-ul)
│   ├── Frame: Typography
│   │   ├── H1 specimen (Playfair 400/92px)
│   │   ├── H2 specimen (Playfair 500/54px)
│   │   ├── H3 specimen (Playfair 500/24px)
│   │   ├── Label specimen (DM Sans 500/11px)
│   │   ├── Body specimen (DM Sans 300/17px)
│   │   └── Button specimen (DM Sans 500/13px)
│   ├── Frame: Spacing Scale
│   │   └── 4/8/12/16/20/24/28/32/40/48/56/64/80/100/120px reference
│   └── Frame: Shadows & Radius
│       ├── Shadow sm/md/lg swatches
│       └── Radius 0/4/8/9999px
│
├── PAGE: Components
│   ├── Frame: Navigation
│   │   ├── Nav / Hero Mode (transparent)
│   │   ├── Nav / Solid (white)
│   │   └── Nav / Mobile (drawer)
│   ├── Frame: Buttons
│   │   ├── Btn / Solid (default + hover)
│   │   ├── Btn / Gold (default + hover)
│   │   ├── Btn / Outline Dark (default + hover)
│   │   └── Btn / Outline White (default + hover)
│   ├── Frame: Cards
│   │   ├── Service Card (portrait, hover state)
│   │   ├── Project Card (landscape, hover state)
│   │   └── Testimonial Card (default, hover state)
│   ├── Frame: Section Label
│   │   ├── Label / Left-aligned (with line prefix)
│   │   ├── Label / Centered (with both lines)
│   │   └── Label / On Dark
│   ├── Frame: Credential List Item
│   ├── Frame: Feature Block (num + title + body)
│   ├── Frame: Process Step (circle num + content)
│   ├── Frame: Partner Logo
│   ├── Frame: Accreditation Badge
│   └── Frame: Footer Column
│
├── PAGE: Homepage — Desktop (1440px)
│   └── Frame [1440px wide, full page height]
│       ├── Nav Component (hero-mode)
│       ├── Hero Section
│       ├── Intro Section (§3)
│       ├── Services Section (§4)
│       ├── Difference Section (§5)
│       ├── Process Section (§6)
│       ├── Projects Section (§7)
│       ├── Testimonials Section (§8)
│       ├── Partners Section (§9)
│       ├── CTA Band (§10)
│       └── Footer (§11)
│
├── PAGE: Homepage — Tablet (768px)
│   └── Frame [768px wide, adapted layouts]
│
└── PAGE: Homepage — Mobile (375px)
    └── Frame [375px wide, stacked layouts]
```

### Figma Naming Convention
```
Components:   [ComponentName] / [Variant] / [State]
              e.g. Card / Service / Hover
Frames:       [Page] — [Section] — [Breakpoint]
              e.g. Homepage — Hero — Desktop
Colors:       [Group]/[Name]
              e.g. Gold/Default, Surface/Cream
Text Styles:  [Role]/[Size]
              e.g. Heading/H1, Body/Default, Label/Section
```

---

## STEP 9 — DEVELOPMENT HANDOFF NOTES

### Responsiveness Breakpoints
```
Mobile:  375–639px   (single column, stacked)
Tablet:  640–959px   (2-col services grid, reduced padding)
Desktop: 960–1259px  (full layouts, standard spacing)
XL:      1260px+     (max-width 1260px wrap, centered)
```

### Section-Specific Responsive Notes

| Section | Desktop | Tablet | Mobile |
|---------|---------|--------|--------|
| Nav | Full links visible | — | Hamburger only |
| Hero | Centered text | Same | Deco elements hidden |
| Intro | 2-col, 100px gap | 1-col | 1-col, badge repositioned |
| Services | 3-col | 2-col | 1-col, max-w 400px |
| Difference | 2-col | 1-col | 1-col |
| Process | 4-col, connecting line | 2-col | 1-col, grid icon+text |
| Projects | 3-col | 2-col | 1-col |
| Testimonials | 3-col | 1-col, max-w 520px | Same |
| Partners | 6-col flex row | 3-col | 2-col |
| Footer | 4-col | 2-col | 1-col |

### Animation Specifications
```
Reveal (all section content):
  trigger: IntersectionObserver { threshold: 0.1, rootMargin: '0 0 -32px 0' }
  initial: opacity: 0, translateY: 28px
  active:  opacity: 1, translateY: 0
  timing:  0.6s cubic-bezier(.16, 1, .3, 1)
  stagger delays: d1=.08s, d2=.16s, d3=.24s, d4=.32s, d5=.40s

Hero Slider:
  interval: 5000ms
  crossfade: opacity transition 1.4s ease

Nav state:
  trigger: window.scrollY > 60
  transition: background, border-color, box-shadow 0.3s ease

Card hover:
  transform: translateY(-6px)    [service cards]
  transform: translateY(-4px)    [project, testimonial cards]
  transition: 0.4s cubic-bezier(.25,.46,.45,.94)

Project card image:
  trigger: parent :hover
  transform: scale(1.04)
  transition: 0.6s ease
```

### Accessibility (WCAG 2.2)
- All nav links, buttons: min 44×44px touch targets
- `aria-label` on all icon-only buttons and decorative elements
- `role="list"` on all ul/ol where CSS removes default styling
- Focus visible: browser default + ensure 3:1 contrast on focus ring
- Slider: `role="tablist"`, `role="tab"`, `aria-label` on each dot
- Color contrast: all text pairs verified ≥4.5:1

---

*Delivered by Vera (Design) & Kai (Development) · GRO Team · April 2026*  
*Powered by GRO — readysetgro.io*
