# LaTeX Formatting Rules

## University Text Assignments

- Default storage location for LaTeX assignment artifacts: `tasks/year_2/science_projects_kovalenko`, unless the user specifies another folder.
- Keep both source `.tex` and compiled `.pdf` files.
- Default reusable template: `templates/latex/ukrainian-university-assignment-template.tex`.
- Default document class for Ukrainian university text assignments: `extarticle` with `14pt` and `a4paper`.
- Default font: Times New Roman through `fontspec`.
- Prefer `XeLaTeX` or `LuaLaTeX` for Ukrainian text and Unicode formulas.
- Use Ukrainian as the main language unless the user asks for another language.
- Do not add extra vertical spacing between paragraphs; set `\parskip` to `0pt`.
- Use a first-line paragraph indent, typically `1.25cm`, unless the assignment requires another style.
- Use page margins: top `2cm`, bottom `2cm`, left `2.5cm`, right `1cm`.
- Align list markers at `1.25cm`.
- Format section and paragraph titles in bold.
- Add one blank line of vertical space between major sections. In LaTeX, use a controlled section macro rather than manually inserting repeated empty lines.
- Use `amsmath` for displayed equations and put important formulas in `\[ ... \]`.
- Use semantic math notation where possible, for example `D_{\mathrm{ray}}(t)` instead of plain text `D_ray(t)`.
- Keep English technical terms in parentheses after Ukrainian terms when useful for clarity.
- For dissertation-related assignments, connect the content to the official PhD topic: `Методи та програмні засоби рельєфного текстурування для систем формування тривимірних графічних зображень`.
- If PDF compilation is required, compile from the `.tex` source with a real LaTeX engine. If no LaTeX engine is available, state the limitation and do not present a non-LaTeX export as a true LaTeX compilation.

## Dissertation-Oriented Defaults

- Use the current Ukrainian dissertation formatting baseline from the Ministry of Education and Science of Ukraine Order No. 40 dated 2017-01-12, as amended by Order No. 759 dated 2019-05-31.
- For full dissertation drafts, use A4 paper, Times New Roman, 14 pt, and 1.5 line spacing unless the university, supervisor, or dissertation council provides a stricter template.
- Recommended page margins for dissertation-style documents and current university assignments: left `25mm`, right `10mm`, top `20mm`, bottom `20mm`.
- A dissertation may be prepared in LaTeX if the resulting PDF follows the required visual formatting.
- Bibliographic descriptions in Ukrainian dissertations may use a selected recognized style with regard to DSTU 8302:2015. For this project, use APA formatting when the user asks for literature/references in APA.

## DOCX-Derived Dissertation Profile

Extracted from the local Word sample `Дисертація-1.docx` at `/Users/admin/Documents/Documents - Admin’s MacBook Pro/Personal/PhD/papers/Дисертація-1.docx`.

- Page format: A4 portrait, `21.0cm x 29.7cm`.
- Use following margins: left `2.5cm`, right `1.0cm`, top `2.0cm`, bottom `2.0cm`.
- Header/footer distance: approximately `1.25cm`.
- The sample also contains at least one landscape A4 section for wide material. In LaTeX, use `pdflscape` or a controlled `landscape`/`\newgeometry` block only when a wide table or appendix requires it.
- Normal/body style: Times New Roman, `14pt`, justified alignment, 1.5 line spacing, no paragraph spacing after.
- Body paragraphs commonly use first-line indent around `1.25cm` (`708` Word twips).
- Main heading style: centered, bold, Times New Roman 14 pt inherited from body, with spacing after about `12pt`.
- Second-level headings in the sample are numbered, justified, and inherit body typography.
- Table text in the sample is smaller, approximately `9pt`, centered, with compact line spacing. Use smaller table text only when needed for dense data.
- Figure captions are centered, smaller than body text, and placed close to the figure.
- The sample uses footnotes/endnotes, so dissertation templates should not block later use of `\footnote{...}`.

LaTeX geometry matching the observed DOCX sample:

```latex
\geometry{
  left=25mm,
  right=10mm,
  top=20mm,
  bottom=20mm,
  headsep=12.5mm,
  footskip=12.5mm
}
```

Use this stricter DOCX-derived geometry for dissertation-style drafts when matching an existing Ukrainian dissertation sample is more important than preserving the current assignment layout.

## Recommended LaTeX Preamble

