# Walkthrough - Sales Connect Mobile Redesign

## 🔄 Re-Swapped Dashboard Order: Leads Assigned on Top, Weekly Target Below

Updated the Home dashboard layout to position **LEADS ASSIGNED** at the top, followed by **WEEKLY TARGET** and the operational KPI cards:

![Leads Assigned Above Weekly Target](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_home_leads_then_target.png)

### ✨ Changes Applied
1. **Immediate Lead Visibility**: The **LEADS ASSIGNED** metric card (showing total assigned leads `24` with `+4 New Today`) is now placed directly below the greeting and date filter bar.
2. **Target & Pipeline Overview**: The **WEEKLY TARGET** hero progress card (`3 of 4 Units Sold`, 75% gauge) appears immediately after, leading naturally into the four KPI status cards (*Follow-ups*, *Test Drives*, *Bookings*, *Deliveries*).
3. **100% Dynamic Parity**: All date range filters ("Today", "This Week", "This Month") continue to update metrics across both sections dynamically.
4. **100% Parity Verified**: `index.html` and `sales_connect_redesign.html` maintain complete 0-diff parity.

---

## ➕ Removed Quick Actions Row & Added Floating "Add Enquiry" Button (FAB)

Removed the static 2-card Quick Actions hub (`Add Enquiry` & `Add New Booking`) from the top of the Home dashboard, and introduced a modern Floating Action Button (`+ Add Enquiry` FAB) docked on the bottom right:

![Floating Add Enquiry Button on Home Screen](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_home_fab_centered.png)

### ✨ Changes Applied
1. **Removed Static Quick Actions Row**: Removed the top `[ + Add Enquiry ]` and `[ 📝 Add New Booking ]` card container from `#screen-home`, clearing vertical clutter and allowing **WEEKLY TARGET** and **LEADS ASSIGNED** to immediately lead the dashboard view.
2. **Modern Floating Action Button (FAB)**: Created `#fabAddEnquiry` positioned at `bottom-20 right-4` directly above the bottom navigation bar. Features brand gradient blue styling, subtle white plus badge, bold typography, and tap elevation feedback.
3. **One-Tap Category Modal**: Tapping the FAB triggers `openAddEnquiryModal()`, displaying the smooth bottom-sheet modal to select between **Sales Enquiry** (4-step form), **Service Enquiry**, or **Other Enquiry**.
4. **Context-Aware Visibility**: The FAB displays on main dashboard browsing screens (`Home` and `Enquiry`) and automatically hides on enquiry forms, details screens, and booking workflows to preserve clean form layouts.
5. **100% Parity Verified**: `index.html` and `sales_connect_redesign.html` maintain complete 0-diff parity.

---

## 🔄 Swapped Weekly Target and Leads Assigned Sections on Home Dashboard

Swapped the **WEEKLY TARGET** and **LEADS ASSIGNED** cards on the Home dashboard (`#screen-home`):

![Swapped Weekly Target and Leads Assigned](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_home_swapped_target_leads.png)

### ✨ Changes Applied
1. **Prioritized Sales Target**: The **WEEKLY TARGET** progress card (with units sold, circular SVG progress ring, and target-to-goal progress bar) now appears immediately beneath the Quick Action shortcuts.
2. **Streamlined Leads & KPI Pipeline**: The **LEADS ASSIGNED** card (Total Leads Assigned: 24) now seamlessly leads directly into the four pipeline breakdown cards (Follow-ups, Test Drives, Bookings, Deliveries).
3. **100% Dynamic Parity**: All date range filters ("Today", "This Week", "This Month") continue to update metrics across both sections dynamically.
4. **100% Parity Verified**: `index.html` and `sales_connect_redesign.html` maintain complete 0-diff parity.

---

## 📞 Removed "Call Customer" & "WhatsApp" Buttons from Booking Details Pages

Removed the `[ 📞 Call Customer ]` and `[ 💬 WhatsApp ]` quick action buttons from the Booking Details banner card across all booking details pages (`#screen-booking-details`):

![Clean Booking Details Banner](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_booking_details_clean.png)

### ✨ Changes Applied
1. **Removed Action Buttons Row**: Removed `#bdetCallBtn` ("Call Customer") and `#bdetWaBtn` ("WhatsApp") alongside their enclosing grid container from `#screen-booking-details`.
2. **Clean Banner Presentation**: The main Booking Info banner card now cleanly showcases the Booking ID, Customer Name, Token Amount, and Token status pill without visual clutter.
3. **Safe Script Updating**: Safely updated `openBookingDetails(bookingId)` to eliminate DOM references to the removed buttons, preventing any null pointer exceptions while retaining full functionality across all booking records.
4. **100% Parity Verified**: `index.html` and `sales_connect_redesign.html` maintain complete 0-diff parity.

---

## 🎨 Cleaned Stage Filter Accordion (Removed Background Color & Reset Text)

Updated the **Stage** filter section inside the Filter Bottom Sheet Modal (`#filterModal`):

![Cleaned Stage Filter Section](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_stage_filter_clean.png)

### ✨ Changes Applied
1. **Removed Custom Tinted Background**: Changed the container from `bg-[#F5F9FF]` to clean `bg-white`, perfectly blending with the other filter accordion cards.
2. **Removed "Reset" Text**: Eliminated the redundant inline Reset button from the Stage section header, leaving a clean chevron toggle icon on the right.
3. **100% Parity Verified**: `index.html` and `sales_connect_redesign.html` verified with 0 diff.

---

## 🚫 Clean Text-Only Cancel & Submit Booking Buttons

Removed the `fa-xmark` (`x`) and `fa-check` (`✓`) icons from the **Cancel** and **Submit Booking** action buttons on the New Vehicle Booking screen (`#screen-booking-create`):

![Text-Only Cancel & Submit Booking Buttons](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_booking_buttons_no_icons.png)

### ✨ Changes Applied
1. **Removed Icons**: Eliminated `<i class="fa-solid fa-xmark">` from the Cancel button and `<i class="fa-solid fa-check">` from the Submit Booking button.
2. **Centered Text-Only Layout**: Both buttons now display clean, balanced typography (`Cancel` and `Submit Booking`) without redundant icon clutter.
3. **100% Parity Verified**: `index.html` and `sales_connect_redesign.html` maintain complete 0-diff parity.

---

## ⬆️ Automatic Top-of-Screen Scroll Reset on Page Landing

Resolved the page navigation scroll behavior so that whenever a user lands on any screen or switches tabs, the view **always starts from the top of the screen (`scrollTop = 0`)**:

![Landing at Top of Vehicle Bookings](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_screen_booking_top.png)

### ✨ Technical Enhancements
1. **Added `id="mobile-viewport"` to Primary Scroll Region**:
   - Explicitly assigned `id="mobile-viewport"` to the main scrollable `<main>` element, ensuring all internal element queries (`document.getElementById('mobile-viewport')`) resolve directly to the primary viewport.
2. **Robust Multi-Layer `resetScrollToTop()` Mechanism**:
   - Immediately sets `scrollTop = 0` on the viewport container, `window`, `document.body`, and `document.documentElement`.
   - Uses `mainEl.scrollTo({ top: 0, left: 0, behavior: 'instant' })` to avoid laggy animation jumps.
   - Re-asserts in `requestAnimationFrame` and a subsequent 30ms tick to guarantee no layout shifts or asynchronous DOM repaints retain stale scroll offsets.
3. **Universally Integrated Across Navigation**:
   - Triggers on all screen switches (`switchScreen`): bottom navigation tabs, card clicks (Enquiry Details, Booking Details), header profile/notifications, and back buttons.
   - Triggers on wizard step transitions (`navigateSalesStep` / `updateSalesStepUI`).
   - Triggers on horizontal activity tabs switching (`switchLeadActTab`, `switchActivityTab`).
4. **100% Parity Verified**: `index.html` and `sales_connect_redesign.html` remain in complete zero-diff parity.

---

## 🔐 OTP Verification Flow & Lead Generation Confirmation

Implemented the complete end-to-end OTP verification and Lead Generated Confirmation experience triggered immediately upon submitting Step 4 (PII Information) of the Sales Enquiry Form (`#screen-sales-enquiry`).

````carousel
![Sales Enquiry Step 4 - Ready to Submit](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_sales_step4_view.png)
<!-- slide -->
![OTP Verification Modal](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_sales_otp_modal.png)
<!-- slide -->
![Lead Generated Confirmation Modal](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_lead_generated_success.png)
````

### ✨ Key Features Implemented

1. **Seamless Step 4 Transition**:
   - In Step 4 (`#sales-step-4`), the SMS checkbox is selected by default and WhatsApp is easily toggleable matching the user's reference mockup (`media_1791962853003.png`).
   - Clicking **Submit** on Step 4 calls `openSalesOtpModal()`, seamlessly bringing up the security verification flow instead of an abrupt exit.

