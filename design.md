# hidenothin — Design Specification
> Accurate recreation guide based on visual analysis of the original landing page.

---

## 1. Typography

### Font Families
| Role | Font | Weight | Style |
|---|---|---|---|
| Display / Headlines | **Instrument Serif** | 400 Regular | Normal + **Italic** |
| Body / UI / Nav | **Inter** | 300–400 | Normal |
| Code / Section numbers | **JetBrains Mono** | 300–400 | Normal |

### Google Fonts Import
```css
@import url('https://fonts.googleapis.com/css2?family=Instrument+Serif:ital@0;1&family=Inter:wght@300;400;500&family=JetBrains+Mono:wght@300;400&display=swap');
```

### Font Usage by Element
| Element | Font | Notes |
|---|---|---|
| Hero headline | Instrument Serif | "hide" in italic |
| Section headings (What we make, How we work…) | Instrument Serif | Italic for accent word |
| Large section numbers (02, 03…) | JetBrains Mono | Monospaced, light weight |
| Body paragraphs | Inter | 300–400 weight |
| Navigation links | Inter | 12px, regular |
| Service lists | Inter | 13px, 300 weight |
| Footer wordmark "hidenothin" | Instrument Serif | Large display |
| Breadcrumbs / labels | JetBrains Mono | 10–11px, muted |

### Typography Scale
```css
/* Section numbers (02, 03...) — JetBrains Mono */
font-family: 'JetBrains Mono', monospace;
font-size: clamp(80px, 12vw, 160px);
font-weight: 300;
line-height: 1;

/* Hero headline — Instrument Serif */
font-family: 'Instrument Serif', serif;
font-size: clamp(36px, 6vw, 72px);
font-weight: 400;
line-height: 1.1;

/* Section headings — Instrument Serif */
font-family: 'Instrument Serif', serif;
font-size: clamp(28px, 4vw, 52px);
font-weight: 400;
line-height: 1.15;

/* Italic accent words (hide, make, work, project) */
font-style: italic;

/* Manifesto lines — Instrument Serif */
font-family: 'Instrument Serif', serif;
font-size: clamp(18px, 2.5vw, 24px);
line-height: 1.8;

/* Body text — Inter */
font-family: 'Inter', sans-serif;
font-size: 14px;
font-weight: 300;
line-height: 1.6;

/* Nav links — Inter */
font-family: 'Inter', sans-serif;
font-size: 12px;
font-weight: 400;
letter-spacing: 0.02em;

/* Labels / breadcrumbs — JetBrains Mono */
font-family: 'JetBrains Mono', monospace;
font-size: 10px;
font-weight: 300;
letter-spacing: 0.05em;
```

---

## 2. Color Palette

Only 3 base colors are used across the entire site:

```css
:root {
  /* ── Core 3 Colors ── */
  --cream:   #F2EFE8;   /* Main page background — warm off-white */
  --blue:    #1F3DD0;   /* Manifesto block background; accent */
  --black:   #141414;   /* All text, borders, icons */

  /* ── Derived (tints/opacity of the 3 above) ── */
  --white:          #FFFFFF;          /* Text on blue section */
  --muted:          rgba(20,20,20,0.4);   /* Secondary / label text on cream */
  --border:         rgba(20,20,20,0.12);  /* Subtle divider lines */
  --card-bg:        rgba(20,20,20,0.08);  /* Team placeholder cards */
  --blue-muted:     rgba(255,255,255,0.5);/* Muted text on blue block */
}
```

### Color Usage Map
| Element | Color |
|---|---|
| Page background | `#F2EFE8` |
| All body text | `#141414` |
| All headlines | `#141414` |
| Nav links | `#141414` |
| Manifesto section background | `#1F3DD0` |
| Manifesto text | `#FFFFFF` |
| Section number (large) | `#141414` |
| Divider lines | `rgba(20,20,20,0.12)` |
| Team card backgrounds | `rgba(20,20,20,0.08)` |
| Muted / secondary text | `rgba(20,20,20,0.4)` |
| Footer background | `#F2EFE8` (same as page) |

---

## 3. Layout & Grid

### Overall Structure
- **Max width:** `1280px`, centered with `auto` margins
- **Horizontal padding:** `40px` desktop, `20px` mobile
- **Layout system:** CSS Grid with mixed full-width + asymmetric columns

### Grid Pattern
```css
.container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 0;
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 40px;
}
```

