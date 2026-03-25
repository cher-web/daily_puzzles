# Design System Strategy: The Structured Editorial

## 1. Overview & Creative North Star
### Creative North Star: "The Tactile Blueprint"
This design system rejects the ephemeral, floaty nature of modern web design in favor of something physically grounded and unapologetically structured. Inspired by high-end print editorial and Neo-Brutalist architecture, the system prioritizes clarity through heavy-handed strokes, sharp geometric precision, and a high-contrast palette. 

We are moving away from "digital squiggles" and soft blurs. Instead, we treat the screen as a physical workspace where every element is "clamped" into place with solid borders and hard-edged shadows. The experience should feel like interacting with a premium, heavy-stock paper journal—intentional, tactile, and bold.

---

## 2. Colors & Surface Logic
The palette is rooted in earthy, high-saturation tones—Ochre (`primary`), Terracotta (`secondary`), and Teal (`tertiary`)—balanced against an architectural Off-White (`background`).

### The "Heavy Stroke" Rule
Unlike traditional systems that use light 1px lines, this system **prohibits 1px borders**. All container boundaries and interactive elements must be defined by a solid 2px or 3px stroke using the `on_background` (#1c1c15) or `outline` (#857464) tokens.

### Surface Hierarchy & Layering
We use the surface-container tiers to create a "stacked sheet" effect:
*   **Base Layer:** `surface` (#fcf9ee) serves as the canvas.
*   **Structural Sections:** Use `surface_container_low` (#f7f4e9) for secondary background areas.
*   **Interactive Cards:** Place `surface_container` (#f1eee3) or `surface_container_highest` (#e5e2d8) on top of the base layer.
*   **The "Accent Strip":** Utilize high-contrast background shifts (e.g., a `primary` ochre header) to divide major sections without relying on lines.

### Signature Textures
While the system is Neo-Brutalist, we achieve "high-end" polish by using subtle gradients on large action surfaces. Transitioning from `primary` (#895100) to `primary_container` (#d98c2f) gives buttons and headers a slight "ink-on-paper" depth that flat hex codes lack.

---

## 3. Typography
The type system is built on **Plus Jakarta Sans**. It is designed to be loud, authoritative, and perfectly legible.

*   **Headers (Display & Headline):** Use `Extra Bold` weight, `Uppercase`, and a `0.05em` letter-spacing. Headers must feel like headlines in a broadsheet newspaper.
*   **Titles:** Use `Bold` weight for card titles to maintain hierarchy against the heavy borders.
*   **Body:** Use `Medium` weight for `body-lg` and `body-md` to ensure stroke weights don't disappear behind the 3px container lines.
*   **Labels:** All-caps `label-md` is used for metadata, providing a "technical drawing" aesthetic.

---

## 4. Elevation & Depth: Hard-Edged Logic
We abandon soft Gaussian blurs entirely. Depth in this system is a binary state: an object is either on the page or lifted off it.

*   **Hard-Offset Shadows:** When a component requires "lift" (like a primary button or a floating card), use a hard-edged box shadow. 
    *   *Spec:* `4px 4px 0px 0px #1c1c15` (on-surface).
*   **Tonal Layering:** For non-interactive depth, nest containers. A `surface_container_highest` block inside a `surface` section creates a recessed, "punched-in" look without needing shadows.
*   **Zero Roundedness:** All `border-radius` tokens are strictly **0px**. Any rounding is a violation of the system's architectural integrity.

---

## 5. Components

### Buttons
*   **Primary:** `primary` background, `on_primary` text (Bold Caps), 3px solid `on_background` border. Must feature a 4px hard-edged shadow on hover.
*   **Secondary:** `surface` background, `on_surface` text, 2px solid `on_background` border.
*   **Tertiary:** No border, all-caps `label-md` text with a 2px underline using the `secondary` terracotta token.

### Cards & Lists
*   **The Divider Rule:** Forbid the use of standard horizontal rules (`<hr>`). Separate list items using a 2px `outline` border or by alternating `surface` and `surface_container_low` backgrounds.
*   **Card Anatomy:** Use a "Leading Color Block" (as seen in the reference teal/tertiary strips) to categorize content types visually.

### Input Fields
*   **State Logic:** 2px solid `outline`. On focus, the border thickens to 3px `primary` and gains a 4px hard-edged shadow. 
*   **Labels:** Labels should be positioned *inside* the border perimeter in the top-left, using `label-sm` in all caps.

### Navigation Bar
*   **Segmented Blocks:** Use heavy vertical 2px strokes to separate navigation items. Each "tab" should feel like a solid button in a physical control panel.

---

## 6. Do's and Don'ts

### Do
*   **Do** use intentional asymmetry. A card can have a hard-edged shadow on the bottom-right while being aligned to the left of the grid.
*   **Do** use the `secondary` (Terracotta) and `tertiary` (Teal) colors for "tagging" and status indicators (Easy/Medium/Hard).
*   **Do** embrace white space. High-contrast systems need "breathing room" to prevent the heavy lines from feeling claustrophobic.

### Don't
*   **Don't** use any radius values. If a component library defaults to 4px, manually override to 0px.
*   **Don't** use soft drop shadows. If it looks "fuzzy," it is off-brand.
*   **Don't** use low-contrast text. Accessibility is built into the Neo-Brutalist aesthetic; ensure all text on color blocks uses the appropriate `on_` token (e.g., `on_primary`).
*   **Don't** use 1px lines. They look like "mistakes" next to the 3px structural borders.