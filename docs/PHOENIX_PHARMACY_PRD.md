# PHOENIX PHARMACY — PRODUCT REQUIREMENTS DOCUMENT (PRD)
**Pharmacy Operations and Inventory Intelligence SaaS Platform**
*Target Market: Nigerian Community Pharmacies & Regional Multi-Branch Retailers*

---

## SECTION A: PROBLEM VALIDATION

### 1. Deep Dive: The Three Core Operational Problems in Nigerian Community Pharmacy

#### Problem 1: Inaccurate Inventory Records, Stock Discrepancies, and Poor Movement Accountability
* **Operational Reality:** Community pharmacies in Nigerian urban centers (e.g., Lagos, Abuja, Port Harcourt, Ibadan, Kano) manage between 2,000 and 10,000 active SKUs across prescription drugs (POM), pharmacy-only medicines (P), over-the-counter (OTC) items, and fast-moving consumer goods (FMCG). Most operate on fragmented desktop POS systems or manual paper ledgers. Stock counts on shelves frequently do not match ledger records. Sales attendants and interns regularly dispense without immediate logging, borrow units between dispensaries and over-the-counter counters without transfer slips, or fail to record damaged packs.
* **People Affected:**
  * **Superintendent Pharmacists:** Bear statutory liability under the Pharmacy Council of Nigeria (PCN) Act 2022 for unauthorized stock movements, unrecorded controlled substances (e.g., codeine syrups, benzodiazepines, opioids), and unaccounted stock variations.
  * **Pharmacy Owners / Managing Directors:** Suffer direct margin erosion and lack visibility into whether revenue drops are caused by low footfall or systemic shrinkage.
  * **Inventory Managers / Store Keepers:** Spend 15–25 hours per month performing grueling, non-conclusive physical reconciliations with disputed blame.
  * **Sales Assistants / Dispensary Techs:** Work in high-stress, low-trust environments subject to arbitrary salary deductions for unexplained stock deficits.
* **Operational & Financial Consequences:**
  * **Uncontrolled Shrinkage:** 4% to 9% of inventory value lost annually to internal pilferage, unrecorded breakages, and unlogged staff dispensing.
  * **Ghost Stockouts:** System records show stock availability when the shelf is empty; patients presenting prescriptions are turned away, leading to lost revenue and customer defection to rival community pharmacies.
  * **False Reordering:** Purchasing items that are already sitting in an unorganized backroom or bulk store.
* **Existing Manual Workarounds:**
  * Paper "Bin Cards" or "Tally Cards" tucked into stock shelves or drawers.
  * Physical monthly or quarterly "shut-down" stock counts where the pharmacy closes for 24–48 hours.
  * WhatsApp staff groups where dispensary attendants post photos of empty shelves or torn blister packs.
  * Excel spreadsheets maintained on a single PC, frequently corrupted, overwritten, or out-of-date.

---

#### Problem 2: Expired and Near-Expiry Medicines Caused by Inadequate Batch and Expiry Monitoring
* **Operational Reality:** Drug supply chains in Nigeria rely heavily on open-market wholesale clusters (e.g., Idumota in Lagos, Head Bridge in Onitsha, Sabon Gari in Kano) alongside formal pharmaceutical distributors. Wholesalers frequently discount short-dated stock (3–6 months to expiry) at steep discounts. Pharmacy buyers purchase these lots without systematic batch logging. On the dispensary shelf, staff habitually pick the frontmost or topmost pack (First-In, First-Out or random picking) rather than the First-Expired, First-Out (FEFO) batch. Older batches are pushed to the back of deep dispensary drawers until they expire undetected.
* **People Affected:**
  * **Patients:** At risk of receiving sub-therapeutic or decomposed medications; loss of clinical confidence if dispensed near-expired products.
  * **Superintendent Pharmacists:** Risk severe PCN and NAFDAC regulatory sanctions, compounding license suspensions, and professional disciplinary tribunal hearings if expired drugs are discovered on active shelves during unannounced inspections.
  * **Pharmacy Owners:** Absorb 100% financial write-offs on expired stock since Nigerian distributors rarely accept returns on expired medicines unless pre-negotiated under strict credit agreements.
* **Operational & Financial Consequences:**
  * Direct capital destruction: 3% to 7% of annual inventory procurement value ends up as expired waste.
  * Hazardous disposal costs: Regulated destruction through authorized waste agencies (e.g., LAWMA Healthcare Waste in Lagos) incurs fees and documentation burdens.
  * Regulatory closure: NAFDAC or PCN sealing of premises during routine post-marketing surveillance when expired packs are found in active dispensing areas.
* **Existing Manual Workarounds:**
  * "Expiry Books" or physical registers where pharmacists attempt to record the expiry date of new stock at arrival (abandoned during peak rush hours).
  * Colored sticky labels or highlighter marks applied manually to pack boxes (fade, fall off, or get ignored).
  * End-of-month panic shelf sweeps searching for products expiring in the current month.
  * Discount "dumping": Rushed fire-sales of near-expiry antibiotics or antimalarials to neighborhood clinics at break-even or below-cost prices.

---