```latex
\documentclass[14pt,a4paper]{extarticle}

\usepackage{fontspec}
\usepackage[ukrainian,english]{babel}
\usepackage{amsmath}
\usepackage{amssymb}
\usepackage{geometry}
\usepackage{enumitem}
\usepackage{indentfirst}
\usepackage{microtype}
\usepackage{ragged2e}
\usepackage{setspace}

\geometry{
  left=25mm,
  right=10mm,
  top=20mm,
  bottom=20mm
}

\setmainfont{Times New Roman}
\setlength{\parindent}{1.25cm}
\setlength{\parskip}{0pt}
\setlength{\emergencystretch}{3em}

% Use \onehalfspacing for dissertation-style drafts.
% Use \singlespacing or \linespread{1.0} only when the assignment explicitly expects compact text.
\onehalfspacing

\setlist{nosep,leftmargin=1.25cm,labelsep=0.25cm}

\newcommand{\eng}[1]{\foreignlanguage{english}{#1}}
\newcommand{\sectiontitle}[1]{%
  \par\vspace{\baselineskip}%
  \noindent\textbf{#1}\par
}
```

## Section Spacing

- Major sections should be separated by one line of vertical space.
- Do not create section spacing by adding many empty lines in the source. Prefer a macro such as:

```latex
\newcommand{\sectiontitle}[1]{%
  \par\vspace{\baselineskip}%
  \noindent\textbf{#1}\par
}
```

- For the first section after a title block, remove the preceding `\vspace{\baselineskip}` manually if it creates too much space.

## References And APA Style

- The literature section title should be centered.
- Use the Ukrainian title `Список використаних джерел` unless the assignment explicitly asks for `Література` or `References`.
- Format literature entries as numbered Ukrainian dissertation-style references unless the user explicitly requests strict APA. In this local rule, the year goes at the end of the entry, after pages if pages are present.
- For this project, bibliography entries should have no normal paragraph first-line indent. Use `leftmargin=0.75cm`, `labelwidth=1cm`, and `labelsep=0cm` so the bibliography item number aligns with the main text edge while leaving enough reserved marker width for two-digit items such as `[10]`.
- Bibliography text alignment should be justified.
- Keep a single paragraph per source entry. Do not split one source into multiple paragraphs.
- If strict APA 7 compliance is required by a journal or supervisor, verify whether numbered references and year-at-end references are acceptable. The current local preference is numbered Ukrainian dissertation-style entries.

Recommended manual bibliography block:

```latex
\begin{center}
\textbf{Список використаних джерел}
\end{center}

\begingroup
\setlength{\parindent}{0pt}
\setlength{\leftskip}{0pt}
\setlength{\rightskip}{0pt}
\setlength{\parskip}{0pt}
\justifying

\begin{enumerate}[leftmargin=0.75cm,labelwidth=1cm,labelsep=0cm,align=left,label={[\arabic*]},itemsep=0pt,topsep=0pt,parsep=0pt]
  \item Author, A. A. Title of work. \textit{Journal or Publisher}, 2024.
  \item Author, B. B., \& Author, C. C. Title of article. \textit{Journal Title}, vol. 12, no. 3, pp. 45--67, 2023.
\end{enumerate}

\endgroup
```

If `\justifying` is used, make sure this package is present in the preamble:

```latex
\usepackage{ragged2e}
```

For larger dissertation projects with many sources, prefer `biblatex` with an APA style file only after confirming that the selected LaTeX toolchain supports `biber`. For small university assignments, manual APA entries are simpler and more reliable with Tectonic.

## Creating A New Assignment From The Template

1. Copy `templates/latex/ukrainian-university-assignment-template.tex` into the target task folder.
2. Rename the copied file according to the assignment.
3. Replace the title, student line, research topic, section headings, body text, formulas, and bibliography entries.
4. Compile from the folder containing the `.tex` file:

```bash
tectonic your-file.tex
```

5. Keep the `.tex` source and compiled `.pdf`; LaTeX service files such as `.aux`, `.log`, `.out`, `.xdv`, and `.synctex.gz` are ignored by Git.

## Source References For Formatting Rules

- Ministry of Education and Science of Ukraine: Order No. 40 dated 2017-01-12, `Про затвердження Вимог до оформлення дисертації`, current version amended on 2019-07-12: https://zakon.rada.gov.ua/laws/show/z0155-17
- NAUKA overview of dissertation formatting requirements: https://nauka.gov.ua/information/vymohy-do-oformlennia-dysertatsiinoi-roboty/
- National Library of Ukraine named after V. I. Vernadskyi summary of dissertation formatting requirements: https://nbuv.gov.ua/node/5989
- DSTU 8302:2015 bibliographic references standard record: https://online.budstandart.com/ua/catalog/doc-page.html?id_doc=64411
