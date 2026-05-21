# ANU Master of Philosophy (Applied Epidemiology) (MAE) Thesis Template

A LaTeX template for the Master of Philosophy (Applied Epidemiology) (MAE) program at the Australian National University (ANU). The MAE thesis has an unusual structure with four independent field research projects, each with its own reference list.

---

## About this template

This template was created by Holly Gibbons (MAE 2025) to help future MAE students get started with their thesis without having to build a LaTeX setup from scratch. The original code and structure are Holly's own work; Claude (Anthropic's AI assistant) was used to help develop and document the template.

If you run into any issues using this template, or if there is anything you would like to see added or improved, Holly would be very happy to hear from you: hollyfgibbons@outlook.com

Best of luck with your thesis!!!!!!!!!!!

---

## Project structure

```
├── main.tex                             # Master document — start here
├── preamble.tex                         # All packages, fonts, and formatting
├── abbreviations.tex                    # Abbreviation definitions
├── reference_library.bib                # BibTeX bibliography
│
├── front_matter/
│   ├── abstract.tex
│   ├── acknowledgement.tex
│   ├── abbreviations_static.tex         # Printed abbreviations list (auto-generated)
│   └── originality_statement.tex
│
├── titlepage/
│   ├── titlepage.tex
│   └── anu-logo-colour.pdf
│
├── experience/experience.tex            # Ch 1: Placement overview and competencies
├── data_analysis/data_analysis.tex      # Ch 2: Project 1 — Data analysis
├── surveillance/surveillance.tex        # Ch 3: Project 2 — Surveillance system
├── epistudy/epistudy.tex                # Ch 4: Project 3 — Epidemiological study
├── outbreak/outbreak.tex                # Ch 5: Project 4 — Outbreak investigation
└── teaching/teaching.tex                # Ch 6: Teaching and field activities
```

---

## Key features

- **Per-chapter reference lists** — each chapter ends with its own numbered reference list, using `biblatex` with `refsection=chapter`. Citation numbers restart at [1] in each chapter.
  
- **Local TOC, list of figures, and list of tables** per chapter, using `etoc`.

- **Automatic abbreviation expansion** — abbreviations expand in full on first use per chapter (e.g. "polymerase chain reaction (PCR)") using `glossaries-extra`.

- **Vancouver-style citations** — superscript numbers, sorted by order of appearance.

- **ANU-compliant formatting** — Helvetica font, 2.5 cm margins, A4 paper, originality statement.

---

## Prerequisites

| Tool | Purpose |
|------|---------|
| pdfLaTeX | Main compiler |
| Biber | Bibliography processor (replaces BibTeX) |
| latexmk | Build orchestration (optional, recommended locally) |

All of these are included in TeX Live and MiKTeX distributions.

---

## Using on Overleaf

1. Download this repository as a ZIP file (GitHub: **Code → Download ZIP**)
2. In Overleaf: **New Project → Upload Project** → select the ZIP
3. Open **Menu** (top left) → **Compiler** → select **pdfLaTeX**
4. Click **Recompile**

Overleaf runs Biber automatically — no extra configuration needed.

---

## Using locally

With `latexmk` installed, run from the project root:

```bash
latexmk main.tex
```

The included `latexmkrc` file tells latexmk to use pdfLaTeX and Biber automatically.

To clean auxiliary files:

```bash
latexmk -C
```

---

## Zotero integration

### Option A — One-time export

1. In Zotero, select your library or a collection
2. **File → Export Library** (or right-click a collection → **Export Collection**)
3. Format: **Better BibLaTeX** *(requires the Better BibTeX plugin — see Option B)*
4. Save as `reference_library.bib` and replace the existing file in your project
5. In Overleaf: upload the new `.bib` via the file tree on the left

### Option B — Continuous sync (recommended)

1. Install the [Better BibTeX plugin](https://retorque.re/zotero-better-bibtex/) for Zotero
2. Right-click your Zotero library or collection → **Export Collection**
   - Format: **Better BibLaTeX**
   - Tick **Keep updated**
3. Zotero keeps the exported `.bib` file up to date on your computer automatically
4. Re-upload to Overleaf whenever you add new references

### Option C — Overleaf native Zotero sync (not recommended - it's not flexible to format changes)

In Overleaf: **Menu → Sync → Zotero**

This requires a linked Zotero account (configured under Overleaf account settings). Overleaf imports your entire Zotero library as a `.bib` file automatically.

### Citing references

```latex
Text here.\cite{author_keyword_year}   % → superscript number in text
```

The citation key (e.g. `smith_title_2024`) is shown in the **Citation Key** column in Zotero (visible after installing Better BibTeX).

---

## Customising the template

### Step 1 — Replace placeholder text

Search for the following strings and replace them throughout the project:

| Placeholder | File(s) |
|---|---|
| `TITLE OF THESIS` | `titlepage/titlepage.tex` |
| `THESIS TITLE` | `preamble.tex` (`pdftitle`) |
| `YOUR FULL NAME` | `preamble.tex`, originality environment in `preamble.tex` |
| `AUTHOR FULL NAME` | `titlepage/titlepage.tex` |
| `YEAR -- YEAR` | `titlepage/titlepage.tex` |
| `DATE OF SUBMISSION` | `preamble.tex`, originality environment |
| `PLACEMENT UNIT / DEPARTMENT` | `titlepage/titlepage.tex`, `front_matter/abstract.tex` |
| `Dr SUPERVISOR NAME` | `titlepage/titlepage.tex` |
| `PROJECT TITLE 1–4` | `data_analysis/data_analysis.tex` through `outbreak/outbreak.tex` |

### Step 2 — Add your placement logo

In `titlepage/titlepage.tex`, replace the TikZ placeholder block with:

```latex
\includegraphics[height=3.8cm]{titlepage/placement_logo.png}
```

Upload your logo file to the `titlepage/` folder.

### Step 3 — Add your abbreviations

In `abbreviations.tex`:

```latex
\newabbreviation{KEY}{SHORT}{Long form description}
```

Use in text with `\gls{KEY}`. First use per chapter expands to "Long form description (SHORT)"; subsequent uses show "SHORT" only. The printed abbreviations list in the front matter is generated automatically — no manual updates needed.

For plurals:

```latex
\newabbreviation[
  longplural  = {long form plurals},
  shortplural = {SHORTs}
]{KEY}{SHORT}{Long form singular}
```

### Step 4 — Add your references

Replace `reference_library.bib` with your Zotero export (see Zotero integration above).

---

## Per-chapter reference lists

Each chapter file ends with:

```latex
\clearpage
\addcontentsline{toc}{section}{References}
\printbibliography[heading=subbibliography, title={References}]
```

Only references cited within that chapter appear in that chapter's list. Numbers restart at [1] in each chapter.

---

## Reordering chapters

In `main.tex`, reorder the `\include` lines — all numbering updates automatically:

```latex
\include{experience/experience}
\include{data_analysis/data_analysis}
\include{surveillance/surveillance}
\include{epistudy/epistudy}
\include{outbreak/outbreak}
\include{teaching/teaching}
```

---

## Adding figures and tables

Place images in the relevant chapter folder (e.g. `data_analysis/figures/`). Include them with:

```latex
\begin{figure}[H]
    \centering
    \includegraphics[width=0.85\textwidth]{data_analysis/figures/my_figure.png}
    \caption{Caption text.}
    \label{fig:my_figure}
\end{figure}
```

Figures exported from R, Stata, or SPSS can be included as PNG or PDF files directly.

---
