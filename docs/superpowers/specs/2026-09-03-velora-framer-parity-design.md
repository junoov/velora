# Velora Framer Parity Design

## Goal

Make local Astro page match `https://velora-template.framer.website/` at reference viewport widths `1440`, `1200`, `810`, and `390` with the exported Framer page and live browser rendering as sources of truth.

## Scope

- Match section geometry, responsive breakpoints, typography, colors, borders, radii, image crops, copy, section order, and total document height at all four reference widths.
- Match visible behavior: fixed translucent navigation, Lenis smooth scrolling, hero entrance motion, scroll-triggered reveals, word-by-word summaries, hover/focus states, work cards, service images, experience rows, review carousel, mobile menu, footer CTA, and floating template widget.
- Keep existing Astro component boundaries and local assets. Use CSS for responsive geometry and GSAP/ScrollTrigger only for motion.
- Preserve semantic HTML, keyboard focus states, reduced-motion behavior, lazy image loading, and static Astro build compatibility.
- Do not add dependencies, port Framer's generated class tree, or implement unsupported interactions.

## Reference breakpoints and geometry

### Shared rules

- Page background white; hero tint `rgba(247, 245, 242, 0.35)`.
- Fixed navigation is `64px` high when closed, with desktop horizontal padding `80px`, tablet `40px`, and phone `24px`; mobile drawer expands the navigation without changing document flow below it.
- Main section containers use max width `1400px`; desktop padding `80px`, tablet `80px 40px`, phone `64px 24px`.
- Section headings use the shared dash/label treatment. Desktop section header width is `1040px`; phone headers stack with `24px` gap.
- Work cards use two columns above `810px`, one column below it, `24px` desktop / `20px` tablet / `16px` phone gaps, `4:3` images, and unchanged card dimensions on hover.
- Services use native sticky rows at `top:120px`, producing the reference pile effect until the list boundary releases the stack. Desktop rows are horizontal with `40px` gap, `12px` vertical padding, `60%` text content, and `180px` image height. Tablet rows stack their text but keep the reference row padding. Phone rows use column flow, `16px` gap, `24px` vertical padding, and image aspect ratio `2.785`.
- About summary is sticky at `top:64px` only on desktop. Tablet and phone use normal flow.
- Review cards are `500px × 360px` on desktop, `360px` high on tablet/phone, with `24px` padding and `8px` radius. Phone viewport is `342px × 420px` including its `24px` bottom inset.
- Footer uses `40px 80px` desktop padding, `40px` tablet padding, `40px 24px` phone padding, and `80px` contact/content gap on phone.

### Measured section targets

Targets are viewport-relative document boxes measured from the live reference at `900px` viewport height. Small subpixel differences from font rasterization are acceptable; section starts and heights must remain within a few pixels.

| Viewport | Hero | Works | Services | About | Reviews | Footer | Body |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| `1440×900` | `0–900` | `900–2368` | `2368–3546.6` | `3546.6–4204.7` | `4204.7–4784.7` | `4784.7–5420.4` | `5420` |
| `1200×900` | `0–900` | `900–2218` | `2218–3396.6` | `3396.6–4054.7` | `4054.7–4634.7` | `4634.7–5234.6` | `5235` |
| `810×900` | `0–900` | `900–1925.2` | `1925.2–3078.6` | `3078.6–4084.5` | `4084.5–4921.9` | `4921.9–5443.6` | `5444` |
| `390×900` | `0–722.1` | `722.1–2459.6` | `2459.6–3935.7` | `3935.7–4970.8` | `4970.8–5673.4` | `5673.4–6303` | `6303` |

Important phone subtargets:

- Hero container begins at `y=64`, uses `24px 24px 48px`, `64px` content gap, and ends at `h=658.1`; hero height is content-driven, not `100vh`.
- Service list begins at `y=2686.6`; each phone image is `342px × 122.8px` and each row is about `295px` including `24px` top/bottom padding.
- About summary is `342px × 269px`; experience list begins at `y=4308.7`, has `598px` height, and each main item is `47.6px` with about `119.6px` cadence.
- Review slideshow box is `x=24, y=5189.4, w=342, h=420`; cards are `342px × 360px` with `24px` padding.
- Footer heading is `342px × 61.2px`; footer content starts at `y=5899.2`.