#### Problem 3: Poor Procurement Decisions Caused by Limited Visibility into Movement, Levels, and Replenishment
* **Operational Reality:** Replenishment is predominantly reactive, informal, and driven by "gut feel" or whoever shouts loudest on the pharmacy floor. Because the pharmacy owner or superintendent lacks automated sales velocity metrics and lead-time tracking, purchasing decisions oscillate between two extremes: acute stockouts of high-demand chronic medications (e.g., amlodipine, metformin, telmisartan) and capital over-commitment to slow-moving, high-cost specialty items. In the volatile macroeconomic climate of Nigeria (currency devaluation, volatile wholesale price adjustments, fuel inflation affecting delivery costs), poor purchasing depletes liquid working capital.
* **People Affected:**
  * **Managing Directors / Purchasing Pharmacists:** Experience constant working capital squeeze; cash tied up in dead stock while credit lines with major distributors (e.g., Worldwide Healthcare, Chi Pharmaceuticals, Evans, Fidson) are exhausted.
  * **Patients with Chronic Conditions:** Face fragmented refills; forced to switch brands or visit multiple facilities, disrupting medication adherence.
  * **Dispensary Staff:** Bear the brunt of customer frustration and lose commission or sales bonuses.
* **Operational & Financial Consequences:**
  * Stockout rate of 12% to 22% on top-tier essential medications.
  * Cash-flow paralysis: 20% to 35% of total inventory value remains stagnant on shelves for >120 days ("dead stock").
  * Emergency procurement premium: Buying 1–2 packs from proximate retail competitors at retail or near-retail prices to fulfill immediate prescriptions, forfeiting wholesale margins.
* **Existing Manual Workarounds:**
  * "Want Books" or "Shortage Notebooks" kept on the counter where staff scribble drug names as they run out.
  * Daily WhatsApp voice notes or text lists sent to wholesale market sales reps.
  * Supplier price sheets compared manually across physical invoices.
  * Arbitrary bulk buys based solely on supplier promotions ("Buy 10, Get 1 Free") without checking historical consumption rates.

---

### 2. Separation of Verified Facts vs. Assumptions Requiring Field Validation

| Category | Verified Operating Realities (Empirical Facts) | Assumptions Requiring Field Validation |
| :--- | :--- | :--- |
| **Inventory & Staffing** | • Dispensary staffing turnover in Nigerian urban pharmacies is high (frequent rotations of NYSC pharmacist interns and junior sales assistants).<br>• Power and internet connectivity are intermittent, requiring local resilience.<br>• Most drugs have manufacturer barcodes, but local repackaged generics and herbs often lack GS1-compliant barcodes. | • Staff will consistently scan batch barcodes or manually input batch numbers during peak hours without bypassing the system.<br>• Non-pharmacist sales attendants have adequate digital literacy to operate guided reconciliation workflows on low-end tablets or smartphones. |
| **Suppliers & Procurement** | • The open market (Idumota, Onitsha, Sabon Gari) does not provide electronic invoices; paper receipts and handwritten waybills remain standard.<br>• Wholesale prices fluctuate rapidly with foreign exchange and manufacturer tariff adjustments. | • Distributors will share structured digital price lists or catalogs with pharmacy software platforms.<br>• Pharmacies are willing to log cost prices accurately without fear of tax agency audits or staff seeing business margins. |
| **Expiries & FEFO** | • NAFDAC and PCN impose strict on-the-spot fines and confiscate expired medicines.<br>• Wholesalers do not take back expired stock without explicit prior credit agreements. | • Dispensary staff will respect system-directed FEFO picking prompts instead of grabbing the physically nearest pack on the shelf.<br>• A 90/60/30-day alert horizon provides sufficient lead time for Nigerian pharmacies to liquidate near-expiry stock. |

---

## SECTION B: PRODUCT DEFINITION

### 1. Value Proposition
**Phoenix Pharmacy** is an intelligent pharmacy operations and inventory SaaS platform engineered specifically for Nigerian independent pharmacies and multi-branch retail chains. It delivers **real-time stock truth, eliminates avoidable expiry losses through enforced FEFO batch tracking, and automates cash-conscious replenishment**—transforming chaotic dispensary shelves into a predictable, audit-ready clinical business.

### 2. Ideal Customer Profile (ICP)
* **Primary Target:** Independent community retail pharmacies (1–3 locations) and emerging regional retail chains (4–15 locations).
* **Geography:** Commercial and metropolitan centers in Nigeria (Lagos, FCT Abuja, Rivers/Port Harcourt, Oyo/Ibadan, Kano, Anambra/Onitsha).
* **Business Characteristics:**
  * Active stock holding: 1,500 to 10,000 distinct SKUs.
  * Monthly turnover: ₦5,000,000 to ₦60,000,000+ per branch.
  * Staff profile: 1 Superintendent Pharmacist, 1–2 Relief/Intern Pharmacists, 2–6 Sales Attendants/Technicians, 1 Inventory/Accounts Officer.
  * PCN (Pharmacy Council of Nigeria) registered premises.
  * Pain triggers: Recently incurred major expiry losses (>₦500,000), experienced unexplained inventory shrinkage, or suffered regulatory audit penalties.

### 3. Primary Users & Jobs-To-Be-Done (JTBD)

