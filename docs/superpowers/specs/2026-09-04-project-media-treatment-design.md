# Project and Capability Media Treatment

## Goal

Reduce glare in the project gallery and make every capability image explain Rizky's actual technical scope while preserving Velora's quiet editorial character.

## Approved Direction

- Give project cards one restrained elevation level using a hairline edge and a two-part low-opacity shadow.
- Lower screenshot luminance and saturation at rest, then restore them slightly on hover and keyboard focus.
- Keep the existing 4:3 geometry, metadata, zoom, and description overlay.
- Replace all four decorative capability photographs with local technical SVG diagrams.
- Use one shared visual language: near-black canvas, warm sand accent, off-white strokes, small labels, and no gradients or neon effects.

## Capability Visuals

- Frontend: responsive browser frames and component regions.
- Backend: request, server, and database flow with compact status lines.
- Network: router, switch, workstation, and subnet topology.
- Security: application-security audit matrix and request inspection.

The diagrams are explanatory editorial artwork, not fabricated screenshots or evidence of tool output.

## Follow-up Change (same session)

- Replace the hero portrait with the user's landscape photo (`/assets/hero-rizky-landscape.jpg`), rendered fully grayscale via CSS filter, and point the OG image at the same asset.
- Trim the Proyek Pilihan gallery to the two launched projects, NovLink and Roller Customize, and adjust the section summary accordingly.

## Responsive and Accessibility Contract

- Preserve the service row's existing desktop sticky behavior and mobile wide crop.
- Keep essential diagram content inside the center safe area so it survives both crops.
- Give every image a descriptive Indonesian alternative text.
- Preserve visible keyboard focus and reduced-motion behavior.

## Verification

- Run `npm run build`.
- Render at 1440px and 390px, with focused captures of Proyek Pilihan and Kemampuan.
- Check card hover/focus treatment, clipping, horizontal overflow, failed assets, and browser console errors.
