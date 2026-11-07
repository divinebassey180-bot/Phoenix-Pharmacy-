# PHOENIX PHARMACY — UX ARCHITECTURE SPECIFICATION
**Enterprise SaaS Information Architecture, Interaction Design & Responsive Operational Blueprints**
*Target Users: Nigerian Community Pharmacy Owners, Superintendents, Branch Managers, Inventory Officers & Attendants*

---

## A. NAVIGATION ARCHITECTURE

### 1. Global Navigation Paradigm & Structural Hierarchy

Phoenix Pharmacy utilizes a **dual-tier contextual navigation model** engineered for high-throughput pharmacy environments:
* **Desktop / Large Displays (≥1024px):** Persistent, collapsible primary sidebar on the left (240px expanded, 72px icon-only rail). Contextual branch switcher and user profile remain anchored at top-left and top-right respectively.
* **Tablet Devices (768px – 1023px):** Collapsible sidebar rail (72px) with flyout drawer panels on click, optimizing horizontal workspace for dense inventory tables.
* **Mobile / Android Handhelds (<768px):** Fixed bottom utility bar with the 4 highest-frequency operational actions (`Dispense/FEFO`, `Receive/GRN`, `Expiry`, `Alerts`) plus a top app header housing the Branch Switcher, Quick Barcode Scanner icon, and a hamburger menu for secondary modules.

```
┌────────────────────────────────────────────────────────────────────────────────────────┐
│ TOP HEADER: [Branch Switcher: Ikeja Main Branch ▼]     [Quick Scan 📷] [User: Dr. Bassey (Superintendent) ▼] │
├──────────────┬─────────────────────────────────────────────────────────────────────────┤
│ SIDEBAR      │ MAIN CONTENT WORKSPACE                                                  │
│ • Overview   │                                                                         │
│ • Stock Ctrl │ Breadcrumbs: Inventory > Stock Reconciliation > Cycle Count #1042        │
│ • Expiry     │ ┌─────────────────────────────────────────────────────────────────────┐ │
│ • Reorder    │ │ Module Header: Action Buttons & Secondary Tabs                      │ │
│ • Products   │ ├─────────────────────────────────────────────────────────────────────┤ │
│ • Suppliers  │ │ Filter Bar: Search (debounced), Status, Category, Date               │ │
│ • Reports    │ ├─────────────────────────────────────────────────────────────────────┤ │
│ • Team       │ │ Data Table / Card Grid (Sortable, Batch-Aware, Responsive)           │ │
│ • Settings   │ └─────────────────────────────────────────────────────────────────────┘ │
└──────────────┴─────────────────────────────────────────────────────────────────────────┘
```

---

### 2. Role-Based Access Control (RBAC) Navigation Matrix

| Module / Screen | Pharmacy Owner (MD) | Superintendent Pharmacist | Branch Manager | Inventory Officer | Dispensary Attendant | Platform Admin |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **Overview (Executive Metrics & P&L)** | Full Access | Full Access | Branch Only | Hidden | Hidden | Global System |
| **Stock Control — On-Hand Inventory** | View / Edit | View / Edit | View / Edit | View / Edit | View Only | View Only |
| **Stock Control — Receiving (GRN)** | View / Approve | View / Approve | View / Approve | Full Access | Hidden | View Logs |
| **Stock Control — Transfers & Transit** | Full Access | Full Access | Branch In/Out | Create/Receive | Hidden | View Logs |
| **Stock Control — Reconciliation & Audits** | Final Sign-off | Sign-off & Audit | Create & Count | Blind Count Only | Blind Count Only | Audit Logs |
| **Stock Control — Discrepancy & Shrinkage**| Full Access | Full Access | Branch Only | Log Issue Only | Hidden | View Logs |
| **Expiry Intelligence — Dashboard & Alerts**| Full Access | Full Access | Branch Only | View / Action | View (Pick FEFO) | View Logs |
| **Procurement — Reorder Recommendations** | Full Access | Review / Edit | Recommend Only | Hidden | Hidden | Hidden |
| **Procurement — Purchase Orders (PO)** | Approve & Send | Create / Send | Create Draft | Hidden | Hidden | View Logs |
| **Product Catalogue Master** | Full Access | Full Access (Author)| View Only | View / Edit Shelf | View Only | Schema Config |
| **Supplier Directory & Terms** | Full Access | View / Edit | View Only | View Contacts | Hidden | View Logs |
| **Reports & Statutory Audit Trail** | Full Access | Full Access (PCN) | Branch Reports | Operational Only | Hidden | Security Logs |
| **Team Management & Permissions** | Full Access | Pharmacist & Below | View Branch Team | Hidden | Hidden | Global Tenancy |
| **Settings (PCN License, Outlets, Master)**| Full Access | Premises License | Branch Info | Hidden | Hidden | System Config |

