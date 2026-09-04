# Velora Design System

## 0. Research Log

- [Refero Grafik](https://styles.refero.design/style/0226e028-3cd3-440d-b469-ca459267161d), design system, 4 September 2026. Observed from the indexed reference: monochrome editorial grid, hairline framing, and project artifacts used as the imagery. Reusable pattern: let real work and technical artifacts carry the image area. Deliberately not copying: the sharp three-column grid and complete rejection of elevation.
- [Chester's Garden](https://styles.refero.design/style/a639fa6c-1705-47c2-b452-d4479469a734), design system, 4 September 2026. Observed from the indexed reference: restrained paper-like surfaces with a one-pixel inset edge and one low shadow level for selected image cards. Reusable pattern: combine a hairline edge with a soft, low-opacity shadow rather than a heavy floating card. Deliberately not copying: masonry composition and serif-led typography.
- [DUAI Project Gallery](https://github.com/siosio34/duai-hackerton-project-gallery), product repository, 4 September 2026. Observed from the project description: deterministic technical SVG compositions replace stock imagery and fake screenshots. Reusable pattern: capability sections may stay text-only and evidence-led when representative screenshots are unavailable. Deliberately not copying: its generative visuals and vermillion accent.
- [Numbered Services (shadcn-ui-blocks)](https://www.shadcn-ui-blocks.com/blocks/portfolio-pro/services-sections/numbered-services), pattern library, 4 September 2026. Observed: large-numbered ruled rows with a title, plain description, and honest scope. Reusable pattern: capability notes as plain editorial text. Deliberately not copying: its component code and muted-foreground tokens.

### Brand marks
- Header wordmark: `Vian.`, set in Inter 600. Rizky Noviansyah remains the formal name in the hero, footer, and metadata.
- Monogram: geometric black `V.` glyph (`/assets/logo-mark.svg`), also rendered as the favicon on a white tile. No gradients, 3D, or code-symbol cliches.
- [Prashant's Interactive Website Design Portfolio](https://www.pinterest.com/pin/prashants-interactive-website-design-portfolio--414260865710375177/), Pinterest preview, 4 September 2026. Only the public search preview was accessible. Reusable pattern: developer work is presented through interface artifacts rather than generic lifestyle photography. Deliberately not copying: page composition, branding, or proprietary imagery.
- Anti-reference: generic dark developer dashboards with neon gradients, terminal decoration, and repeated icon cards. These patterns would conflict with Velora's quiet editorial identity and make the portfolio interchangeable.

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
| Project edge | `--project-edge` | `rgba(18, 18, 18, 0.08)` | Hairline frame around project media |

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
- **Structure**: number, title/description group, and a typographic poster panel.
- **Variants**: desktop `180px` poster panel right of `60%` text; phone full-width poster at ratio `2.785` with a permanent note strip.
- **Spacing**: `--space-3` vertical inset, `--space-10` column gap.
- **States**: rest (clean poster), hover/focus (poster blurs, note appears), divider emphasis.
- **Accessibility**: article with readable text; note is decorative repetition of the visible description.
- **Motion**: transform/opacity/filter only; sticky placement remains CSS.

### Capability posters
- **Structure**: local SVG typographic panels, one per capability: `FE`, `BE`, `NET`, `SEC`.
- **Rules**: monochrome `#fafafa` paper with black display type, hairline grid lines, real technical vocabulary. No fake dashboards, cyber icons, gradients, or generative illustration.

### Work card (editorial monochrome)
- **Structure**: bordered card holding framed grayscale media, a blur note layer, and a caption row of title, arrow, and category.
- **Variants**: two-column desktop grid; single column phone.
- **Spacing**: `12px` card inset, `14px` media-to-meta gap, `4px` media radius, `6px` card radius, hairline `--project-edge` frame on `--bg-card`.
- **States**: rest (grayscale), hover/focus (media blurs and darkens, note with description and stack rises), active link.
- **Accessibility**: semantic anchor, meaningful alt, focus-visible note reveal, visible focus outline.
- **Motion**: transform/opacity/filter only; no elevation or color restoration.

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

Use **minimal**, with tonal surfaces and hairline borders for structure. The page relies on surface contrast and typography instead of drop shadows; the floating template widget remains the only elevated layer.

- Light cards use `--bg-card` against `--bg`; project work is framed with `--project-edge` and no shadow.
- Dividers use `--line` or `--dark-line`; hover dividers use `--line-hover`.
- The floating widget uses a low-opacity glass shell, a dark preview surface, and a restrained shadow.
- Project screenshots render permanently grayscale and blur with a note on hover; project color never returns inside the gallery so the page keeps one editorial rhythm.
- Capability posters are typographic SVG panels. Do not use stock photography, generative diagrams, fake dashboards, neon cyber imagery, or decorative gradients.
- Never add arbitrary neon glows, heavy shadows, or decorative gradients.
