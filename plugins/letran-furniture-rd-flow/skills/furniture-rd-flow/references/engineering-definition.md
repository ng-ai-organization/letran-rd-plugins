# Stage 04 - Engineering Definition

## Goal

Turn the approved concept into a controlled first-pass technical definition with the least possible user input. AI proposes first. User confirms only decisions that cannot be safely inferred or that materially affect production, safety, cost or BOM.

## Entry condition

Start when a concept is selected/stable enough or the user asks to continue to technical specifications. Do not require a separate approval ritual.

## Source priority

Use inputs in this order:
1. approved concept/revision and visible geometry;
2. confirmed project brief and Design DNA;
3. company production context;
4. company material reference library for Stage 04+ only;
5. external benchmark/standards research only when needed and clearly labeled.

Never use rendered labels/numbers as controlled dimensions.

## Default workflow

1. Extract the product list and shared collection decisions.
2. Build a **Collection Standard** for shared technical choices where sensible.
3. Build a **Product Engineering Card** for every SKU.
4. Run sanity checks for ergonomics, structural load path, manufacturability, weaving integration and Indoor/Outdoor suitability.
5. Map frame needs to the company material reference library without changing the concept merely to force a match.
6. Create a **Confirmation Queue** containing only material blockers, grouped into at most 3-5 questions.
7. Report readiness for Stage 05.

## Collection Standard

For multi-product collections, propose and reuse common rules when technically appropriate:
- steel section/profile family and finish philosophy;
- powder-coat system/color family;
- weaving material family and visual pattern language;
- cushion/fabric family and Indoor/Outdoor requirement;
- hardware/fastener family where applicable;
- weld/assembly philosophy and visible-detail language.

Do not force one tube/profile on every product when loads or geometry differ.

## Product Engineering Card

For each product include only relevant fields.

### 1. Dimensions and ergonomics
- overall W/D/H;
- seat/table/work heights as applicable;
- clearances, angles and reach relationships;
- product-to-product relationships in a collection, e.g. chair-to-table fit.

Use sensible proposals when exact values are unavailable. Mark them `AI Proposal`; do not pretend they are measured from a render.

### 2. Frame and structure
- section/profile family and nominal size proposal;
- wall thickness proposal or TBD;
- major load path and supports;
- bend strategy and critical radii if relevant;
- weld/joint strategy;
- subassembly breakdown.

For chair/seating families that match company practice, prefer separately fabricated frame subassemblies welded in a final jig unless the concept clearly requires another method.

### 3. Weaving
Carry the approved visual language forward, then define engineering needs separately:
- coverage zones;
- path logic;
- anchor/termination concept;
- profile/diameter: proposal or TBD;
- pitch/tension: proposal or TBD;
- measured consumption and labor: TBD until controlled geometry/path exists.

Never derive rope chemistry, actual diameter, tension or consumption from an image alone.

### 4. Cushion/upholstery
When applicable:
- thickness and comfort intent;
- foam/density class proposal or TBD;
- cover construction;
- fixing method;
- drainage/quick-dry requirements for Outdoor;
- fabric performance class as proposal/TBD.

### 5. Mechanisms/hardware
When applicable:
- swivel base/mechanism;
- KD joints;
- adjusters/glides;
- fasteners/inserts;
- stackability or nesting features.

### 6. Finish and environment
- powder-coat finish intent;
- corrosion protection needs for Outdoor;
- contact-point protection and feet/glides;
- compatibility notes for glass, wood, stone-look or other secondary materials.

### 7. Risks and validation
List only meaningful risks, e.g. unsupported span, weak load path, difficult bend, inaccessible weld, weaving interference, unstable base, drainage trap, excessive SKU variation or likely cost driver.

## Status model

Use:
- `R&D Confirmed`
- `Factory Confirmed`
- `AI Proposal`
- `Calculated`
- `Benchmark`
- `TBD`

Each critical engineering line should have a status. Avoid false precision.

## Material reference rule

The mechanical-material catalog is a reference of items the company has used, not proof of stock, price, supplier availability or approval.

Selection logic:
1. determine the technical need first;
2. search the library for compatible profile/size candidates;
3. choose one primary candidate and optionally one fallback if useful;
4. prefer an existing candidate only if it preserves the design intent and technical need;
5. if none is suitable, flag `AI Proposal - vật tư mới / chưa có trong danh mục`;
6. do not silently change visible concept geometry to fit catalog material.

## Minimum-input Confirmation Queue

Ask only about decisions that materially change the engineering outcome. Examples:
- factory-only capability such as minimum bend radius or available tooling;
- required load rating/test standard when it affects section sizing;
- exact mechanism/hardware choice;
- exact rope profile if needed before BOM;
- KD vs fixed when logistics/cost materially changes.

Batch questions. Prefer options or a default recommendation, e.g.:
- `A. Giữ AI Proposal hiện tại`
- `B. Dùng quy cách nhà máy khác`
- `C. Để TBD và tiếp tục BOM sơ bộ`

Do not ask for dimensions/materials the AI can reasonably propose and label.

## User-facing output template

### Engineering Summary
`AI đã hoàn thiện sơ bộ: [X] AI Proposal | [Y] Confirmed | [Z] TBD`

**Collection Standard**
- Khung/finish: ...
- Đan: ...
- Cushion/material chung: ...
- Assembly philosophy: ...

### Cần xác nhận
Show only 0-5 grouped blockers. If none, say `Không cần thêm thông tin ở thời điểm này.`

### [Product name] - Technical Card
- Kích thước & ergonomics: ...
- Khung & kết cấu: ...
- Đan: ...
- Nệm/hardware: ...
- Vật tư tham khảo: ...
- Rủi ro/TBD: ...

### Readiness
Use one:
- `Chưa sẵn sàng cho BOM`
- `Sẵn sàng sơ bộ cho BOM`
- `Sẵn sàng handoff kỹ thuật`

Give one sentence explaining why.

## Acceptance gate for Stage 04 complete

Stage 04 is complete enough for preliminary BOM when:
- every product has a coherent structural concept and assembly breakdown;
- major dimensions/ergonomic relationships are proposed or confirmed;
- main material/profile families are mapped or clearly flagged as new/TBD;
- weaving/cushion/hardware scopes are defined enough to estimate structure;
- no unresolved issue blocks quantity takeoff at a screening level.

Do not require all factory details to be confirmed before a preliminary BOM. Carry explicit TBD items forward.

## Stage checkpoint

Before moving to Stage 05, record the active concept/revision, Collection Standard, locked engineering decisions, critical `AI Proposal`/`TBD`, blockers and BOM readiness using the compact checkpoint format in `project-state.md`.