| User Role | Persona & Responsibilities | Core Job-to-be-Done (JTBD) |
| :--- | :--- | :--- |
| **Superintendent Pharmacist** | Clinical and legal lead; regulatory custodian under PCN Act. | *"When regulatory inspectors visit or when my staff dispense medicines, I want complete assurance that zero expired drugs exist on shelves and all controlled movements are logged, so that our operating license and clinical reputation remain intact."* |
| **Pharmacy Owner / Managing Director** | Capital allocator and business executive. | *"When I review monthly working capital, I want to see exactly where cash is tied up, stop unverified stock loss, and buy only what will sell within 30 days, so that my cash flow is healthy and profitable."* |
| **Inventory / Store Manager** | Central receiver, warehouse clerk, stock auditor. | *"When new stock arrives from suppliers, I want a fast, foolproof way to record batches, costs, and expiries and reconcile discrepancies instantly, so that our ledger matches physical shelves 100%."* |
| **Dispensary Pharmacist / Attendant** | Frontline customer-facing counter staff. | *"When I serve a customer, I want to immediately know which shelf drawer and which exact batch to pick (FEFO) without calculating dates in my head, so that I can serve customers quickly and accurately."* |

---

### 4. System Architecture: How the Three Modules Share Data & Collaborate

The platform functions as a unified operational data loop where each transaction informs the next:

```
    ┌────────────────────────────────────────────────────────┐
    │              1. RECEIVING & BATCH INGESTION            │
    │  • Validates Purchase Order vs Goods Received Note     │
    │  • Captures Batch Number, Expiry Date, Unit Cost       │
    │  • Assigns specific shelf/bin location                 │
    └──────────────────────────┬─────────────────────────────┘
                               │ (Creates Batch Records & updates Ledger)
                               ▼
    ┌────────────────────────────────────────────────────────┐
    │             2. FEFO & DISPENSING / MOVEMENT            │
    │  • Enforces First-Expired, First-Out pick sequence     │
    │  • Tracks real-time depletion by batch                 │
    │  • Triggers color-coded Expiry Risk Horizons           │
    └──────────────────────────┬─────────────────────────────┘
                               │ (Generates Sales Velocity & Batch Depletion Data)
                               ▼
    ┌────────────────────────────────────────────────────────┐
    │         3. REPLENISHMENT & INVENTORY INTELLIGENCE      │
    │  • Computes Run-Out Dates based on moving velocity     │
    │  • Factors Supplier Lead Times & MOQ                   │
    │  • Generates Suggested Purchase Orders                 │
    └──────────────────────────┬─────────────────────────────┘
                               │ (Auto-populates Expected PO for Receiving)
                               └─────────────────────────────┘
```

1. **Ingestion to Batch Memory:** When a shipment arrives, the Receiving Module logs the exact batch ID, expiry date, quantity, and landed cost. It creates immutable sub-batch records tied to the master SKU.
2. **Batch Memory to Operational Front:** As medicines are dispensed, transferred, or adjusted, the system forces consumption against the earliest-expiring active batch (FEFO). Depletions continuously update both SKU aggregate levels and batch-specific balances.
3. **Operational Front to Replenishment Brain:** The system calculates real-time consumption velocity (e.g., 14-day and 30-day rolling averages) alongside remaining batch lifespans. If a batch is nearing expiry before its projected depletion at current velocity, the intelligence engine flags it as an "Impending Expiry Loss" and throttles new reorders.
4. **Replenishment to Receiving:** Generated and approved purchase orders flow back into the Receiving module as "Expected Inbound Shipments," enabling 1-click receiving discrepancy validation.

---

### 5. Out of Scope: What Phoenix Pharmacy Will Deliberately NOT Do in First Release (v1)

To guarantee high adoption, stability, and speed of delivery, the following are strictly excluded from v1:
1. **Full Point-of-Sale (POS) Cash Register & Payment Gateway Processing:** Phoenix Pharmacy will not process card payments, bank transfers, cash-till balances, or print thermal fiscal receipts in v1. It will integrate stock deduction via simple dispensing confirmations or standard API/file hooks from existing cash registers.
2. **Clinical Patient EHR / Disease Management:** No chronic disease tracking, lab test logs, or clinical consultations. (Prescription drug dispensing logging will record patient phone/name for traceability only).
3. **Consumer-Facing E-Commerce & Home Delivery:** No customer mobile apps, online storefronts, or courier fleet management.
4. **Direct Automated NAFDAC / PCN Portal API Integration:** While the system outputs 100% compliant audit logs and regulatory export sheets, it will not attempt live automated electronic filings to government agency portals (which currently lack stable public APIs).
5. **Pharmaceutical Compounding & Manufacturing ERP:** No raw chemical formulation, bill of materials (BOM) yield calculations, or factory batch compounding modules.

---

## SECTION C: FUNCTIONAL REQUIREMENTS

---

### Module 1: Product Catalogue & Master Data Management

