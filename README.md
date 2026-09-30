# BITS Pilani Digital – Advanced Grading Console

A browser-based grading console built for the **BITS Digital CodeForge V1.0** challenge. An instructor uploads a marks file, picks a course, tunes grade boundaries while watching live analytics, and exports the final grades.

> **Note:** This is a prototype created for a challenge. It is **not** an official BITS Pilani grading tool.

**Live demo:** _add your deployed URL here_

## Features

- **Upload** marks as `.xlsx`, `.xls` or `.csv`
- **Strict validation** – exactly three columns; invalid rows are reported with row numbers
- **Auto round-up** of fractional marks (e.g. 81.2 → 82)
- **Course selection** with a unique, sorted course list
- **Live analytics** – histogram with bell curve, Min / Max / Average / Median, grade counts
- **Grade range editor** with validation (continuous ranges covering 0–100)
- **Result tables** – student grades, aggregations and grade distribution, updated live
- **Session timer** – starts when a course is selected, stops on finalize, resets on course change
- **Grading-time log** – time taken per course, with Excel download; resets on new file upload
- **Exports** on *Finalize & Download*:
  - `<Course>_grades.csv` – grades, aggregations and grade distribution
  - `<Course>_report.html` – shareable report with the chart, aggregations and grades (printable to PDF)
- Responsive layout and basic accessibility (ARIA labels, focus outlines, reduced-motion support)

## Input file format

| BITS ID  | Course   | Total Marks |
|----------|----------|-------------|
| 2024XXXX | Course A | 82          |
| 2024YYYY | Course A | 71.4        |

- Exactly three columns: **BITS ID**, **Course**, **Total Marks**
- Marks on a **0–100** scale; fractional marks are rounded **up** to the next whole number
- Do **not** include students who are to receive an **NC** grade

## Default grade ranges

| A | A- | B | B- | C | C- | D | E |
|---|----|---|----|---|----|---|---|
| 80–100 | 70–79 | 60–69 | 50–59 | 40–49 | 30–39 | 20–29 | 0–19 |

Ranges must be continuous, with **A ending at 100** and **E starting at 0**.

## How to use

1. Enter the **instructor name** (required).
2. Upload the **marks file**.
3. Select a **course**.
4. Review the analytics and adjust grade ranges if needed.
5. Click **Finalize & Download** to get the CSV and the report.
6. Use **Download Excel** in the time-log table for grading time per course.

## Run locally

No build step is needed.

```bash
git clone <your-repo-url>
cd <your-repo>
# open index.html in a browser
```

An internet connection is needed on first load because [SheetJS](https://sheetjs.com/) is loaded from a CDN.

## Deploy to GitHub Pages

1. Push `index.html` (and this README) to a GitHub repository.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select `main` and `/ (root)`, then save.
4. Your site will be available at `https://<username>.github.io/<repo>/`.

The app also works on Netlify or Vercel by deploying the folder as a static site.

## Tech stack

- HTML, CSS and vanilla JavaScript (single file)
- [SheetJS (xlsx)](https://sheetjs.com/) for reading Excel/CSV and writing the Excel time log
- Canvas API for the histogram and bell curve

## Project structure

```
.
├── index.html   # the complete application (logo embedded)
└── README.md
```

## Bug fixes and enhancements

The full bug fix log and the list of enhancements are in the submission document (`BITS_CodeForge_Submission.docx`).

## Known limitations

- The chart is delivered in a separate HTML report because a CSV cannot contain images.
- Marks must be on a 0–100 scale.
- Data is processed entirely in the browser; nothing is uploaded to a server.

## Author

Manish P Kharatamal