---

## B. SCREEN INVENTORY (MVP SPECIFICATION)

### 1. Module: Overview
* **SCR-001: Operational & Executive Dashboard**
  * *Purpose:* Real-time command center providing daily operational pulse.
  * *Components:* 
    * KPI Stat Strip: Total On-Hand Valuation (₦), Near-Expiry Stock Value at Risk (<60d), Stockout Count (Class A), Active Stock Discrepancies.
    * Quick Action Floating Bar: `Receive Delivery (GRN)`, `FEFO Fast Dispense`, `Log Discrepancy`, `Run Rapid Count`.
    * Critical Alerts Feed: Quarantined expired batches, unconfirmed in-transit transfers (>24h), low-stock chronic essentials.
    * 7-day Sales Velocity vs. Stock Depletion graph.

### 2. Module: Stock Control
* **SCR-002: Live Inventory Ledger**
  * *Purpose:* View, filter, and drill into all active stock across branches down to batch level.
  * *Components:* Dual view toggle (Aggregated SKU View vs. Expanded Batch View); search by brand, generic, or barcode; shelf location badge; status filters (`In Stock`, `Low`, `Out of Stock`, `Quarantined`).
* **SCR-003: Goods Receiving & GRN Management**
  * *Purpose:* Log supplier deliveries, verify against purchase orders, and ingest batch numbers and expiries.
  * *Components:* List of historical GRNs; "New Stock Delivery" multi-step drawer/modal; invoice photo upload preview; PO line matching table.
* **SCR-004: Stock Transfers & Transit Escrow**
  * *Purpose:* Move stock between central bulk store and dispensary, or between branches.
  * *Components:* Active Transfers table with status badges (`Pending Dispatch`, `In-Transit`, `Discrepancy Detected`, `Received`); "Initiate Transfer" modal with FEFO batch selection guidance.
* **SCR-005: Physical Stock Count & Reconciliation**
  * *Purpose:* Conduct periodic wall-to-wall or category cycle counts.
  * *Components:* Active Audit Sessions list; "Start New Count" setup screen; "Blind Count Entry Sheet" (quantities hidden from counters); "Variance & Discrepancy Review" screen with auto-calculated ₦ discrepancy.
* **SCR-006: Stock Adjustments & Damage Write-Offs**
  * *Purpose:* Record breakages, clinic use, theft, or approved destruction.
  * *Components:* Adjustment history table with reason codes; "New Adjustment" form with image attachment and multi-tier approval indicator.

### 3. Module: Expiry Intelligence
* **SCR-007: Expiry Horizons Dashboard**
  * *Purpose:* Proactive visual command center to prevent expiry losses.
  * *Components:* 
    * 4 Tabbed Horizon Buckets: `Critical (<30 Days / Expired)`, `High Risk (31–90 Days)`, `Watchlist (91–180 Days)`, `Safe (>180 Days)`.
    * Summary banner: "₦X,XXX,XXX at Risk Across Y Batches".
    * Batch Action Drawer: One-click actions to `Mark for Liquidation / Discount`, `Initiate Return to Supplier`, `Quarantine for Disposal`.
* **SCR-008: Quarantined & Destruction Log**
  * *Purpose:* Maintain regulatory records of expired/quarantined medicines isolated from active inventory.
  * *Components:* Quarantined stock list, printable NAFDAC/PCN Destruction Certificate generator, hazardous waste agency pickup receipt logger.

### 4. Module: Procurement Intelligence
* **SCR-009: Reorder Recommendation Hub**
  * *Purpose:* Automated replenishment suggestions based on sales velocity, lead times, and stock levels.
  * *Components:* Supplier-grouped recommendation cards; one-click `Add to PO`; pack-size rounding indicators; run-out date estimates ("Stock will deplete in 4 days").