#### Feature 1.1: Standardized Clinical Product Master
* **Purpose:** Establish a single source of truth for all products stocked across pharmacy branches, preventing duplicate names and inconsistent pack sizes.
* **Primary User:** Inventory Manager, Superintendent Pharmacist.
* **Inputs:** Brand name, Generic/INN name, Strength (e.g., 500mg), Dosage Form (Tablet, Suspension, Capsule, IV), Pack Size / Unit of Measurement (e.g., Box of 10x10, Bottle of 100ml), NAFDAC Registration Number, Barcode / GTIN (optional for unbarcoded generics), Category (Prescription POM, OTC, Personal Care, Surgical), Storage Condition (Ambient, Cold Chain 2–8°C), Minimum Reorder Point (units), Target Maximum Level.
* **Expected Outputs:** Clean catalog directory, searchable by brand, generic, or barcode; shelf-location tagging; printable internal shelf barcode labels.
* **Business Rules:**
  * System must prevent creation of identical (Generic + Strength + Form + Pack Size + Brand) entries.
  * Cold chain items must be visually flagged with a refrigeration indicator across all workflows.
  * Deletion of a SKU is blocked if historical transaction records or active inventory exist (archive/inactive status only).
* **Acceptance Criteria:**
  * Search responds in <200ms across 10,000 SKUs when filtering by generic or brand.
  * Bulk import via standardized CSV template with validation error preview before committing.

---

### Module 2: Supplier Directory & Commercial Terms

#### Feature 2.1: Pharmaceutical Distributor Management
* **Purpose:** Maintain records of verified drug importers, manufacturers, and open-market wholesale distributors with their commercial terms and lead times.
* **Primary User:** Inventory Manager, Managing Director.
* **Inputs:** Supplier Company Name, Contact Person, Phone Numbers (primary WhatsApp contact), Email, Physical Warehouse Address (e.g., Idumota, Ikeja, Onitsha), PCN Premises License Number (if formal distributor), Payment Terms (Cash on Delivery, 7-day credit, 14-day credit, 30-day credit), Expected Delivery Lead Time (in days), Bank Payment Details.
* **Expected Outputs:** Active supplier profile, supplier performance scorecard (lead time adherence, fill rate, historical discrepancy rate).
* **Business Rules:**
  * If credit terms are set, the system tracks outstanding invoice aging against the supplier.
  * Warning trigger if a supplier with expired PCN premises verification is selected for a new Purchase Order.
* **Acceptance Criteria:**
  * User can filter products by primary supplier and view historical purchase price trends per supplier over 12 months.

---

### Module 3: Stock Receiving & Goods Received Notes (GRN)

#### Feature 3.1: Purchase Order Reconciliation & Batch Ingestion
* **Purpose:** Log inbound stock physically delivered by suppliers, record batch specifics, verify landed costs, and identify delivery shortages/damages.
* **Primary User:** Store Manager, Pharmacist on Duty.
* **Inputs:** Supplier Invoice Number, Purchase Order Reference (optional for ad-hoc drop shipments), Date Received, Receiving Location/Store, Line Item Entry:
  * Product SKU
  * Quantity Received (Packs and Units)
  * Free/Bonus Units Received (promotional stock)
  * Manufacturer Batch Number
  * Expiry Date (MM/YYYY or DD/MM/YYYY)
  * Unit Purchase Price (₦ landed cost before VAT/withholding)
  * Damage / Shortage quantity (if any)
  * Physical invoice image upload / snapshot (via camera or scanner).
* **Expected Outputs:** Generated Goods Received Note (GRN) with system timestamp, updated on-hand inventory balances, updated weighted average cost (WAC) per SKU, discrepancy discrepancy report if delivered quantity != ordered quantity.
* **Business Rules:**
  * **Hard Regulatory Rule:** Rejection of items with expiry dates less than 6 months out unless explicitly authorized by the Superintendent Pharmacist with a mandatory override reason code ("Pre-agreed Fast-Track Dispensing").
  * Batch number and expiry date are strictly mandatory for all pharmaceutical items (POM and P categories). No receiving entry can be saved without them.
  * Cost price variations exceeding 10% compared to last purchase price trigger a confirmation modal to prevent typing errors.
* **Acceptance Criteria:**
  * Completed GRN locks immediately; updates to historical GRNs can only be performed via an authorized adjustment ledger entry with an audit log.

---

### Module 4: Stock Transfers & Multi-Location Adjustments

#### Feature 4.1: Inter-Branch and Sub-Store Transfers
* **Purpose:** Manage stock movements between central bulk stores and retail dispensary shelves, or between different pharmacy branches.
* **Primary User:** Store Keeper, Dispensary Pharmacist.
* **Inputs:** Source Location, Destination Location, Product, Selected Batch ID (guided by FEFO), Transfer Quantity, Transfer Notes.
* **Expected Outputs:** Transfer Request document, In-Transit State indicator, Goods Inward Transfer Acceptance by recipient location.
* **Business Rules:**
  * Transferred stock leaves source inventory immediately and enters an "In-Transit" escrow status until the destination user confirms physical receipt.
  * Any variance between dispatched and received quantity triggers an automatic "Transfer Discrepancy" incident requiring supervisory sign-off.
* **Acceptance Criteria:**
  * Both source and destination audit trails record the originating user, dispatch timestamp, accepting user, and receipt timestamp.

#### Feature 4.2: Stock Adjustments & Damage Write-Offs
* **Purpose:** Record inventory changes outside of normal sales or receiving (e.g., broken bottles, water damage, internal clinic/first-aid use, expired destruction).
* **Primary User:** Superintendent Pharmacist, Store Manager.
* **Inputs:** SKU, Batch ID, Adjustment Type (Damage, Theft/Shrinkage, Internal Clinic Use, Found Stock, Expired Safe Destruction), Quantity, Supporting Photo (optional), Justification Text.
* **Expected Outputs:** Stock adjustment voucher, ledger debit/credit, write-off valuation report.
* **Business Rules:**
  * Write-offs with a total value exceeding ₦25,000 require Managing Director 2-factor approval or secondary supervisor authorization.