## Motion

- Hero intro elements start at opacity `.001`, `translateY(-20px)`; portrait, name, scroll link, and widget start at opacity `.001`, `translateY(20px)`.
- Reference hero spring config is damping `58`, stiffness `400`, mass `1`; delays are `0`, `0.1`, `0.2`, with widget delay `3s`. Preserve the existing GSAP implementation where the rendered result matches these values.
- Work cards and About elements reveal from opacity `0`, `translateY(30px)`; service title, description, and image reveal from opacity `0`, `translateY(8px)`.
- Footer CTA reveals from opacity `.001`, `translateX(-24px)`.
- Word spans start at opacity `.001`, blur `2px`, and `translateY(10px)`; reveal with `0.05s` stagger.
- Scroll-triggered reveals run once when the element enters the lower viewport; no layout dimensions change during animation.
- Reduced motion disables Lenis and clears reveal transforms while keeping content visible.

## Component changes

- `src/styles/global.css`: keep shared typography and section primitives aligned with reference breakpoint values; avoid global overrides that leak desktop dimensions into phone layouts.
- `src/components/Nav.astro`: remove desktop shell width constraint so logo and links align to the reference viewport; preserve accessible mobile drawer state and focus behavior.
- `src/components/Hero.astro`: make phone hero content-driven by overriding desktop `height:100vh`; retain desktop cap and portrait offset only where measured.
- `src/components/Works.astro`: retain reference copy and responsive card geometry.
- `src/components/Services.astro`: retain native `position:sticky; top:120px` rows at every breakpoint; enforce phone image aspect ratio and responsive row/content sizing.
- `src/components/About.astro`: tune phone experience row height/cadence and tablet/phone section geometry without changing semantic row interactions.
- `src/components/Reviews.astro`: align responsive section heights and carousel viewport/card sizing; preserve button and pointer-drag behavior.
- `src/components/Footer.astro`: remove desktop heading minimum height from tablet/phone; match responsive footer title, CTA, content layout, and total height.
- `src/layouts/BaseLayout.astro`: adjust motion timing/selectors only when direct reference comparison proves a difference; keep Lenis, GSAP, ScrollTrigger, anchor offset, and reduced-motion paths.
- `src/components/FloatingWidget.astro`: align desktop CTA dimensions and typography with the reference; keep phone hidden and preserve both external destinations.

## Interaction contract

- Desktop navigation links remain visible; phone navigation shows only logo/toggle until opened. Toggle updates `aria-expanded` and drawer `aria-hidden`, animates two-line icon into an X, and closes after internal-link activation or desktop resize.
- Anchors scroll through Lenis with a `-64px` navigation offset; reduced-motion fallback uses native scrolling.
- Work cards expose overlay on hover/focus and scale image without changing card size.
- Service images scale on row hover without changing row size.
- Experience rows expose the hover/focus underline; rows remain keyboard focusable.
- Review carousel supports previous/next controls when shown, pointer drag over `40px`, responsive card step calculation, and resize recalculation.
- Footer CTA and widget links retain their external/mail destinations and keyboard focus states.

## Acceptance checks

1. `npm run build` exits `0`.
2. Local page loads at `1440`, `1200`, `810`, and `390` without console errors.
3. Section starts, heights, body height, first-viewport navigation, hero content, and image boxes match measured targets.
4. Scrolling through all sections triggers the expected reveal states without layout jumps.
5. Mobile menu closed/open states, anchor scrolling, work hover/focus, service hover, experience hover/focus, carousel controls/drag, footer CTA, and widget destinations remain functional.
6. Reduced-motion mode leaves all content visible and disables smooth/reveal motion.

## Constraints

The repository has no active Git metadata. This specification is written locally and cannot be committed unless Git is initialized separately; repository initialization and unrelated destructive changes are out of scope.