* **SCR-010: Purchase Order (PO) Management**
  * *Purpose:* Create, edit, approve, and dispatch purchase orders.
  * *Components:* PO list (Draft, Approved, Dispatched, Partially Received, Fulfilled); PO detail sheet; "Export to WhatsApp" formatting preview; Download PDF Purchase Order.

### 5. Module: Products
* **SCR-011: Product Catalogue Master**
  * *Purpose:* Central repository of all pharmaceutical and retail SKUs.
  * *Components:* Product list table with clinical filters (POM, OTC, Controlled, Cold Chain); CSV bulk import modal with interactive data mapper; "New Product Registration" slide-over drawer.
* **SCR-012: Product Detail & Movement History**
  * *Purpose:* 360-degree forensic view of a specific SKU.
  * *Components:* SKU metadata card, active batches breakdown table, 90-day movement ledger (every GRN, dispense, transfer, and adjustment), ABC/VEN classification tags.

### 6. Module: Suppliers
* **SCR-013: Supplier Directory & Scorecards**
  * *Purpose:* Manage wholesale distributor profiles, credit agreements, and performance.
  * *Components:* Supplier cards/table, lead-time tracking, credit terms countdown, supplier-specific purchase history.
* **SCR-014: Supplier Detail & Catalog Pricing**
  * *Purpose:* Individual distributor view with payment terms and historical price changes.

### 7. Module: Reports
* **SCR-015: Inventory & Compliance Reports**
  * *Purpose:* Regulatory and operational reporting.
  * *Components:* PCN Statutory Inspection Report Generator, Dangerous Drugs / Controlled Substances Ledger, Stock Discrepancy & Shrinkage Breakdown, Monthly Capital Waste (Expiries & Damages) Report.
* **SCR-016: Immutable Audit Trail**
  * *Purpose:* Forensic search of all user actions across the platform.
  * *Components:* Filterable event feed (User, Action Type, SKU, Timestamp, IP Address, Reason Code).

### 8. Module: Team and Permissions
* **SCR-017: User Management & Roles**
  * *Purpose:* Invite staff, assign granular operational roles, toggle branch access.
  * *Components:* Staff table, "Invite New Team Member" modal, role assignment selector, one-click deactivation switch.

### 9. Module: Settings
* **SCR-018: Organization & Branch Settings**
  * *Purpose:* Manage business entity details and physical retail outlets.
  * *Components:* Pharmacy Name, PCN Premises License Number, Head Office Address, Branch List with outlet creation modal, Tax/VAT rules.

---

## C. CRITICAL WORKFLOWS

---

### Workflow 1: Create a Pharmacy Organisation
* **Starting Point:** Platform onboarding landing page (`/register-org`) following invitation or platform signup.
* **Actor:** Pharmacy Owner (Managing Director).
* **Step-by-Step Flow:**
  1. User enters business entity details and primary contact information.
  2. User enters statutory PCN Superintendent Pharmacist details and license number.
  3. User sets operating currency (default: NGN ₦) and financial year start date.
  4. System validates inputs and generates the root tenant account.
* **Required Fields:** Organization Legal Name, Trading Name, Head Office Physical Address, State, Primary Contact Phone, Contact Email, PCN Premises Certificate Number.
* **Validations:** Unique business name; valid Nigerian phone format (`+234...` or `080...`); valid email format; valid PCN license structure.
* **Permissions:** Platform Superadmin / Organization Owner.
* **Success State:** Organization created; user redirected to "Add Your First Branch" setup screen.
* **Failure States:** Duplicate email/license error modal; network timeout with "Save Draft & Retry" local storage fallback.

---

### Workflow 2: Add a Branch
* **Starting Point:** Settings > Branches (`/settings/branches`) > Click `+ Add New Branch`.
* **Actor:** Pharmacy Owner, Platform Admin.
* **Step-by-Step Flow:**
  1. User clicks `+ Add Branch` button opening a slide-over panel.
  2. Enters branch nickname, physical address, state, and branch-specific PCN premises license.
  3. Designates a Superintendent or Branch Pharmacist in Charge from existing staff or enters an email invite.
  4. Selects default storage zones for this branch (e.g., Dispensary Shelf, Bulk Store, Cold Fridge).
  5. Clicks `Create Branch`.
