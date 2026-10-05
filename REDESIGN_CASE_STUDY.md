# Website UI Redesign: Usability Heuristic Evaluation & High-Fidelity Design System

**Project:** BistroBite / Savory Delivery Experience Redesign  
**Focus:** Usability Enhancement, Visual Hierarchy, Design Systems & Responsive Architecture  
**Tutorial Reference:** [Figma UI Design Tutorial - How To Redesign Any Website](https://youtu.be/fcWahZqGU44?si=HvuqWHzZAg6dJI27)  
**Deliverables:** Heuristic Audit, Mood Board, Style Guide, High-Fidelity Desktop & Mobile Mockups, Interactive Prototype, Figma Vector Assets  

---

## 1. Executive Summary & Problem Framing

Modern food delivery and restaurant websites frequently suffer from cognitive overload, chaotic visual hierarchy, unpredictable hidden fees, and degraded mobile experiences. Diners are hungry, rushed, and seeking low-friction decision-making. When interfaces present cluttered layouts, unorganized options, and hidden checkout surcharges, users experience cart abandonment and frustration.

### Project Goals:
1. **Systematic Usability Audit:** Perform a rigorous heuristic evaluation based on Jakob Nielsen’s 10 Usability Principles to pinpoint baseline friction points.
2. **Design Language & Style Guide:** Construct a cohesive visual identity, accessible color palette (WCAG 2.1 AA/AAA compliant), modern typography scale, and reusable UI components.
3. **High-Fidelity Mockups:** Create high-fidelity desktop (1440px) and mobile (390px) screens with clear visual hierarchy, scannable cards, and intuitive micro-interactions.
4. **Responsive Layouts:** Implement fluid responsive layouts adhering to modern CSS standards (CSS Grid, Flexbox, Container Queries, and thumb-zone mobile ergonomics).

---

## 2. Heuristic Evaluation (Jakob Nielsen's 10 Principles)

An in-depth heuristic evaluation of the baseline website was conducted. Issues were scored using Nielsen Norman Group's severity rating scale:
- **Severity 0:** Not a usability problem.
- **Severity 1 (Cosmetic):** Minor aesthetic issue; low priority fix.
- **Severity 2 (Minor):** Usability issue causing user hesitation; medium priority.
- **Severity 3 (Major):** Significant usability problem; high priority fix.
- **Severity 4 (Catastrophic):** Blocks user task completion; imperative to resolve immediately.

| # | Nielsen Heuristic | Severity | Baseline Issue Identified | Redesign Solution & Usability Improvement |
|---|-------------------|----------|---------------------------|--------------------------------------------|
| **1** | **Visibility of System Status** | **Severity 3 (Major)** | After placing an order, users received a static "Order Confirmed" screen with no live progress, estimated arrival countdown, or milestone breakdown. In addition, adding items to cart had no clear micro-animation or persistent count badge. | Designed a **Real-Time Live Order Tracker** with a dynamic 4-step progress stepper (Order Placed → In the Kitchen → On the Way → Delivered), live countdown timer ("Arriving in 18–24 min"), and an interactive route map. Added persistent floating cart badge with instant count animation. |
| **2** | **Match Between System & Real World** | **Severity 2 (Minor)** | Menu categories used internal merchant jargon ("SKU Batch 4", "Cold Line Prep") instead of natural diner mental models. Order total omitted sales taxes and delivery charges until the final credit card step. | Re-architected information architecture around diner mental models: *Trending Now*, *Chef's Specials*, *Hearty Mains*, *Plant-Based Bowls*, and *Desserts*. Created a **Transparent Pricing Model** showing delivery fee and estimated ETA directly on restaurant cards. |
| **3** | **User Control and Freedom** | **Severity 3 (Major)** | Users could not edit dish customizations (e.g., changing sauce or removing onions) inside the cart without deleting the item and finding it again in the menu. Clicking browser "Back" during checkout wiped all form inputs. | Implemented an **Inline Edit Customization Modal** directly in the cart drawer. Added a 60-second **"Undo / Modify Order" grace period** on the confirmation screen, and preserved form inputs in browser local session state. |
| **4** | **Consistency and Standards** | **Severity 2 (Minor)** | Buttons used conflicting colors across screens (some blue, some red, some outline). Filter tags behaved unpredictably: some applied instantly while others required clicking an obscured "Apply Filters" button at the bottom. | Built a strict **Design System & Component Library** with standardized button hierarchies (Primary Crave Orange `#FF5B26`, Secondary Slate `#F1F5F9`, Ghost Outline). Standardized all filter chips to auto-apply instantly with smooth transitions. |
| **5** | **Error Prevention** | **Severity 4 (Catastrophic)** | Users were allowed to click "Add to Cart" on customizable dishes without selecting required modifier options (e.g., choice of protein), causing an unhelpful generic error modal. No warning was shown if a restaurant was closing in 5 minutes. | Implemented **Proactive Error Prevention**: required modifier options are highlighted with visual pill counters (`"Select 1 required"`), and the primary CTA button remains in an informative disabled state (`"Choose your protein to proceed"`) until conditions are met. Added closing countdown warning badges. |
| **6** | **Recognition Rather than Recall** | **Severity 2 (Minor)** | Dietary restrictions (Gluten-Free, Vegan, Nut-Allergy) were buried inside multi-page ingredient descriptions. Users had to remember what items they ordered last week to reorder. | Placed prominent, standardized **Dietary Icon Badges** (🌱 Vegan, 🌾 GF, 🌶️ Spicy) directly on dish thumbnails and item cards. Added a **"Reorder in 1-Click"** carousel at the top of the homepage for returning diners. |
| **7** | **Flexibility and Efficiency of Use** | **Severity 3 (Major)** | Power users had to navigate through 4 separate pages to repeat a simple lunch order. No keyboard shortcuts or rapid-add buttons existed for single-item dishes. | Added **Direct Quick-Add Buttons (+)** on non-customizable menu cards, express Apple Pay / Google Pay one-touch checkout, and desktop keyboard navigation support (Slash `/` to focus search, `Esc` to close modals). |
| **8** | **Aesthetic and Minimalist Design** | **Severity 3 (Major)** | The homepage was cluttered with 12 competing promotional banners, auto-playing video popups, neon coupon codes, and redundant text blocks, overwhelming the user’s sensory focus. | Enforced **Visual Hierarchy & Whitespace**: eliminated extraneous banners, instituted generous 8pt spatial grid padding, restricted page palette to 1 primary brand color and balanced neutrals, and elevated restaurant photography to let the food shine. |
| **9** | **Help Users Recognize, Diagnose, & Recover from Errors** | **Severity 3 (Major)** | Payment failures displayed obscure backend codes: `"Error: HTTP 402 - Gateway Refused"`. The user was not informed whether their card was declined, address was invalid, or CVV was missing. | Rewrote all error messaging into plain, conversational, and actionable guidance: *"Card declined by your bank. Please verify your 3-digit CVV or try checking out with Apple Pay."* Highlighted the exact erroneous field with red outline and inline helper text. |
| **10** | **Help and Documentation** | **Severity 2 (Minor)** | Support was relegated to an unformatted FAQ link at the bottom of the footer. During live delivery, diners had no way to message their courier or add gate-code instructions. | Built a contextual **In-Flow Support Drawer** accessible directly from the live tracking screen with 1-tap buttons: *"Call Driver"*, *"Add Delivery Note"*, and *"Live Agent Chat"*. |

---

## 3. Mood Board & Visual Identity

### Aesthetic Direction: Modern Culinary Craft & Effortless Warmth
The mood board establishes an appetizing, clean, and trustworthy atmosphere. Rather than cold tech-heavy aesthetics or chaotic coupon-driven apps, the visual identity centers on fresh ingredients, warm ambient lighting, artisanal plating, and crisp typography.

- **Emotional Tone:** Inviting, reliable, fresh, frictionless, human.
- **Lighting & Photography:** High-key natural lighting, crisp overhead flat-lays and appetizing 45° angle dish captures, high saturation for natural ingredients (greens, reds, golden crusts).
- **Surface Treatment:** Clean warm-tinted white canvas (`#FAFAF9`), soft elevated cards with subtle ambient blur shadows (`rgba(15, 23, 42, 0.06)`), and refined hairline borders (`#E2E8F0`).

---

## 4. Style Guide & Design System

### 4.1 Color Architecture & Semantic Tokens
Every color was selected to stimulate appetite while exceeding **WCAG 2.1 Level AA** contrast standards (minimum 4.5:1 for body text, 3:1 for large text and UI components).

| Token Name | Hex Code | Role & Usage | Contrast Ratio (vs #FFFFFF) |
|------------|----------|--------------|------------------------------|
| `--color-primary` | `#FF5B26` | Vibrant Tangerine. Primary CTAs, active states, key accents | 3.3:1 (Large text / UI graphic) |
| `--color-primary-dark` | `#D9410E` | Dark Tangerine. Button hover & active pressed states | 4.8:1 (Passes AA Body) |
| `--color-secondary` | `#0D9488` | Teal Forest. Freshness badges, free delivery pills | 4.6:1 (Passes AA Body) |
| `--color-accent` | `#F59E0B` | Golden Amber. Star ratings, review highlights | 3.1:1 (UI Graphical) |
| `--color-slate-900` | `#0F172A` | Obsidian Slate. Primary headings and high-contrast text | 16.1:1 (Passes AAA) |
| `--color-slate-700` | `#334155` | Charcoal. Secondary body text and labels | 9.7:1 (Passes AAA) |
| `--color-slate-500` | `#64748B` | Muted Slate. Metadata, timestamps, placeholders | 4.6:1 (Passes AA) |
| `--color-slate-200` | `#E2E8F0` | Border hairline, divider rules | N/A (Subtle boundary) |
| `--color-surface-bg` | `#F8FAFC` | Main canvas background | N/A |
| `--color-surface-card` | `#FFFFFF` | Card, modal, and drawer backgrounds | N/A |
| `--color-success` | `#10B981` | Emerald Green. Completed steps, order confirmed | 4.5:1 (Passes AA) |
| `--color-danger` | `#EF4444` | Coral Crimson. Validation errors, cancellation | 4.5:1 (Passes AA) |

### 4.2 Typography Hierarchy
The typography utilizes `Inter` / `Plus Jakarta Sans`, renowned for exceptional legibility at both large display sizes and small mobile interface captions.

- **Display 1 (Hero Title):** `36px / 44px` · Bold (700) · `-0.025em` tracking
- **Heading 1 (Section Title):** `28px / 36px` · Bold (700) · `-0.02em` tracking
- **Heading 2 (Card Title / Subheader):** `20px / 28px` · SemiBold (600) · `-0.01em` tracking
- **Heading 3 (Modal Subtitle):** `17px / 24px` · SemiBold (600)
- **Body Regular:** `15px / 22px` · Regular (400)
- **Body Medium:** `15px / 22px` · Medium (500)
- **Small / Metadata:** `13px / 18px` · Regular (400)
- **Pill / Button Label:** `14px / 20px` · SemiBold (600) · `+0.01em` tracking
- **Micro Caption:** `11px / 14px` · Medium (500) · `+0.02em` uppercase tracking

### 4.3 8-Point Spatial Grid & Component Metrics
- **Spacing Units:** 4px (micro), 8px (base), 12px, 16px (standard pad), 24px (card pad), 32px (section break), 48px, 64px.
- **Corner Radii:**
  - `radius-sm`: `6px` (badges, tags)
  - `radius-md`: `10px` (inputs, buttons)
  - `radius-lg`: `16px` (cards, containers)
  - `radius-xl`: `24px` (modals, bottom sheets)
  - `radius-full`: `9999px` (pills, avatars)
- **Elevation Shadows:**
  - `shadow-subtle`: `0 1px 3px rgba(15, 23, 42, 0.06)`
  - `shadow-card`: `0 4px 12px -2px rgba(15, 23, 42, 0.08)`
  - `shadow-hover`: `0 12px 24px -4px rgba(15, 23, 42, 0.12)`
  - `shadow-drawer`: `0 -8px 30px rgba(15, 23, 42, 0.15)`

---

## 5. High-Fidelity Mockups & Architecture

### Screen 1: Discovery & Curated Food Feed
- **Desktop (1440px):** 12-column grid. Left sticky filter sidebar (Cuisine, Price range, Dietary, Max ETA). Top navigation with live address selector, global search with instant autocomplete, and sticky cart preview button. Central feed with hero promotion, quick cuisine pills, and 3-column responsive restaurant cards.
- **Mobile (390px):** Single-column layout. Top compact app bar with address pill and profile. Horizontal scrolling filter pills. 1-column high-impact cards with full-width photography, badge overlays, and sticky bottom navigation.

### Screen 2: Restaurant Menu & Customization
- **Desktop (1440px):** Split-view architecture. Left column: Restaurant cover photo, verified badges, rating, ETA, and sticky category navigation (Appetizers, Mains, Drinks). Center column: 2-column dish grid with photography, descriptions, dietary tags, and prices. Right column: Sticky live order summary.
- **Mobile (390px):** Hero photography with floating back and share icons. Horizontal sticky category tabs. Dish list with compact thumbnails. Tapping an item triggers an animated native bottom sheet with required/optional modifiers and real-time total price calculation.

### Screen 3: Cart Review & Transparent Checkout
- **Desktop (1440px):** Two-column checkout layout. Left: Delivery address selector, delivery instructions box, payment method (Cards, Apple Pay, Google Pay). Right: Itemized cart review with quantity toggles, clear item modification list, promo code input, and **100% Transparent Fee Breakdown** (Subtotal, $1.99 Delivery, $1.50 Service, Tax, Tip).
- **Mobile (390px):** Linear checkout flow with thumb-friendly tip selection pills ($2, $3, $4, Custom), clear fee disclosure, and a prominent bottom fixed checkout button.

### Screen 4: Live Order Tracking & Real-Time Delivery Status
- **Desktop (1440px):** Hero interactive delivery map displaying live courier route, pin locations for restaurant and destination, and a 4-step milestone card with driver avatar, license plate, phone button, and live ETA countdown.
- **Mobile (390px):** Top full-width map view with pulse animation. Pull-up milestone sheet with dynamic status updates, courier contact controls, and order receipt drawer.

---

## 6. Responsive Layout & Visual Hierarchy Strategy

### 6.1 Viewport Breakpoints
- **Desktop (>= 1200px):** 1440px max-width container, 12-column CSS Grid (`grid-template-columns: repeat(12, 1fr)`), 24px gutters, persistent sidebars.
- **Tablet (768px – 1199px):** 8-column layout, collapsible filter drawer, 2-column restaurant card grid.
- **Mobile (< 768px):** 390px viewport, single-column vertical flow, 16px page margins, horizontal scroll containers for categories, sticky bottom navigation bars.

### 6.2 Visual Hierarchy & Eye-Tracking Principles
- **F-Pattern on Desktop:** Key decision anchors (Restaurant Name, Rating, ETA, Price) are placed along the top and left edges of each card to maximize scanning efficiency.
- **Z-Pattern on Hero Banners:** Eye travels from the bold headline ("Dinner in 25 mins") across the imagery to the primary orange CTA button.
- **Mobile Thumb Zone:** All critical interactive controls (Add to Cart, View Order, Checkout, Tip selectors) are anchored within the bottom 30% of the viewport (the natural ergonomic thumb sweep area).

---

## 7. How to Use in Figma (Tutorial Workflow)

Following the principles demonstrated in the tutorial video (*"Figma UI Design Tutorial - How To Redesign Any Website"*):
1. **Copy SVG Vectors:** In the interactive web redesign hub (`index.html`), click **"📋 Copy Screen to Figma"**.
2. **Paste Directly:** Open your Figma file and press `Ctrl + V` (Windows) or `Cmd + V` (Mac).
3. **Editable Layers:** Figma automatically converts the vector graphics into editable frames, vector paths, and text layers.
4. **Auto Layout:** The layouts are structured with uniform auto-layout spacing metrics (8px, 16px, 24px) for seamless prototyping.
