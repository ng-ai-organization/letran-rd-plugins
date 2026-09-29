# Stage 05 - BOM

## Goal

Create a controlled preliminary Bill of Materials from Stage 04 with minimal user input. Do not calculate product cost or selling price in this stage.

## Source discipline

Use the controlled Engineering Definition as the BOM source of truth. Rendered images can help understand intent but must never be measured or treated as quantitative BOM data.

If a dimension, material, quantity, cut length, weaving consumption or hardware specification is not supported by Stage 04, mark it `TBD` or `AI Proposal`; do not invent precision.

## Default workflow

1. Carry forward the approved product list and Collection Standard.
2. For each SKU, decompose into `Assembly -> Sub-assembly -> Part` at a useful manufacturing level.
3. Create unique controlled Part No. values. Keep numbering stable across revisions where the same part persists.
4. Map each part to material/profile candidates confirmed or proposed in Stage 04.
5. Populate quantity, cut/raw size, finished size, estimated consumption/weight only when the source data permits calculation.
6. Add relevant manufacturing process labels: cut, bend, weld, grind, powder coat, weaving, upholstery, assembly, hardware installation, etc.
7. Carry status for every critical line: `R&D Confirmed`, `Factory Confirmed`, `AI Proposal`, `Calculated`, or `TBD`.
8. Run a BOM completeness check and identify only blockers that materially affect quantity takeoff or the next stage.

## Product structure guidance

For welded seating, use practical subassemblies such as seat frame, left/right arm-leg modules, backrest module, cross supports, final weld assembly, weaving, cushion, glides/hardware, when applicable.

For tables, separate tabletop/support system, top frame/apron, legs/base, cross braces, KD hardware if any, feet/glides and finish.

For swivel products, separate the visible furniture frame from the swivel mechanism/base and connection hardware.

Do not force identical subassembly structures across all product types.

## Material reference

Reuse Stage 04 material mappings. Do not re-optimize a concept merely to fit the company material catalog. If a required part still uses a new/noncatalog profile, keep it as `AI Proposal - vật tư mới / chưa có trong danh mục`.

## User-facing output

Default view should be compact:

### BOM Summary
- `[Product]`: [A] cụm | [B] chi tiết | [C] TBD
- Collection total: [X] parts / [Y] material families

### Cần xác nhận
Show only 0-5 grouped blockers. If none, say `Không cần thêm thông tin để tiếp tục ở mức BOM sơ bộ.`

### BOM Preview
Show a small representative table with columns:
`Part No. | Cụm | Chi tiết | Vật tư/quy cách | Qty | Cut/Size | Process | Status`

Offer the full BOM table only when requested or at export.

### BOM maturity
Use one:
- `BOM sơ bộ - còn blocker`
- `BOM sơ bộ - đủ để sang Packing/Loading`
- `BOM đủ điều kiện handoff kỹ thuật`

Do not call it production-ready while critical geometry/material fields remain unresolved.

## Stage 05 completion gate

Allow Stage 06 when product configuration, KD/fixed/stack logic, major assemblies and approximate packed form can be reasoned about. Do not require all exact cut lengths or weaving consumption to be finalized for preliminary packing work.