* **Required Fields:** Branch Name, Physical Address, City/Town, State, Branch Phone, PCN Premises License Number.
* **Validations:** Branch name unique within organization; PCN license number format check.
* **Permissions:** Pharmacy Owner only.
* **Success State:** New branch appears in Branch Switcher dropdown; initial default storage locations initialized.
* **Failure States:** Subscription branch limit reached (displays upgrade modal); duplicate license error.

---

### Workflow 3: Register a Product
* **Starting Point:** Products (`/products`) > Click `+ Register Product`.
* **Actor:** Superintendent Pharmacist, Inventory Manager.
* **Step-by-Step Flow:**
  1. User clicks `+ Register Product` opening the Product Registration Drawer.
  2. User types Brand Name or Generic Name (system provides live autocomplete against the pre-loaded Nigerian Master Drug Index of 3,000 standard drugs).
  3. If matched, clinical dosage, form, and standard strength are auto-filled. If custom, user enters Strength, Form, and Pack Size.
  4. User enters NAFDAC Reg Number, Barcode (via USB scanner or manual entry), and Category (POM, OTC, Controlled).
  5. Sets storage temperature requirement (Ambient vs. Cold Chain 2–8°C) and Default Minimum Reorder Point.
  6. Clicks `Save Product`.
* **Required Fields:** Brand Name, Generic/INN Name, Strength, Dosage Form, Pack Size / Unit of Measurement, Clinical Category.
* **Validations:** Duplicate prevention: checks if identical (Generic + Strength + Form + Pack Size + Brand) exists; NAFDAC number format validation (e.g., `04-XXXX` or `A4-XXXX`).
* **Permissions:** Superintendent Pharmacist, Inventory Officer.
* **Success State:** Product card appears at top of catalogue; toast notification: *"Product registered successfully. Ready for stock receiving."*
* **Failure States:** Duplicate product detected: displays matching product card with option to edit existing SKU instead of creating duplicate.

---

### Workflow 4: Receive a New Stock Delivery (GRN Ingestion)
* **Starting Point:** Stock Control > Receiving (`/stock-control/receiving`) > Click `+ New Stock Delivery`.
* **Actor:** Store Keeper, Dispensary Pharmacist.
* **Step-by-Step Flow:**
  1. User selects Supplier and enters Supplier Invoice Number and Delivery Date.
  2. Optional: Selects pre-existing Purchase Order to auto-populate expected line items.
  3. Optional: Uploads/snaps a clear photo of physical paper invoice for audit records.
  4. Adds line items: searches product, inputs Delivered Quantity, Bonus Quantity, Batch Number, Expiry Date, and Landed Unit Cost Price (₦).
  5. System validates expiry date (>6 months default).
  6. User clicks `Finalize & Ingest Stock`.
  7. System displays confirmation summary with total invoice value; user confirms.
* **Required Fields:** Supplier ID, Invoice Number, Delivery Date, Receiving Branch, SKU, Quantity Received, Batch Number, Expiry Date, Unit Cost Price.
* **Validations:** Batch number cannot be blank; expiry date cannot be in the past or within 180 days (unless Superintendent override code entered); cost price > 0.
* **Permissions:** Store Keeper, Branch Manager, Superintendent Pharmacist.
* **Success State:** GRN locked with unique ID (e.g., `GRN-2026-0842`); on-hand inventory updated immediately; WAC cost recalculated; audit log written.
* **Failure States:** Short-dated batch detected: blocks save and displays *"Batch expires in <180 days. Requires Superintendent approval to ingest."*

---

### Workflow 5: Record Batch Numbers and Expiry Dates
* **Starting Point:** Contextual within Receiving (Workflow 4) or Stock Adjustments (Workflow 6).
* **Actor:** Store Keeper, Dispensary Pharmacist.
* **Step-by-Step Flow:**
  1. On line-item entry, focus shifts to `Batch Number` field.
  2. User inputs alphanumeric batch string (e.g., `B7049X`) or scans 2D GS1 DataMatrix code on the pack box.
  3. Focus shifts to `Expiry Date` field.
  4. User inputs MM/YYYY via masked input or date picker.
  5. System calculates remaining days and displays instant color indicator:
     * *Green:* >180 days.
     * *Amber:* 90–180 days.
     * *Red:* <90 days (blocks entry unless authorized).
