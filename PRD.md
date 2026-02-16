# M&P Anniversary Timeline - Product Requirements Document

## Overview

Create a romantic vertical scroll timeline website celebrating a couple's journey together. Milestones appear beautifully as the viewer scrolls down, creating an immersive storytelling experience.

---

## File Structure

```
/anniversary-timeline/
├── index.html          # Main app (HTML + inline CSS + JS in single file)
├── milestones.json     # Editable milestone data (separate file)
└── /images/            # Image folder (empty for now, will add later)
```

---

## Design System

### Color Palette (Soft Pastels)

| Purpose          | Color Code | Description    |
|------------------|------------|----------------|
| Background       | `#FDF8F5`  | Warm cream     |
| Timeline spine   | `#E8D5D0`  | Dusty rose     |
| Accent           | `#D4A5A5`  | Muted blush    |
| Text primary     | `#5C4A4A`  | Warm brown     |
| Text secondary   | `#8B7676`  | Soft mauve     |
| Card background  | `#FFFFFF`  | White          |
| Card shadow      | `rgba(92, 74, 74, 0.1)` | Soft shadow |

### Typography

- **Title/Header:** `Playfair Display` (Google Fonts) - elegant serif
- **Dates:** `Cormorant Garamond` (Google Fonts) - refined, classic
- **Body text:** `Lato` (Google Fonts) - clean, readable

Import from Google Fonts:
```
Playfair Display:400,600
Cormorant Garamond:400,500
Lato:400
```

---

## Page Structure

### 1. Header Section

- Large elegant title: "M&P" using Playfair Display
- Centered, with generous padding top (30vh)
- Subtle scroll-down indicator (animated chevron or "scroll" text)
- Background: warm cream (`#FDF8F5`)

### 2. Timeline Section

- Central vertical line (timeline spine) running down the page
- Spine color: dusty rose (`#E8D5D0`), 2-3px width
- Milestone cards positioned alternating left and right of the spine
- Each milestone has:
  - Circular date marker on the spine (accent color with white text)
  - Card with title (and optional image placeholder)
  - Subtle connection line from card to spine

### 3. Footer Section (Optional)

- Simple heart icon or "❤" at the bottom of timeline
- Indicates end of journey (so far)

---

## Milestone Card Design

Each card should include:

- **Date badge:** MM/YY format, styled prominently
- **Title:** The milestone text
- **Image area:** Placeholder space (gray dashed border for now, will add images later)
- **Card styling:**
  - White background
  - Soft shadow
  - Rounded corners (8-12px)
  - Padding: 24px
  - Max-width: 350px

### Desktop Layout
- Cards alternate left and right of the center spine
- Odd milestones: left side
- Even milestones: right side

### Mobile Layout (< 768px)
- Single column
- Spine moves to left edge
- All cards stack on the right side
- Full width cards with margin

---

## Animations & Interactions

### Scroll-Triggered Reveal

Use Intersection Observer API (no external libraries):

1. Milestone cards start with:
   - `opacity: 0`
   - `transform: translateY(30px)`

2. When card enters viewport (threshold: 0.2):
   - Animate to `opacity: 1`
   - Animate to `transform: translateY(0)`
   - Transition: `0.6s ease-out`

3. Stagger effect: slight delay between consecutive cards

### Hover Effects

- Cards: subtle lift (`translateY(-4px)`) and increased shadow
- Smooth transition: `0.3s ease`

### Timeline Spine (Optional Enhancement)

- Spine could "fill" with accent color as user scrolls
- Creates sense of progress through the journey

---

## Data File: milestones.json

```json
{
  "couple": "M&P",
  "milestones": [
    {
      "id": 1,
      "date": "MM/YY",
      "title": "Met for the first time",
      "image": null
    },
    {
      "id": 2,
      "date": "MM/YY",
      "title": "Entschuldigung",
      "image": null
    },
    {
      "id": 3,
      "date": "MM/YY",
      "title": "Chatted day & night",
      "image": null
    },
    {
      "id": 4,
      "date": "MM/YY",
      "title": "Met after long",
      "image": null
    },
    {
      "id": 5,
      "date": "MM/YY",
      "title": "Met",
      "image": null
    }
  ]
}
```

The `image` field will later hold the filename (e.g., `"first-meeting.jpg"`).

---

## Technical Requirements

### index.html Specifications

1. **Single file** containing all HTML, CSS, and JavaScript (inline)
2. **No external dependencies** except Google Fonts
3. **Fetch milestones.json** on page load and dynamically render timeline
4. **Use Intersection Observer** for scroll animations (native JS)
5. **Responsive design** with CSS media queries
6. **Semantic HTML** structure

### CSS Requirements

- CSS custom properties (variables) for colors
- Flexbox/Grid for layout
- Smooth animations with `transition` and `transform`
- Mobile-first or desktop-first with proper breakpoints

### JavaScript Requirements

- Fetch and parse `milestones.json`
- Generate milestone HTML dynamically
- Set up Intersection Observer for each milestone card
- Handle animation classes on intersection

---

## Implementation Notes

1. **Start with milestones.json** - create the data file first
2. **Build HTML structure** - header, timeline container, footer
3. **Style with CSS** - apply the full design system
4. **Add JavaScript** - fetch data, render, animate
5. **Test responsiveness** - check mobile and desktop layouts

---

## Future Enhancements (Not for initial build)

- Add images to milestones
- Background music toggle
- Parallax scrolling effects
- Share button
- Print-friendly version

---

## Success Criteria

- Timeline loads and displays all milestones from JSON
- Smooth scroll-triggered animations work
- Responsive on mobile and desktop
- Elegant, romantic aesthetic matching the design system
- Easy to add new milestones by editing milestones.json
