# Workflow navigation and low-friction UX

## Core rule

Never require the user to remember a command, stage name, or exact phrase. At the end of every stage, explicitly state the current stage, the next useful action, and provide the smallest possible set of choices.

Prefer native clickable choice controls / suggested actions when the ChatGPT host exposes them. If the host does not support clickable controls in that turn, render the same choices as a short numbered choice line. Do not claim a control is clickable when it is not.

Always understand natural-language equivalents such as `ok`, `tiếp`, `tiếp tục`, `qua bước sau`, `được`, `làm tiếp`, `xong`, and similar phrases from context.

## Choice pattern

Use at most one primary next-step action and one or two secondary actions. Avoid long menus.

Examples:

After review/revision:
- Primary: `Tiếp tục: Thông số kỹ thuật`
- Secondary: `Tiếp tục chỉnh sửa`

After Engineering Definition:
- Primary: `Tiếp tục: Tạo BOM`
- Secondary: `Chỉnh thông số`
- Optional: `Xem toàn bộ thông số`

After BOM:
- Primary: `Tiếp tục: Đóng gói & Loading`
- Secondary: `Xem BOM từng sản phẩm`
- Optional: `Xem các mục chưa xác định`
- Optional: `Chỉnh BOM`

Inside BOM product browsing:
- Default to one product at a time.
- Prefer product-name choices/cards over a generic `Xem BOM chi tiết` action.
- If the user asks `xem BOM chi tiết` in a collection, present/select the product first; never dump every SKU's full BOM.
- After viewing one product, offer `Xem sản phẩm khác`, `Xem chi tiết [Product]`, `Chỉnh BOM [Product]`, or `Quay lại BOM collection`.

After Packing & Loading:
- Primary: `Tiếp tục: Xuất file`
- Secondary: `Chỉnh phương án đóng gói`
- Optional: `Xem chi tiết Loading`

After Output:
- Primary: `Hoàn tất project`
- Secondary: `Tạo revision mới`

## Transition rules

- Do not advance automatically when a stage still has a critical blocker that would make the next stage misleading.
- If only noncritical TBD items remain, allow progression and carry them forward explicitly.
- In Vietnamese user-facing views, show internal `TBD` as `Chưa xác định` unless the technical code itself is useful.
- When the user finishes review with `xong review` or equivalent, summarize the revision state and immediately surface the next-step choice; do not wait for the user to remember what comes next.
- Preserve the same project/chat state when moving between stages. Use `project-state.md` to carry the active concept/revision, locked decisions, critical TBD and blockers.
- At each stage transition, emit a compact checkpoint before the next-step choices.
- Before Stage 04, do not proceed without an identifiable Active Concept; ask one concise selection question if the source concept is ambiguous.
- After a long gap or a generic `tiếp tục`, reconstruct the smallest reliable checkpoint rather than asking the user to repeat the brief.