* **Required Fields:** Batch Number String (max 40 chars), Expiry Month, Expiry Year.
* **Validations:** Regex check for alphanumeric characters; month between 01–12; year ≥ current calendar year.
* **Permissions:** Store Keeper, Pharmacist.
* **Success State:** Batch badge rendered inline next to product; batch ID tied to inventory transaction ledger.
* **Failure States:** Past date entered: input highlighted in red with error *"Cannot enter an expired batch into active inventory."*

---

### Workflow 6: Adjust Inventory After Physical Counting (Cycle Count)
* **Starting Point:** Stock Control > Reconciliation (`/stock-control/reconciliation`) > Select Completed Count Session > `Review Variances`.
* **Actor:** Superintendent Pharmacist, Managing Director.
* **Step-by-Step Flow:**
  1. User reviews the Variance Report generated from physical count entries.
  2. Items with zero variance are automatically flagged as `Verified`.
  3. For items with discrepancies, user reviews: System Quantity, Counted Quantity, Discrepancy Units, and Discrepancy Value (₦).
  4. For variances > ₦5,000, user inputs an investigation note or assigns a re-count task.
  5. User selects adjustment reason: `Shrinkage/Unexplained Deficit`, `Unrecorded Breakage`, or `Found Stock`.
  6. User clicks `Authorize & Apply Adjustments`.
* **Required Fields:** Count Session ID, Justification Reason Code per discrepancy, Sign-off Password/PIN.
* **Validations:** Total absolute discrepancy calculated; if net negative variance > ₦25,000, requires Managing Director approval.
* **Permissions:** Superintendent Pharmacist, Pharmacy Owner.
* **Success State:** Stock ledger adjusted to match physical shelf count; adjustment voucher created; PCN audit trail recorded.
* **Failure States:** Unauthorized attempt to commit variance without reason code: blocks commit and highlights missing reason fields.

---

### Workflow 7: Investigate a Stock Discrepancy
* **Starting Point:** Stock Control > Discrepancies (`/stock-control/discrepancies`) or from the Overview alert banner.
* **Actor:** Superintendent Pharmacist, Store Manager.
* **Step-by-Step Flow:**
  1. User clicks on a flagged SKU with an active discrepancy (e.g., "Artemether-Lumefantrine 80/480mg — Discrepancy: -6 packs").
  2. System opens the **Forensic Investigation Drawer**.
  3. Shows chronological 30-day timeline: Last verified count, all inbound GRNs, all dispensings, all transfers, and recorded breakages.
  4. Displays staff members who handled the item and FEFO override logs.
  5. User marks investigation finding: `Confirmed Pilferage`, `Misplaced to Other Shelf`, `Unrecorded Dispensing`, or `Data Entry Error`.
  6. Submits investigation report; if stock found on another shelf, user clicks `Re-allocate Shelf` to close discrepancy.
* **Required Fields:** Discrepancy ID, Finding Category, Action Taken, Investigator Notes.
* **Validations:** Finding category mandatory before case closure.
* **Permissions:** Superintendent Pharmacist, Branch Manager.
* **Success State:** Discrepancy status updated to `Resolved`; corrective journal posted if necessary; report archived in audit files.
* **Failure States:** Incomplete documentation blocks resolution.

---

### Workflow 8: Identify and Action Near-Expiry Products
* **Starting Point:** Expiry Intelligence (`/expiry`) or Mobile Bottom Bar > `Expiry`.
* **Actor:** Dispensary Pharmacist, Store Manager.
* **Step-by-Step Flow:**
  1. User opens Expiry Intelligence and filters by `Critical (<30d)` or `High Risk (31–90d)`.
  2. Table lists all at-risk batches with current stock, daily sales velocity, and projected run-out date.
  3. System highlights batches where `Projected Depletion Date > Expiry Date` ("Will Not Clear in Time").
  4. User checks checkboxes on 3 batches and clicks `Batch Action`:
     * Option A: `Discount / Clearance List` (flags item for active promotional dispensing).
     * Option B: `Initiate Transfer` (moves batch to a high-volume branch where it can clear before expiry).
     * Option C: `Return to Supplier` (generates supplier return debit note if credit agreement exists).
     * Option D: `Quarantine for Disposal` (for expired stock).
  5. Confirms action.
