# MarkdownTools local recreation

Working implementation built from the observed behavior documented in ../工具页分析.md. Original source bundles are research evidence and are not application dependencies.

## Run

```powershell
$env:PATH = 'F:\node\install;' + $env:PATH
Set-Location F:\REA\markdowntools\replica
npm run dev
```

Open http://127.0.0.1:3000 . Production: `npm run build`, then `npm start`.

## Implemented

Homepage, searchable/category-filtered tool directory, responsive navigation, Markdown editor with sanitized preview, HTML→Markdown, Markdown→HTML, CSV/JSON→Markdown table, visual table editor, basic word count and Markdown formatting. Output copy/download controls are shared.

## Added in milestone 2

Markdown→PDF with A4/Letter/A5 and margin controls, Markdown→DOCX, DOCX→Markdown, PDF text extraction, English OCR, Mermaid editor, Markdown viewer with KaTeX and Mermaid, plain-text extraction, case conversion, table of contents generation and Slack syntax adaptation. The shared Markdown editor also renders diagrams and formulas. Total: 18 tools.

PDF export opens the browser print dialog; choose Save as PDF. OCR initially downloads worker/core/English trained data from the dependency's configured CDN. PDF files stay in browser memory. Uploaded documents are limited to 20 MB. OCR is English-only; it is not a Chinese OCR implementation.

QA: `qa.cjs` covers 8 original browser checks; `qa-advanced.cjs` covers 10 added checks including real DOCX download/import, PDF extraction, English OCR, diagrams, math and print styles. Results are saved as JSON. Test PDF/DOCX files are in this folder.

Dependency audit: 3 moderate findings from mammoth→argparse→sprintf-js. Registry latest sprintf-js remains in the affected range; a forced downgrade of mammoth is not applied. The affected dependency is a command-line parser; DOCX conversion is browser-only here. This is not a claim that the dependency is vulnerability-free.

## Remaining

This is not the complete 98-tool site. Account persistence, remaining tools and closer visual parity are subsequent work. DOCX complex layouts and nested lists need further fidelity work; PDF extraction uses text positions and does not recover original Markdown structure. The independent homepage design preserves the toolkit structure; it is not a pixel-identical copy. Font loading uses Google Fonts; input content is processed by browser code.

## V3 milestone
Six evidence-backed text tools added: snake, kebab, title, alternating case, character counter and reading time. Total: 24 tools. Methods and REA evidence: ../method/V3/流程.md. 18 reference inputs plus 3 controls/layout checks passed; the original 8 browser checks also passed.


## V4 milestone
Five table tools added: Markdown table to CSV/JSON/HTML/LaTeX and table formatter. Total: 29 tools. Evidence and process: ../method/V4/流程.md. Build passed; 21 V4 checks, 8 base checks and 21 V3 checks passed. CSV output quoting, HTML/LaTeX escaping and code-block preservation verified.


## V5
98 basic tool entries. 69 new entries are simplified initial implementations, not complete equivalents. See ../method/V5/流程.md for important limitations. Build and 69-page smoke check passed.