* **Acceptance Criteria:**
  * Write-offs immediately deduct from on-hand batch balances and appear on the Financial Loss Report.

---

### Module 5: Stock Reconciliation & Physical Cycle Counting

#### Feature 5.1: Blind Physical Stock Audits
* **Purpose:** Validate physical shelf stock against digital system stock without letting staff see the expected quantities, eliminating confirmation bias.
* **Primary User:** Pharmacist Intern, Inventory Auditor, Superintendent.
* **Inputs:** Audit Scope (Full Store, Category, Shelf Rack, or High-Value ABC Class A), Counted Quantity per Batch, Physical Count Notes.
* **Expected Outputs:**
  * Physical vs. System Variance Sheet (Variance in Units and Variance in Naira).
  * Discrepancy Percentage: `(Abs(Physical - System) / System) * 100`.
  * Auto-generated reconciliation adjustment proposal.
* **Business Rules:**
  * Counters cannot see system expected quantities on their counting screen ("Blind Audit").
  * System automatically highlights items with variances > 2% or absolute financial discrepancy > ₦5,000 for mandatory immediate recount.
  * Applying reconciliation requires Superintendent or MD sign-off.
* **Acceptance Criteria:**
  * System captures exact count timestamps and produces an exportable PCN-compliant Annual/Quarterly Stock Audit Certificate.

---

### Module 6: Batch & Expiry Management

#### Feature 6.1: Multi-Batch Tracking & Visual Expiry Horizons
* **Purpose:** Provide complete visibility into every distinct drug batch residing in the pharmacy, categorizing expiry risk into actionable visual time horizons.
* **Primary User:** Dispensary Pharmacist, Store Manager.
* **Inputs:** Automated continuous evaluation of stored batch dates against the current date.
* **Expected Outputs:**
  * Expiry Dashboard with 4 distinct risk buckets:
    * **Critical (Red):** Expiring within 30 days or already expired.
    * **High Risk (Amber):** Expiring in 31–90 days.
    * **Watchlist (Yellow):** Expiring in 91–180 days.
    * **Safe (Green):** Expiring in >180 days.
  * Total monetary value at risk displayed per horizon.
* **Business Rules:**
  * If a batch crosses into the 0-day mark (expired), it is **automatically quarantined**: the system blocks it from being selected for sale or transfer and flags it for regulatory disposal.
* **Acceptance Criteria:**
  * Daily background cron evaluates all batches at 00:01 WAT and updates status badges and notifications.

---

### Module 7: Enforced FEFO (First-Expired, First-Out) Support

#### Feature 7.1: FEFO Dispensing Guidance & Override Controls
* **Purpose:** Ensure that stock with the closest expiry date is consistently dispensed before newer batches, preventing shelf aging.
* **Primary User:** Dispensary Pharmacist, Sales Attendant.
* **Inputs:** SKU scan or search during dispensing.
* **Expected Outputs:** Primary recommendation showing the specific Batch Number, Expiry Date, and Shelf Location of the batch that must be picked.
* **Business Rules:**
  * The system defaults to the earliest expiring batch.
  * If the staff member manually selects a newer batch while an older valid batch exists:
    * The system displays an **Enforced Override Modal**: *"You are bypassing Batch [X] expiring in [Y] days. Please provide an override reason."*
    * Mandatory Reason Selection: (1) Physical damage to older batch box, (2) Patient requested longer expiry for travel/bulk purchase, (3) Batch misplaced/not physically found on shelf.
    * Overrides are logged in the Compliance Audit Trail and flagged on the Superintendent's weekly report.
* **Acceptance Criteria:**
  * Dispensing execution is completed in fewer than 3 clicks or a single barcode scan.

---

### Module 8: Low-Stock Monitoring & Buffer Rules

#### Feature 8.1: Dynamic Reorder Points (ROP) & Out-of-Stock Alerts
* **Purpose:** Prevent stockouts of essential medicines by triggering timely alerts before inventory reaches zero, factoring in supplier delivery delays.
* **Primary User:** Inventory Manager, Purchasing Pharmacist.
* **Inputs:** Average Daily Consumption (ADC over trailing 30 days), Supplier Lead Time (days), Safety Buffer Stock Days (default: 7 days for local suppliers, 14 days for inter-state).
* **Expected Outputs:**
  * Computed Reorder Level: `ROP = (ADC * Lead Time) + Safety Stock`.
  * Real-time "Stock Status" tags:
    * **Stockout (Red):** 0 units on hand.
    * **Critical Low (Amber):** On-hand ≤ Safety Stock.
    * **Reorder Needed (Yellow):** On-hand ≤ ROP.
    * **Optimal (Green):** ROP < On-hand ≤ Maximum Stock.
    * **Overstocked (Blue):** On-hand > Maximum Stock (capital drag).
* **Business Rules:**
  * System alerts trigger on the dashboard and via an optional daily morning email/digest summary.
* **Acceptance Criteria:**
  * Changes in sales velocity automatically adjust ROP weekly.