* **Required Fields:** Batch IDs, Action Selection, Destination/Discount value.
* **Validations:** Cannot initiate transfer to a branch where the same SKU is already overstocked.
* **Permissions:** Pharmacist, Store Manager.
* **Success State:** Items re-badged with selected action status; notifications dispatched to dispensary counter screens.
* **Failure States:** Action blocked if batch has a pending unconfirmed transfer.

---

### Workflow 9: Record Stock Movements (FEFO Counter Dispensing)
* **Starting Point:** Overview > `FEFO Fast Dispense` or Mobile Bottom Bar > `Dispense`.
* **Actor:** Dispensary Pharmacist, Sales Attendant.
* **Step-by-Step Flow:**
  1. User scans barcode on product pack or searches by brand/generic name.
  2. System immediately displays product card with the **FEFO Recommended Batch**:
     * Highlights Batch Number, Expiry Date (days remaining), and exact Drawer/Shelf coordinate.
  3. User enters quantity to dispense.
  4. If user physically picks the recommended batch: clicks `Confirm Dispense` (or presses `Enter` / scans pack barcode) — 1 click completion.
  5. If user overrides and selects a newer batch: system triggers the **Override Reason Modal**:
     * User selects reason: `Damaged packaging on older batch`, `Patient travel/bulk request`, `Batch not located on shelf`.
     * Overrides are logged.
  6. Stock decrements immediately from on-hand batch balance.
* **Required Fields:** SKU, Batch ID, Quantity Dispensed.
* **Validations:** Quantity cannot exceed total on-hand batch stock; override requires mandatory reason selection.
* **Permissions:** Dispensary Attendant, Pharmacist, Store Keeper.
* **Success State:** Instant visual toast: *"Dispensed [Qty] of [Product] (Batch [X])"*; on-screen counter updates in <100ms.
* **Failure States:** Out of stock attempt: blocks dispensing with modal *"Insufficient stock in this batch."*

---

### Workflow 10: Generate and Review a Reorder Recommendation
* **Starting Point:** Procurement Intelligence > Reorders (`/procurement/reorders`).
* **Actor:** Purchasing Pharmacist, Managing Director.
* **Step-by-Step Flow:**
  1. User navigates to Reorder Hub; system has automatically grouped low-stock items by their Primary Supplier.
  2. User selects a supplier card (e.g., "Chi Pharmaceuticals — 8 Items Recommended").
  3. System displays line items showing: Current Stock, 30-day Consumption Velocity, Lead Time, Recommended Reorder Quantity (rounded to whole pack sizes), and Estimated Line Cost.
  4. User can inline-edit quantities, remove items, or add additional ad-hoc items.
  5. Checks "Total PO Estimated Cost" against available working capital budget.
  6. Clicks `Generate Purchase Order`.
  7. Modal provides two dispatch channels: `Download PDF PO` and `Export to WhatsApp Message` (formats order text cleanly for sales reps).
* **Required Fields:** Supplier ID, Approved Line Items, Pack Quantities.
* **Validations:** Order quantities must be positive integers in multiples of pack sizes; alerts if near-expiry stock already exists for an item.
* **Permissions:** Purchasing Pharmacist, Managing Director.
* **Success State:** Formal Purchase Order created with status `Dispatched`; expected inbound shipment registered for the Receiving module.
* **Failure States:** Attempt to order without a designated supplier: prompts user to assign a supplier first.

---

## D. INTERACTION STANDARDS

### 1. Search and Filtering
* **Debounced Execution:** All search inputs debounced to **300ms** to preserve network and rendering performance.
* **Multi-Parameter Search:** Single unified search box accepts: Brand Name, Generic/INN Name, Manufacturer Batch Number, or NAFDAC Registration Number.
* **Filter Persistence:** Active filters (Status, Branch, Category, Expiry Horizon) persist in URL query parameters (`?status=low_stock&horizon=critical`), enabling bookmarking, browser back-button integrity, and direct link sharing among team members.
* **Reset Trigger:** Visible `Clear All Filters` pill appears whenever any filter is active.

### 2. Table Behaviour & Data Density
* **Sticky Column Headers:** Table headers remain pinned at top of viewport during vertical scrolling.
* **Horizontal Scrolling with Locked Identity:** On dense tables (e.g., Live Inventory Ledger), the first column (`Product Name / SKU`) remains frozen horizontally while operational data columns scroll smoothly.
* **Visual Status Indicators:** No raw numeric codes; every state has a high-contrast badge:
  * *Critical/Expired/Out of Stock:* Coral Red (`#E05252`)
  * *High Risk/Near Expiry/Low Stock:* Amber Gold (`#E0A832`)
  * *Optimal/In Stock:* Emerald Green (`#4CAF82`)
  * *Overstocked/Informational:* Soft Blue (`#4A90E2`)
