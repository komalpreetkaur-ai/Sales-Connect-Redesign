# OTP Verification Flow & Lead Generation Confirmation

Implement an end-to-end OTP verification modal and subsequent "Lead Generated Successfully" confirmation dialog upon submitting Step 4 (PII Information) of the Sales Enquiry Form.

## Background & Context

In the Sales Enquiry Form (`#screen-sales-enquiry`), Step 4/4 presents Terms & Conditions and OTP Verification channels (SMS / WhatsApp). When the user clicks the **Submit** button (`#salesBtnNext`), the application should not dismiss silently or show a generic browser alert. Instead, it must launch a seamless OTP entry modal where the 4-digit verification code is entered, followed by an official Lead Generated confirmation view detailing the registered lead, reference ID, and clear next-action CTAs ("View in Enquiries" and "Create Another Enquiry").

---

## User Review Required

> [!IMPORTANT]
> - **OTP Auto-fill & Test Helper**: A test chip `Auto-fill Test OTP: 4829` will be included in the modal so testers and users can instantly populate all 4 digit boxes with one tap. Any 4-digit code (e.g., 4829, 1234, 0000) will be accepted for verification.
> - **Lead Reference ID**: Follows the Sales Connect standard format (e.g., `ENQ987875455`), dynamically linked to the newly generated lead.
> - **Feed Prepending**: Verifying the OTP prepends the new lead card directly to the top of `#screen-enquiry` (`#enquiryCardsContainer`), increments the "All" counter (24 -> 25) and "New" counter (3 -> 4), and applies a pulse highlight when navigating to it.

---

## Proposed Changes

 Grouped by layer:

### Sales Enquiry Step 4 & Modals Markup

#### [MODIFY] [index.html](file:///Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/index.html)
#### [MODIFY] [sales_connect_redesign.html](file:///Users/komalpreet/.gemini/antigravity/brain/841d8135-5e2d-494d-8f72-ecf6fb143304/sales_connect_redesign.html)

1. **Step 4 Form Defaults & Integration**:
   - Ensure `checkSms` is checked by default and `checkWhatsapp` is available for selection matching `media_1791962853003.png`.
   - Update `navigateSalesStep(1)` on Step 4 to invoke `openSalesOtpModal()` instead of directly saving.

2. **OTP Verification Modal (`#salesOtpModal`)**:
   - Centered backdrop with glassmorphic blur (`fixed inset-0 bg-slate-900/60 backdrop-blur-xs`).
   - Clean iOS-inspired card (`bg-white rounded-3xl max-w-[360px] p-6 space-y-4 shadow-2xl`).
   - Icon badge: Shield / Key security icon in blue tint.
   - Dynamic recipient phone display (`#salesOtpPhoneDisplay`) and delivery channels (`via SMS & WhatsApp` or `via SMS`).
   - 4 discrete digit inputs (`#salesOtp1`, `#salesOtp2`, `#salesOtp3`, `#salesOtp4`):
     - Auto-advance to next input on digit keystroke.
     - Auto-retreat to previous input on backspace.
     - 4-digit clipboard paste support.
   - One-tap helper chip: `Auto-fill Test OTP: 4829`.
   - 30-second live resend countdown timer with clickable "Resend OTP" button on expiration.
   - Primary Action: `Verify & Submit` button; Secondary Action: `Cancel / Back`.

3. **Lead Generated Confirmation Modal (`#leadSuccessModal`)**:
   - Celebratory emerald checkmark badge icon (`bg-emerald-50 text-emerald-500 border-4 border-emerald-100`).
   - Heading: "Lead Generated Successfully!"
   - Subtitle: "Enquiry has been created and assigned to your sales pipeline."
   - Lead Summary Card:
     - Reference ID: e.g., `ENQ987875455` with "Open Lead" badge.
     - Customer avatar, name, and phone number.
     - Grid specs: Preferred Vehicle / Model, Stage (`New`), Category (`Sales`), Created Timestamp.
     - Conditional Exchange Vehicle badge if an exchange vehicle was entered in Step 3.
   - Action CTAs:
     - `View in Enquiries`: Closes modal, switches screen to `#screen-enquiry`, scrolls to top, and highlights the newly prepended lead card.
     - `Create Another Enquiry`: Closes modal, resets sales enquiry form fields, resets step wizard back to Step 1, and stays on `#screen-sales-enquiry`.

4. **Testing Deep Links**:
   - `?screen=sales-enquiry&step=4&modal=otp` -> Opens Step 4 with OTP Modal active.
   - `?screen=sales-enquiry&step=4&modal=lead_success` -> Opens Step 4 with Lead Success Modal active.

---

## Verification Plan

### Automated / Headless Chrome Verification
1. Run headless Chrome captures with `BypassSandbox: true` (macOS headless Chrome requires unsandboxed execution):
   - `screenshot_sales_otp_modal.png` via `http://localhost:9847/?screen=sales-enquiry&step=4&modal=otp`
   - `screenshot_lead_generated_success.png` via `http://localhost:9847/?screen=sales-enquiry&step=4&modal=lead_success`
2. Test end-to-end interactive flow via headless node/browser script or query verification.
3. Verify 100% parity: `diff -u index.html sales_connect_redesign.html` returns 0.

### Manual Verification
- Navigate from Step 1 through Step 4 of the Sales Enquiry Form.
- Click **Submit** on Step 4 and confirm `#salesOtpModal` appears with customer's phone number.
- Tap **Auto-fill Test OTP: 4829** and click **Verify & Submit**.
- Confirm `#leadSuccessModal` displays the generated reference ID and customer details.
- Tap **View in Enquiries** and verify navigation to `#screen-enquiry` with the new lead card highlighted at the top.
