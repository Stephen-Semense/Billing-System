# ⚡ Unit Billing System

## Website Link: https://stephen-semense.github.io/Billing-System/

A lightweight, client-side billing calculator for **VECO Electric** and **MCWD Water** utility distribution across 4 residential units. Built with vanilla HTML, CSS, and JavaScript — no backend or dependencies required.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![License](https://img.shields.io/badge/License-MIT-green.svg)

---

## 📋 Table of Contents

- [Features](#features)
- [How It Works](#how-it-works)
- [Usage Instructions](#usage-instructions)
- [Print Modes](#print-modes)
- [Example Computation](#example-computation)
- [Formulas](#formulas)
- [File Structure](#file-structure)
- [Screenshots](#screenshots)
- [License](#license)

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| **Dual Billing** | Separate tabs for Electric (VECO) and Water (MCWD) |
| **Auto-Calculation** | Real-time computation as you type |
| **4 Submetered Units** | All 4 units have individual previous/current readings |
| **Bill Settings** | Enter total bill, bill month, due date, and rate per unit |
| **Dashboard Summary** | Total Electric, Total Water, Grand Total, and Total Units Bill |
| **Total Units Bill** | Displays the sum of your actual VECO + MCWD bill inputs |
| **Two Print Modes** | Print Default (full report) and Print Units (clean unit view) |
| **Print-Ready Report** | One-click print with bill info, breakdown, and submeter readings |
| **Responsive Design** | Works on desktop, tablet, and mobile |
| **Zero Dependencies** | Single HTML file — no installation needed |

---

## 🧮 How It Works

All 4 units use **individual submeters**. Each unit's bill is calculated from its own usage multiplied by the rate.

```
Unit Bill = (Current Reading − Previous Reading) × Rate
```

**Total Units Bill** (dashboard): Shows the sum of the **Total VECO Bill** and **Total MCWD Bill** amounts you enter in the Bill Settings. This reflects your actual utility provider bills.

---

## 🚀 Usage Instructions

### 1. Open the File
Simply open `index.html` in any modern web browser (Chrome, Firefox, Edge, Safari).

```bash
# Optional: serve locally
python -m http.server 8000
# Then visit http://localhost:8000
```

### 2. Enter Electric Bill (VECO Tab)
- **Bill Month** — The billing period (e.g., `2026-05`)
- **Due Date** — Payment deadline
- **Rate per kWh** — Your current electricity rate
- **Total VECO Bill** — The actual amount on your VECO statement
- **Previous / Current Readings** — Submeter readings for Units 1, 2, 3, and 4
- Results update automatically as you type

### 3. Enter Water Bill (MCWD Tab)
- **Bill Month** — The billing period
- **Due Date** — Payment deadline
- **Rate per cu.m** — Your current water rate
- **Total MCWD Bill** — The actual amount on your MCWD statement
- **Previous / Current Readings** — Submeter readings for Units 1, 2, 3, and 4
- Results update automatically as you type

### 4. View Dashboard (Home Tab)
- **Total Electric** — Sum of calculated electric bills for all 4 units
- **Total Water** — Sum of calculated water bills for all 4 units
- **Grand Total** — Combined total of all calculated bills
- **Total Units Bill** — Sum of your actual VECO + MCWD bill inputs
- Consolidated table of all 4 units with per-unit and grand totals

### 5. Print Report
Select a print mode from the dropdown (bottom-right) and click **🖨️ Print**:

---

## 🖨️ Print Modes

The system offers **two print layouts** via a dropdown selector:

### Print Default
Shows the **complete report** with all details:
- Summary cards (Total Electric, Total Water, Grand Total, Total Units Bill)
- Home — Bill Summary table
- VECO & MCWD Bill Information (Month, Due Date, Rate, Total Bill)
- Submeter Readings
- Electric & Water Bill Breakdown tables
- Total kWh / cu.m Used summary

### Print Units
Shows a **clean, simplified report** focused on unit billing:
- Summary cards (Total Electric, Total Water only)
- Home — Bill Summary table
- VECO & MCWD Bill Information (Month, Due Date only)
- Submeter Readings
- Electric & Water Bill Breakdown tables
- Total kWh / cu.m Used summary

**Hidden in Print Units:**
- ❌ Grand Total summary card
- ❌ Total Units Bill summary card
- ❌ Rate per kWh / cu.m column
- ❌ Total VECO / MCWD Bill amounts

---

## 📊 Example Computation

### Scenario
A residential building receives the following monthly bills:
- **VECO Electric**: ₱4,850.00 (Rate: ₱11.50/kWh)
- **MCWD Water**: ₱980.00 (Rate: ₱22.00/cu.m)

Submeter readings are recorded as follows:

| Unit | Electric Prev | Electric Curr | Water Prev | Water Curr |
|------|--------------|---------------|------------|------------|
| Unit 1 | 10,250 | 10,320 | 450 | 458 |
| Unit 2 | 8,450 | 8,510 | 320 | 326 |
| Unit 3 | 12,000 | 12,150 | 580 | 590 |
| Unit 4 | 9,500 | 9,620 | 410 | 420 |

### Electric Calculation (VECO)

```
Unit 1: (10,320 − 10,250) × ₱11.50 = 70 kWh × ₱11.50 = ₱805.00
Unit 2: (8,510 − 8,450) × ₱11.50 = 60 kWh × ₱11.50 = ₱690.00
Unit 3: (12,150 − 12,000) × ₱11.50 = 150 kWh × ₱11.50 = ₱1,725.00
Unit 4: (9,620 − 9,500) × ₱11.50 = 120 kWh × ₱11.50 = ₱1,380.00
─────────────────────────────────────────────────────────────────
Total Calculated: ₱4,600.00
Total kWh Used: 70 + 60 + 150 + 120 = 400 kWh
```

### Water Calculation (MCWD)

```
Unit 1: (458 − 450) × ₱22.00 = 8 cu.m × ₱22.00 = ₱176.00
Unit 2: (326 − 320) × ₱22.00 = 6 cu.m × ₱22.00 = ₱132.00
Unit 3: (590 − 580) × ₱22.00 = 10 cu.m × ₱22.00 = ₱220.00
Unit 4: (420 − 410) × ₱22.00 = 10 cu.m × ₱22.00 = ₱220.00
─────────────────────────────────────────────────────────────────
Total Calculated: ₱748.00
Total cu.m Used: 8 + 6 + 10 + 10 = 34 cu.m
```

### Dashboard Summary

| Card | Value | Source |
|------|-------|--------|
| **Total Electric** | ₱4,600.00 | Calculated from submeters |
| **Total Water** | ₱748.00 | Calculated from submeters |
| **Grand Total** | ₱5,348.00 | Sum of calculated totals |
| **Total Units Bill** | ₱5,830.00 | VECO (₱4,850) + MCWD (₱980) |

### Unit Breakdown Table

| Unit | Electric | Water | Total |
|------|----------|-------|-------|
| Unit 1 | ₱805.00 | ₱176.00 | **₱981.00** |
| Unit 2 | ₱690.00 | ₱132.00 | **₱822.00** |
| Unit 3 | ₱1,725.00 | ₱220.00 | **₱1,945.00** |
| Unit 4 | ₱1,380.00 | ₱220.00 | **₱1,600.00** |
| **GRAND TOTAL** | **₱4,600.00** | **₱748.00** | **₱5,348.00** |

---

## 📐 Formulas

### Core Logic

```javascript
// For each unit (1–4)
Usage    = Current_Reading − Previous_Reading
Bill     = Usage × Rate

// Dashboard totals
Total Electric   = Unit 1 Elec + Unit 2 Elec + Unit 3 Elec + Unit 4 Elec
Total Water      = Unit 1 Water + Unit 2 Water + Unit 3 Water + Unit 4 Water
Grand Total      = Total Electric + Total Water
Total Units Bill = Total VECO Bill (input) + Total MCWD Bill (input)

// Print summaries
TotalKwhUsed = kWh₁ + kWh₂ + kWh₃ + kWh₄
TotalCuMUsed = cu.m₁ + cu.m₂ + cu.m₃ + cu.m₄
```

### Currency Formatting

All amounts are displayed in **Philippine Peso (₱)** with 2 decimal places:
```javascript
'₱' + amount.toLocaleString('en-PH', { minimumFractionDigits: 2, maximumFractionDigits: 2 })
// Example: 4850 → "₱4,850.00"
```

---

## 📁 File Structure

```
unit-billing-system/
├── index.html          # Complete application (HTML + CSS + JS)
└── README.md           # This file
```

> **Note**: This is a single-file application. All styles and scripts are embedded for zero-dependency portability.

---

## 🖼️ Screenshots

### Dashboard View
The home tab displays summary cards (Total Electric, Total Water, Grand Total, Total Units Bill) and a consolidated table of all 4 units.

### Electric Tab
Input bill month, due date, rate, total bill, and submeter readings for all 4 units.

### Water Tab
Same logic as electric, configured for MCWD water billing.

### Print Default Preview
Complete report with all details including Bill Information, Submeter Readings, Bill Breakdown, and summary totals.

### Print Units Preview
Clean simplified report showing only essential unit billing information — no rates or total bills.

---

## ⚙️ Technical Details

### Browser Compatibility
- Chrome 80+
- Firefox 75+
- Safari 13+
- Edge 80+

### No Build Step Required
Since this is vanilla HTML/CSS/JS, there is no build process, bundler, or package manager needed. Simply edit the file and refresh the browser.

### Customization
To change default values, edit the `value` attributes in the HTML:

```html
<!-- Default electric rate -->
<input type="number" id="elec-rate" value="17.00" step="0.01">

<!-- Default water rate -->
<input type="number" id="water-rate" value="28.00" step="0.01">
```

---

## 🛡️ Data Privacy

All calculations happen **entirely in your browser**. No data is sent to any server, stored in cookies, or written to localStorage. Your billing data stays on your machine.

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

## 🙋 FAQ

**Q: What is the difference between "Grand Total" and "Total Units Bill"?**
> A: **Grand Total** is the sum of all calculated submeter bills. **Total Units Bill** is the sum of the actual VECO and MCWD bill amounts you entered. They may differ if your rate or readings don't exactly match the provider's billing.

**Q: What is "Total kWh / cu.m Used"?**
> A: This is the **sum of all units' usage** (kWh for electric, cu.m for water), shown below each bill breakdown table in the print report.

**Q: What is the difference between Print Default and Print Units?**
> A: **Print Default** shows the complete report with all details including rates and total bills. **Print Units** shows a clean simplified report with only essential unit billing information — perfect for distributing to tenants.

**Q: Can I add more units?**
> A: Currently supports exactly 4 units. To add more, modify the JavaScript loops (`for (let i = 1; i <= 4; i++)`) and add corresponding HTML inputs.

**Q: Does it save data between sessions?**
> A: No — refresh the page and data resets. This is by design for privacy. Use the Print feature to save a PDF record.

**Q: Can I use this for commercial buildings?**
> A: Yes, as long as each unit has its own submeter.

---

<p align="center">Built with ⚡ for hassle-free utility billing</p>