---

### Module 9: Product Movement Analysis & Inventory Stratification

#### Feature 9.1: ABC / VEN Matrix Analysis
* **Purpose:** Prioritize inventory management focus based on financial impact (ABC analysis) and clinical criticality (VEN analysis).
* **Primary User:** Managing Director, Superintendent Pharmacist.
* **Inputs:** Trailing 90-day sales transaction data and product clinical categorization.
* **Expected Outputs:**
  * 3x3 Matrix Grid categorizing every SKU:
    * **ABC Classification:** Class A (top 70% of revenue/value, typically 10-15% of SKUs), Class B (next 20% of value), Class C (bottom 10% of value).
    * **VEN Classification:** Vital (life-saving drugs: insulin, adrenaline, anti-hypertensives, oxytocin), Essential (standard therapeutics: antibiotics, analgesics), Non-Essential (vitamins, cosmetics, OTC wellness).
  * Fast-Moving vs. Dead Stock (>90 days zero movement) report with monetary valuation.
* **Business Rules:**
  * Items classified as **Vital (V)** can never have their safety stock reduced to zero, even if consumption velocity drops.
* **Acceptance Criteria:**
  * User can filter dead stock list by supplier to negotiate return-for-credit or trade-in deals.

---

### Module 10: Reorder Recommendations & Purchase Order Builder

#### Feature 10.1: Algorithmic Replenishment Engine
* **Purpose:** Convert consumption data, lead times, and supplier minimums into one-click, supplier-grouped purchase orders.
* **Primary User:** Purchasing Pharmacist, Managing Director.
* **Inputs:** Current On-Hand Stock, Incoming In-Transit Orders, Reorder Points, Minimum Order Quantities (MOQ), Pack Size constraints, Available Working Capital Budget (optional).
* **Expected Outputs:**
  * Suggested Reorder List aggregated by Supplier.
  * Recommended Order Quantity: `ROQ = (Target Max Stock) - (On-Hand + In-Transit)`.
  * One-click conversion into PDF / WhatsApp-ready Purchase Order document.
* **Business Rules:**
  * Order quantities must automatically round up to the nearest whole pack size (e.g., if need is 14 ampoules and pack size is 10, suggest 20 ampoules / 2 packs).
  * If a product has a near-expiry batch currently in stock with slow velocity, the system displays a warning: *"Warning: Existing stock of this SKU has slow movement. Reordering will compound expiry risk."*
* **Acceptance Criteria:**
  * User can edit suggested quantities and approve the PO in <60 seconds.

---

### Module 11: Compliance Reporting & Immutable Audit History

#### Feature 11.1: PCN-Compliant Audit Ledger & Forensic Logging
* **Purpose:** Maintain an incorruptible log of every inventory event for regulatory compliance, internal accountability, and shrinkage investigation.
* **Primary User:** Superintendent Pharmacist, Internal Auditor.
* **Inputs:** Automatic capture of: User ID, Role, Event Type (Receive, Dispense, Transfer, Adjust, Recount, FEFO Override), SKU, Batch ID, Quantity Before, Quantity After, Timestamp, IP Address.
* **Expected Outputs:**
  * Filterable, exportable (CSV/PDF) Audit Trail.
  * Controlled Substance Register (electronic Form B equivalent for DDA/narcotic reporting).
  * User Activity Log (tracking after-hours or weekend inventory modifications).
* **Business Rules:**
  * Audit logs are **strictly immutable**: No user, including the Managing Director or System Admin, can edit or delete an audit log entry.
* **Acceptance Criteria:**
  * Audit queries by SKU or Batch ID return complete cradle-to-grave history within 1 second.

---

## SECTION D: MVP BOUNDARIES

To launch a resilient, bug-free, and high-impact initial product for Nigerian pharmacies without scope bloat, features are triaged into three strict tiers:

```
┌────────────────────────────────────────────────────────────────────────┐
│                          TIER 1: ESSENTIAL FOR MVP                     │
│  • Clinical Product Master Catalog (Generic, Brand, Strength, Form)   │
│  • Supplier Directory (Wholesalers, Contacts, Payment Terms)           │
│  • Stock Receiving with Mandatory Batch & Expiry Capture (GRN)         │
│  • Single-Store Stock Ingestion & Real-Time On-Hand Balances           │
│  • Batch Expiry Horizon Dashboard (30/90/180 Days, Red/Amber Alerts)   │
│  • FEFO-Guided Dispensing Deductions & Manual Override Logging         │
│  • Basic Low-Stock Alerts (Static Minimum Thresholds)                  │
│  • Physical Stock Count & Variance Sheet (Reconciliation)              │
│  • Immutable Audit Trail (Receiving, Adjustments, Overrides)           │
│  • User Roles: Owner/Superintendent vs. Store Manager vs. Attendant    │
└────────────────────────────────────┬───────────────────────────────────┘
                                     │
                                     ▼
┌────────────────────────────────────────────────────────────────────────┐
│                        TIER 2: IMPORTANT AFTER MVP                     │
│  • Multi-Branch Inventory Visibility & Inter-Branch Stock Transfers    │
│  • Blind Physical Stock Audits (Masked Expected Quantities)            │
│  • Automated Dynamic Reorder Level (ROP) based on 30-day velocity      │
│  • Algorithmic Suggested Purchase Order Generator (Grouped by Vendor)  │
│  • WhatsApp PO Sharing (Direct export to supplier WhatsApp format)     │
│  • ABC Analysis & Dead-Stock (>90 days) Capital Tracking               │
│  • Mobile Camera Barcode Scanning for fast receiving and dispensing   │
└────────────────────────────────────┬───────────────────────────────────┘
                                     │
                                     ▼
┌────────────────────────────────────────────────────────────────────────┐
│                        TIER 3: FUTURE EXPANSION                        │
│  • Multi-Vendor Price Comparison Matrix across Major Wholesalers       │
│  • Electronic Controlled Substance Register (Automated PCN Form B)     │
│  • POS Hardware Integration (Receipt Printers & Cash Drawers)          │
│  • Supplier Credit & Accounts Payable Ledger Aging Integration         │
│  • AI-Powered Seasonal Demand Forecasting (e.g., Malaria season surge) │
│  • Offline-First Progressive Web App (PWA) with Background Sync        │
└────────────────────────────────────────────────────────────────────────┘
```

