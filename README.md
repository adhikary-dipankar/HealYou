# HealYou

# Design System Strategy: Clinical Serenity

## 1. Overview & Creative North Star
The "Creative North Star" for this design system is **The Empathetic Pathologist**. This concept moves away from the cold, sterile "hospital-app" aesthetic and toward a high-end, editorial experience that balances clinical authority with human warmth. 

We break the "template" look by rejecting the standard grid of boxed content. Instead, we use **Intentional Asymmetry** and **Soft Layering**. The layout should feel like a series of clean, physical sheets of high-grade paper and frosted glass. By prioritizing massive amounts of "negative space" (using our `20` and `24` spacing tokens), we reduce cognitive load for patients and practitioners alike, creating a sense of calm in high-stress medical environments.

---

## 2. Colors & Surface Philosophy
The palette is rooted in deep, professional blues and clinical whites, but its sophistication comes from how we transition between them.

### The "No-Line" Rule
**Explicit Instruction:** Do not use 1px solid borders to define sections. Traditional borders create visual noise and "trap" the user's eye. 
*   **The Alternative:** Boundaries are defined solely through background shifts. Place a `surface_container_lowest` card on a `surface_container_low` background. This creates a natural, soft edge that feels modern and premium.

### Surface Hierarchy & Nesting
Treat the UI as a physical stack.
*   **Base:** `background` (#f8f9fb).
*   **Structural Sections:** Use `surface_container` or `surface_container_low`.
*   **Actionable Cards:** Use `surface_container_lowest` (#ffffff) to make them "pop" forward toward the user.
*   **Overlays:** Utilize `surface_bright` to highlight active focal points.

### The "Glass & Gradient" Rule
To avoid a flat, "budget" feel, use **Glassmorphism** for floating elements (like bottom navigation or urgent modals). 
*   **Implementation:** Use `surface` at 80% opacity with a `backdrop-filter: blur(20px)`.
*   **Signature Textures:** For primary CTAs, do not use flat hex codes. Apply a subtle linear gradient from `primary` (#0040a1) to `primary_container` (#0056d2) at a 135-degree angle to give the button "soul" and a tactile, pressed-glass quality.

---

## 3. Typography: The Editorial Authority
We utilize a dual-font system to balance readability with high-end character.

*   **Display & Headlines (Manrope):** This geometric sans-serif provides a modern, authoritative tone. Use `display-lg` and `headline-md` with tight letter-spacing (-0.02em) to create a bold, editorial look for health summaries or welcome screens.
*   **Body & Labels (Inter):** Chosen for its exceptional legibility in small sizes (clinical data, prescriptions). 
*   **The Hierarchy Rule:** Always pair a large `headline-sm` with a much smaller `body-md`. The high contrast in scale signals importance instantly, allowing users of all ages to scan the page without "reading" every word.

---

## 4. Elevation & Depth
We eschew the "drop shadow" of the 2010s in favor of **Tonal Layering**.

*   **Ambient Shadows:** If a card must float (e.g., a critical notification), use a shadow color tinted with `on_surface` at 5% opacity, with a blur radius of at least `32px`. It should feel like a soft glow, not a dark smudge.
*   **The "Ghost Border" Fallback:** In high-contrast accessibility modes where tonal shifts aren't enough, use the `outline_variant` token at **15% opacity**. This provides a "hint" of a boundary without cluttering the interface.
*   **Depth through Blur:** Use `surface_tint` overlays with high blur values to create "blobs" of color behind surface layers, suggesting depth and movement without explicit structural lines.

---

## 5. Components

### Buttons: The Tactile Anchor
*   **Primary:** Rounded `full` (pill-shape). Uses the signature Primary-to-Container gradient. Label is `title-sm` in `on_primary`.
*   **Secondary:** No background. Use a `ghost border` (outline_variant at 20%) and `primary` text.
*   **Interaction:** On hover, shift the gradient 10%. On press, scale the component down to 98%.

### Cards & Lists: The "Breathable" Container
*   **Rule:** Forbid divider lines. 
*   **Spacing:** Use spacing token `6` (2rem) between list items. Separate different data types using a subtle shift from `surface_container_lowest` to `surface_container_low`.
*   **Corners:** All cards must use `xl` (1.5rem) roundedness to maintain the "friendly/trustworthy" mandate.

### Input Fields: Minimalist Clarity
*   **Style:** Unfilled, using only a bottom stroke of `outline_variant` (2px). When focused, the stroke transforms into a `primary` color glow. 
*   **Labels:** Floating `label-md` that never disappears, ensuring patients don't lose context.

### Specialized Medical Components
*   **Status Indicators:** Use `tertiary` (Warm Orange/Red) for urgent alerts and `primary` for "Healthy/Normal" states. Indicators should be accompanied by a `label-sm` to ensure accessibility for color-blind users.
*   **The "Health Pulse" Graph:** Use `primary` for data lines with a `primary_fixed` soft glow underneath to simulate an organic, living metric.

---

## 6. Do’s and Don’ts

### Do
*   **Do** use the `24` (8.5rem) spacing token for top-level page margins to create a "Gallery" feel.
*   **Do** use `title-lg` for all medical terminology to ensure it is the first thing the eye sees.
*   **Do** utilize "Surface Nesting" to group related lab results without using boxes or lines.

### Don't
*   **Don't** use 100% black. Use `on_surface` (#191c1e) for all text to maintain a soft, premium feel.
*   **Don't** use the `DEFAULT` or `sm` roundedness for primary containers; it feels too "technical" and "sharp." Stick to `lg` and `xl`.
*   **Don't** cram information. If a screen feels full, it needs a secondary sub-page. Silence is a feature in medical design.

---

## Frontend-only UI (no backend)

This repo contains UI prototypes under `Healt_App/*/code.html`. A simple frontend-only SPA wrapper is provided at `index.html` that loads those screens and lets you navigate them as one app.

### Run locally

Because the wrapper uses `fetch()` to load the HTML screens, you must serve the folder over HTTP (not `file://`).

```bash
cd /Users/dipankaradhikary/Projects/Health/HealYou
python3 -m http.server 5173
```

Then open `http://localhost:5173` in your browser.

### Screens

- Home menu: `/#/`
- All screens list: `/#/screens`
- Direct screen route: `/#/screen/<screen_id>` (example: `/#/screen/home_dashboard`)