# Project State and Checkpoints

## Goal

Keep long furniture R&D chats coherent across concept selection, revisions, engineering, BOM, packing/loading and output. Maintain a compact internal project state and expose only the checkpoint information the user needs.

## State model

Track these fields throughout the project:
- `Project`: collection/project name or generated working name.
- `Mode`: `Single Product` or `Collection`.
- `Current Stage`: 01-07.
- `Active Concept`: selected concept, hybrid concept, or `Not selected`.
- `Active Revision`: `Base`, `R01`, `R02`, etc.
- `Products`: requested SKU/product list.
- `Design DNA`: shared collection rules that remain active.
- `Locked Decisions`: user-confirmed decisions that should not change silently.
- `Open Issues`: review or technical issues not yet resolved.
- `TBD / AI Proposal`: unresolved controlled data that must carry forward.
- `Readiness`: current stage readiness and any blocker.

Do not dump this entire state on every turn. Use it internally and surface a concise checkpoint at stage transitions, after a major revision, or when the user asks for status.

## Concept selection gate

Before Stage 04, the project must have an `Active Concept`.

Valid cases:
- user explicitly selects Concept 01/02/03;
- user asks to combine concepts;
- user approves the latest revised concept;
- user uses clear natural language such as `chọn cái này`, `lấy concept 2`, `ok mẫu này`.

For hybrids, create a new controlled concept label such as `Hybrid H01` and record its sources, e.g. `silhouette from Concept 02 + base from Concept 01`. Do not keep calling it Concept 01 or 02 after the architecture has materially changed.

If the user asks to enter Stage 04 without any concept being identifiable, ask one concise selection question rather than proceeding with an ambiguous source.

## Revision control

Use revision IDs `R01`, `R02`, ... for consolidated review batches.

For each review issue track:
- `Issue ID`: `R01-01`, `R01-02`, ...
- `Scope`: collection-wide or product/SKU.
- `Observation`: exact user-reported issue.
- `Action`: intended change.
- `Status`: `Open`, `Applied`, `Rejected`, or `Deferred`.

While the user is listing issues, keep collecting under a pending review batch. When the user says `xong review`, `review xong`, `ok review xong`, or equivalent:
1. freeze the issue list for that batch;
2. assign the next revision ID;
3. apply or summarize the requested changes;
4. mark issue statuses;
5. update `Active Revision`;
6. surface the next action.

If the user requests an immediate fix before saying review is complete, apply that item but keep the current batch open unless the user clearly closes it.

Do not lose earlier accepted fixes when a later issue is added. Do not reopen `Rejected` or `Deferred` issues unless the user requests it.

## Locked decisions

Treat explicit user confirmations as locked unless the user changes them. Examples:
- selected concept/hybrid;
- weaving coverage zones;
- swivel/fixed/KD strategy;
- visible frame language;
- product list;
- market/use context;
- factory-confirmed material or mechanism.

A later AI proposal must not silently override a locked decision. If a conflict appears, show it as a tradeoff or ask for confirmation.

## Stage checkpoint

At every stage transition, create a compact checkpoint with this structure:

### Checkpoint
- `Stage completed`: ...
- `Active concept / revision`: ...
- `Locked`: 2-5 key decisions only.
- `Carry forward`: critical `AI Proposal` / `TBD` only.
- `Blockers`: none, or the smallest actionable list.
- `Next`: next stage/action.

Do not repeat a full technical table in the checkpoint.

## Stage handoff rules

### 03 -> 04
Carry forward:
- active concept/hybrid and revision;
- approved Design DNA;
- all applied review issues;
- visible design intent that must be preserved;
- unresolved design risks.

### 04 -> 05
Carry forward:
- controlled dimensions and engineering proposals;
- Collection Standard;
- product assembly logic;
- material mappings and status;
- technical TBD/blockers.

### 05 -> 06
Carry forward:
- BOM maturity;
- assembly/KD/fixed/stack/nest logic;
- approximate weights or dimensions only when controlled enough;
- packaging-critical TBD.

### 06 -> 07
Carry forward:
- packing mode and status;
- packed dimensions/weights with their status;
- preliminary vs verified loading distinction;
- unresolved logistics assumptions.

## Recovery after a long chat

If the user says `tiếp tục`, `đang tới đâu`, or returns after many turns, reconstruct the smallest reliable checkpoint from the current chat/project state before taking the next action. Do not ask the user to re-enter the whole brief.

If two possible states conflict, state the conflict explicitly and ask one targeted question. Never guess which concept/revision is active when that choice would change downstream engineering.