Most sections use a **left-heavy** or **right-heavy** split — large number on one side, heading on the other. Intentionally offset, not strict equal grid.

---

## 4. Navigation

```
[hidenothin logo]          [Work]  [About]  [Thoughts]  [Contact]     [Book a call →]
```

- Fixed/sticky top nav
- Logo: `hidenothin` in **Instrument Serif Regular**, ~14px
- Nav links: **Inter**, 12px, no underline on idle
- Right CTA: `Book a call →` — Inter, small text link, no button style
- Background: transparent over cream, no border

---

## 5. Section-by-Section Breakdown

---

### SECTION 1 — Hero
```
[Breadcrumb: No. 01 / The Studio]   ← JetBrains Mono, 10px

We do what most
studios hide.                    [Photo: outdoor wooden chair/table scene]

[Short tagline paragraph]        ← Inter 14px
[small CTA link: "→ see our work"]
```

- Text left (~60%), image right (~40%)
- Headline: **Instrument Serif**, "hide" in italic
- Image: sharp corners, no border-radius
- Breadcrumb: JetBrains Mono, muted `rgba(20,20,20,0.4)`

---

### SECTION 2 — What we do
```
02                    What we do ( * )

              We design, build, and create media for companies that would rather
              hire one studio than two. The result is better.
```

- `02` → JetBrains Mono, ~140px, light
- Heading → Instrument Serif
- `( * )` → inline, same size, regular weight
- Body → Inter, 14px, max-width ~420px

---

### SECTION 3 — What we make (transition)
```
03                                        What we make
```

Pure typography row. Large `03` in JetBrains Mono left, italic Instrument Serif heading far right.

---

### SECTION 4 — Services: Design (01*)
```
01*
Design
                [3-column list]          [Photo: blue flowers]
[description text]
```

- Number + asterisk: JetBrains Mono
- "Design": Instrument Serif heading
- List + description: Inter 13px, 300 weight, line-height 1.8
- Image: sharp corners

---

### SECTION 5 — Services: Engineering (02+)
```
[Photo: abstract golden light]          02+
                                        Engineering
[description text columns]
```

Image left, number + heading right. Asymmetric split.

---

### SECTION 6 — Services: AI media (03*)
```
03*
AI media
[Photo: white chair in green grass]
[description text]
```

---

### SECTION 7 — Manifesto / Blue Block
```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  We scope before we start.
  We name the people doing the work.
  We do not outsource and pretend otherwise.
  We send one shared doc, not a deck.
  We say no when a project is wrong for us.
  If the work is bad, you should be able to see that too.
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

- **Background:** `#1F3DD0` — full viewport width breakout
- **Text:** `#FFFFFF`, Instrument Serif Regular
- **Font size:** ~20–24px, line-height 1.8
- **No heading, no section number**
- Small label top-right: `hidenothin`, JetBrains Mono, 10px, `rgba(255,255,255,0.5)`

---

### SECTION 8 — How we work
```
05                    How we work

[Step labels left]        [Description right]
1–2 weeks, start to ship.
We talk through on the first call.
The actual work is hidden.
Testing. We do the work.
One shared doc. One weekly call.
```

- Step labels: JetBrains Mono, muted
- Descriptions: Inter, 14px
- Thin `1px` divider lines between steps: `rgba(20,20,20,0.12)`

---

### SECTION 9 — The Studio
```
06                              The studio

Anuj Tewari                 ← Instrument Serif, large
[Short bio paragraph]       ← Inter, 14px

[Team grid: 4–5 placeholder cards]
[Card labels below: name, role, date]
```

- Team cards: `background: rgba(20,20,20,0.08)`, sharp corners
- Card labels: Inter, 11–12px

---

### SECTION 10 — Start a project
```
07                              Start a project

"Tell us what you want to begin with. We need every message and reply
within two working days. Email: hello@hidenothin.com"
```

- Email: Inter, underline link, `#141414`

---

### SECTION 11 — Footer
```
hidenothin                          ← Instrument Serif, ~70px

[Col 1 links]    [Col 2 links]    [hello@hidenothin.com]
Work             About
Services         Thoughts
Process          Contact
```

- Background: `#F2EFE8` (same as page)
- Links: Inter, 12px, `#141414`
- Wordmark: Instrument Serif

---

## 6. Spacing System

```css
:root {
  --space-xs:   8px;
  --space-sm:   16px;
  --space-md:   32px;
  --space-lg:   64px;
  --space-xl:   120px;
  --space-xxl:  180px;
}

section {
  padding-top: var(--space-xxl);
  padding-bottom: var(--space-xxl);
}
```

