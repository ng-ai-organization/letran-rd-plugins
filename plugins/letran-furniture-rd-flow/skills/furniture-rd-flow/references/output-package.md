# Stage 07 - Output / R&D Package

## Goal

Package the project's controlled R&D information into useful deliverables without overstating file fidelity or technical maturity.

## Default user choice

Present a small set of actions:
- Primary: `Xuất bộ hồ sơ R&D đầy đủ`
- Secondary: `Xuất cho kỹ thuật`
- Optional: `Chọn file cần xuất`

Prefer native clickable choices when available; otherwise show short numbered choices.

## Full R&D package

When supported by the current tool environment, assemble a project package containing appropriate outputs such as:
- concept / collection board images, preferably JPG/PNG;
- lifestyle scene images for multi-product collections;
- Project Summary / Design DNA / revision history;
- Technical Specification in PDF/DOCX or another available document format;
- BOM in XLSX/CSV;
- Packing & Loading summary in XLSX/PDF/CSV;
- controlled 2D exchange such as DXF/DWG-compatible output only when controlled geometry exists;
- 3D handoff such as OBJ/SCAD/STEP only when the environment and geometry fidelity genuinely support it.

Do not claim a file was created if the current ChatGPT/tool environment cannot actually create it.

## Engineering handoff package

Prioritize:
- Engineering Definition;
- BOM;
- controlled dimensions and material mappings;
- assembly/subassembly breakdown;
- open TBD / confirmation list;
- available 2D/3D exchange files.

Always include an `ENGINEERING HANDOFF - CẦN XÁC NHẬN` section listing unresolved critical items and their status.

## File readiness rules

Assess each output independently:
- `Ready`: enough controlled data and tool support exist to create it.
- `Preliminary`: useful but based on AI Proposal/TBD assumptions.
- `Not ready`: insufficient controlled geometry/data or unavailable tool capability.

Examples:
- BOM XLSX may be Ready while 3D STEP is Not ready.
- A DXF generated from controlled 2D dimensions may be Preliminary until engineer verification.

Never generate a decorative placeholder file and present it as engineering-ready.

## Versioning

Use a stable project/collection name and increment package revision rather than overwrite prior releases, e.g. `TEST03_R&D_Package_V01`, then `V02` after controlled revisions.

Prefer folders:
`01_Concept`, `02_Technical`, `03_BOM`, `04_Packing_Loading`, `05_2D_3D`, plus a Project Summary.

## Pre-export readiness summary

Before creating files, show a concise matrix:
- Concept
- Technical
- BOM
- Packing/Loading
- 2D
- 3D

For each, show Ready / Preliminary / Not ready and one short reason. Noncritical TBD items do not block exporting an R&D package; preserve them explicitly in the package.

## Completion actions

After output:
- Primary: `Hoàn tất project`
- Secondary: `Tạo revision mới`

A revision stays in the same chat/project and preserves Design DNA, history and controlled IDs where appropriate.
