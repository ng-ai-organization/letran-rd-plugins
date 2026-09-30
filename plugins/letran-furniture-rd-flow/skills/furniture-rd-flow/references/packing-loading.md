# Stage 06 - Packaging & Loading

## Goal

Develop a preliminary packaging and container-loading plan from Stages 04-05 while minimizing user input and clearly separating proposals from verified logistics data.

## Source discipline

Use controlled product dimensions, assembly/KD strategy, stack/nest logic and BOM structure. Never calculate final loading from product dimensions alone when packed dimensions are unknown.

If carton/stack dimensions are `AI Proposal`, all derived CBM and loading values must be labeled `Calculated from AI Proposal` and remain preliminary.

## Default workflow

For each SKU:
1. Determine likely packing mode: fixed assembled, KD, stack, nest, multi-pack or another justified method.
2. Propose pcs/carton or pcs/stack, orientation and protection strategy.
3. Identify scratch, impact, deformation, moisture and weaving/cushion risks.
4. Propose packed L/W/H and gross weight only when enough source data exists; otherwise mark relevant fields TBD.
5. Calculate CBM from packed dimensions when available.
6. Estimate single-SKU loading for common requested containers such as 20GP, 40GP and 40HC, using explicit dimensional/container assumptions.
7. Report utilization as screening-level, not guaranteed physical loading, unless an actual layout has been validated.

## Mixed collection loading

In Collection Mode, support two views:
- `Single-SKU Loading`: each SKU independently.
- `Mixed Loading`: collection mix only when the user provides or accepts an order ratio.

Do not force the user to provide a SKU mix just to complete Stage 06. Complete single-SKU screening first. Ask for mix only when mixed loading is actually wanted.

## Design-protection rule

Optimize packaging without silently changing the approved design. Priority:
1. keep approved design;
2. optimize via orientation, stacking/nesting, protection or sensible KD already compatible with the design;
3. if a design change could materially improve logistics, present it as an optional tradeoff for user decision.

Example: `Chuyển chân bàn sang KD có thể giảm CBM; giữ thiết kế hiện tại hay xem phương án KD?`

## User-facing output

### Packing & Loading Summary
For each SKU show only:
- Packing mode
- pcs/carton or stack
- packed dimensions/status
- CBM/status
- approximate container loading/status

### Cần xác nhận
Show only meaningful blockers such as factory stack limit, whether KD is permitted, verified packed dimensions, or required container type.

### Readiness
Use one:
- `Chưa đủ dữ liệu loading`
- `Loading sơ bộ - dựa trên AI Proposal`
- `Sẵn sàng cho hồ sơ R&D`
- `Sẵn sàng handoff logistics` only when packed dimensions/weights are appropriately verified.

## Calculation caution

Do not imply that simple CBM division equals a guaranteed container quantity. Account for orientation, unusable space, stacking constraints and loading practicality; describe estimates as screening until a layout or real packing test confirms them.

## Stage checkpoint

Before moving to Stage 07, record packing mode, packed-dimension status, loading maturity, logistics assumptions/TBD, blockers and next action using the compact checkpoint format in `project-state.md`.
