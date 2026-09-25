# Implementation Plan - Redesigning STAGE & WORKFLOW (All 7 Stages Visible)

Redesigning the **STAGE & WORKFLOW** component in [`sales_connect_redesign.html`](file:///Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/sales_connect_redesign.html) to display **all 7 stages on-screen at once** without requiring horizontal scrolling or suffering from side cutoffs.

## User Review Required

> [!IMPORTANT]
> **Proposed Redesign Layout Options for 7-Stage Workflow**:
> 
> ### 🌟 Option A: Compact 2-Row Connected Workflow Matrix (Recommended)
> - **Layout**: Displays all 7 stage pills across 2 connected rows (Row 1: Steps 1-4; Row 2: Steps 5-7) fitting perfectly within the `402px` container.
> - **Visual Hierarchy**:
>   - **Completed Steps (1 & 2)**: Soft blue pill with checkmarks (`✓`).
>   - **Active Step (3: Qualified)**: Solid primary blue pill with pulsing indicator (`Step 3 of 7: Qualified`).
>   - **Upcoming Steps (4, 5, 6, 7)**: Crisp slate pills with numbered indicators.
> - **Interactivity**: Clicking any stage instantly updates the active stage.
> 
> ### 📋 Option B: Vertical Stepper Pipeline Card
> - **Layout**: Displays all 7 stages stacked vertically with a continuous left-side progress line, status badges, and expandable details.

---

## Open Questions

> [!NOTE]
> Which layout style do you prefer for displaying all 7 stages:
> 1. **Option A (2-Row Connected Matrix)**: Fits all 7 stage pills horizontally across 2 rows for quick 1-tap switching.
> 2. **Option B (Vertical Stepper Pipeline)**: Stacked vertical timeline showing all 7 stages top-to-bottom.

---

## Proposed Changes

### UI Components (`sales_connect_redesign.html`)

#### [MODIFY] [sales_connect_redesign.html](file:///Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/sales_connect_redesign.html)

- Replace the horizontal scrolling stepper container (`scrollbar-none`) with a responsive 2-row / grid 7-stage connected workflow component.
- Update `setModernStep` JS function to handle the 2-row layout state updating seamlessly.

---

## Verification Plan

### Automated Tests
- Syntax check HTML and JavaScript functions in browser environment.

### Manual Verification
- Verify all 7 stages (`New Inquiry`, `Contacted`, `Qualified`, `Test Drive`, `Negotiation`, `Closed - Won`, `Closed - Lost`) are 100% visible on a 402px mobile screen without scrolling.
- Test interactive stage selection on click.
