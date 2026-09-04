# Velora Design System

## 1. Atmosphere & Identity

Velora is a quiet, editorial portfolio: generous white space, restrained typography, and small interactions that reward scrolling without competing with the work. Its signature is the monochrome gallery rhythm interrupted by warm sand accents and a tactile stack of sticky service panels.

## 2. Color

### Palette

| Role | Token | Value | Usage |
|------|-------|-------|-------|
| Page surface | `--page` | `rgba(245, 246, 245, 0.5)` | Document canvas behind sections |
| Primary surface | `--bg` | `#ffffff` | Main light sections |
| Tinted surface | `--bg-tint` | `rgba(247, 245, 242, 0.35)` | Hero and soft surfaces |
| Card surface | `--bg-card` | `#fafafa` | Work and testimonial cards |
| Subtle surface | `--bg-subtle` | `rgba(247, 245, 242, 0.35)` | Media placeholders |
| Primary text | `--text` | `#000000` | Headlines and primary controls |
| Secondary text | `--text-secondary` | `#212121` | Lead summaries |
| Muted text | `--text-muted` | `#6d6d6d` | Body copy and supporting labels |
| Label text | `--text-label` | `#595959` | Section labels |
| Faint text | `--text-faint` | `#999999` | Service numbers and tertiary metadata |
| Default line | `--line` | `#f4f4f4` | Dividers and card outlines |
| Hover line | `--line-hover` | `#aeaeae` | Interactive divider state |
| Warm accent | `--gold` | `#e3caa6` | Footer display accent and selection |
| Dark surface | `--dark` | `#000000` | Footer and dark CTA |
| Dark divider | `--dark-line` | `rgba(255, 255, 255, 0.15)` | Footer separators |

### Rules

- Use the existing monochrome palette with one warm accent; do not introduce gradients or unrelated colors.
- Interactive states may change opacity or use the documented hover line, but never rely on color alone.
- Raw color values are allowed only when declared here first.

## 3. Typography

### Scale

| Level | Size | Weight | Line Height | Tracking | Usage |
|-------|------|--------|-------------|----------|-------|
| Display | SVG fit text: desktop/mobile `161.202px`, tablet `113.103px` | 500 | desktop/mobile `193.442px`, tablet `135.723px` | desktop/mobile `-9.67211px`, tablet `-6.78616px` | Footer headline |
| H1 | `80px` / `64px` / `40px` | 500 | `1.2` | `-0.06em` | Hero name |
| H2 | `64px` / `58px` / `36px` | 500 | `1.2` | `-0.06em` | About name |
| H3 | `48px` / `38px` / `32px` | 500 | `1.2-1.3` | `-0.05em` | Hero welcome |
| Section label | `26px` / `22px` / `18px` | 500 | `1.3` | `-0.05em` | Section headings |
| H5 | `22px` / `20px` / `18px` | 500 | `1.4` | `-0.05em` | Cards, service titles, and mobile footer CTA |
| Footer CTA | `32px` / `26px` / `22px` | 500 | `44.8px` / `36.4px` / `28.6px` | `-1.6px` / `-1.3px` / `-1.1px` | Footer contact link |
| Body | `16px` | 400 | `1.4` | `-0.04em` | Body, metadata, links |
| Micro | `13px` | 500 | `1.4` | `-0.03em` | Service numbers |

### Font Stack

- Primary: `Inter, "Inter Placeholder", sans-serif`, backed by live Framer Latin Inter WOFF2 files for weights `400`, `500`, `600`, and `700`.
- Display: the same Inter family; no second display family is needed for this reference.

### Rules

- Load Inter with a non-blocking strategy and keep the browser fallback metrically close.
- Footer display text renders as live-style SVG/foreignObject fit text: desktop/mobile viewBox `0 0 1078.6721135643265 193`, tablet viewBox `0 0 756.786155952226 136`, with overflow clipping and no transform.
- Use `font-variant-numeric: tabular-nums` only for future numeric data, not for editorial copy.
- Keep summaries readable and use `text-wrap: balance` where wrapping differs by viewport.

## 4. Spacing & Layout

### Base Unit

All spacing derives from a base of **4px**.

| Token | Value | Usage |
|-------|-------|-------|
| `--space-1` | `4px` | Icon/link inset |
| `--space-2` | `8px` | Inline gaps |
| `--space-3` | `12px` | Compact card inset |
| `--space-4` | `16px` | Standard component gap |
| `--space-5` | `20px` | Mobile content gap |
| `--space-6` | `24px` | Card and mobile page padding |
| `--space-8` | `32px` | Group separation |
| `--space-10` | `40px` | Tablet page padding |
| `--space-12` | `48px` | Composed section gap |
| `--space-16` | `64px` | Header/mobile section rhythm |
| `--space-20` | `80px` | Desktop section padding |

