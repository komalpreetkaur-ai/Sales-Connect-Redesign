# Walkthrough - Sales Connect Mobile Redesign

The **Category Tab Slider** on the **All Active Follow-Ups** screen in [`sales_connect_redesign.html`](file:///Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/sales_connect_redesign.html) has been redesigned into a unified **iOS-Style Segmented Control Slider**.

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

## 🔍 Dedicated Follow-Ups Screen (`FOLLOW-UPS` Card Flow)

1. **Clickable FOLLOW-UPS KPI Card**:
   - Tapping the **FOLLOW-UPS** card (`15, +3 new today`) on the Home screen directly opens the **Follow-Ups Management** screen (`#screen-activities`).

2. **Mobile App Date Filter Popup & Custom Date Range**:
   - **Mobile Bottom Sheet Popup Modal (`#actDateFilterModal`)**: Tapping the date filter button opens a clean mobile app bottom sheet popup modal matching mobile app guidelines with a top drag indicator handle and backdrop blur.
   - **Preset Date Options**: Includes options with real-time lead counts (`All Dates (7)`, `Today (3)`, `This Week (5)`, `This Month (7)`).
   - **Custom Date Range Selector**: Features a **Custom Date Range** action row with icon (`<i class="fa-solid fa-sliders text-[#007AFF]"></i>`). Tapping it smoothly opens the interactive April 2026 Calendar Date Picker Modal (`#dateRangePickerModal`), allowing users to pick custom start and end dates and update the header button label dynamically (e.g. `1/04 - 14/04`).

3. **Structured Feed (Today's Follow-Ups First)**:
   - **Section 1: TODAY'S FOLLOW-UPS (Shown FIRST!)**:
     - Prominently displays today's due leads (`Priya M.`, `Shreya S.`, `Rohan Verma`) with `DUE TODAY` badges & green accent rings.
   - **Section 2: UPCOMING & OTHER FOLLOW-UPS (Shown SECOND!)**:
     - Lists all other upcoming and historical follow-up leads (`Kumari T.`, `Harsh M.`, `Akash S.`, `Rahul K.`).

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

## 📊 Home Screen Target & KPIs Redesign

- **Redesigned Target & KPIs Hero Section**: Updated exclusively to match the provided high-fidelity reference UI.
  - **Header & Pill Badge**: `WEEKLY TARGET & KPIS` with a top-right light blue `75% Achieved` pill badge (`bg-[#EFF6FF] text-[#007AFF] px-3.5 py-1 rounded-full border border-blue-100`).
  - **Dark Hero Card Container**: Sleek dark navy card container (`bg-[#182030] rounded-3xl p-5 text-white shadow-lg`).
  - **Target Header & Title**: `WEEKLY VEHICLE SALES TARGET` subtitle in muted grey text above large white bold title `3 of 4 Units Sold`.
  - **Interactive Circular Progress SVG Gauge**: A custom SVG circular donut gauge with gradient ring fill (`#007AFF` to `#10B981`) and dynamic `75%` text center.
  - **Gradient Progress Bar & Goal Indicator**: High-contrast blue-to-emerald gradient progress bar (`from-[#007AFF] via-cyan-400 to-[#10B981]`), `Target: 4 Units` label on bottom left, and `1 Unit to Goal 🔥` indicator in vibrant emerald green on bottom right.

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

## 🌐 Live Prototype Link

- **Local HTML File**: [sales_connect_redesign.html](file:///Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/sales_connect_redesign.html)
- **Live Local Server**: [http://localhost:9847/sales_connect_redesign.html](http://localhost:9847/sales_connect_redesign.html)