---

## SECTION E: BUSINESS MODEL RECOMMENDATION

*Note: In accordance with strategic discovery guidelines, this model defines structural tiering and value metrics without fabricating unverified market pricing figures.*

### 1. Subscription Structure for Independent Community Pharmacies (1–3 Branches)
* **Value Metric:** Number of physical locations (branches) + active SKU tier.
* **Tiering Structure:**
  * **Tier 1: Solo Community Pharmacy (Single Location)**
    * Includes: 1 Active Branch, up to 3,500 active SKUs.
    * Users: 1 Superintendent Pharmacist, 1 Store Manager, up to 4 Dispensary Attendants.
    * Features: Complete MVP operational stack (Receiving, Batch/Expiry FEFO, Reconciliations, Low-Stock Alerts, Audit Logs).
    * Billing Frequency: Monthly or Annual upfront (with 15–20% discount to incentivize cash predictability).
  * **Tier 2: Growth Retailer (1–3 Branches)**
    * Includes: Up to 3 Branches, up to 10,000 active SKUs.
    * Users: Unlimited staff seats with granular role-based permissions.
    * Features: Multi-branch stock visibility, inter-branch transfers, automated velocity-based reordering.

### 2. Commercial Structure for Multi-Branch Operators & Regional Chains (4–15+ Branches)
* **Tiering Structure:** **Enterprise Multi-Branch**
  * **Base Platform Fee:** Covers central warehouse operations, unified master catalog management, and administrative oversight.
  * **Per-Branch Increment:** Predictable linear monthly charge per additional active branch location.
  * **Value Metric:** Centralized purchasing intelligence, consolidated supplier orders, and cross-branch inventory balancing (transferring near-expiry stock from low-velocity branches to high-velocity branches).
  * **Support Level:** Dedicated account onboarding, custom staff training workshops, historical data migration assistance from legacy spreadsheets.

### 3. Payment Mechanics Tailored to Nigeria
* **Local Currency Billing:** Billed in Nigerian Naira (NGN) to shield pharmacy operators from foreign exchange volatility.
* **Payment Rails:** Automated recurring direct debit via Nigerian payment switches (Paystack/Flutterwave) alongside corporate direct bank transfer verification for annual corporate accounts.

---

## SECTION F: MEASURABLE OPERATIONAL SUCCESS METRICS

To prove direct return on investment (ROI) within 90 days of deployment, the platform will track five key operational KPIs:

```
┌───────────────────────────────────────────────────────────────────────────────────────┐
│                           CORE OPERATIONAL KPI SCORECARD                              │
├───────────────────────────────────┬───────────────────┬───────────────────────────────┤
│ Metric Name                       │ Calculation / Formulation                         │ Target Benchmark (90 Days)   │
├───────────────────────────────────┼───────────────────┼───────────────────────────────┤
│ 1. Inventory Discrepancy Rate     │ (Total Variance Units / Total Audited Units) * 100 │ Reduction from >8% to <1.5%   │
├───────────────────────────────────┼───────────────────┼───────────────────────────────┤
│ 2. Value of Stock Near Expiry     │ Sum of landed cost for stock in 0-60 day horizon  │ 40% to 65% reduction via FEFO │
├───────────────────────────────────┼───────────────────┼───────────────────────────────┤
│ 3. Essential Stockout Frequency   │ (Stockout Hours on Class A/Vital SKUs) / Total Hrs│ Cut stockout instances by 70% │
├───────────────────────────────────┼───────────────────┼───────────────────────────────┤
│ 4. Reconciliation Completion Time │ Total elapsed hours to complete monthly audit     │ Reduced from 24 hrs to <4 hrs │
├───────────────────────────────────┼───────────────────┼───────────────────────────────┤
│ 5. Reorder Recommendation Utility │ (Suggested PO Lines Accepted Without Edit) / Total│ >75% acceptance rate          │
└───────────────────────────────────┴───────────────────┴───────────────────────────────┘
```

1. **Inventory Discrepancy Rate:**
   * **Definition:** Absolute variation between physical count and system records across audited SKUs.
   * **Target:** Lower from Nigerian industry average of 6–10% down to under 1.5%.