### Grid

- Max content width: `1400px` outer container with `1240px` desktop content after `80px` padding.
- Desktop content origin at a `1440px` browser viewport: x `92.5px` when the reference `15px` scrollbar gutter is present.
- Desktop grid: 2-column Works grid, 9-column Reviews composition, and two-column About composition.
- Breakpoints: phone `<810px`, tablet `810px-1199.98px`, desktop `>=1200px`.
- Fixed navigation height: `64px`; service sticky offset: `120px`; About summary sticky offset: `64px`.

### Rules

- Preserve the reference's asymmetry: section labels sit in a narrow left rail while summaries and content occupy the right.
- Prefer CSS Grid for multi-column geometry and `min-height: 100dvh` for viewport-height surfaces.
- Every custom spacing value must be a documented section-level exception or a multiple of 4px.

## 5. Components

### Section header
- **Structure**: dash + label on the left, summary paragraph on the right.
- **Variants**: desktop split; tablet/phone stacked.
- **Spacing**: `--space-6` internal gap, `--space-20` desktop section padding, `--space-16` phone rhythm.
- **States**: static with scroll word reveal when motion is enabled.
- **Accessibility**: real heading element and readable summary text.
- **Motion**: word-by-word opacity/translate/blur reveal.

### Underline link
- **Structure**: text + inline SVG arrow.
- **Variants**: standard link and large dark-footer CTA.
- **Spacing**: `--space-2` icon gap and `--space-2` hit-area inset.
- **States**: default, hover, active, keyboard focus.
- **Accessibility**: semantic anchor, visible focus outline, meaningful label.
- **Motion**: underline width and arrow transform only.

### Sticky service row
- **Structure**: number, title/description group, cropped image.
- **Variants**: desktop/tablet `204px`; phone natural content-driven height.
- **Spacing**: `--space-3` vertical inset, `--space-10` column gap.
- **States**: default, hover/focus-within image emphasis.
- **Accessibility**: article with readable text and meaningful image alt.
- **Motion**: content enters with a short translate/opacity reveal; sticky placement remains CSS.

### Review carousel
- **Structure**: clipped viewport, horizontal card track, dot pagination.
- **Variants**: desktop partial next-card peek; phone nearly full-width card.
- **Spacing**: `10px` track gap and `--space-6` card padding.
- **States**: selected slide, inactive slide, pointer drag, keyboard dot focus.
- **Accessibility**: `aria-current` pagination and `aria-hidden` inactive slides.
- **Motion**: interruptible transform-only slide transition; no autoplay.

## 6. Motion & Interaction

### Timing

| Type | Duration | Easing | Usage |
|------|----------|--------|-------|
| Micro | `200-300ms` | `cubic-bezier(0.44, 0, 0.56, 1)` | Link and control feedback |
| Standard | `400-600ms` | `cubic-bezier(0.16, 1, 0.3, 1)` | Carousel and drawer |
| Emphasis | `900ms` | spring approximation, stiffness `400`, damping `58`, mass `1` | Hero/reveal entrances |
| Scroll-driven | tied to scroll | linear/progressive | Word reveals and sticky stack |

### Rules

- Use one Lenis instance and one animation-frame loop; forward its scroll event to ScrollTrigger.
- Animate only `transform`, `opacity`, and `filter`; sticky layout is controlled by CSS.
- Hero: top content enters from `-20px`, portrait from `20px`, with delays `0`, `.1s`, `.2s`.
- Works reveal from `30px`; service content/image reveal from `8px`; summaries reveal word by word from `10px` plus `2px` blur.
- Reduced motion disables smooth scroll and reveal transforms but leaves content and controls visible and usable.

## 7. Depth & Surface

### Strategy

Use **mixed**, with restrained tonal surfaces for cards and borders/dividers for structure. Shadows are reserved for the floating template widget because it must read as a separate fixed layer.

- Light cards use `--bg-card` against `--bg` rather than generic drop shadows.
- Dividers use `--line` or `--dark-line`; hover dividers use `--line-hover`.
- The floating widget uses a low-opacity glass shell, a dark preview surface, and a restrained shadow.
- Never add arbitrary neon glows, heavy shadows, or decorative gradients.