2. **Interactive OTP Verification Modal (`#salesOtpModal`)**:
   - **Visual Presentation**: Glassmorphic dark backdrop (`bg-slate-900/60 backdrop-blur-xs`) and rounded-3xl dialog card with a blue security shield icon.
   - **Recipient Context**: Displays the customer's phone number dynamically (e.g. `+91 98112 33445`) and transmission channel badge `(via SMS)` or `(via SMS & WhatsApp)`.
   - **4 Discrete Digit Boxes**: Auto-advances focus to the next box upon typing a digit, supports backspace to jump to the previous box, and handles 4-digit clipboard pasting.
   - **Instant Test OTP Helper**: Clickable `Auto-fill Test OTP: 4829` helper chip populates all 4 boxes in one tap for effortless testing.
   - **Live Countdown Timer**: 30-second live resend countdown that switches to an active "Resend OTP" button on expiration.
   - **Validation Feedback**: Highlights missing boxes and displays clear validation guidance if submitted incomplete.

3. **Lead Generated Confirmation Modal (`#leadSuccessModal`)**:
   - **Celebration Badge**: Mint emerald checkmark badge with circular border.
   - **Confirmation Typography**: Clear "Lead Generated Successfully!" heading with descriptive subtitle.
   - **Dynamic Lead Summary Card**:
     - Lead Reference ID (e.g. `ENQ987875455`) with document icon and `Open Lead` status pill.
     - Customer initials avatar (`VS`), full name (`Vikram Singhania`), and phone number.
     - 4-item specification grid: Preferred Vehicle / Model (`Suzuki Hayabusa 2025`), Stage (`● New`), Category (`Sales`), and Created Timestamp (`Today, 10:45 AM`).
     - Conditional Exchange Vehicle badge if an exchange vehicle was entered.
   - **Primary CTA: "View in Enquiries" (`viewGeneratedLeadInEnquiries()`)**:
     - Closes modal, navigates to `#screen-enquiry`, resets stage filter to `All`, scrolls to top, and applies a gentle highlight pulse to the newly created lead card.
     - Automatically increments pipeline counters (`All` from 24 -> 25, `New` from 3 -> 4).
   - **Secondary CTA: "Create Another Enquiry" (`createNewAnotherEnquiry()`)**:
     - Closes modal, clears the form inputs, resets the wizard back to Step 1, and readies the form for a new entry.

4. **100% Parity Verified**:
   - Both `index.html` and `sales_connect_redesign.html` verified with `diff -u` returning 0.

---

## 🚗 Cleaned Booking Cards (Removed Call & WhatsApp Action Buttons)

Removed the Call (`fa-phone`) and WhatsApp (`fa-whatsapp`) quick-action buttons from all booking cards in the Vehicle Bookings list (`#screen-booking`):

![Cleaned Booking Cards with Details Link Only](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_booking_cards_clean.png)

### ✨ Improvements
1. **Uncluttered Booking Card Footer**:
   - The card footer now cleanly displays delivery date (`Delivery: 10 Oct 2026`) aligned to the left, and the single tap-target `Details >` aligned to the right.
   - Eliminates redundant small icon buttons that cramped the card footer.
2. **Consistent Customer Contact Flow**:
   - Tapping the card or `Details >` opens the full dedicated Booking Details screen (`#screen-booking-details`) where full customer communications and actions can be performed.
3. **100% Parity**: Both `index.html` and `sales_connect_redesign.html` remain identical.

---

## 📱 Pipeline Stage Selector & Bottom Sheet Picker (Zero Tabs Redesign)

Redesigned the Pipeline Stage selector to completely eliminate the tabs appearance in favor of an **Executive Filter Card with an iOS Bottom Sheet Picker**:

![Stage Selector Card (Default State)](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_stage_selector_card.png)

![Stage Picker Bottom Sheet Modal](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_stage_picker_bottom_sheet.png)

![Filtered State (Test Drive Active with Quick Reset)](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_stage_selector_filtered_testdrive.png)

### ✨ Why This Design Completely Solves the Problem
1. **Zero "Tabs" Look**:
   - Replaced the bulky 3x3 block of tabs with a clean, low-profile selector card (~55px height) taking minimal vertical space.
   - Leads below have immediate breathing room without being pushed down the screen.
2. **Native iOS Bottom Sheet Picker (`#stagePickerModal`)**:
   - Tapping anywhere on the selector card or on `Select ▾` slides up an elegant modal bottom sheet.
   - Categorized into **Overview** (`All Stages • 24 Leads`), **Active Deal Journey** (`New`, `Follow-up`, `Test Drive`, `Negotiation`, `Booking`), and **Completed & Outcomes** (`Delivered`, `Close Lost`, `Junk`).
   - Every single stage displays a dedicated icon, full descriptive subtitle, lead count badge, and active checkmark (`✓`).
3. **One-Tap Quick Reset**:
   - When a stage filter is active (e.g. `Test Drive`), a quick `Reset` button appears right on the card, enabling the user to reset to all leads with a single tap without reopening the modal.
4. **Zero Dragging / Zero Cutoff**:
   - All 9 stages are clearly legible vertically in the sheet with no awkward horizontal scrolling.
5. **100% Parity**: Both `index.html` and `sales_connect_redesign.html` are identical.

---

## 🔥 Expanded Priority Actions Today & Removed "+ New Booking" Button

Addressed the user requests:
1. **Added More Priority Action Cards** under **PRIORITY ACTIONS TODAY** on the Home Dashboard.
2. **Removed "+ New Booking" Button** from the Vehicle Bookings screen header.

![Expanded Priority Actions Cards](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_home_priority_actions_scrolled.png)

![Booking Screen without New Booking Button](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_booking_no_new_button.png)

### ✨ Changes Applied
1. **Priority Actions Today (5 High-Priority Automotive Tasks)**:
   - **Overdue Follow-up** (Priya M. • Negotiation): 2h overdue alert with phone and WhatsApp actions.
   - **Test Drive Confirmation** (Shreya S. • Test Drive): 10:30 AM Home Test Drive Baleno confirmation.
   - **Advance Token Pending** (Rupesh Bhatt • Booking): ₹50,000 token clearance alert.
   - **Delivery PDI Sign-off** (Vikram Malhotra • Delivery Ready): 4:00 PM Grand Vitara delivery & gate-pass clearance.
   - **Loan Disbursal Action** (Amit Patel • Financing): Expiring bank sanction letter follow-up.
   - Updated urgent badge indicator to `5 Urgent`.
   - Card clicks navigate directly to enquiry details.

2. **Cleaned Vehicle Bookings Header**:
   - Removed `<button onclick="openCreateBookingForm()"> + New Booking </button>` from the header of `#screen-booking` as requested.
   - Header is now clean and uncluttered with back navigation and clear section title.

3. **100% Parity Maintained**: Both `index.html` and `sales_connect_redesign.html` are identical.

---

## 📱 Redesigned Pipeline Stage Filter (All Options Visible at a Glance)

Redesigned the **Pipeline Stage** filter selector on the Enquiries screen (`#screen-enquiry`) from a cut-off single-row horizontal drag/scroll container into a clean, balanced **3x3 all-visible dashboard matrix** with count badges:

![Redesigned Pipeline Stages Matrix](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_pipeline_stages_redesign.png)

![Filtered by Test Drive](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_pipeline_stage_testdrive.png)

### ✨ Problem Solved & Key Improvements
1. **Zero Hidden Options / No Dragging Required**:
   - Previously, stages after `Test Drive (4)` (such as `Negotiation`, `Booking`, `Delivered`, `Close Lost`, and `Junk`) were hidden off-screen to the right and required horizontal scrolling/dragging that users didn't notice or find discoverable.
   - Now, all **9 options** (`All 24`, `New 3`, `Follow-up 5`, `Test Drive 4`, `Negotiation 4`, `Booking 3`, `Delivered 2`, `Close Lost 2`, `Junk 1`) are arranged in a balanced 3x3 matrix, visible immediately without any dragging.
2. **Distinct Active/Inactive Contrast**:
   - The selected stage stands out prominently with bold brand blue (`#007AFF`), white text, and a crisp shadow.
   - Inactive stages are subtle with crisp borders and gentle hover/active feedback.
3. **Toggle & Seamless Filtering**:
   - Tapping an active filter toggles back to `All (24)`.
   - Card filtering and dynamic top count badge (`Total: 24`, `Test Drive: 4`, etc.) continue to update instantly.
4. **100% Parity Maintained**: Both `index.html` and `sales_connect_redesign.html` are identical and verified with zero diff.

---

## 🔔 Complete App Notifications Flow