* **Row Click Behaviour:** Clicking a row opens a non-disruptive slide-over drawer (Desktop/Tablet) or full-screen card (Mobile) without leaving the table view.

### 3. Pagination & Scroll Performance
* **Hybrid Virtualized Pagination:** Default page size of 25 rows with a quick selector (`25`, `50`, `100`, `All`).
* **Summary Text:** Clear footer counter: *"Showing 1–25 of 3,420 items"*.
* **Keyboard Navigation:** `← Previous` and `Next →` buttons accessible via standard arrow shortcuts.

### 4. Form Validation & Clinical Safety
* **Inline Real-Time Feedback:** Fields validate on blur with clear, non-cryptic error copy positioned directly underneath the offending input (never generic toast errors).
* **Currency Formatting:** All financial inputs automatically format with Nigerian Naira thousand-separators (`₦ 14,500.00`) to prevent trailing zero entry errors.
* **Destructive Action Protections:** Deletions, write-offs, and reconciliations require explicit confirmation modals with clear financial consequences summarized in bold.

### 5. Notifications & User Feedback
* **Toast Hierarchy:**
  * *Success:* Auto-dismisses in 3.5 seconds; subtle bottom-right position.
  * *Warning (e.g., Short-dated batch detected):* Persistent with explicit `Acknowledge` button.
  * *Critical Error (e.g., Negative stock block):* Center-anchored modal with sound/vibration cue on mobile.

### 6. Empty States & First-Time Guidance
* **Actionable Empty States:** Every empty state features a clean illustration, an explanation of why the screen is empty, and a primary call-to-action button (e.g., *"No purchase orders found. Create your first supplier order to automate receiving."*).

### 7. Offline & Low-Bandwidth Resilience
* **Network Status Banner:** Sticky persistent banner at the top of the interface if connectivity drops:
  * *"Offline Mode: Working from local cache. Counter lookups and dispensing queue active. Syncing will resume automatically when connected."*
* **Optimistic Local Mutations:** Dispensing and stock checks update locally in IndexedDB cache immediately, preventing counter holdups during network dips, and sync to server upon reconnection.

---

## E. MOBILE-FIRST RESPONSIVE ARCHITECTURE (ANDROID OPTIMIZED)

In Nigerian community pharmacies, floor staff and locum pharmacists frequently operate using inexpensive Android smartphones (e.g., Tecno, Infinix, Samsung A-series) and 8-inch tablets at the counter rather than full desktop workstations.

```
┌────────────────────────────────────────────────────────────────────────────────────────┐
│                        VIEWPORT RESPONSIVENESS COMPARISON MATRIX                       │
├─────────────────────┬──────────────────────────┬───────────────────────────────────────┤
│ Operational Feature │ Android Phone (<768px)   │ Tablet (768px–1023px) │ Desktop (≥1024px)     │
├─────────────────────┼──────────────────────────┼───────────────────────┼───────────────────────┤
│ Main Navigation     │ Fixed 4-icon Bottom Bar  │ 72px Icon Sidebar     │ 240px Full Sidebar    │
│ Barcode Scanning    │ Direct Device Camera OCR │ Camera or USB Scanner │ USB / Bluetooth Wand  │
│ Tables / Lists      │ Touch-Friendly Card List │ Dense Scrolling Table │ Multi-Column Table    │
│ Action Dialogs      │ Bottom Sheet Modal       │ Centered Modal Window │ Slide-over Side Panel │
│ Physical Stock Count│ Stepper Card by Shelf    │ Split Screen (2 Racks)│ Grid Data Entry       │
└─────────────────────┴──────────────────────────┴───────────────────────┴───────────────────────┘
```

### Detailed Responsive Adaptation of Major Workflows

#### 1. Stock Receiving (Workflow 4)
* **Desktop:** Wide split-screen view: Left side displays PDF/image of supplier invoice; right side displays interactive line-item entry grid with full keyboard tab navigation.
* **Tablet:** Full-width editable data table; tapping a line opens an inline batch/expiry popover.
* **Android Phone:** Step-by-step card workflow. Phone camera takes photo of paper invoice; line items are added one by one via a bottom-sheet drawer with large numeric keypad buttons for quantity and cost.