2. **Value of Stock Approaching Expiry:**
   * **Definition:** Total Naira valuation of medicines residing in the <60-day expiry window without active sales velocity.
   * **Target:** Minimum 50% decrease within 4 months through enforced FEFO picking and early warning liquidation.
3. **Essential Stockout Frequency:**
   * **Definition:** Frequency of stock depletion events on designated "Vital" and "Class A" medications (e.g., top 50 chronic and anti-infective lines).
   * **Target:** Zero unpredicted stockouts; 80% reduction in emergency competitor retail purchases.
4. **Stock Reconciliation Completion Rate & Velocity:**
   * **Definition:** Percentage of catalog successfully audited during scheduled cycle counts and time required to complete.
   * **Target:** Full cycle audit completed in under 4 hours per month without shutting down pharmacy operations.
5. **Reorder Recommendation Usefulness:**
   * **Definition:** Ratio of algorithmic purchase suggestions accepted by the purchasing pharmacist without manual override.
   * **Target:** >75% acceptance rate within 60 days of algorithm baseline calibration.

---

## SECTION G: RISK ANALYSIS & MITIGATION STRATEGY

| Risk Category | Specific Operational / Technical Risk | Severity | Concrete Mitigation Strategy |
| :--- | :--- | :--- | :--- |
| **Operational Risk** | **Staff Workload Resistance during Rush Hours:** Attendants skip batch logging or FEFO picking when queues form at the dispensary counter. | **HIGH** | • Keep FEFO pick confirmation to a single keystroke or barcode scan.<br>• Implement a "Rapid Dispense Queue" where dispensing can be temporarily flagged and reconciled within a 2-hour window.<br>• Provide Superintendent weekly compliance scorecards showing override rates per attendant. |
| **Security Risk** | **Insider Theft & Data Manipulation:** Staff intentionally adjusting stock records to mask physical pilferage. | **HIGH** | • Strictly immutable audit logs stored in append-only tables.<br>• Two-person integrity rule: Stock adjustments above ₦10,000 require independent supervisor authorization.<br>• Blind stock audit mode prevents counters from knowing what the system expects. |
| **Data Integrity Risk** | **Garbage In, Garbage Out on Master Data:** Duplicate drug entries (e.g., "Augmentin 625mg", "Augmentin 625 mg tab", "Co-amoxiclav 625mg") destroying inventory accuracy. | **HIGH** | • Pre-loaded Nigerian Master Pharmaceutical Catalog covering top 3,000 registered brands and generics.<br>• Fuzzy matching and uniqueness validation during SKU creation.<br>• Disallow ad-hoc product creation by regular dispensary attendants (Superintendent privilege only). |
| **Adoption Risk** | **Intermittent Power and Poor Internet:** Unstable electricity and mobile data dropouts in Nigerian urban fringe areas paralyzing the counter. | **CRITICAL** | • Lightweight application bundle (<2MB initial load).<br>• Local browser storage cache allowing continuous counter lookups and queue logging during brief network dropouts.<br>• Multi-device responsiveness (functions smoothly on cheap Android tablets and 4G smartphones). |
| **Regulatory Risk** | **Non-Compliance with PCN & NAFDAC Requirements:** Platform records failing to meet statutory standards for controlled substance inspection or premises audit. | **HIGH** | • Align data fields precisely with PCN Form B (Inspection of Premises and Poison Books).<br>• Automated 1-click generation of NAFDAC-mandated Expired Drug Destruction Application dossiers.<br>• Continuous compliance review by qualified Nigerian pharmacist consultants. |

---

## SECTION H: UNANSWERED QUESTIONS REQUIRING VALIDATION WITH NIGERIAN PHARMACY OPERATORS

Before building the frontend and database schemas, the following specific field questions must be validated through direct user interviews with community pharmacists and pharmacy owners in Nigeria:

1. **Receiving Workflow Habits:**
   * *When a shipment of 50 cartons arrives from Idumota or Onitsha, does the pharmacist unbox and verify every single batch number immediately on the sidewalk/receiving dock, or do cartons sit in the store room for days before being entered into the system?*
2. **Pack Splitting & Unit Dispensing:**
   * *How often do pharmacists split blister packs (e.g., dispensing 4 tablets out of a 10-tablet blister, or 1 sachet out of a carton of 50)? How should the inventory model represent fractional units without causing rounding reconciliation errors?*
3. **Cash-Till Coexistence:**
   * *If Phoenix Pharmacy does not operate the cash drawer in v1, how will dispensary staff handle the double-entry friction of ringing the sale on an existing POS/cash register while simultaneously confirming stock deduction in Phoenix?*
4. **Wholesaler Invoice Formats:**
   * *What percentage of local wholesalers provide printed invoices with typed batch numbers versus handwritten receipts with illegible notes? (Determines whether optical character recognition / invoice scanning is viable).*
5. **Near-Expiry Return Agreements:**
   * *Do local distributors have informal return windows (e.g., "return within 3 months to expiry for 70% credit"), and how should the system notify the pharmacist to trigger those returns before the window closes?*
6. **Controlled Substances Verification:**
   * *Are pharmacists willing to log patient identification (name, phone number, doctor's prescription) during dispensing of controlled medicines (e.g., dihydrocodeine, tramadol, diazepam) inside the inventory app, or does that create unacceptable counter friction?*
