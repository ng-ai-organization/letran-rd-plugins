# Stage 05 - BOM

## Goal

Create a controlled preliminary Bill of Materials from Stage 04 with minimal user input. Do not calculate product cost or selling price in this stage.

The default user experience must make a multi-product collection easy to scan. Never dump the complete BOM of all SKUs into the chat by default.

## Source discipline

Use the controlled Engineering Definition as the BOM source of truth. Rendered images can help understand intent but must never be measured or treated as quantitative BOM data.

If a dimension, material, quantity, cut length, weaving consumption or hardware specification is not supported by Stage 04, keep the internal status as `TBD` or `AI Proposal`; do not invent precision.

### User-facing status wording

Keep `TBD` as the internal controlled status, but display it to Vietnamese users as **`Chưa xác định`** by default. Do not make users decode the abbreviation.

Examples:
- Internal: `TBD` -> UI: `Chưa xác định`
- Internal: `AI Proposal` -> UI: `AI đề xuất`
- Internal: `R&D Confirmed` -> UI: `R&D xác nhận`
- Internal: `Factory Confirmed` -> UI: `Nhà máy xác nhận`
- Internal: `Calculated` -> UI: `Đã tính`

The export/technical handoff may preserve the controlled English status code alongside the Vietnamese label when useful.

## Default workflow

1. Carry forward the approved product list and Collection Standard.
2. For each SKU, decompose into `Assembly -> Sub-assembly -> Part` at a useful manufacturing level.
3. Create unique controlled Part No. values. Keep numbering stable across revisions where the same part persists.
4. Map each part to material/profile candidates confirmed or proposed in Stage 04.
5. Populate quantity, cut/raw size, finished size, estimated consumption/weight only when the source data permits calculation.
6. Add relevant manufacturing process labels: cut, bend, weld, grind, powder coat, weaving, upholstery, assembly, hardware installation, etc.
7. Carry status for every critical line: `R&D Confirmed`, `Factory Confirmed`, `AI Proposal`, `Calculated`, or `TBD`.
8. Run a BOM completeness check and identify only blockers that materially affect quantity takeoff or the next stage.
9. Present the BOM through progressive disclosure: Collection Overview -> Product BOM Card -> selected-product detail -> export.

## Product structure guidance

For welded seating, use practical subassemblies such as seat frame, left/right arm-leg modules, backrest module, cross supports, final weld assembly, weaving, cushion, glides/hardware, when applicable.

For tables, separate tabletop/support system, top frame/apron, legs/base, cross braces, KD hardware if any, feet/glides and finish.

For swivel products, separate the visible furniture frame from the swivel mechanism/base and connection hardware.

Do not force identical subassembly structures across all product types.

## Material reference

Reuse Stage 04 material mappings. Do not re-optimize a concept merely to fit the company material catalog. If a required part still uses a new/noncatalog profile, keep it as `AI Proposal - vật tư mới / chưa có trong danh mục`.

## Progressive disclosure UX

### Level 1 - Collection BOM Overview (default for 2+ products)

Show one compact row per product. Do not show part-level rows here.

Recommended columns:
`Sản phẩm | Cụm | Chi tiết | Chưa xác định | Trạng thái`

Then show a short **Cần chú ý** section containing only the material exceptions/blockers across the collection.

End with a product-first action, not a full-detail dump:
- Primary: `Tiếp tục: Đóng gói & Loading`
- Secondary: `Xem BOM từng sản phẩm`
- Optional: `Xem các mục chưa xác định`
- Optional: `Chỉnh BOM`

If the user asks `xem BOM chi tiết` for a multi-product collection, first show/select the product to inspect. Never interpret it as permission to print every BOM row for every SKU.

### Level 2 - Product BOM Card (default after product selection)

Show only one selected product at a time.

Use this structure:

**[Product name] - BOM**
- Tổng quan: [A] cụm | [B] chi tiết | [C] chưa xác định
- BOM maturity: [status]

#### A. Visual structure / exploded view

When image generation or a suitable existing product visual is available, prefer a simple exploded structure view with numbered callouts for the main assemblies/parts. Keep the number of callouts readable, typically 6-12.

Rules:
- Map each callout number to a controlled BOM summary row.
- Use the approved product geometry/design as the visual source.
- Do not infer dimensions, quantities or material specifications from the generated image.
- Generated labels/callouts are presentation aids only; the controlled BOM remains authoritative.
- If a combined side-by-side visual + BOM card layout is supported, use it. Otherwise show the exploded visual first and the compact controlled table immediately below it.
- If reliable image generation is not available, omit the exploded visual without blocking the BOM flow.

#### B. Compact controlled BOM table

Default table should contain only the main assemblies/material groups, not every tube/screw/insert.

Recommended columns:
`No. | Cụm / Chi tiết chính | Vật tư / Quy cách | Qty / SP | Trạng thái`

Use about 6-12 rows when possible. Group minor repeated parts/hardware into a controlled summary line when this does not hide an engineering blocker.

Display missing data as **`Chưa xác định`**, not `TBD`.

#### C. Exceptions first

Below the card show only unresolved items that deserve user attention, e.g.:
- `3 mục chưa xác định`
- `Cơ cấu xoay chưa khóa`
- `Quy cách dây đan chưa xác nhận`

Do not repeat every normal/confirmed line.

#### D. Product navigation

After one Product BOM Card, offer:
- `Xem sản phẩm khác`
- `Xem chi tiết [Product]`
- `Chỉnh BOM [Product]`
- `Quay lại BOM collection`

Prefer native clickable choices when available. In Collection Mode, `Xem sản phẩm khác` should surface the product names rather than ask the user to type them.

### Level 3 - Selected-product detailed BOM

Only show full part-level BOM when the user explicitly requests detail for one selected product.

Use columns such as:
`Part No. | Assembly | Sub-assembly | Part | Material | Spec | Qty | Cut/Size | Process | Status`

Do not automatically continue into the next product. After the table, return to product navigation.

If the selected product has many lines, summarize in chat and prefer XLSX/CSV for the complete engineering table rather than creating a very long chat response.

### Level 4 - Full collection BOM export

The complete multi-SKU BOM belongs in an export file (prefer XLSX/CSV when supported) or a deliberate user request, not in the normal conversational view.

Never make `Xem BOM chi tiết` load the entire collection by default.

## Single-product mode

For one-product projects, skip Collection Overview and open the Product BOM Card directly. Keep the same progressive disclosure: compact card first, full part table only on request.

## BOM maturity

Use one:
- `BOM sơ bộ - còn blocker`
- `BOM sơ bộ - đủ để sang Packing/Loading`
- `BOM đủ điều kiện handoff kỹ thuật`

Do not call it production-ready while critical geometry/material fields remain unresolved.

## Stage 05 completion gate

Allow Stage 06 when product configuration, KD/fixed/stack logic, major assemblies and approximate packed form can be reasoned about. Do not require all exact cut lengths or weaving consumption to be finalized for preliminary packing work.

## Stage checkpoint

Before moving to Stage 06, record BOM maturity, assembly logic, locked material/part decisions, packaging-critical `AI Proposal`/`TBD`, blockers and next action using the compact checkpoint format in `project-state.md`.