---

## 7. Visual Details & Micro-patterns

- **Asterisk marks** (`*`) next to section numbers (01*, 03*) — JetBrains Mono, superscript-like, ~60% size
- **Plus marks** (`+`) next to "02+" — same treatment
- **No box shadows** anywhere on the page
- **No border-radius** on images or cards (all sharp/square corners)
- **No hover animations** — only subtle underline on text links
- **Divider lines:** `1px solid rgba(20,20,20,0.12)`, used sparingly
- **Section numbers** are decorative typographic elements — not in badges or bubbles

---

## 8. Image Treatment

| Section | Description |
|---|---|
| Hero | Natural outdoor scene, rectangular, ~400×350px |
| Design | Portrait crop, blue flowers close-up |
| Engineering | Abstract bokeh/golden light |
| AI media | White chair on green outdoor lawn |

- All images: **sharp corners (border-radius: 0)**
- No CSS filters or color overlays
- Images slightly break the grid — not perfectly aligned to column edges

---

## 9. Responsive Breakpoints

```css
@media (max-width: 1024px) {
  /* Stack grid to single column */
  /* Reduce section number font size */
}

@media (max-width: 768px) {
  /* Full-width sections */
  /* Nav collapses to hamburger or minimal */
  /* Section numbers: 80px */
}

@media (max-width: 480px) {
  padding: 16px;
  font-size: 13px; /* body */
}
```

---

## 10. HTML Structure Skeleton

```html
<body>
  <!-- background: #F2EFE8; font: Inter by default -->

  <nav><!-- Instrument Serif logo + Inter links + CTA --></nav>

  <section id="hero">
    <div class="hero-text">
      <span class="label">No. 01 / The Studio</span>  <!-- JetBrains Mono -->
      <h1>We do what most studios <em>hide.</em></h1>  <!-- Instrument Serif -->
      <p>Tagline...</p>  <!-- Inter -->
    </div>
    <div class="hero-image"><img src="chair.jpg" /></div>
  </section>

  <section id="what-we-do">
    <span class="section-num">02</span>  <!-- JetBrains Mono -->
    <div>
      <h2>What we do <span>( * )</span></h2>  <!-- Instrument Serif -->
      <p>Body copy...</p>  <!-- Inter -->
    </div>
  </section>

  <section id="what-we-make">
    <span class="section-num">03</span>
    <h2>What we <em>make</em></h2>
  </section>

  <section id="design">...</section>
  <section id="engineering">...</section>
  <section id="ai-media">...</section>

  <section id="manifesto">
    <!-- background: #1F3DD0; color: #fff; Instrument Serif -->
    <p>We scope before we start.</p>
    <!-- ... -->
  </section>

  <section id="how-we-work">...</section>
  <section id="studio">...</section>
  <section id="start">...</section>

  <footer>...</footer>
</body>
```

---

## 11. CSS Variables — Complete Token Set

```css
:root {
  /* ── Colors (only 3 base) ── */
  --cream:          #F2EFE8;
  --blue:           #1F3DD0;
  --black:          #141414;

  /* ── Derived ── */
  --white:          #FFFFFF;
  --muted:          rgba(20, 20, 20, 0.4);
  --border:         rgba(20, 20, 20, 0.12);
  --card-bg:        rgba(20, 20, 20, 0.08);

  /* ── Fonts ── */
  --font-display:   'Instrument Serif', Georgia, serif;
  --font-body:      'Inter', Helvetica, sans-serif;
  --font-mono:      'JetBrains Mono', 'Courier New', monospace;

  /* ── Spacing ── */
  --gap-section:    clamp(80px, 12vw, 180px);
  --gap-inner:      clamp(24px, 4vw, 64px);
  --padding-x:      clamp(20px, 5vw, 80px);

  /* ── Type sizes ── */
  --num-size:       clamp(80px, 12vw, 160px);
  --h1-size:        clamp(36px, 6vw, 72px);
  --h2-size:        clamp(28px, 4vw, 52px);
  --body-size:      14px;
  --label-size:     10px;
  --nav-size:       12px;
}
```

---

*This document provides everything needed to faithfully recreate the hidenothin.com landing page — with the exact 3 colors (#F2EFE8, #1F3DD0, #141414) and 3 fonts (Instrument Serif, JetBrains Mono, Inter).*
