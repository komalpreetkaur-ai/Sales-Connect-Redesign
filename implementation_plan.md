# Implementation Plan - Follow-Up Cards, Test Drive Booking Flow (Swiggy/Zomato Slot Style), Comments & Action History

Implement a dedicated, streamlined experience for Follow-Up leads when accessed from the Home screen KPI card. Show exclusively leads whose status is "Follow-up", provide a frictionless 3-tap flow on each card to schedule a Test Drive using a Swiggy / Zomato dining slot reservation style UI (date carousel + morning/afternoon/evening time slots), allow inline comment additions with fast suggestion chips, and display a rich, real-time Action History timeline for each lead.

---

## 1. Problem Statement & User Requirements

1. **Only Follow-up Status Leads on Screen**:
   - When tapping the "FOLLOW-UPS" card on the Home screen (`openFollowUpsScreen()`), show *only* cards whose status is "Follow-up".
   - Replace mixed-stage cards (Negotiation, Qualified, Test Drive, Booking Planned) with true follow-up leads.
   - Screen header and badge counts accurately represent active follow-up leads.

2. **Streamlined Flow on Each Card to Move to Test Drive State**:
   - Each card features a clear, accessible CTA button: **"Test Drive"** (with car icon).
   - Frictionless, complete in very few steps (low friction).
   - Clicking the CTA opens a popup / sheet modal inspired by **Swiggy Dineout / Zomato Dining Slot Reservation**:
     - **Horizontal Date Strip**: Scrollable cards with Weekday (TODAY, TOMORROW, SAT...), Date number, and Month.
     - **Categorized Time Slot Grid**:
       - ☀️ Morning Slots (10:00 AM, 10:30 AM, 11:00 AM, 11:30 AM)
       - 🌤️ Afternoon Slots (12:30 PM, 01:30 PM, 02:30 PM, 03:30 PM)
       - 🌙 Evening Slots (04:30 PM, 05:30 PM, 06:30 PM, 07:15 PM)
     - **Drive Location Preference**: `Dealership Showroom` vs `Customer Doorstep`.
     - **Optional Request Notes**: Short text input.
     - **Sticky Action Footer**: Live slot summary badge + "Confirm & Move to Test Drive" button.
   - Upon confirmation:
     - Lead status updates from `Follow-up` to `Test Drive`.
     - Card is removed from the Follow-up list with smooth transition.
     - New test drive entry is added to `#screen-test-drives`.
     - An entry is logged into the lead's Action History timeline.
     - Toast notification informs the user of successful scheduling.
     - Counter badges update across screens.

3. **Comments & Action History for Leads Not Ready to Move**:
   - On each follow-up card:
     - **Quick Comment Input**: Input field + "Post" button.
     - **Quick Suggestion Chips**: 1-tap tag chips (`Call tomorrow`, `Family discussion`, `Loan approval`, `Price compare`) to instantly populate the comment field.
     - **Real-Time Action History**:
       - Interactive accordion (`Action History (X) ▾`) showing the complete chronological log of events:
         - Calls, Follow-ups, Comments, Brochures, Test Drives, and Lead Creation.
         - Colored icon nodes, event title, detailed description, author, and timestamp.
       - Posting a new comment immediately appends it to the lead's history and updates the count badge in real time.

---

## 2. Proposed Implementation Steps

### Layer 1: Data Model & JavaScript Engine
- Define `followUpLeadsData`:
  - An array of realistic, complete follow-up leads (Rahul K., Priya M., Gurjant Singh, Kumari T., Harsh M., Vikram Sengupta), all having `status: 'Follow-up'`.
  - Rich initial action histories for each lead with calls, notes, brochures, and creation timestamps.
- Implement rendering and management functions:
  - `renderFollowUpScreen()`: Populates `#todayFollowupsCardsContainer` and `#otherFollowupsCardsContainer` dynamically from `followUpLeadsData`.
  - `openTestDriveBookingModal(leadId)`: Launches the Swiggy/Zomato style slot picker for the selected lead.
  - `selectTestDriveDate(dateStr, el)`: Selects active date in the horizontal date carousel.
  - `selectTestDriveSlot(slotStr, el)`: Selects active time slot in the categorized grid.
  - `selectTestDriveLocation(locStr, el)`: Toggles between Dealership and Doorstep.
  - `confirmTestDriveBooking()`: Moves lead to Test Drive state, updates Test Drive screen, adds history item, shows toast, and updates counters.
  - `addLeadComment(leadId)`: Saves inline comment to lead's history, refreshes timeline, and shows confirmation toast.
  - `quickFillComment(leadId, text)`: Populates input with pre-set template.
  - `toggleLeadHistory(leadId)`: Smoothly expands/collapses the action history accordion.
  - `showAppToast(message, type)`: Displays a sleek floating toast notification.

### Layer 2: Markup Updates in `index.html` and `sales_connect_redesign.html`
- Update `#screen-activities`:
  - Clean title: "Follow-Up Leads", subtitle: "Manage leads currently in follow-up status", and dynamic badge.
  - Search input and Date Filter seamlessly integrated with `searchActivityFollowups()` and `filterFollowupDateRange()`.
  - Structured card containers `#todayFollowupsCardsContainer` and `#otherFollowupsCardsContainer`.
- Add `#testDriveBookingModal`:
  - Swiggy / Zomato Dining Slot reservation style popup dialog with backdrop blur.
  - Horizontal day cards carousel.
  - Morning, Afternoon, Evening slot buttons.
  - Dealership vs Doorstep toggle.
  - Slot summary bar and confirmation button.
- Add `#appToastNotification` floating container.

### Layer 3: Parity & Verification
- Verify 100% parity: `diff index.html sales_connect_redesign.html` returns 0.
- Use headless Chrome to capture screenshots and verify:
  1. Home screen tapping "FOLLOW-UPS" card opening `#screen-activities`.
  2. Follow-up screen showing only cards with `Status: Follow-up`.
  3. Swiggy / Zomato Dining Slot Booking Modal open with interactive date and time slots.
  4. Card with expanded Action History and newly posted comment.
  5. Test Drive screen after scheduling a test drive.
- Commit and push to `origin/main`.