Built an interactive **Notifications Center** screen (`#screen-notifications`) wired directly to the top app header bell icon (`<button onclick="switchScreen('notifications')">`):

![Interactive Notifications Center](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_notifications_flow.png)

### ✨ Features & Implementation
1. **Direct Header Bell Integration**:
   - Tapping the notification bell icon (with unread badge indicator) in the top header transitions immediately to the Notifications Screen from any screen in the app.
   - The back button cleanly returns to whichever screen the user was previously viewing via `goBackFromDetails()`.
2. **Category Filter Tabs**:
   - `All (6)`, `Unread (3)`, `Leads (2)`, `Reminders (2)`, and `Updates (2)` with dynamic filtering and zero-state messaging.
3. **Realistic Automotive CRM Alerts**:
   - **New Lead Assigned**: Shows priority badge (`Hot Priority`) and deep-links directly to the lead.
   - **Test Drive in 30 Mins**: Shows scheduled slot (`2:30 PM`) and opens the Test Drives schedule.
   - **Follow-up Call Due**: Highlights overdue action (`Mohit Kumar`) and links to log activities.
   - **Token Received (₹50,000)**: Verified booking alert deep-linking into booking details (`BK987875364`).
   - **Delivery Ready**: PDI completion notice linking to the deliveries screen.
   - **Target Progress 🎯**: Weekly goal milestone update.
4. **Mark As Read & Deep-Linking**:
   - Tapping any notification automatically marks it as read and jumps directly into the associated workflow.
   - Tapping **Mark read** clears all unread badges and hides the red notification dot from the top header bell icon.
5. **Exact Parity Maintained**: Both `index.html` and `sales_connect_redesign.html` are completely identical and synchronized.

---

## 🔄 Updated Stage & Workflow to 5 Core Stages

Updated the **STAGE & WORKFLOW** component on the Enquiry / Lead Details screen (`#screen-enquiry-details`) to reflect the requested 5 stages:
1. **New**
2. **Follow-up**
3. **Test Drive**
4. **Negotiation**
5. **Close Lost**

![Updated 5 Stages Workflow Component](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_5_stages_workflow.png)

### ✨ Changes Applied
1. **Streamlined 5-Stage Architecture**:
   - Replaced the previous 7-stage layout with the 5 stages requested: `New`, `Follow-up`, `Test Drive`, `Negotiation`, and `Close Lost`.
   - **Row 1 (Active Progress)**: `1. New`, `2. Follow-up`, `3. Test Drive` in a clean 3-column layout.
   - **Next Pipeline Stages Indicator**: Divider line transitioning into closing stages.
   - **Row 2 (Closing)**: `4. Negotiation` and `5. Close Lost` in a balanced 2-column layout.
2. **Interactive Stepper Dynamics**:
   - Updated `setModernStep()` function to dynamically handle the 5 stages, update the status pill (`Step 2 of 5: Follow-up`), mark prior steps as completed with blue checkmarks, and highlight active steps.
   - Added signature red/rose accenting for `5. Close Lost`.
3. **Exact Parity Maintained**: Both `index.html` and `sales_connect_redesign.html` are completely identical and synchronized.

---

## 👤 Removed "+ Activity" Button from Lead Details Header

Removed the redundant `+ Activity` button from the customer card header on the Enquiry / Lead Details screen (`#screen-enquiry-details`) as requested:

![Clean Lead Details Header](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_enquiry_details_clean.png)

### ✨ Changes Applied
1. **Removed Redundant "+ Activity" CTA**: Removed `<button onclick="openLeadActivitiesScreen()">+ Activity</button>` from the customer summary card header.
2. **Clean Profile Actions**: The top header now cleanly presents the customer communication actions (call, email) alongside `+ Booking`, eliminating button crowding while full activity timeline functionality remains accessible in the dedicated **Activities** tab right below.
3. **Exact Parity Maintained**: Both `index.html` and `sales_connect_redesign.html` are completely identical and synchronized.

---

## 🔍 Removed "Update" & "+ Add Filter" from Filters Modal

Removed the `Update` link and `+ Add Filter` button from the top header of the Filters modal as requested:

![Clean Filters Modal Header](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_filter_modal_clean.png)

### ✨ Changes Applied
1. **Removed Redundant Action Buttons**: Stripped the underlined `Update` button and the blue `+ Add Filter` pill button from the modal's top right header.
2. **Clean Modal Chrome**: The header now displays the **FILTERS** title with dropdown indicator and a dedicated close button (`✕`), leaving the primary actions cleanly consolidated at the bottom with **Cancel** and **Apply**.
3. **Exact Parity Maintained**: Both `index.html` and `sales_connect_redesign.html` are completely identical and synchronized.

---

## 🎯 Removed "75% Achieved" Tag from Target Header

Removed the `75% Achieved` pill badge from the **WEEKLY TARGET** section header on the Home Dashboard as requested:

![Clean Weekly Target Section Header](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_home_no_target_badge.png)

### ✨ Changes Applied
1. **Removed Tag Pill**: Removed `<span id="homeTargetAchievedBadge">75% Achieved</span>` from the section header.
2. **Harmonized Section Headers**: The **WEEKLY TARGET** title now cleanly mirrors the **LEADS ASSIGNED** header above it without cluttered pill tags. The progress percentage remains clearly visible in the circular indicator within the card.
3. **Exact Parity Maintained**: Both `index.html` and `sales_connect_redesign.html` are completely identical and synchronized.

---

## 🗂️ Removed Lead Priority Section from Enquiries Screen

Removed the **Lead Priority** section (the `LEAD PRIORITY` header, `All Leads 24` button, and the 3 priority cards: `Hot Leads`, `Warm Leads`, `Cold Leads`) from the Enquiries screen (`#screen-enquiry`) as requested:

![Clean Enquiries Screen](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_enquiries_clean.png)

### ✨ Changes Applied
1. **Removed Lead Priority Cards**: Removed the priority cards strip and its header directly below the filter and search toolbar.
2. **Streamlined Pipeline Navigation**: The screen now smoothly transitions from the search & filter bar directly into the **Pipeline Stage** tabs (`All`, `New`, `Contacted`, `Test Drive`, `Negotiation`, etc.) and the lead cards list.
3. **Robust JavaScript State**: Filtering by pipeline stage, search query, and modal filters remains 100% functional without errors.
4. **Exact Parity Maintained**: Both `index.html` and `sales_connect_redesign.html` are completely identical and synchronized.

---

## 🏷️ Cleaned Section Headers (Removed "View All" & "KPIs")

