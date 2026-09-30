# Concept visual output standard

Use this standard whenever concept imagery is generated for R&D review.

## Primary objective

The default concept output must look like a **professional industrial-design presentation board**, not a quick isolated render. Match the visual ambition of a premium European furniture catalog/R&D review sheet: clear hierarchy, realistic furniture proportions, refined material rendering and enough supporting views to judge the design.

## Default collection board

Prefer a wide landscape board on a white/neutral studio background. Include:

1. **Collection title + short style line**.
2. **Compact Design DNA panel**: design language, frame, weaving/material, main colors, cushion/fabric and collection coherence.
3. **Weaving reference area** when the user supplied an image. Show the reference pattern and a close-up application cue; do not invent technical specs.
4. **Concept 01 / 02 / 03**, clearly separated. Each concept should show the requested product family together with one strong hero composition.
5. **Supporting product views/details** where space allows: front, side, 3/4, back or material/detail crop.
6. **Minimal presentation labels only**. Put accurate explanatory text in the chat response, not inside the image.

## Required collection lifestyle scene

When the brief contains **two or more products**, generate at least one additional image showing the products combined and used together as a coherent collection in the selected environment.

- `Indoor`: use a contemporary interior appropriate to the product family and target market, such as dining, living, lounge, cafe or hospitality context.
- `Outdoor`: use a plausible terrace, patio, garden, poolside, balcony or outdoor hospitality context.
- `Cả hai`: provide both Indoor and Outdoor context when image capacity allows; otherwise create the most relevant first and follow with the second.
- Include all major requested product types where spatially plausible. If the collection is too large for one scene, create multiple coordinated scenes rather than omitting products silently.
- Preserve the same Design DNA, colors, materials, weaving language and concept geometry shown on the review board.
- Arrange furniture naturally with believable clearances, scale and use relationships. A dining chair should relate correctly to its table; lounge seating and coffee/side tables should form a plausible conversational group.
- Keep the environment secondary. Avoid excessive decoration, people, dramatic architecture or props that obscure the furniture.
- Treat the scene as a design-validation view for collection coherence and use context, not merely a marketing mood image.


## Required individual product review images

For any collection with two or more products, the lifestyle scene is **not sufficient** for product review. After the user selects or approves a concept/hybrid direction, generate a **Product Review Pack** that covers every requested SKU/product individually.

For each product:
- generate at least one isolated studio image on a white or neutral background;
- default to a clear 3/4 hero view at a readable scale;
- preserve the exact selected Design DNA, materials, colors, weaving language and visible geometry;
- add front, side, back or detail views when they materially help review;
- keep camera logic and visual quality consistent across the collection so products are easy to compare;
- label the product name outside the image in chat when possible rather than relying on generated in-image text.

Do not silently replace individual product images with a collection lifestyle scene. The required collection visual set is:
1. Collection Concept Board;
2. Collection Lifestyle Scene;
3. one individual review image for every requested product after concept selection.

If the image tool cannot generate all requested product images in one turn, generate them in sequential batches and state which products remain. Continue until every requested product is covered before treating visual review as complete.

For a large collection, prioritize one clean hero image per SKU first. Additional orthographic/supporting views can follow on demand.

## Focused concept board

When the user selects one concept for closer review, generate a separate board with:
- one large 3/4 hero view;
- front, side and back views when useful;
- close-ups for weaving, frame joints, cushion and identifying details;
- optional product-family lineup for collection coherence.

## Visual quality controls

- Show requested materials faithfully: steel frame/powder coat, synthetic rattan/PE rope/weaving, cushion and tabletop material as applicable.
- Respect weaving coverage. For "đan phủ kín khung", visibly wrap/cover the intended frame zones while leaving structurally necessary exposed joints/feet/supports plausible.
- Keep products in one concept clearly related by shared tube language, radii, weave rhythm, palette and signature detail.
- Make Concept 01/02/03 differ in form architecture and silhouette, not merely colors.
- Prefer balanced modern-European proportions unless the brief says otherwise.
- Avoid impossible spans, visibly unsupported tabletops, implausible chair geometry, random tube intersections, floating parts or inconsistent leg counts.
- For studio boards, use white/neutral background with soft shadows. For required lifestyle scenes, use the brief's Indoor/Outdoor environment with restrained styling and realistic lighting.

## Text reliability

AI-generated in-image text can be imperfect. Keep it sparse. Never use image text, dimensions, part numbers, BOM numbers or callouts as controlled engineering truth.

## Revision consistency

For revisions, keep roughly the same board layout, camera logic and product scale so changes are easy to compare. Update collection lifestyle scenes whenever visible collection changes would otherwise make them stale. Do not downgrade a later revision to a lone generic render.
