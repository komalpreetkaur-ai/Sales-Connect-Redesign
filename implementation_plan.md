# Redesign Lead Priority (Hot, Warm, Cold) to Stand Out Distinctly

## Problem Diagnosis & Background Context

On the **Enquiries Screen (`#screen-enquiry`)**, there are currently two stacked segmented control bars sitting directly on top of each other:
1. **Top Bar**: `All (24) | Hot (8) | Warm (11) | Cold (5)` (Lead Temperature / Priority)
2. **Bottom Bar**: `All (24) | New (3) | Contacted (5) | Test Drive (4) | Negotiation (4) | ...` (Pipeline Stage)

### Why this design falls short:
- **Visual Monotony & Redundancy**: Stacking two identical gray tracks (`bg-slate-100/90 rounded-2xl`) directly on top of each other looks cluttered and repetitive. Both rows even start with an identical `All (24)` tab.
- **Lost Priority Contrast**: **Hot**, **Warm**, and **Cold** are emotional urgency indicators (🔥 Urgent vs ⚡ Active vs ❄️ Cooling down). When forced into a generic segmented bar where the active state is just a plain white box with blue text (`text-[#007AFF]`), **they do not stand out at all**. Cold leads appear in bright blue, while Hot leads lack any fiery warmth.

---

## Proposed Solution: Interactive Priority Hero Cards Strip

To resolve this, we will replace the generic top tab bar with a **distinct, high-impact Lead Temperature Hero Cards Strip** that gives each priority tier its own unmistakable visual identity, while keeping the **Pipeline Stage bar** below as the single workflow scrubber.

```
┌─────────────────────────────────────────────────────────────┐
│  LEAD PRIORITY                      [ Show All (24) ]       │
├─────────────────┬─────────────────────┬─────────────────────┤
│  🔥 8           │  ⚡ 11               │  ❄️ 5               │
│  Hot Leads      │  Warm Leads         │  Cold Leads         │
│  (High Urgency) │  (Active Nurture)   │  (Cool / Follow-up) │
└─────────────────┴─────────────────────┴─────────────────────┘
┌─────────────────────────────────────────────────────────────┐
│  PIPELINE STAGES                                            │
│  [ All (24) ] [ New (3) ] [ Contacted (5) ] [ Test Drive (4) ] …
└─────────────────────────────────────────────────────────────┘
```

---

## User Review Required

> [!IMPORTANT]
> **Key Design Options for Lead Temperature**:
> We recommend **Option 1 (Hero Stat Cards)** because it completely eliminates the stacked filter look and makes Hot, Warm, and Cold instantly recognizable at a glance. Please review the options below:

### Option 1 (Recommended): Interactive Priority Stat Cards Strip
- **Layout**: A dedicated 3-column interactive card grid plus an `All (24)` header toggle:
  - **🔥 Hot Leads (8)**:
    - Warm amber tint (`bg-amber-50/70 border border-amber-200/80`).
    - Flame icon (`fa-solid fa-fire text-amber-500`).
    - Bold metric `8` in rich amber-600.
    - Active state: Glowing amber focus ring (`ring-2 ring-amber-400 bg-amber-100/60 shadow-xs`), elevating the card.
  - **⚡ Warm Leads (11)**:
    - Vibrant sky blue tint (`bg-blue-50/70 border border-blue-200/80`).
    - Lightning/spark icon (`fa-solid fa-bolt text-[#007AFF]`).
    - Bold metric `11` in brand blue `#007AFF`.
    - Active state: Glowing blue focus ring (`ring-2 ring-blue-400 bg-blue-100/60 shadow-xs`).
  - **❄️ Cold Leads (5)**:
    - Cool slate tint (`bg-slate-50/80 border border-slate-200/80`).
    - Snowflake icon (`fa-solid fa-snowflake text-slate-500`).
    - Bold metric `5` in slate-700.
    - Active state: Elevated slate focus ring (`ring-2 ring-slate-400 bg-slate-100 shadow-xs`).
  - **Header Toggle `All (24)`**:
    - Clean pill button in the section header allowing the user to quickly reset and view all 24 leads, or tapping an active card toggles it back to All.

### Option 2: Vibrant Colored Badge Pills Bar (Compact Alternative)
- A single horizontal row with distinct colored pill badges (not inside a generic gray track):
  - `All (24)` (clean white elevated card with blue text)
  - `🔥 Hot (8)` (amber outline with orange badge)
  - `⚡ Warm (11)` (blue outline with azure badge)
  - `❄️ Cold (5)` (slate outline with cool gray badge)
- Takes up slightly less vertical space than Option 1, but maintains the distinct color identities.

---

## Open Questions

> [!NOTE]
> 1. Do you prefer **Option 1 (3 Interactive Hero Stat Cards)** or **Option 2 (Compact Colored Badge Pills Bar)**?
> 2. Should clicking an active card (e.g. clicking Hot when Hot is already selected) toggle back to `All (24)`, alongside having the dedicated `All (24)` button?

---

## Proposed Changes

### Component: Enquiries Screen Header & Filters (`#screen-enquiry`)

#### [MODIFY] [index.html](file:///Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/index.html)
- Replace lines 668–682 (the duplicate gray segmented temperature bar) with the **Priority Hero Cards Strip**:
  - Add section title `LEAD PRIORITY` with the `All (24)` filter pill.
  - Render the 3 interactive priority cards for Hot, Warm, and Cold with signature icons, metric counters, and status badges.
- Update `filterByTemperature(tempKey, btn)` to toggle active visual styles on the new cards (amber glow ring for Hot, blue glow ring for Warm, slate glow ring for Cold, reset state for All).
- Ensure smooth synchronization with `applyCombinedEnquiryFilters()` so searching and stage filtering continue to work seamlessly.

#### [MODIFY] [sales_connect_redesign.html](file:///Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/sales_connect_redesign.html)
- Apply the identical HTML and JavaScript updates to maintain exact parity with `index.html`.

#### [MODIFY] [walkthrough.md](file:///Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/walkthrough.md)
- Document the new Lead Priority Card design with before/after screenshots and interactive state explanations.

---

## Verification Plan

### Automated & Manual Verification
1. **Diff Parity Check**: Run `diff -u sales_connect_redesign.html index.html` to guarantee complete alignment.
2. **Visual Inspection via Headless Chrome**:
   - Capture screenshot of Enquiries screen with `All (24)` active.
   - Capture screenshot with `🔥 Hot Leads (8)` active.
   - Capture screenshot with `⚡ Warm Leads (11)` active.
   - Capture screenshot with `❄️ Cold Leads (5)` active.
   - Capture screenshot combining `🔥 Hot` with `Contacted` stage filter to verify multi-filter behavior.
3. **Responsive Check**: Confirm fixed mobile width (`402px`) and zero clipping or horizontal overflow.
4. **Git Version Control**: Commit and push changes to `main`.
