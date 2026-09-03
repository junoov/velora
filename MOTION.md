# Velora Motion Contract

## Reference Evidence

- Reference: `https://velora-template.framer.website/`
- Runtime inspected with Chrome DevTools Protocol at `1440x900`, `810x900`, and `390x900`.
- Raw service measurements: `/tmp/opencode/velora-live-service-runtime.jsonl` and `/tmp/opencode/velora-live-service-responsive.jsonl`.

## Scroll Behavior

- Every service row is `position: sticky` with `top: 120px` at desktop, tablet, and phone widths.
- Desktop and tablet service rows are `204px` high with a `205px` natural pitch.
- Phone service rows are about `295px` high with a `296px` natural pitch.
- Effective row position is `clamp(scrollY + 120px, naturalTop, lastRowTop)`. Rows overlap in order and leave the viewport together when the service list ends.
- Service title, description, and image reveal from `opacity: 0; translateY(8px)` as each row enters.
- Work cards reveal from `opacity: 0; translateY(30px)`.
- Section summaries reveal word by word from `opacity: .001; translateY(10px); blur(2px)`.

## Hero

- Welcome, description, and CTA enter from `translateY(-20px)` with delays `0`, `.1s`, and `.2s`.
- Portrait enters from `translateY(20px)` at `.1s`; name at `0s`; scroll link at `.2s`.
- Reference spring: stiffness `400`, damping `58`, mass `1`.

## Reviews

- Three slides, no autoplay.
- Track gap is `10px`; desktop card width is about `611px` inside a `678px` viewport.
- Navigation uses three pagination dots and pointer drag. A drag above `40px` changes one page.
- Slide transitions are interruptible and use an ease-out curve approximating Framer's spring.

## Reduced Motion

- Smooth scrolling and reveal transforms are disabled.
- Content remains visible and all navigation remains functional.
