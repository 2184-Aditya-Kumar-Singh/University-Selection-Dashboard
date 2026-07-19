# 🎓 Masters Abroad — University Explorer Dashboard

An interactive Power BI dashboard for exploring 151 postgraduate Computer Science programmes across 12 European countries — built end-to-end to practice data modeling, DAX, and dashboard design on a real-world, multi-source dataset.

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)

<table>
<tr>
<td width="50%"><img src="https://github.com/user-attachments/assets/921411e4-e09f-4b05-bcb2-9737da85a3a8" width="100%" alt="Dashboard Overview"/></td>
<td width="50%"><img src="https://github.com/user-attachments/assets/8dfce2f4-01cd-42d7-934e-35408e9571eb" width="100%" alt="Spotlight Panel"/></td>
</tr>
</table>

---

## 📖 Overview

This dashboard lets you browse **151 verified university programmes across 12 European countries**, filter by country, search for a specific university, and drill into a full "dossier" view showing rankings, cost breakdown, admission requirements, and scholarship info for any selected programme.

The project's goal was to take a messy, multi-source dataset (rankings, tuition, admissions data scraped and verified from official university sources) and turn it into a clean, fully interactive analytics tool — covering everything from data cleaning and modeling to writing dynamic DAX measures and designing a custom dark-themed UI.

---

## ✨ Features

- **Country filter rail** — click any of 12 countries to instantly narrow the list
- **Live search** — type-ahead university search with no need to press Enter
- **Dynamic spotlight panel** — click (or just filter to) a university to see:
  - QS World Ranking badge
  - Degree, duration, employment rate, acceptance rate
  - Cost of attendance donut chart (Tuition & Fees / Living Costs / Health Insurance / Total)
  - Full admission requirements (IELTS, CGPA, GRE, GMAT, APS, MOI, application deadline)
  - PR pathway and visa difficulty
- **Smart defaults** — selecting a country with no specific university chosen automatically shows that country's top-ranked programme
- **KPI ribbon** — live counts for universities shown, average tuition, average QS rank, and cities covered

---

## 🗂️ Data

The dataset (`Masters_Abroad_2029_AllUniversities.xlsx`) covers:

| Country | Programmes |
|---|---|
| Germany | 27 |
| Italy | 22 |
| France | 18 |
| Netherlands | 13 |
| Sweden | 12 |
| Belgium | 10 |
| Finland | 10 |
| Switzerland | 9 |
| Austria | 8 |
| Ireland | 8 |
| Denmark | 7 |
| Norway | 7 |
| **Total** | **151** |

Each row includes: QS/THE ranking, faculty & department, degree & duration, language & MOI policy, IELTS/TOEFL/GRE/GMAT/APS requirements, application deadlines, tuition & living cost breakdown, total cost (EUR & INR), scholarships, visa difficulty, PR opportunity, and free-text notes on why each programme fits and what to watch for.

> **Note on data accuracy:** rankings and tuition figures were verified via official university sources and QS World Rankings where possible. Where a specific figure (e.g. QS rank, average graduate salary, employment rate) could not be confirmed, the cell is intentionally left blank or marked `Not published` rather than estimated — **always confirm tuition, deadlines, and requirements on the official university website before applying**, as these change year to year.

---

## 🛠️ Tech Stack

- **Power BI Desktop** — data model, DAX measures, report visuals
- **DAX** — dynamic "spotlight" pattern using `LOOKUPVALUE` + a custom `Effective University` fallback measure, so the detail panel always shows relevant data even when only a country (not a specific university) is selected
- **Excel** — source dataset, cleaned and structured for import

---

## 🚀 Getting Started

### Option 1 — Open in Power BI Desktop (recommended)
1. Download [Power BI Desktop](https://www.microsoft.com/en-us/power-platform/products/power-bi/desktop) (free).
2. Clone this repo or download the `.pbix` file.
3. Open `MastersAbroadDashboard.pbix` — no setup needed, data is embedded.

### Option 2 — Rebuild from source data
1. Open `Masters_Abroad_2029_AllUniversities.xlsx` in Power BI Desktop via **Get Data → Excel**.
2. Follow the data cleaning + DAX measures outlined in [`/docs`](./docs) *(if included)*.

---

## 📊 Key DAX Concepts Used

- **Dynamic single-value fallback**: `Effective University` resolves to either the clicked university or the top-ranked one in the current filter context, so cards never go blank when only a country is selected.
- **Disconnected lookup tables**: a small `Requirement Fields` table drives a `SWITCH`-based measure to render admission requirements as label/value rows without hardcoding 8 separate visuals.
- **Text-safe currency formatting**: `"€" & FORMAT(value, "#,##0")` pattern used for display columns needing an inline currency symbol without losing sort/format control on the underlying numeric measures.

---

## 📄 License

This project is for educational and portfolio use. University data is aggregated from public sources and some estimated — verify all figures independently before relying on them for decisions.

---

## 🙋 About

A self-directed project built to practice end-to-end BI development: sourcing and cleaning a real-world dataset, designing a data model, writing DAX for dynamic filtering logic, and building a polished, interactive dashboard from scratch in Power BI. Feedback and suggestions welcome — feel free to open an issue.
