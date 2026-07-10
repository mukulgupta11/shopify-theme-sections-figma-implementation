# GemCommerce Assessment — Shopify Theme Sections (Figma to Code)

## 📋 Overview

This project is a **pixel-perfect Figma-to-Shopify implementation** of a dog food product landing page. It includes fully functional **Shopify Liquid sections** that are modular, reusable, and editable via the Shopify Theme Editor — along with a standalone HTML preview for local testing.

---

## 🗂️ Project Structure

```
gemcommerce_assessment/
├── README.md                  ← Project documentation (this file)
├── preview.html               ← Standalone HTML preview (all sections combined)
├── assets/                    ← Static media: images, icons, GIFs
│   ├── food_1.svg             ← Feature icon: Real Food
│   ├── pet-bowl_1.svg         ← Feature icon: Premium Ingredient
│   ├── pet-food_1.svg         ← Feature icon: Made Fresh
│   ├── vet_1.svg              ← Feature icon: Vet Developed
│   ├── meat_bowl.png          ← Split-plate left half (raw food)
│   ├── dog_food_bowl.png      ← Split-plate right half (kibble)
│   ├── pic_of_dog_and_product.png  ← Stats section hero image
│   ├── dog_eating_gif.gif     ← Benefits section animated GIF
│   ├── dog_food.jpg           ← Benefits section kibble close-up
│   ├── paypal_icon.png        ← Payment method icon
│   ├── visa_icon.png          ← Payment method icon
│   ├── mastercard_icon.png    ← Payment method icon
│   ├── apple_pay_icon.png     ← Payment method icon
│   └── gpay_icon.png          ← Payment method icon
└── sections/                  ← Shopify Liquid section files
    ├── what-makes-us-different.liquid   ← Split-plate features grid
    ├── nutrition-stats.liquid           ← Key stats + dog image
    └── health-benefits-media.liquid     ← Alternating benefits rows
```

---

## 🚀 How to Preview Locally

1. Open a terminal in the project root directory.
2. Start a local server:
   ```bash
   python -m http.server 8000
   ```
3. Open your browser and navigate to:
   ```
   http://localhost:8000/preview.html
   ```

> **Note:** `preview.html` combines all sections into a single page for local design verification. It does not require Shopify to run.

---

## 🧩 Shopify Sections Breakdown

Each `.liquid` file in the `sections/` folder is an independent, self-contained Shopify section with:
- **Inline CSS** scoped to the section
- **`{% schema %}`** block for Theme Editor configurability
- **Fallback defaults** for all content (text, images)

### 1. Brand Features (`what-makes-us-different.liquid`)
- **Layout:** 3-column grid (features | split-plate circle | features) with 40px gaps
- **Components:** 4 icon+text feature cards, CSS split-plate with clip-path, CTA button, trust badges with payment icons
- **Figma Specs:** 60×60px icons, 286px text containers, 462px CTA button width, 12px/40px button padding

### 2. Nutrition Stats (`nutrition-stats.liquid`)
- **Layout:** 2-column grid (570px text | 570px image) with 60px gap
- **Components:** Heading group, "Key Points:" label, 3 stat rows with percentage badges, CTA button, square hero image
- **Figma Specs:** 570×570px image (10px radius), 6px button radius, 12px/40px button padding, #EE6F4B button color

### 3. Health Benefits Grid (`health-benefits-media.liquid`)
- **Layout:** 2 alternating rows (media+text), each 570px × 570px grid with 60px gap
- **Components:** GIF media box, static image box, heading+description text blocks
- **Figma Specs:** 570×480px media (10px radius), 32px text padding, 16px vertical gap

---

## 🎨 Design System

All sections follow a unified design system derived from the Figma file:

| Token | Value | Usage |
|-------|-------|-------|
| **Font** | Inter Tight (Google Fonts) | All text |
| **Heading** | 40px / 600 / 120% / 0.25px | Section titles |
| **Sub Heading** | 19px / 600 / 150% / 0.5px | Feature titles, labels |
| **Paragraph** | 16px / 400 / 150% / 0.5px | Body text, descriptions |
| **Primary Green** | `#15803d` | Accents |
| **CTA Orange** | `#EE6F4B` | Buttons |
| **Dark Text** | `#0f172a` | Headings |
| **Gray Text** | `#475569` | Paragraphs |
| **Border** | `#e2e8f0` | Dividers, card borders |

---

## 🔧 Technical Highlights

- **Pixel-perfect Figma alignment** — All dimensions (widths, heights, paddings, gaps, border-radii) match the Figma inspector values exactly
- **Responsive design** — Media queries for tablet (≤991px) and mobile (≤768px) breakpoints
- **No external CSS frameworks** — Pure vanilla CSS for maximum control
- **Self-contained sections** — Each Liquid file includes its own styles; no global stylesheet dependency
- **Shopify Theme Editor ready** — All content is configurable via `{% schema %}` settings without code changes
- **Semantic HTML5** — Proper heading hierarchy, alt attributes, and accessibility considerations
- **File size fallback optimization** — Heavy assets exceeding the theme's 10MB upload limit (like the 11.9MB GIF and high-res images) are loaded dynamically from Shopify Content Files via the `file_img_url` and `file_url` filters. Small icons are served locally via the `asset_url` filter.

---

## 📐 Figma-to-Code Methodology

1. **Inspected** every frame, text layer, and component in Figma's Properties panel.
2. **Extracted** exact values: widths, heights, paddings, gaps, border-radii, font sizes, weights, line heights, letter spacing, and colors.
3. **Implemented** using CSS Grid for layout and Flexbox for component internals.
4. **Verified** each section side-by-side against the Figma design at 1:1 scale.
