# Copilot instructions

## Build

- Run `make` from the repository root. It invokes `xelatex cv`, producing `cv.pdf`, then copies that file to the published artifact `gabriel_ryan_cv.pdf`.
- Run `make clean` to remove `cv`'s LaTeX intermediates and temporary PDF. It deliberately leaves `gabriel_ryan_cv.pdf` in place.

## Architecture

- `cv.tex` is the canonical resume source. Its preamble defines the page geometry, Noto fonts, colors, and resume-specific layout primitives; the document body contains all published resume content.
- The custom `\rsection`, `\rjob`, `ritemize`, and `\ritem` definitions centralize the visual structure for section headers, dated roles, and compact bullet lists. Prefer these primitives when extending existing sections.
- `Makefile` is the complete publication pipeline. `cv.pdf` and LaTeX auxiliary files are disposable build outputs; `gabriel_ryan_cv.pdf` is the repository's versioned, shareable output and should be regenerated after changing `cv.tex`.
- `experience.txt` and `urls.txt` are standalone reference notes. They are not included by `cv.tex`, so editing them does not change the generated resume.

## Repository conventions

- Preserve the compact, manually tuned layout in `cv.tex`: section spacing is controlled with nearby `\vspace`/`\hspace` adjustments and `minipage` blocks rather than a general resume template or separate style file.
- Format employment and education dates as abbreviated month plus year, with LaTeX's `--` date separator, for example `Mar 2024 -- Present`.
- Use `\rjob{...}{...}` for each role or degree and `ritemize` with `\ritem` for experience bullets so headings, dates, and bullets align consistently.
- Publication entries keep the venue in a bold bracketed label, the title italicized, Gabriel Ryan's name bold, and the paper link inline with `\url`.
- Treat edits to generated `cv.*` files as disposable. Make source changes in `cv.tex`, rebuild, and retain the resulting update to `gabriel_ryan_cv.pdf`.
