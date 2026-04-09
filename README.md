# §199A QBI Deduction Calculator

An interactive, single-page calculator for the **Section 199A Qualified Business Income (QBI) Deduction**, built for use by financial advisors at Rose Financial Management. No installation or backend required — open `index.html` in any modern browser.

---

## What It Does

The calculator walks through the full §199A deduction logic for a given client, including:

- **Below-threshold** filers (full 20% deduction, no wage test)
- **Phase-in range** filers (partial deduction with phased wage limitation)
- **Above-threshold** filers (full wage/property limitation applies)
- **SSTB vs. non-SSTB** business classification (specified service trades or businesses face stricter limits above the threshold)
- **REIT dividends and PTP income** (added directly to the §199A deduction pool)

The result is the client's estimated §199A deduction displayed in real time as you enter inputs.

---

## How to Use

### 1. Enter Client Inputs

Fill in the fields on the left panel:

| Field | Where to Find It |
|---|---|
| Taxable Income | Form 1040, Line 15 |
| QBI from Business | Schedule K-1 / Schedule C |
| W-2 Wages Paid | W-2s issued by the business |
| Qualified Property (UBIA) | Business records / cost basis |
| REIT Dividends | Form 1099-DIV, Box 5 |
| PTP Income | Schedule K-1 (publicly traded partnerships) |

All dollar fields accept formatted input (e.g., `$394,600`) and strip to raw numbers for calculation automatically.

### 2. Set Filing Status and Business Type

- **Filing Status**: Married Filing Jointly or Other (Single, MFS, HOH)
- **Business Type**: Non-SSTB (most businesses) or SSTB (law, accounting, consulting, health, financial services, etc.)

### 3. Select Tax Year

Use the **2025 / 2026** toggle at the top to switch between tax year thresholds. The deduction limits, phase-in ranges, and all calculations update instantly.

> **2026 thresholds** reflect the IRS-published phase-in ranges: MFJ $403,500–$553,500; Other $201,750–$276,750. Note the 2026 phase-in ranges are wider than prior years ($150,000 MFJ / $75,000 Other).

### 4. Read the Results

- **Deduction Estimate** — the calculated §199A deduction
- **Threshold Bar** — shows where the client falls relative to phase-in limits
- **Interactive Flowchart** — highlights the exact decision path taken through the §199A rules
- **Calculation Breakdown** — step-by-step math with labeled line items
- **What Could Change This** — expandable sensitivity scenarios (W-2 wages, qualified property, Roth conversions, retirement contributions) with advisor explanations and IRS references

### 5. Export to PDF

Click **Export PDF** to generate a one-page client-ready summary including:
- Client name and date
- All input values
- Deduction result and verdict
- Decision path and calculation steps
- Sensitivity analysis table

Prepared-by line reads: *Prepared by [Advisor Name] | Rose Financial Management | rosefinancialmanagement.com*

---

## Editing Threshold Constants

Click the **Edit** button (pencil icon, next to the year toggle) to open the **Threshold Constants Editor**. This modal lets you:

- Edit the label and dollar thresholds for either tax year
- Changes are saved to **localStorage** (per-browser, per-device — not global)
- **Reset to Defaults** restores the built-in values
- Link to the IRS source (Rev. Proc.) is provided in the modal for reference

> Changes made here are local only. To update thresholds for all users, edit `DEFAULT_YEAR_CONFIG` in `index.html` and redeploy.

---

## Hosting on GitHub Pages

1. Push `index.html` to a public GitHub repository
2. Go to **Settings → Pages** → Deploy from branch `main`, folder `/`
3. Your URL: `https://yourusername.github.io/repo-name/`

Any changes pushed to the repo immediately update the live site for all users.

---

## Technical Notes

- **Single file**: All logic, styles, and markup live in `index.html` — no build step, no npm, no backend
- **Dependencies (CDN)**: Tailwind CSS, html2pdf.js, Google Fonts (Inter, Cormorant Garamond)
- **Persistence**: Threshold edits use `localStorage`; no data is sent to any server
- **Offline**: Works fully offline once the page has loaded (CDN assets cached by browser)

---

## Disclaimer

This tool is intended for **informational and planning purposes only**. It is not tax or legal advice. Calculations are estimates based on user-provided inputs and published IRS thresholds. Always verify results with a qualified tax professional and the official IRS guidance for the applicable tax year.
