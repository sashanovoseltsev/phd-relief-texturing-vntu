# LaTeX Formatting Rules

## University Text Assignments

- Default storage location for LaTeX assignment artifacts: `tasks/year_2/science_projects_kovalenko`, unless the user specifies another folder.
- Keep both source `.tex` and compiled `.pdf` files.
- Default document class for Ukrainian university text assignments: `extarticle` with `14pt` and `a4paper`.
- Default font: Times New Roman through `fontspec`.
- Prefer `XeLaTeX` or `LuaLaTeX` for Ukrainian text and Unicode formulas.
- Use Ukrainian as the main language unless the user asks for another language.
- Do not add extra vertical spacing between paragraphs; set `\parskip` to `0pt`.
- Use a first-line paragraph indent, typically `1.25cm`, unless the assignment requires another style.
- Format section and paragraph titles in bold.
- Use `amsmath` for displayed equations and put important formulas in `\[ ... \]`.
- Use semantic math notation where possible, for example `D_{\mathrm{ray}}(t)` instead of plain text `D_ray(t)`.
- Keep English technical terms in parentheses after Ukrainian terms when useful for clarity.
- For dissertation-related assignments, connect the content to the official PhD topic: `Методи та програмні засоби рельєфного текстурування для систем формування тривимірних графічних зображень`.
- If PDF compilation is required, compile from the `.tex` source with a real LaTeX engine. If no LaTeX engine is available, state the limitation and do not present a non-LaTeX export as a true LaTeX compilation.