Cleaned up the section headers on the Home Dashboard as requested:
1. Removed the `View All >` CTA button from the **LEADS ASSIGNED** section header.
2. Removed `& KPIs` / `& KPIS` from the Target section header so it reads cleanly as **WEEKLY TARGET** (and adapts to **TODAY'S TARGET** / **MONTHLY TARGET** dynamically).

![Clean Section Headers on Home Screen](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_home_clean_headers.png)

### ✨ Changes Applied
1. **Clean Leads Assigned Header**:
   - Removed the `View All >` button next to `LEADS ASSIGNED`.
   - The total leads card remains fully interactive and clickable (`openEnquiryWithTemperature('all')`).
2. **Simplified Target Section Header**:
   - Changed the static heading from `WEEKLY TARGET & KPIs` to `WEEKLY TARGET`.
   - Updated all dynamic date switch presets (`Today` -> `TODAY'S TARGET`, `This Week` -> `WEEKLY TARGET`, `This Month` -> `MONTHLY TARGET`).
3. **Exact Parity Maintained**: Both `index.html` and `sales_connect_redesign.html` are completely synchronized and identical.

---

## 🎯 Removed Fire Icon from Target Goal Text

Removed the fire emoji (`🔥`) from the **WEEKLY TARGET & KPIs** goal counter on the Home Dashboard as requested:

![Clean Target Goal Text](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_home_no_fire_icon.png)

### ✨ Changes Applied
1. **Clean Professional Typography**: Changed `1 Unit to Goal 🔥` to `1 Unit to Goal` in clean, bold blue (`text-[#007AFF] font-extrabold`).
2. **Preset Synchronization**: Updated the dynamic presets for `Today`, `This Week`, and `This Month` so date filtering continues to display clean text without the fire emoji.
3. **Exact Parity Maintained**: Both `index.html` and `sales_connect_redesign.html` are completely identical and synchronized.

---

## 🧹 Removed FOLLOW-UPS Section from Home Dashboard

Removed the duplicate **FOLLOW-UPS** lead feed section from the bottom of the Home Dashboard as requested:

![Clean Scrolled Home Dashboard](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_home_scrolled_bottom.png)

### ✨ Changes Applied
1. **Removed Redundant Follow-Ups Feed**: Completely removed the bottom `<section>` (`FOLLOW-UPS 6` header, `View All` button, and the list of lead cards), eliminating redundancy with the **Priority Actions Today** section and the dedicated **Activities / Enquiries** screens.
2. **Cleaner, Higher-Focus Home Page**: The Home dashboard now neatly concludes after **PRIORITY ACTIONS TODAY**, focusing the consultant on urgent tasks without cluttering the screen with duplicate lists.
3. **Full Functionality Preserved**: Tapping the **FOLLOW-UPS** KPI card still seamlessly opens the dedicated full-screen Active Follow-ups view (`switchScreen('activities')`).
4. **Exact Parity Maintained**: Both `index.html` and `sales_connect_redesign.html` are completely identical and synchronized.

---

## 🕒 Unified Clock Icons Across KPI Cards

Replaced the arrow trend icons on both **FOLLOW-UPS** and **BOOKINGS** cards with the clean, consistent clock icon matching the **TEST DRIVES** card:

![Unified Clock Icons on Home KPI Cards](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_home_kpi_clock.png)

### ✨ Changes Applied
1. **Replaced Arrow Trend Icons**: Swapped `<i class="fa-solid fa-arrow-trend-up"></i>` with `<i class="fa-regular fa-clock"></i>` on both:
   - **FOLLOW-UPS**: `15` | `<i class="fa-regular fa-clock"></i> +3 new today` (emerald)
   - **BOOKINGS**: `5` | `<i class="fa-regular fa-clock"></i> 1 booked today` (emerald)
2. **Unified Visual Consistency with TEST DRIVES**:
   - **FOLLOW-UPS**: `15` (`🕒 +3 new today`)
   - **TEST DRIVES**: `4` (`🕒 2 scheduled today`)
   - **BOOKINGS**: `5` (`🕒 1 booked today`)
   - **DELIVERIES**: `8` (`2 pending sign-off`)
3. **Synchronized All Date Filter Presets**: Updated dynamic data presets (`Today`, `This Week`, `This Month`) in both files to maintain the clock icon across date filter changes.
4. **Exact Parity Maintained**: Both `index.html` and `sales_connect_redesign.html` are completely identical and synchronized.

---

## ⚡ Streamlined Leads Assigned Card on Home Screen

Cleaned up the **LEADS ASSIGNED** section on the Home Dashboard as requested:

![Streamlined Leads Assigned Card](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_home_leads_cleaned.png)

### ✨ Changes Applied
1. **Removed Hot, Warm, and Cold Cards**: Removed the 3 small cards from inside the card, keeping the home metric card sleek, clean, and focused on total assigned leads (with priority breakdown now properly featured on the Enquiries screen).
2. **Removed "Tap to view >" CTA**: Removed the redundant label and arrow from the right side of the card.
3. **Cleaned Header CTA**: Simplified the section header CTA from `View All (24) >` to `View All >`.

---

## 🔥 Distinct Lead Priority (Hot, Warm, Cold) Hero Stat Cards

Replaced the awkward duplicate stacked filter tab bars with a dedicated, high-impact **Lead Priority Hero Cards Strip** on the Enquiries screen (`#screen-enquiry`), giving Hot, Warm, and Cold leads their own bold, unmistakable visual identity that stands out immediately:

### 📸 Visual Demonstration & Interactive States
````carousel
![Default State - All 24 Leads Visible](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_priority_all.png)
<!-- slide -->
![Hot Leads (8) Active - Glowing Amber Border & Ring](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_priority_hot.png)
<!-- slide -->
![Warm Leads (11) Active - Electric Blue Focus Ring](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_priority_warm.png)
<!-- slide -->
![Cold Leads (5) Active - Cool Slate Focus Ring](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_priority_cold.png)
<!-- slide -->
![Multi-Filter - Hot Leads (8) + Contacted Stage (5) = 2 Matching Leads](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_priority_hot_contacted.png)
````

### ✨ Design Highlights & Functional Improvements
1. **Eliminated Awkward Stacked Duplicate Bars**:
   - Instead of two identical gray segmented pill tracks sitting directly on top of each other, the screen now features two distinct, complementary tiers:
     - **Tier 1 (Lead Priority)**: A visual KPI metric card strip with rich color palettes, large numbers, and signature status icons.
     - **Tier 2 (Pipeline Stage)**: A dedicated horizontal workflow scrubber (`All`, `New`, `Contacted`, `Test Drive`, `Negotiation`...) with its own clear `PIPELINE STAGE` section header.
2. **Signature Priority Themes & Micro-Indicators**:
   - **🔥 Hot Leads (8)**:
     - Warm amber container (`bg-amber-50/70 border-amber-200/90`).
     - Flame icon (`fa-solid fa-fire text-amber-500`).
     - Large bold metric `8` in rich amber-600.
     - Subtitle `● High Urgency` with a pulsing amber indicator.
     - **Active Selection**: Gradient fill, glowing focus ring (`ring-2 ring-amber-400/50 border-amber-500`), elevated shadow, while non-selected cards subtly ease back.
   - **⚡ Warm Leads (11)**:
     - Sky blue container (`bg-blue-50/70 border-blue-200/90`).
     - Lightning bolt icon (`fa-solid fa-bolt text-[#007AFF]`).
     - Large bold metric `11` in brand blue `#007AFF`.
     - Subtitle `● Active Nurture`.
     - **Active Selection**: Elevated gradient fill, glowing blue focus ring (`ring-2 ring-blue-400/50 border-[#007AFF]`).
   - **❄️ Cold Leads (5)**:
     - Cool slate container (`bg-slate-50 border-slate-200/90`).
     - Snowflake icon (`fa-solid fa-snowflake text-slate-500`).
     - Large bold metric `5` in slate-700.
     - Subtitle `● Follow-up`.
     - **Active Selection**: Elevated gradient fill, slate focus ring (`ring-2 ring-slate-400/50 border-slate-600`).
3. **Interactive Toggle & Reset**:
   - **Section Header Toggle**: `All Leads [24]` badge pill in the header allows 1-tap reset to view the entire catalog.
   - **Self-Toggle**: Tapping any currently active card a second time toggles it back off to show `All Leads`.
   - **Live Top Badge**: Screen header badge dynamically synchronizes (e.g. `HOT: 8`, `WARM: 11`, `COLD: 5`, or `HOT: 2` when combining with a stage filter).

---

## 🏷️ Unified Tag Selection Across All Tabs

Standardized all tabs throughout the application to match the user's reference design (`All (24)` styled as an elevated white rounded card with bright brand blue font `#007AFF` nested within a soft neutral track):

### 📸 Visual Demonstration & States
````carousel
![Enquiries Screen - All (24) Tabs Active](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_tabs_enquiry_all.png)
<!-- slide -->
![Enquiries Screen - Hot (8) Temperature Active](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_tabs_enquiry_hot.png)
<!-- slide -->
![Enquiries Screen - Contacted (5) Stage Active](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_tabs_enquiry_contacted.png)
<!-- slide -->
![Enquiry Details Screen - Unified Tabs](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_tabs_details.png)
<!-- slide -->
![Lead Activities Screen - Unified Tabs](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_tabs_lead_activities.png)
````

### ✨ Design System Rules Applied
1. **Container Track**:
   - `bg-slate-100/90 p-1 rounded-2xl border border-slate-200/70 shadow-2xs`
   - Provides a consistent iOS-native segmented track across all tabs.
2. **Active Tab**:
   - `bg-white text-[#007AFF] font-black shadow-2xs rounded-xl`
   - Replaced solid orange/solid blue/colored filled pills with the clean elevated white card and vibrant `#007AFF` blue typography.
3. **Inactive Tabs**:
   - `text-slate-600 hover:text-slate-900 font-bold rounded-xl`
   - Neutral text that contrasts gently with the soft gray track.
4. **Screens & Tab Bars Standardized**:
   - **Enquiries Screen Temperature Tabs**: `All (24)`, `Hot (8)`, `Warm (11)`, `Cold (5)`.
   - **Enquiries Screen Stage Tabs**: `All (24)`, `New (3)`, `Contacted (5)`, `Test Drive (4)`, `Negotiation (4)`, `Booking (3)`, `Delivered (2)`, `Lost (2)`, `Junk (1)`.
   - **Enquiry Details Screen Navigation**: `General`, `Product`, `History`, `+ Activities`.
   - **Lead Activities Screen Tabs**: `Follow Up`, `Comment`, `Brochure`, `New Appointment`, `Auto-comment`.

---

## 📱 Bottom Sheet Slider for Assigned Leads Details (Hot, Warm, Cold Leads)

Implemented a native **Bottom Sheet Slider** that slides up from the bottom of the screen when any of the 3 small cards (`Hot Leads`, `Warm Leads`, `Cold Leads`) or the Total Assigned Leads card is tapped, as requested: *"Open the details in a slider which will come from bottom all the thre small card details"*.

### 📸 Visual Demonstration & States
````carousel
![Clean Home Dashboard with Clickable Cards](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_home_clean.png)
<!-- slide -->
![Hot Leads (8) Bottom Sheet Slider](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_slider_hot.png)
<!-- slide -->
![Warm Leads (11) Bottom Sheet Slider](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_slider_warm.png)
<!-- slide -->
![Cold Leads (5) Bottom Sheet Slider](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_slider_cold.png)
````

### ✨ Key Features Implemented

1. **Native Bottom Sheet Slider (`#assignedLeadsSliderModal`)**:
   - Tapping **HOT LEADS (8)**, **WARM LEADS (11)**, **COLD LEADS (5)**, or the header **TOTAL LEADS ASSIGNED TO YOU (24)** opens a modal that slides up smoothly from the bottom with a dimmed backdrop.
   - **Streamlined Card-Focused Content**: Removed the redundant segmented control tab bar from inside the slider, allowing each card tap to directly showcase its dedicated leads list with maximum vertical readability.
   - **Optimized Padding & Safe Areas**:
     - Generous horizontal padding (`px-5` / 20px) ensuring badges, avatars, and action buttons don't clip at device edges.
     - Centered, unclipped pull handle bar (`mb-0.5`).
     - Proper bottom padding (`pb-6`) and safe spacing for the footer count note and `Open Catalog →` CTA.
   - **Header**:
     - Dynamic title & priority tag (e.g. `🟠 8 Hot Leads (High Priority)`, `🔵 11 Warm Leads (Medium Priority)`, `⚫ 5 Cold Leads (Low Priority)`).
     - Direct CTA link: `View in Leads →` which navigates to the Enquiries screen with the selected temperature pre-filtered.
     - Close `✕` button to dismiss the slider.
   - **Scrollable Lead Cards Feed**:
     - Generously padded lead cards (`p-3 rounded-xl`) with customer avatar circle, initials, and temperature color coding.
     - Customer name, model interest, and stage tag (e.g. `Mohit Kumar`, `Hot Lead`, `Suzuki Brezza ZXi • New Lead`).
     - Instant action buttons: Brand blue **Call** (`fa-phone`) and **WhatsApp** (`fa-whatsapp`) buttons.
     - Tapping any lead card closes the slider and navigates directly to the lead's detailed view.
   - **Bottom Summary Bar**: Displays live count note (e.g. `Showing 8 high priority hot leads`) and an `Open Catalog →` CTA.

2. **Clean & Compact Home Dashboard**:
   - The inline accordion was removed from inside `#homeAssignedMainCard`, keeping the Home screen clean, uncluttered, and fixed height.
   - The 3 small cards (`Hot Leads`, `Warm Leads`, `Cold Leads`) remain compact and responsive.

3. **Enquiries Screen Temperature Segmented Control & Deep Linking**:
   - The dedicated **Temperature Segmented Filter Bar** on `#screen-enquiry` (`All (24) | Hot (8) | Warm (11) | Cold (5)`) remains fully synchronized with all deep links from the slider.

---

## 🚗 Exchange Vehicle Information Form (Sales Enquiry Step 3)

Implemented the **Exchange Vehicle Information** form in the **Sales Enquiry Form** (Step 3: Source Information) matching the user's uploaded design specifications.

### 📸 Visual Comparison & States
````carousel
![First Time Selected (Form Hidden)](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_first_time.png)
<!-- slide -->
![Exchange Selected (Form Revealed)](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_exchange_scrolled.png)
````

### ✨ Key Features Implemented
1. **Interactive Buyer Type Selector (Matching Reference Image 1)**:
   - Designed side-by-side pill cards for **First Time** and **Exchange**:
     - **Selected State**: Outlined blue rounded square with concentric bullseye dot indicator (`#007AFF`) and subtle blue background tint (`bg-blue-50/20 border-[#007AFF]`).
     - **Unselected State**: Clean neutral circular radio indicator (`border-slate-400 bg-white`).
   - Tapping **First Time** hides the exchange form.
   - Tapping **Exchange** immediately reveals the **Exchange Vehicle information** form.

2. **Exchange Vehicle Information Form (Matching Reference Image 2)**:
   - **Header**: `Exchange Vehicle information` in soft slate/gray (`text-slate-500 font-normal`).
   - **Notched / Floating Outlined Labels**:
     - `Manufacturer`: Outlined dropdown with notched label, chevron icon, and manufacturer choices (Maruti Suzuki, Hyundai, Tata Motors, Mahindra, Honda, Toyota, Kia, etc.).
     - `Model`: Outlined dropdown with notched label, dynamically populated based on the chosen manufacturer (e.g. Swift, Dzire, Baleno, Creta, Nexon, etc.).
     - `Variant`: Outlined dropdown with notched label (VXi, ZXi, ZXi Plus, LXi, Delta, Zeta, Alpha, Standard, etc.).
     - `Colour`: Outlined dropdown with notched label (Pearl Arctic White, Metallic Magma Grey, Prime Splendid Silver, Pearl Midnight Black, Phoenix Red, Bluish Black, etc.).
   - **Registration Number Field**:
     - Standard outlined box with interior placeholder `Registration Number*` with uppercase formatting.

3. **Data Integration & Persistence**:
   - Captured exchange information is preserved upon form completion and attached to the newly created enquiry card in the leads catalog.
   - When submitting with an exchange vehicle, the resulting lead card renders an **Exchange** badge indicating vehicle manufacturer, model, and registration.

---

## 🎯 Clean Dashboard Layout (`#screen-home`)
- **Top Section Order**:
  1. Top App Header & Notification Icons
  2. Quick Date Filters (`Today`, `This Week`, `This Month`)
  3. Quick Action Floating Strip (`Enquiries`, `Test Drives`, `Bookings`, `Delivery`)
  4. **LEADS ASSIGNED** Hero Metric Card (Total Assigned + Hot/Warm/Cold breakdown)
  5. **WEEKLY TARGET & KPIs** Performance Progress Card (Donut gauge + 4 KPI Cards Grid)
- **Zero Clutter**: Clean spacing and uncluttered flow without the redundant pipeline banner on the dashboard.

---

## 🔍 Stage-Based Filtering in Enquiries Screen (`#screen-enquiry`)
- **Clean Header (Removed Redundant Active Chips Bar)**:
  - Removed the redundant `ACTIVE: Priority: HOT × Clear all` chips row that previously appeared below the search bar.
  - The temperature segmented tabs (`All | Hot | Warm | Cold`) and stage tabs (`All | New | Contacted...`) already visually show the active selections clearly.
- **Top Segmented Tabs**:
  - Quick stage pill selection (`All`, `New`, `Contacted`, `Test Drive`, `Negotiation`, `Booking`, `Delivered`, `Lost`, `Junk`).
  - Real-time catalog filtering across all sample lead records.
- **Full Sample Catalog**:
  - Sample leads covering all stages with detailed tags, dates, consultant assignments, phone/WhatsApp quick actions, and direct links to the Enquiry Details screen.

---

## 🎨 Redesigned Category Tab Slider (Unified Selection Model)

1. **Unified Active Selection**:
   - Replaced clashing dual styles (pill fill vs outline button vs bottom border lines) with a single, elegant **Segmented Control Slider**.
   - **Active Tab**: Clean white elevated card (`bg-white shadow-xs text-[#007AFF] font-extrabold`) with subtle border.
   - **Inactive Tabs**: Soft slate text (`text-slate-600 font-bold`) with clean active touch states.
   - **Zero Web Hover Effects**: All `hover:` states removed across pills, buttons, cards, and modal options to match native iOS/Android mobile app behavior.

2. **Categorized Icon Labels**:
   - `Follow-Ups (6)`: `<i class="fa-solid fa-list-check"></i>`
   - `Log Activity`: `<i class="fa-solid fa-plus-circle"></i>`
   - `Comments`: `<i class="fa-regular fa-comment-dots"></i>`
   - `Brochures`: `<i class="fa-regular fa-file-pdf"></i>`
   - `Appointments`: `<i class="fa-regular fa-calendar-check"></i>`

3. **Touch-Native Horizontal Track**:
   - Embedded inside a soft neutral track (`bg-slate-100/90 rounded-2xl p-1`) for clean mobile touch interaction.

---

## 📋 Lead Details Activities Flow (`#screen-lead-activities`)

Implemented the full **Activities** flow accessed directly from the **Customer Profile Card** in Enquiry Details (`#screen-enquiry-details` via `+ Activity` button and `Activities` tab):

1. **Header & Navigation**:
   - `<-` Back button returning seamlessly to Enquiry Details.
   - Title **Activities** with dynamic lead reference subhead (`Lead: Gurjant • ENQ00006849`).
   - Clean, horizontal scrollable tab bar with active brand blue indicator (`border-b-2 border-[#007AFF] text-[#007AFF]`).

2. **Tab 1: Follow Up**:
   - Header: `FOLLOW UPS` with `+ Add Follow Up` action.
   - Inline Form: `ADD FOLLOW UP` with date picker (`Followup Date*`), time picker (`Followup Time*`), stage selector, status selector, remarks textarea (`0/100` counter), and `Cancel` / `Save` buttons.
   - Follow-up card matching the uploaded specification:
     - Avatar circle, lead name, formatted date/time.
     - 2x2 grid for **Stage** (e.g. `New`), **Status** (e.g. `Open`), **Followup Date** (`24th Oct 2026`), **Followup Time** (`02:44 PM`).
     - Remarks section with purple chat icon and styled container.

3. **Tab 2: Comment**:
   - Header: `COMMENTS` with `+ Add Comment` action.
   - Inline Form: `ADD COMMENT (ENQ00006849)` with `Comment*` textarea, dynamic `0/100` character counter, and `Cancel` / `Save` buttons.
   - **Pre-populated Comment Cards**:
     - *Comment 1*: Rahul Sharma (Sales Consultant) — Field inquiry for Thar Roxx AX7L Diesel AT, financing plans, and 2018 Swift exchange evaluation.
     - *Comment 2*: Pooja Verma (Team Lead) — Weekend prioritized test drive slot allocation and manager review notes.
   - Dynamic Addition: Seamlessly prepends new user comments to `#leadCommentsList` and increments the total activities counter.

4. **Tab 3: Brochure**:
   - Header: `BROCHURES` with `+ Add Brochure` action.
   - Inline Form: `SHARE BROCHURE` with `Product Id*` selector (Mahindra Thar Roxx, XUV700, Scorpio-N, etc.), `phone`, `email*`, and `Cancel` / `Share` buttons.
   - **Pre-populated Brochure Dispatch Cards**:
     - *Brochure 1*: **Mahindra Thar Roxx Brochure** — Sent to phone `+91 98765 89706` via WhatsApp with `Sent ✓` status and digital catalog details.
     - *Brochure 2*: **Mahindra XUV700 Brochure** — Sent to email `gurjant.singh@gmail.com` via Email with `Sent ✓` status and spec sheet details.
   - Dynamic Dispatch: Pre-pends newly shared brochures with live contact credentials.

5. **Tab 4: New Appointment** (Exact match to reference screenshots):
   - Header: `New Appointments` (left) | `+ Add New Appointment` (right, blue underline link).
   - Inline Form: `NEW APPOINTMENT` with `✕` close button:
     - Single Dropdown selector: `Appointment Type*` with chevron icon.
     - Dropdown options: `Test Drive`, `Home Visit`, `Showroom Visit`.
     - Action buttons: `Cancel` (white button with border) and `Save` (brand blue `#007AFF` button with white text).
   - **Pre-populated Appointment Cards**:
     - *Appointment 1*: **Test Drive** (`Confirmed` badge) — Scheduled for `Tomorrow, 15 Oct` at `11:30 AM` at Dealership Showroom with executive Rahul S.
     - *Appointment 2*: **Showroom Visit** (`Completed` badge) — Scheduled on `12 Oct 2026` at `03:00 PM` for initial consultation and demo.
   - Dynamic Scheduling: Pre-pends newly confirmed appointments and recalculates activity counts.

6. **Dynamic Header Activity Counter (`#leadActTotalBadge`)**:
   - Automatically synchronizes header badge (e.g. `7 Activities`) across Follow-Ups, Comments, Brochures, and Appointments whenever new records are created.

7. **Tab 5: Auto-comment** (System Activity Timeline Feed):
   - Header: `Auto-comments` with system event count pill (`5 System Events`).
   - Chronological audit trail of automated actions and system triggers:
     - **Lead Assigned**: Auto-router assignment to Sales Consultant (`Komalpreet Kaur`) with initial stage set to `New`.
     - **Enquiry Created**: Lead origination via Digital Marketing Campaign (Google Search Ads) with lead ID `ENQ00006849`.
     - **Automated WhatsApp Sent**: Welcome greeting & digital brochure delivered to customer phone (`+91 98765 43210`) with `Delivered ✓✓` status.
     - **Stage Changed**: Automated transition from `New` to `Contacted`.
     - **Brochure Dispatched**: Official specification collateral sent to customer contact channels.

---

## 🎯 Prominent LEADS ASSIGNED Dashboard Metric Card

Added a dedicated **`LEADS ASSIGNED`** hero section directly at the top of the main dashboard feed (`#screen-home`):

1. **Top Dashboard Visibility**:
   - Displays right below Quick Actions so sales consultants instantly see their assigned lead count upon opening the app.
   - Pulsing brand blue indicator dot (`bg-[#007AFF] animate-pulse`) and `View All >` CTA link.

2. **Metrics & Temperature Breakdown Grid**:
   - **Total Assigned Leads**: Large primary metric e.g. `24` with a dynamic highlight badge e.g. `+4 New Today`.
   - **3-Column Lead Breakdown**: Clean, structured breakdown for `Hot Leads` (8), `Warm Leads` (11), and `Cold Leads` (5).

3. **Interactive & Dynamic Date Filtering**:
   - Tapping anywhere on the card opens the full **Enquiries / Leads List** screen (`#screen-enquiry`).
   - Changing the top date filter (`Today`, `This Week`, `This Month`) dynamically updates assigned lead counts, new lead badges, and lead temperature breakdowns.

---

## 📊 4 KPI Grid Cards Unified Flow Structure

All 4 Home Screen KPI cards follow the identical high-fidelity mobile flow structure:

1. **`FOLLOW-UPS` Card (`15, +3 new today`)**:
   - Opens **Follow-Ups Management Screen** (`#screen-activities`).
   - Combined Search Bar + Mobile Bottom Sheet Date Filter Popup (with Custom Date Range Picker).
   - **Section 1: TODAY'S FOLLOW-UPS (Shown FIRST!)** with green pulse animation and `DUE TODAY` badges.
   - **Section 2: UPCOMING & OTHER FOLLOW-UPS (Shown SECOND!)**.

2. **`TEST DRIVES` Card (`4, 2 scheduled today`)**:
   - Opens **Test Drives Management Screen** (`#screen-test-drives`).
   - Combined Search Bar + Mobile Bottom Sheet Date Filter Popup.
   - **Section 1: TODAY'S TEST DRIVE (Shown FIRST!)** (`Amit Roy`, `Neha Gupta`) with `DL Verified ✓` & `Start Drive` CTAs.
   - **Section 2: OTHER TEST DRIVE (Shown SECOND!)** (`Vikram Malhotra`, `Kavita Reddy`).

3. **`BOOKINGS` Card (`5, ₹2.4L revenue`)**:
   - Opens **Vehicle Bookings Screen** (`#screen-booking`).
   - Combined Search Bar + Mobile Bottom Sheet Date Filter Popup + `+ New Booking` CTA.
   - **Section 1: TODAY'S BOOKING (Shown FIRST!)** (`Mike Alex Tyson`, `Aarti Sharma`) with `Confirmed` & `Pre-booked` badges.
   - **Section 2: UPCOMING DELIVERIES & OTHER BOOKINGS (Shown SECOND!)** (`Rohan Verma`, `Pooja Mehta`, `Suresh Patel`).

4. **`DELIVERIES` Card (`8, 2 pending sign-off`)**:
   - Opens **Vehicle Deliveries Screen** (`#screen-deliveries`).
   - Combined Search Bar + Mobile Bottom Sheet Date Filter Popup.
   - **Section 1: TODAY'S DELIVERY (Shown FIRST!)** (`Rajesh Kumar`, `Ananya Deshmukh`) with `PENDING SIGN-OFF ⚠️`, `PDI Ready`, & `Handover` CTAs.
   - **Section 2: UPCOMING & RECENT DELIVERIES (Shown SECOND!)** (`Siddharth Kapoor`, `Meera Sen`).

---

## 🎨 Unified Simple & Clean Design System Across KPI Screens

Eliminated noisy multi-colored UI elements (green, purple, amber, cyan, rose, indigo) across all 4 KPI management screens linked to the dashboard cards (`#screen-activities`, `#screen-test-drives`, `#screen-booking`, `#screen-deliveries`):

1. **Clean Neutral Card Containers**:
   - Standardized all card wrappers to crisp white containers with subtle neutral borders: `bg-white rounded-2xl border border-slate-200/80 shadow-xs`.
   - Removed distracting colored ring outlines and thick status borders (`border-purple-200`, `border-amber-200/90`, `ring-1 ring-amber-100`, `border-emerald-200`).

2. **Unified Brand Blue (`#007AFF`) Section Indicators & Count Badges**:
   - Section pulsing dot indicators updated to brand blue: `bg-[#007AFF] animate-pulse`.
   - Section item count badges standardized to brand blue soft pills: `bg-blue-50 text-[#007AFF] border border-blue-100 font-extrabold`.

3. **Consistent Status Badges & Avatars**:
   - Avatars standardized to brand blue tint: `bg-blue-50 text-[#007AFF] border border-blue-100`.
   - Status badges (`Confirmed`, `Pre-booked`, `Pending Delivery`, `PENDING SIGN-OFF`, `READY HANDOVER`, `PDI IN PROGRESS`, `DELIVERED`) unified to brand blue: `bg-blue-50 text-[#007AFF] border border-blue-100 font-extrabold`.

4. **Brand Blue Primary Action CTAs**:
   - Primary operational buttons (`Start Drive`, `Sign-off`, `Handover`) standardized to solid brand blue: `bg-[#007AFF] text-white rounded-lg text-xs font-bold shadow-xs active:scale-95`.

---

## 🧹 Streamlined Screen Headers (Stage Grid Pills Removed)

- Removed the stage filter pill grid bars (`All`, `Today`, `Upcoming`, `Completed`, etc.) across all screens for a clean, uncluttered layout focused on search, date filtering, and the primary structured feeds.

---

## 📱 2-Row Multi-Column Stage Grid (Exclusive to "View All" Follow-Ups Screen)

1. **Removed from Home Screen**:
   - Cleaned up the Home screen `ACTIVE FOLLOW-UPS` section by removing the 2-row stage filter grid for a streamlined, clutter-free feed.

2. **Exclusive to "View All" Screen (`#screen-activities`)**:
   - The non-scrolling 2-row stage grid (`All (6)`, `Hot (2)`, `Test Drive (2)`, `Warm (1)`, `Follow-up (1)`) is now exclusively displayed on the dedicated **All Active Follow-Ups** screen accessed via **View All**.

3. **Removed Today's Appointment Timeline**:
   - Removed the `TODAY'S APPOINTMENT TIMELINE` section from the Home screen for a cleaner, streamlined layout focused on key funnel metrics.

---

## 👤 Bottom Navigation Bar Update

- Removed **Notification** item from the bottom navigation bar.
- Replaced **More** (`fa-solid fa-ellipsis`) with **Profile** (`fa-regular fa-user`).
- Clean 4-item bottom navigation layout: **Home**, **Enquiry**, **Booking**, and **Profile**.

---

## 📝 Select Enquiry Category Modal, 4-Step Sales Form & Service Enquiry Form

1. **App-Native Category Selection Bottom Sheet Modal (No-Icon Design)**:
   - Tapping `+ Add New Enquiry` opens an iOS/Android native bottom sheet modal (**"Select Enquiry Category"**).
   - **Zero Icons**: Removed all category icons for a clean, typography-focused native app feel.
   - **Action Cards**:
     - **Sales Card**: Title + Subtitle ("Vehicle purchases & new model enquiries") with a clean pill action badge.
     - **Service Card**: Title + Subtitle ("Vehicle maintenance & workshop bookings") with a clean pill action badge.
     - **Other Card**: Title + Subtitle ("General requests & support queries") with a clean pill action badge.
   - Dedicated red **Cancel** CTA button at the bottom.

2. **4-Step Sales Enquiry Form (`#screen-sales-enquiry`)**:
   - Dedicated full-screen step wizard with progress indicator bar (`25%`, `50%`, `75%`, `100%`).
   - **Step 1: 1/4 Personal Information**: `Outlet Id*` dropdown, `Title*` (`Mr`, `Ms`), `First Name*`, `Middle Name`, `Last Name`, `Email`, `Phone*`, `Address*`, and `Remark*` label & field.
   - **Step 2: 2/4 Product Information**: `Category Id*`, `Model*`, `Variant`, `Colour`, `Likely purchase date*` (`24/09/2026`).
   - **Step 3: 3/4 Source Information**: `Source of Enquiry*`, `Sub Source`, `Customer Type*`, `Buyer Type`.
   - **Step 4: 4/4 PII Information**: **Terms & Conditions** consent checkboxes, **OTP Verification** (SMS / WhatsApp), and **Submit** CTA.

3. **Single-Page Service Enquiry Form (`#screen-service-enquiry`)**:
   - Matches the uploaded Service Enquiry specification and design from the reference screens.
   - **Header**: Back button (`<-`), title **Service Enquiry**, and a dedicated `Service` category badge.
   - **Form Fields (`Enquiry Information`)**:
     - `Title*` dropdown (`Mr`, `Ms`, `Mrs`, `Dr`, `Prof`).
     - `First Name*` (Text input, Required).
     - `Middle Name` (Text input, Optional).
     - `Last Name` (Text input, Optional).
     - `Email` (Email input, Optional).
     - `Phone*` (Phone number input e.g. `8679543125`, Required).
     - `Outlet Id*` dropdown (e.g. `Eicher Trucks and Buses - TRR T...`, `Mahindra Flagship Service - North`, etc.).
     - `Category Id*` dropdown (e.g. `bus`, `truck`, `lcv`, `hcv`, `passenger`).
     - `Sub Category Id` dropdown (e.g. `HD BUS07`, `Pro 2000`, `Pro 3000`, `Pro 6000 Series`, `Standard Maintenance`).
     - `Lead Source*` dropdown (e.g. `Website`, `Walk-in`, `Call Center`, `Referral`, `Service Campaign`).
     - `Remark` textarea with live `0/100` character counter.
   - **Action CTA**: Prominent blue rounded `Save` button with validation & success alert.

4. **Single-Page Other Enquiry Form (`#screen-other-enquiry`)**:
   - Matches the uploaded reference screenshot for the **Other** category flow.
   - **Header**: Back button (`<-`), title **Other Enquiry**, and a dedicated purple `Other` category badge.
   - **Form Fields (`Enquiry Information`)**:
     - `Outlet Id*` (Top field, required dropdown selector).
     - `Title*` dropdown (`Mr`, `Ms`, `Mrs`, `Dr`, `Prof`).
     - `First Name*` (Text input, Required).
     - `Middle Name` (Text input, Optional).
     - `Last Name` (Text input, Optional).
     - `Email` (Email input, Optional).
     - `Phone*` (Phone number input, Required).
     - `Lead Source*` dropdown (pre-selected to `Website`).
     - `Remark*` (Mandatory text area field with required `*` and live `0/100` character counter).
   - **Action CTA**: Blue rounded `Save` button with mandatory validation for `Outlet Id*`, `Title*`, `First Name*`, `Phone*`, and `Remark*`.

---

## 📊 Home Screen Target & KPIs Redesign (Light Distinct Accent Theme)

- **Redesigned Target & KPIs Hero Section**: Styled with a distinctive light ice-blue gradient background that makes the sales target stand out as the primary focal point amidst all standard white cards on the dashboard:
  - **Light Distinct Card Container**: Soft ice-blue gradient (`bg-gradient-to-br from-[#F0F6FF] via-[#EBF4FE] to-[#F5F8FF] rounded-3xl p-5 border border-[#BFDBFE] shadow-sm relative overflow-hidden`) with a subtle ambient radial glow (`bg-blue-200/40 blur-xl`).
  - **Header & Pill Badge**: `WEEKLY TARGET & KPIS` with top-right brand blue `75% Achieved` pill badge (`bg-[#EFF6FF] text-[#007AFF] px-3.5 py-1 rounded-full border border-blue-100/90`).
  - **Target Header & Title**: `WEEKLY VEHICLE SALES TARGET` uppercase category label in slate-500 above bold dark slate title `3 of 4 Units Sold` (`text-[#0F172A]`).
  - **Clean Circular Progress SVG Gauge**: Embedded in a white backdrop pill (`bg-white/80 shadow-2xs`) with soft blue SVG track (`stroke-blue-100`), vibrant brand blue gradient arc (`#007AFF` to `#00C6FF`), and brand blue center text (`text-[#007AFF] font-black`).
  - **Brand Blue Progress Bar & Goal Indicator**: High-contrast white track with subtle border (`bg-white/90 border border-blue-100/70`), vibrant brand blue progress fill (`bg-[#007AFF]`), `Target: 4 Units` label, and `1 Unit to Goal 🔥` highlight in brand blue (`text-[#007AFF] font-extrabold`).

![Target Card Standout Visual](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_target_standout.png)

---

## 🚗 Redesigned Vehicle Bookings Flow & Booking Cards

1. **Vehicle Bookings Management Screen (`#screen-booking`)**:
   - **Header & Stats**: Shows total vehicle bookings count badge e.g. `3 Total` (updates dynamically).
   - **Instant Search Bar**: Filter booking cards instantly by customer name, car model, variant, or status.
   - **Redesigned Vehicle Booking Cards**:
     - **Customer Details**: Name (e.g. `Mike Alex Tyson`, `Aarti Sharma`), Phone Number, and Email ID.
     - **Status Badges**: Clean pill badges e.g. `Confirmed` (blue), `Pending Delivery` (amber), `Pre-booked` (indigo).
     - **Car Specifications Card**: Car Model (e.g. `Mahindra Thar Roxx`, `Mahindra XUV700`), Variant (e.g. `AX7 L Diesel AT`), Colour (e.g. `Midnight Black`), and Token Amount Paid (e.g. `₹21,000`).
     - **Delivery & Quick Actions**: Expected delivery date and one-touch **Call** and **WhatsApp** CTAs.
   - **`Pre-booking` Quick Action CTA (Dashboard Home)**: Tapping the green **Pre-booking** card on the main dashboard directly opens the **New Vehicle Booking Form** (`#screen-booking-create`).
   - **`+ New Booking` Floating CTA**: Opens the redesigned single-page booking form from the Bookings list screen.

2. **Single-Page New Vehicle Booking Form (`#screen-booking-create`)**:
   - **Customer Information Section**:
     - `Customer Full Name*` (Mandatory field with error highlight if left blank).
     - `Phone Number*` (Mandatory 10-digit number validation).
     - `Email ID` (Optional field).
   - **Vehicle & Booking Details Section**:
     - `Car Model*` (Dropdown selector: Mahindra Thar Roxx, XUV700, Scorpio-N, Thar 4x4, XUV400 EV, Bolero Neo).
     - `Variant` & `Colour` input fields.
     - `Token Amount (₹)` & `Expected Delivery Date`.
   - **Action CTAs**:
     - **Cancel CTA**: Discards changes and returns to the Bookings list.
     - **Submit Booking CTA**: Validates mandatory fields, creates a new booking card dynamically on `#screen-booking`, alerts success, and updates total count.

3. **Dedicated Booking Details Screen (`#screen-booking-details`)**:
   - **Clickable Booking Cards & Details CTAs**: Tapping any vehicle booking card or its `Details >` CTA button opens the full-screen `#screen-booking-details`.
   - **Header & Navigation**: Displays booking reference ID (e.g. `Ref: BK987875311`), back button returning to Bookings tab, and current status badge.
   - **Customer Information Card**: Displays customer name, phone number, email address, and residential address with one-touch **Call Customer** and **WhatsApp** action buttons.
   - **Vehicle Specifications Card**: Detailed breakdown of Model Name, Variant, Colour, and Ex-Showroom Price.
   - **Payment & Delivery Details Card**: Booking Date, Expected Delivery Date, Payment Mode (e.g. UPI / NetBanking), and Transaction ID.
   - **Interactive 5-Step Booking Status Timeline**:
     - Visual vertical progress tracker with numbered step icons & green completion checkmarks.
     - Tracks steps: `Pre-booking Registered` -> `Token Amount Received` -> `Vehicle Allotment & VIN Tagging` -> `In Transit / Showroom Dispatch` -> `Final Delivery & Key Handover`.
   - **Action CTAs**: Includes `Download Booking Receipt PDF` button with confirmation toast and `Back to Bookings` CTA.

---

## 📞 Brand Blue Icon-Only Action Buttons (Call & WhatsApp)

1. **Icon-Only Layout Across Feeds**:
   - Replaced text-labeled Call and WhatsApp action buttons (`Call`, `WhatsApp`) across Priority cards, Enquiries feed, Follow-ups feed, Test Drives feed, and Bookings feed with clean, icon-only buttons (`<i class="fa-solid fa-phone"></i>`, `<i class="fa-brands fa-whatsapp"></i>`).

2. **Removed from Deliveries Cards**:
   - Completely removed Call and WhatsApp action buttons from all cards on the **Vehicle Deliveries Management Screen** (`#screen-deliveries`), keeping only operational CTAs like `Sign-off` and `Handover`.

3. **Unified Brand Blue Styling**:
   - Both Call and WhatsApp action buttons use consistent brand blue styling (`bg-blue-50 text-[#007AFF] border border-blue-200`) matching all other blue CTAs across the application.

---

## 🎚️ Drag Filter Track for Pipeline Stages (`#screen-enquiry`)

- **Transition to Clean Drag Filter Design**: Replaced the multi-row wrapped chips layout with a streamlined single-line horizontal **Drag Filter** track:
  - **Removed Redundant Header**: Completely eliminated the "↔ DRAG FILTER All (24 Leads)" header text above the track for maximum cleanliness, vertical breathing room, and a pure native app feel.
  - **Single Track Layout**: Clean horizontal drag row (`#enquiryDragFilterTrack`) with hidden scrollbar (`.no-scrollbar`), supporting native mobile touch-pan gestures as well as smooth desktop mouse drag-and-scroll.
  - **Peek & Fade Affordance**: Dual gradient edge fades (`#dragFilterLeftFade` and `#dragFilterRightFade`) that dynamically adjust opacity as the user scrolls, providing a visual cue for additional off-screen stages.
- **Complete 9-Stage Coverage**:
  - `All (24)`, `New (3)`, `Follow-up (5)`, `Test Drive (4)`, `Negotiation (4)`, `Booking (3)`, `Delivered (2)`, `Close Lost (2)`, `Junk (1)`
- **Auto-Centering & Filter Interaction**:
  - Tapping any chip immediately filters the leads list, highlights the active chip in solid brand blue (`#007AFF`), and auto-centers the active chip in the drag view via `chip.scrollIntoView({ behavior: 'smooth', inline: 'center' })`.
  - The top badge right next to "Enquiries" dynamically updates (e.g., `Total: 24` or `Test Drive: 4`).
  - Drag threshold detection prevents accidental filter selection while swiping/dragging.

![Clean Drag Filter Default State](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_drag_filter_clean_default.png)

![Clean Drag Filter Active Test Drive Filter](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_drag_filter_clean_testdrive.png)

---

## 🔘 Unified `View Details >` Solid Blue Button on Booking Cards (`#screen-booking`)

- **Replaced Plain Text Link**: Removed the plain text `Details >` label on booking cards and replaced it with the exact solid brand blue `View Details >` button style used on Lead Cards:
  - Container styling: `px-3.5 py-1.5 bg-[#007AFF] text-white rounded-xl text-xs font-extrabold shadow-xs active:scale-95 flex items-center gap-1 cursor-pointer`.
  - Icon: Chevron right (`<i class="fa-solid fa-chevron-right text-[10px]"></i>`).
- **Complete Visual Consistency**: All 3 static booking cards (`BK987875311`, `BK987875364`, `BK987875399`) and all dynamically generated booking cards now share the exact same high-contrast CTA button as lead cards on the Enquiries screen.

![Booking Cards with Solid Blue View Details Button](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_booking_view_details_button.png)

---

## 🗂️ Updated Stage Filter Section in Filter Bottom Sheet Modal (`#filterModal`)

- **Standardized Section Heading**: Renamed the filter section header from `Stage/ status` to clean `Stage`.
- **Refined Stage Options**: Replaced the previous nested sub-statuses with 5 direct, actionable stage checkboxes:
  - `New`
  - `Follow-up`
  - `Test Drive`
  - `Negotiation`
  - `Close Lost`
- **Section Reset & Filter Application**:
  - Clicking the dedicated `Reset` button in the Stage header clears all checked options in the Stage section.
  - Tapping `Apply` filters the lead cards on `#screen-enquiry` according to the selected stages and syncs the filter chips / badges.

![Updated Stage Filter in Modal](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_stage_filter_modal.png)

---

## 📅 Standardized `Appointment` Tab in Lead Activities (`#screen-lead-activities`)

- **Renamed Tab**: Updated the horizontal activity tab title from `New Appointment` to clean **`Appointment`**, matching the concise noun convention used by peer tabs (`Follow Up`, `Comment`, `Brochure`, `Appointment`, `Auto-comment`).
- **Unified Section Headings & CTAs**:
  - Section title standardized to **`Appointments`**.
  - Action button updated to **`+ Add Appointment`**.
  - Form heading updated to **`APPOINTMENT`**.
  - Empty state updated to `No appointments found.`.

![Appointment Tab in Activities](/Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/screenshot_lead_appointment_active.png)

---

## 🌐 Live Prototype Link

- **Local HTML File**: [sales_connect_redesign.html](file:///Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/sales_connect_redesign.html)
- **Live Local Server**: [http://localhost:9847/sales_connect_redesign.html](http://localhost:9847/sales_connect_redesign.html)