#### 2. FEFO Counter Dispensing (Workflow 9)
* **Desktop:** Search bar with instant keyboard shortcuts (`Ctrl+K`); recommended batch highlighted in green table row; `Enter` key confirms dispense.
* **Tablet:** Side-by-side view: Product search list on left; active cart and FEFO drawer coordinates on right.
* **Android Phone:** Full-screen high-contrast touch interface. Large "Scan Barcode" button at top. When product is scanned or selected, a prominent green card displays:
  * *"Pick Batch: [B409] | Drawer: [D-2] | Exp: Nov 2026"*
  * Single giant `Confirm Pick` button spanning the bottom thumb zone.

#### 3. Physical Stock Audit & Cycle Counting (Workflow 6)
* **Desktop:** Multi-column spreadsheet-like entry grid with batch filtering and bulk CSV variance import.
* **Tablet:** Rack-by-rack checklist view with tactile `+` and `-` quantity steppers.
* **Android Phone:** Dedicated "Walk-the-Aisle" count mode. Counter displays one shelf rack at a time; user scans product or searches name, enters physical count on large numeric pad, and hits `Next Product` without ever seeing expected quantities.

---

## F. TESTABLE ACCEPTANCE CRITERIA FOR CRITICAL WORKFLOWS

| Workflow | Unique ID | Testable Acceptance Criteria |
| :--- | :--- | :--- |
| **Org Creation** | `AC-ORG-01` | Given valid business data and a unique PCN license, when submitted, organization is initialized and owner lands on branch setup within 1.5 seconds. |
| **Org Creation** | `AC-ORG-02` | Given an already-registered email or duplicate PCN number, system displays specific field-level inline error without clearing other input fields. |
| **Add Branch** | `AC-BRN-01` | Given an active organization, when a new branch is created with valid address and license, it immediately appears in the global Branch Switcher dropdown. |
| **Product Reg** | `AC-PRD-01` | Given a generic name query, autocomplete suggestions from the 3,000-drug master directory populate within 200ms. |
| **Product Reg** | `AC-PRD-02` | Attempting to register an exact duplicate (Brand + Generic + Strength + Form + Pack Size) is blocked with an alert linking directly to the existing product record. |
| **Receiving** | `AC-RCV-01` | Entering a batch with an expiry date <180 days triggers a blocking modal requiring an authorized Superintendent override code to proceed. |
| **Receiving** | `AC-RCV-02` | Finalizing a GRN instantly increments on-hand batch balances and recalculates the Weighted Average Cost (WAC) across all active inventory views. |
| **Batch Expiry** | `AC-EXP-01` | Daily cron at 00:01 WAT accurately transitions batches from Safe to Watchlist (180d), High Risk (90d), Critical (30d), and Quarantined (0d). |
| **Batch Expiry** | `AC-EXP-02` | Any batch reaching 0 days to expiry is automatically locked from the dispensing selection list and moved to the Quarantined tab. |
| **Stock Count** | `AC-REC-01` | In Blind Count mode, expected system stock quantities and financial valuations are completely absent from DOM elements accessible to counting staff. |
| **Stock Count** | `AC-REC-02` | Applying reconciliation adjustments creates an irreversible audit voucher and updates on-hand balances to equal physical count. |
| **FEFO Dispense**| `AC-DIS-01` | System unconditionally presents the earliest-expiring active batch as the default pick recommendation. |
| **FEFO Dispense**| `AC-DIS-02` | Selecting a newer batch when an older valid batch exists forces an override modal requiring one of the three statutory reason codes before stock decrement. |
| **Reorder Hub** | `AC-RRD-01` | Suggested reorder quantities are automatically rounded up to the nearest whole pack size integer based on catalog packaging rules. |
| **Reorder Hub** | `AC-RRD-02` | Clicking "Export to WhatsApp" generates a clean, plain-text purchase order with product names, strengths, pack counts, and supplier account notes formatted for instant mobile sharing. |
| **Audit Trail** | `AC-AUD-01` | Every inventory write, adjustment, receipt, and FEFO override creates an immutable database record containing User ID, Timestamp, Event Type, and IP Address. |
