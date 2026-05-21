# ANU MAE thesis template

A LaTeX template for the Master of Philosophy (Applied Epidemiology) (MAE) program at the Australian National University (ANU). The MAE thesis has an unusual structure with four independent field research projects, each with its own reference list.

This template was created by me (Holly Gibbons, MAE 2025), to help future MAE students with formatting, allowing them to focus more on their projects. It will enable Scholars to get started on their thesis without needing to build a LaTeX setup from scratch. The original code and structure are my own work, developed for my own thesis; Claude (Anthropic's AI assistant) was used to assist in developing and documenting the template.

If you run into any issues using this template, or if there is anything you would like to see added or improved, I would be very happy to hear from you: hollyfgibbons@outlook.com

Best of luck with your thesis!!!!!!!!!!!

---

## What is LaTeX?
### A guide for MAE students (no LaTeX experience required)

LaTeX (pronounced "lah-tech") is a document preparation system. Instead of formatting as you type (like Word), you write your content in plain text files (`.tex` files) and LaTeX automatically handles all the formatting, including:
* Numbering chapters, figures, tables, and references
* Building the table of contents
* Generating reference lists at the end of each chapter

**The key benefits for the MAE thesis:**
* References for each chapter are generated automatically
* Figures and tables are numbered and listed automatically, with updates applied when changes are made
* The table of contents updates automatically as content is added
* A list of abbreviations is generated automatically
* Cross-referencing and hyperlinks remain functional when compiled as a PDF
* No need to combine multiple PDFs or Microsoft Word documents to produce a complete thesis

You write your content in `.tex` files using Overleaf (or a local text editor). When you click **Recompile** in Overleaf, LaTeX processes all the files and produces a PDF.

---

## Getting started

The template can be downloaded and used in either Overleaf (online) or locally on your computer. Please see the comparison table below to help decide which one is best for you.

| Overleaf | Locally |
|----------|--------|
| Runs in your browser | Runs on your computer |
| No software installation required | Requires installing a LaTeX distribution and tools |
| Compilation happens on Overleaf servers | Compilation happens locally on your machine |
| Easy setup and quick to get started | More setup required initially |
| Built-in collaboration and sharing | Collaboration requires external tools (e.g., Git) |
| Limited control over environment | Full control over packages and build process |
| Requires internet connection | Works offline |
| Suitable for beginners | Better for advanced users or large projects |

### How to open the template in Overleaf
1. Download this repository as a ZIP file (*GitHub → Code → Download ZIP*)
2. In Overleaf: *New Project → Upload Project* → select the ZIP
3. Open *Menu* (top left) → *Compiler* → select **pdfLaTeX**
4. Click **Recompile**

---

> **Before you write anything in Overleaf**
>
> Check with your field supervisor that you have permission to use a cloud-based platform such as Overleaf before uploading any thesis content.
>
> Data sharing and confidentiality obligations can vary between placements. As an example of one approach, my placement agreed that I could use Overleaf provided that:
> 1. only tables and figures were uploaded (no raw data) and
> 2. any content written or uploaded was approved by my supervisor before being added to the project
>
> Your placement may have different requirements. If in doubt, ask your field supervisor before you begin.

---

### How to open the template locally
1. Install a LaTeX distribution (e.g., TeX Live or MikTeX)
2. Install package `latexmk`
3. Create a new .tex file (if using MikTex select the image of the notepad with a 'T'
4. From the project root, run:
```bash
latexmk main.tex
```
3. The included `latexmkrc` file configures `latexmk` to use pdfLaTeX and Biber automatically

4. To clean auxiliary files:
```bash
latexmk -C
```

---


## Setting up Zotero integration

This step will allow you to instantly cite references as you start writing in your chapters. I have outlined two options to set up integration with Zotero. I do not recommend using the automatic integration between Zotero and Overleaf because the data is much harder to format.

### Option A: One-time export
1. In Zotero, select your library or a collection
2. **File → Export Library** (or right-click a collection → **Export Collection**)
3. Format: **Better BibLaTeX** *(requires the Better BibTeX plugin — see Option B)*
4. Save as `reference_library.bib` and replace the existing file in your project
5. In Overleaf: upload the new `.bib` via the file tree on the left

### Option B: Continuous sync (recommended)
1. Install the [Better BibTeX plugin](https://retorque.re/zotero-better-bibtex/) for Zotero
2. Right-click your Zotero library or collection → **Export Collection**
   - Format: **Better BibLaTeX**
   - Tick **Keep updated**
3. Zotero keeps the exported `.bib` file up to date on your computer automatically
4. Re-upload to Overleaf whenever you add new references

### Citing references

```latex
Text here.\cite{author_keyword_year}   % → superscript number in text
```

The citation key (e.g. `smith_title_2024`) is shown in the **Citation Key** column in Zotero (visible after installing Better BibTeX).

---

## Outline of template structure

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

## Customising the template

### Step 1: Fill in your personal details

#### Thesis title, name, and supervisors

Open `titlepage/titlepage.tex` and replace the placeholder text:

| Find this | Replace with |
|---|---|
| `TITLE OF THESIS` | Your thesis title |
| `AUTHOR FULL NAME` | Your full name |
| `YEAR -- YEAR` | e.g. `2024 -- 2026` |
| `PLACEMENT UNIT,` | Your unit name |
| `PLACEMENT DEPARTMENT` | Your department/organisation |
| `Dr SUPERVISOR NAME` | Your academic supervisor |
| `Ms SUPERVISOR NAME 1` | Your first field supervisor |
| `Mr SUPERVISOR NAME 2` | Your second field supervisor |

#### PDF properties and originality statement

Open `preamble.tex` and search for the section labelled
`% ===================== Hyperlinks =====================`
Update:
- `THESIS TITLE` → your thesis title
- `YOUR FULL NAME` → your name
- Add relevant keywords separated by commas

Then search for
`% ===================== Front Matter Environments =====================`
Update:
- `YOUR FULL NAME` → your name
- `DATE OF SUBMISSION` → e.g. `1st~October~2025`
  *(The `~` symbol prevents a line break between the day and month — keep it)*

#### Field placement logo

Upload your placement organisation's logo to the `titlepage/` folder (as a `.png` or `.pdf`).

In `titlepage/titlepage.tex`, find the comment `% Replace the block below with your placement logo` and replace the TikZ grey-box placeholder block with:

```latex
\includegraphics[height=3.8cm]{titlepage/your_logo_filename.png}
```

---

### Step 2: Choose your document format

ANU requires different margins depending on how your thesis will be submitted. The template defaults to the digital submission format. If you need to produce a print-ready version, change **one line in each of two files** — keeping the option number the same in both.

**In `main.tex`**, activate the correct `\documentclass` option:

| Option | When to use |
|---|---|
| Option 1 (default) | Digital submission — all margins 2.5 cm |
| Option 2 | Hard copy, single-sided printing — binding margin 4 cm |
| Option 3 | Hard copy, double-sided printing — inner binding margin 4 cm |

**In `preamble.tex`**, activate the matching `\usepackage{geometry}` option (same option number).

To activate an option, remove the `%` at the start of that line, and add `%` to the start of the currently active line.

---

### Step 3: Name your chapters

Open each chapter file and replace `PROJECT TITLE 1` (or 2, 3, 4) with your actual project title:

| File | Replace |
|---|---|
| `data_analysis/data_analysis.tex` | `PROJECT TITLE 1` → your data analysis project title |
| `surveillance/surveillance.tex` | `PROJECT TITLE 2` → your surveillance project title |
| `epistudy/epistudy.tex` | `PROJECT TITLE 3` → your epidemiological study title |
| `outbreak/outbreak.tex` | `PROJECT TITLE 4` → your outbreak investigation title |

---

### Step 4: Write your content

Each chapter is a separate `.tex` file. Open the file for the chapter you want to write and add your text below the relevant section heading.

#### How text works in LaTeX

- Type normally — a blank line between paragraphs creates a new paragraph
- No need to indent paragraphs (the template handles this)
- **Bold text:** `\textbf{your text}`
- *Italic text:* `\textit{your text}`

#### Special characters

These characters have special meaning in LaTeX. If you need to type them in your text, use the version in the right column:

| Character | How to type it |
|---|---|
| `%` (percent) | `\%` |
| `&` (ampersand) | `\&` |
| `$` (dollar sign) | `\$` |
| `_` (underscore) | `\_` |
| `#` (hash) | `\#` |
| `--` (en-dash, for ranges) | `--` |
| `---` (em-dash) | `---` |
| `''` (open quote) | ` `` ` (two backticks) |
| `''` (close quote) | `''` (two apostrophes) |

---

### Step 5: Add a figure

A figure is any image — an epicurve, a map, a chart exported from R/Stata/SPSS/Excel.

**Save your image file** (as `.png` or `.pdf`) in the relevant chapter folder, e.g. `data_analysis/figures/`.

**Then add this block** in your chapter where you want the figure to appear:

```latex
\begin{figure}[H]
    \centering
    \includegraphics[width=0.85\textwidth]{data_analysis/figures/my_figure.png}
    \caption{Weekly case counts by symptom onset date, Location, Month Year.}
    \label{fig:epicurve}
\end{figure}
```

**What each part means:**

| Part | What it does |
|---|---|
| `[H]` | Places the figure **H**ere — at this exact position in the text |
| `\centering` | Centres the image on the page |
| `width=0.85\textwidth` | Sets the image width to 85% of the text width — adjust as needed |
| `{data_analysis/figures/my_figure.png}` | The path to your image file |
| `\caption{...}` | The caption that appears **below** the figure |
| `\label{fig:epicurve}` | A unique name for cross-referencing — **must start with `fig:`** |

**To refer to the figure in your text:**

```latex
As shown in \cref{fig:epicurve}, cases peaked in week 3.
```

This automatically produces: "As shown in Figure 1, cases peaked in week 3." — the number updates automatically if you add or move figures.

> **Tip:** Always reference every figure in your text before it appears. A figure should never appear without being mentioned in the text.

---

### Step 6: Add a table

The simplest approach is to export your table from R, Stata, or Excel as a `.png` image and include it like a figure — but inside a `table` environment so LaTeX treats it as a table (numbering it in the list of tables).

**Save your table image** in the relevant chapter folder, e.g. `data_analysis/tables/`.

```latex
\begin{table}[H]
    \caption{Number of cases by age group, Location, Year.}
    \label{tab:age_groups}
    \centering
    \begin{tabular}{c}
        \includegraphics[width=0.95\textwidth]{data_analysis/tables/age_table.png}
    \end{tabular}
\end{table}
```

**Key differences from figures:**

| | Tables | Figures |
|---|---|---|
| Caption position | **Above** the image | **Below** the image |
| Label prefix | Must start with `tab:` | Must start with `fig:` |
| Typical width | `0.95\textwidth` | `0.85\textwidth` |

**To refer to the table in your text:**

```latex
\cref{tab:age_groups} shows the distribution of cases by age group.
```

This produces: "Table 1 shows the distribution of cases by age group."

> **Tip:** `\cref{}` (lowercase c) produces "Table 1" or "Figure 1". `\Cref{}` (uppercase C) produces the same but capitalised — use `\Cref{}` at the start of a sentence.

---

### Step 7: Abbreviations

The abbreviations system works in two places that are connected automatically:

- **`abbreviations.tex`** — where you define abbreviations. This drives both the in-text expansion and the printed front matter list.
- **`front_matter/abbreviations_static.tex`** — the abbreviations page printed in the thesis front matter. This generates itself automatically from your `\gls{}` usage — you do not need to edit it.

#### Defining an abbreviation

Open `abbreviations.tex` and add a line:

```latex
\newabbreviation{WHO}{WHO}{World Health Organization}
```

The three parts are:
1. `{WHO}` — the **key** (what you type in `\gls{WHO}` — must be unique, no spaces)
2. `{WHO}` — the **short form** (what appears after first use, e.g. "WHO")
3. `{World Health Organization}` — the **long form** (what appears on first use)

#### Using an abbreviation in your text

Type `\gls{KEY}` wherever you want the abbreviation to appear:

```latex
Data were submitted to the \gls{WHO} surveillance system.
```

- **First use in the chapter:** "Data were submitted to the World Health Organization (WHO) surveillance system."
- **All subsequent uses:** "Data were submitted to the WHO surveillance system."

Abbreviation tracking resets automatically at the start of each chapter, so each chapter re-expands abbreviations on first use. This is handled by `\glsresetall[abbreviations]` in each chapter file — do not remove those lines.

#### For plural forms

```latex
\glspl{RACF}
```

To define a plural, use this format in `abbreviations.tex`:

```latex
\newabbreviation[
  longplural  = {residential aged care facilities},
  shortplural = {RACFs}
]{RACF}{RACF}{residential aged care facility}
```

#### The front matter list

The abbreviations page in the front matter is generated automatically. It lists — in alphabetical order, in the same visual style as the rest of the front matter — every abbreviation you used with `\gls{}` anywhere in your thesis. Abbreviations defined in `abbreviations.tex` but never used with `\gls{}` are excluded.

**You do not need to edit `front_matter/abbreviations_static.tex`.** Recompile your document (twice if needed in Overleaf) and the list updates itself.

> **If an abbreviation is missing from the front matter list**, check that you used `\gls{KEY}` in your text — abbreviations typed manually (not via `\gls{}`) are not tracked.

---

### Step 8: Cite a reference

#### Step 8a — Add the reference to your `.bib` file

The easiest way is to export from Zotero (see [Zotero integration](#zotero-integration) above). If adding manually, open `reference_library.bib` and add an entry:

**Journal article:**
```bibtex
@article{smith_article_title_2024,
  title        = {Title of the article},
  author       = {Smith, John and Jones, Mary},
  journaltitle = {Journal of Applied Epidemiology},
  volume       = {10},
  number       = {2},
  pages        = {100--110},
  date         = {2024},
  doi          = {10.0000/example},
}
```

**Website:**
```bibtex
@online{who_webpage_2025,
  title   = {Title of the webpage},
  author  = {{World Health Organization}},
  url     = {https://www.who.int/example},
  urldate = {2025-06-01},
  date    = {2025-01-01},
}
```

> **Tip:** For organisation authors (not a person), wrap the name in double braces: `{{World Health Organization}}` — this stops LaTeX treating the first word as a first name.

The citation key is the first item after the `@article{` or `@online{` — in the example above it is `smith_article_title_2024`. You choose the key; the convention is `lastname_word_year`.

#### Step 8b — Cite in your text

```latex
Blood lead levels above 5 µg/dL are considered elevated.\cite{smith_article_title_2024}
```

This inserts a superscript number (e.g. ¹) in your text. The full reference appears automatically in the **References** section at the end of that chapter — you do not need to do anything else.

**Cite multiple references at once:**

```latex
This finding has been reported across several studies.\cite{smith_2024,jones_2023,taylor_2022}
```

This inserts compressed superscripts like ¹⁻³.

---

### Step 9: Cross-reference a section or appendix

You can reference any section, figure, table, or appendix anywhere in the document:

```latex
\cref{chap:project_1}    →  "Chapter 2"
\cref{fig:epicurve}      →  "Figure 1"
\cref{tab:age_groups}    →  "Table 1"
\cref{app:lay_summary}   →  "Appendix A"
```

The label must be defined in the relevant file with `\label{...}`. Each chapter file already has its label defined at the top (e.g. `\label{chap:project_1}`).

---

### Step 10: Remove empty local lists

At the top of each chapter there is a local list of tables and a local list of figures. If a chapter has no tables or figures, these pages will be blank and should be removed.

**To remove an empty local list**, find these lines near the top of the chapter file and delete them (or add a `%` at the start of each line to comment them out):

```latex
\locallistoftables    % remove if this chapter has no tables
\locallistoffigures   % remove if this chapter has no figures
\clearpage            % remove this \clearpage if you removed both lists above
```

---

### Step 11: Add or modify sections

Each chapter uses `\section{}`, `\subsection{}`, and `\subsubsection{}` to organise content:

```latex
\section{Methods}
\subsection{Study population}
\subsubsection{Inclusion criteria}
```

LaTeX numbers them automatically. To add a new section, copy a `\section{}` line and change the title. To remove a section, delete it.

Sections at the paragraph level (for detailed sub-points) use:

```latex
\paragraph*{Confirmed case}
% text here
\paragraph*{Probable case}
% text here
```

The `*` means the paragraph heading is not numbered.

---

### Step 12: Add an appendix to a chapter

Each chapter has a `\begin{subappendices}...\end{subappendices}` block at the end. Inside it, each appendix is a `\section{}`.

PDF appendices (e.g. a factsheet, presentation slides, or manuscript) are included one page at a time using `\includegraphics`. Add one line per page:

```latex
\begin{subappendices}

\clearpage
\section{Lay summary}
\label{app:lay_summary}
\nopagebreak
\centering
\includegraphics[page=1,width=\textwidth]{data_analysis/appendices/factsheet.pdf}
\clearpage
\includegraphics[page=2,width=\textwidth]{data_analysis/appendices/factsheet.pdf}
% Add more lines for additional pages
\RaggedRight

\end{subappendices}
```

Upload your file to the chapter's `appendices/` subfolder before compiling. Adjust the number of `\includegraphics` lines to match the number of pages in your PDF.

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

In `main.tex`, simply reorder the `\include` lines — all numbering updates automatically:

```latex
\include{experience/experience}
\include{data_analysis/data_analysis}
\include{surveillance/surveillance}
\include{epistudy/epistudy}
\include{outbreak/outbreak}
\include{teaching/teaching}
```

---

## Troubleshooting

| Problem | Likely cause | Solution |
|---|---|---|
| Red error in Overleaf | Syntax error (missing `}` or `\end{}`) | Click the log icon — it shows the file and line number |
| `Undefined control sequence` | Misspelled command | Check spelling — LaTeX is case-sensitive |
| `Citation ... undefined` warning | Key in `\cite{}` does not match `.bib` file | Check the key matches exactly (case-sensitive) |
| Figure or table number is wrong | Another figure was added or removed | Click Recompile twice — numbers auto-update |
| Abbreviation does not expand | Not defined in `abbreviations.tex` | Add the `\newabbreviation{}` entry |
| Abbreviation missing from front matter list | Used manually in text, not via `\gls{}` | Replace the manual text with `\gls{KEY}` |
| Text runs off the page | Very long unbreakable word or URL | Wrap in `\url{}` or add `\-` to suggest a hyphen point |
| Blank page between chapters | Normal for double-sided layout | Expected — leave it; or switch to Option 1 or 2 in `main.tex` and `preamble.tex` |
| Overleaf times out on compile | Very large PDF appendices | Compress your appendix PDFs before uploading |

---

## Quick reference

| Task | Command |
|---|---|
| Bold text | `\textbf{text}` |
| Italic text | `\textit{text}` |
| New page | `\clearpage` |
| Use abbreviation | `\gls{KEY}` |
| Use abbreviation (plural) | `\glspl{KEY}` |
| In-text citation | `\cite{key}` |
| Cross-reference | `\cref{label}` |
| Cross-reference (sentence start) | `\Cref{label}` |
| Label a figure | `\label{fig:name}` inside `\begin{figure}` |
| Label a table | `\label{tab:name}` inside `\begin{table}` |
| Label a section | `\label{sec:name}` after `\section{}` |
| Comment a line | Add `%` at the start of the line |
| En-dash (number ranges) | `--` (e.g. `2020--2024`) |
| Em-dash | `---` |
| Non-breaking space | `~` (e.g. `Figure~1`) |
