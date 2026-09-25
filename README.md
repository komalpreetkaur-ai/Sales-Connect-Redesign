# 🚗 Sales Connect - Mobile UI Redesign

A modern, touch-native mobile redesign of the **Sales Connect** automotive sales & service management application. Built with Tailwind CSS, FontAwesome icons, and interactive single-page application (SPA) JavaScript flow.

---

## 🌟 Key Features & Redesigned Workflows

### 1. 📱 Interactive Mobile Navigation & Docked Bar
- **Docked Navigation Bar**: 4 key bottom tabs (**Home**, **Enquiry**, **Booking**, **Profile**).
- **Smooth SPA Transitions**: Zero-page reload navigation across screens.

### 2. 📝 Multi-Category Add Enquiry Flow
- **App-Native Category Sheet**: Icon-free bottom modal to select enquiry category (**Sales**, **Service**, **Other**).
- **Sales Enquiry (4-Step Form Wizard)**:
  - Step 1: Personal Information (`Outlet Id*`, `Title*`, `Name*`, `Phone*`, `Address*`, `Remark`)
  - Step 2: Product Information (`Category*`, `Model*`, `Variant`, `Colour`, `Purchase Date*`)
  - Step 3: Source Information (`Lead Source*`, `Sub Source`, `Customer Type*`, `Buyer Type`)
  - Step 4: Terms Consent & OTP Verification (`SMS` / `WhatsApp`)
- **Service Enquiry (Single-Page Form)**:
  - `Title*`, `First Name*`, `Middle Name`, `Last Name`, `Email`, `Phone*` (`8679543125`), `Outlet Id*` (`Eicher Trucks and Buses`), `Category Id*` (`bus`), `Sub Category Id` (`HD BUS07`), `Lead Source*` (`Website`), and `Remark` with live character counter (`0/100`).
- **Other Enquiry (Single-Page Form)**:
  - `Outlet Id*` (Top required field), `Title*`, `First Name*`, `Middle Name`, `Last Name`, `Email`, `Phone*`, `Lead Source*`, and `Remark*` (Mandatory field with required asterisk and character counter).

### 3. 🚗 Redesigned Vehicle Bookings Management Flow
- **Bookings Dashboard**: Dynamic vehicle booking cards, status indicators (`Confirmed`, `Pending Delivery`, `Pre-booked`), live search filter, and total count badges.
- **New Booking Creation Form**: Single-page creation form with required validation (`Customer Name*`, `Phone Number*`), car details, token amount, expected delivery date, and Cancel/Submit CTAs.
- **Dashboard Integration**: Direct one-tap **Pre-booking** CTA on the main home screen.

### 4. 📊 Funnel Performance & My Pipeline
- **Continuous Multi-Color Funnel Track**: Visual ratio representation across sales pipeline stages.
- **Interactive Stage Cards**: Instant filtering for `Assigned (45)`, `Qualified (30)`, `Test Drive (15)`, `Negotiation (6)`, and `Booking / Won (3)`.

---

## 📂 Repository Structure

```
├── index.html                    # Main entry point for GitHub Pages & web servers
├── sales_connect_redesign.html   # Full mobile app redesign prototype source
├── README.md                     # Project documentation & overview
├── walkthrough.md                # Comprehensive design walkthrough & specifications
├── implementation_plan.md        # Technical implementation & component structure
└── assets/                       # Image assets & screenshot resources
```

---

## 🚀 How to Run Locally

1. **Clone the repository**:
   ```bash
   git clone https://github.com/komalpreetkaur-ai/Sales-Connect-Redesign.git
   cd Sales-Connect-Redesign
   ```

2. **Launch a local server**:
   ```bash
   # Using Python 3
   python3 -m http.server 8000
   ```

3. **Open in Browser**:
   Navigate to `http://localhost:8000` or open `index.html` directly in any web browser.

---

## 📄 License
MIT License - Created for Sales Connect UI/UX Redesign.
