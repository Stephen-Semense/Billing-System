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
| **Unit 4 Logic** | Automatically calculates the remaining balance for Unit 4 (master meter) |
| **Dashboard** | Consolidated summary of all units with grand totals |
| **Validation Alerts** | Warns when Unit 4 amount turns negative (over-distribution) |
| **Print Ready** | One-click print-friendly report generation |
| **Responsive Design** | Works on desktop, tablet, and mobile |
| **Zero Dependencies** | Single HTML file — no installation needed |

---

## 🧮 How It Works

This system uses a **"remaining balance"** method for Unit 4:

1. **Units 1–3** have individual submeters. Their bills are calculated directly from usage × rate.
2. **Unit 4** does not have a submeter. Its bill is whatever remains after subtracting Units 1–3 from the total utility bill.

```
Unit 4 Bill = Total Bill − (Unit 1 + Unit 2 + Unit 3)
```

> ⚠️ **Important**: If the submeter total exceeds the main bill, Unit 4 becomes negative. The system will display a warning — lower your rate or verify your readings.

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
- **Total VECO Bill** — The amount shown on your VECO statement
- **Rate per kWh** — Your current electricity rate
- **Previous / Current Readings** — Submeter readings for Units 1, 2, and 3
- Click **Calculate** or just type — results update automatically

### 3. Enter Water Bill (MCWD Tab)
- **Total MCWD Bill** — The amount shown on your MCWD statement
- **Rate per cu.m** — Your current water rate
- **Previous / Current Readings** — Submeter readings for Units 1, 2, and 3
- Click **Calculate** or just type — results update automatically

### 4. View Dashboard (Home Tab)
- See consolidated totals for all 4 units
- Electric + Water breakdown per unit
- Grand total at a glance

### 5. Print Report
Click the floating **🖨️ Print** button (bottom-right) to generate a clean, print-friendly report.

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

### Electric Calculation (VECO)

```
Unit 1: (10,320 − 10,250) × ₱11.50 = 70 kWh × ₱11.50 = ₱805.00
Unit 2: (8,510 − 8,450) × ₱11.50 = 60 kWh × ₱11.50 = ₱690.00
Unit 3: (12,150 − 12,000) × ₱11.50 = 150 kWh × ₱11.50 = ₱1,725.00
─────────────────────────────────────────────────────────────────
Submeter Total: ₱3,220.00
Unit 4 (Remaining): ₱4,850.00 − ₱3,220.00 = ₱1,630.00
```

### Water Calculation (MCWD)

```
Unit 1: (458 − 450) × ₱22.00 = 8 cu.m × ₱22.00 = ₱176.00
Unit 2: (326 − 320) × ₱22.00 = 6 cu.m × ₱22.00 = ₱132.00
Unit 3: (590 − 580) × ₱22.00 = 10 cu.m × ₱22.00 = ₱220.00
─────────────────────────────────────────────────────────────────
Submeter Total: ₱528.00
Unit 4 (Remaining): ₱980.00 − ₱528.00 = ₱452.00
```

### Dashboard Summary

| Unit | Electric | Water | Total |
|------|----------|-------|-------|
| Unit 1 | ₱805.00 | ₱176.00 | **₱981.00** |
| Unit 2 | ₱690.00 | ₱132.00 | **₱822.00** |
| Unit 3 | ₱1,725.00 | ₱220.00 | **₱1,945.00** |
| Unit 4 (Remaining) | ₱1,630.00 | ₱452.00 | **₱2,082.00** |
| **GRAND TOTAL** | **₱4,850.00** | **₱980.00** | **₱5,830.00** |

---

## 📐 Formulas

### Core Logic

```javascript
// For each submeter unit (1-3)
Usage    = Current_Reading − Previous_Reading
Bill     = Usage × Rate

// For master meter unit (4)
Subtotal = Bill₁ + Bill₂ + Bill₃
Unit4    = Total_Bill − Subtotal
```

### Validation Rules

| Condition | Result |
|-----------|--------|
| `Unit4 ≥ 0` | ✅ Normal — display in yellow/neutral |
| `Unit4 < 0` | ⚠️ Warning — submeters exceed total bill |
| `Usage < 0` | ❌ Invalid — current reading less than previous |

### Currency Formatting

All amounts are displayed in **Philippine Peso (₱)** with 2 decimal places:
```javascript
'₱' + amount.toLocaleString('en-PH', { minimumFractionDigits: 2 })
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
The home tab displays summary cards and a consolidated table of all units.

### Electric Tab
Input total bill, rate, and submeter readings. Unit 4 calculates automatically.

### Water Tab
Same logic as electric, configured for MCWD water billing.

### Print Preview
Clean, tabular output optimized for printing or saving as PDF.

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
<!-- Default electric total -->
<input type="number" id="elec-total" value="4850">

<!-- Default rate -->
<input type="number" id="elec-rate" value="11.50" step="0.01">
```

---

## 🛡️ Data Privacy

All calculations happen **entirely in your browser**. No data is sent to any server, stored in cookies, or written to localStorage. Your billing data stays on your machine.

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

## 🙋 FAQ

**Q: Why is Unit 4 showing a negative amount?**
> A: The combined submeter bills for Units 1–3 exceed the total bill. Lower the rate or double-check your readings.

**Q: Can I add more units?**
> A: Currently supports exactly 4 units (3 submetered + 1 master). To add more, modify the JavaScript loops (`for (let i = 1; i <= 3; i++)`) and add corresponding HTML inputs.

**Q: Does it save data between sessions?**
> A: No — refresh the page and data resets. This is by design for privacy. Use the Print feature to save a PDF record.

**Q: Can I use this for commercial buildings?**
> A: Yes, as long as your billing structure follows the "remaining balance" method for the master meter unit.

---

<p align="center">Built with ⚡ for hassle-free utility billing</p>
