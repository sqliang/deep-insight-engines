---
name: pdf-reader
description: |
  Read, extract and summarize PDF files with automatic OCR fallback for scanned/image-based PDFs.
  Use this skill whenever the user asks to read/extract/summarize PDF content.
  Triggers on: "read this PDF", "extract PDF content", "summarize this PDF", "what's in this PDF",
  "convert PDF to markdown", "batch process PDFs", "PDF 内容", "读取 PDF", "总结 PDF".
  This skill handles everything automatically — conversion + structured summary with frontmatter.
---

# PDF Reader

Convert PDFs to structured markdown — text-based via Microsoft markitdown, image-based via tesseract OCR.
**Fully automatic**: the script handles conversion, you handle structured summarization.

---

## Step 1: Check Dependencies

```bash
which markitdown || echo "MISSING: uv tool install markitdown[pdf]"
which pdftoppm || echo "MISSING: brew install poppler"
which tesseract || echo "MISSING: brew install tesseract"
tesseract --list-langs 2>&1 | grep -q chi_sim || echo "MISSING: brew install tesseract-lang"
```

If anything is missing, tell the user to install it and stop.

---

## Step 2: Run Conversion

**CRITICAL — output must land in the user's project root, NOT under `.claude/skills/`.**

The Bash tool's working directory defaults to the skill directory. You must explicitly set `-o` to an absolute path pointing to the project root.

**How to determine the project root:** The skill lives at `<project-root>/.claude/skills/pdf-reader/scripts/`. Strip `/\.claude/skills/pdf-reader/scripts` from the skill's base directory to get the project root.

**Command template:**
- Script: `<skill-base-dir>/scripts/cli.py` (absolute)
- Input: `<absolute-path-to-pdf-file-or-dir>` (absolute)
- Output: `<project-root>/pdf-output/` (absolute — this is the key fix)

```bash
uv run <skill-base-dir>/scripts/cli.py "<absolute-input-path>" -o "<project-root>/pdf-output/"
```

Example:
```bash
uv run /Users/sqliang/work/超级个体/.claude/skills/pdf-reader/scripts/cli.py \
  "/Users/sqliang/work/超级个体/some-talk.pdf" \
  -o "/Users/sqliang/work/超级个体/pdf-output/"
```

What the script does: auto-detects text vs image PDFs, runs the right extractor, and produces:

```
pdf-output/
├── Index.md
└── <pdf-name>/
    ├── 00-full.md          # Raw markdown
    ├── 01-summary.md       # Placeholder — YOU fill this NOW
    ├── 02-meta.json
    └── 03-ocr/             # Only for image PDFs
```

The script will print `[ACTION REQUIRED]` at the end — do NOT ignore this.

---

## Step 3: Generate Structured Summaries (REQUIRED)

**This is mandatory. Do not skip this step. Do not end the conversation before completing it.**

For each PDF subdirectory under `<project-root>/pdf-output/` (the same absolute output path from Step 2):

1. Read `<project-root>/pdf-output/<pdf-name>/00-full.md`. If it's long, at minimum read the first 200 lines and skim the rest.
2. Write `<project-root>/pdf-output/<pdf-name>/01-summary.md` using the EXACT format below — frontmatter MUST be valid YAML between `---` delimiters.

### Format Template

```markdown
---
title: Document Title (extracted or inferred from content)
tldr: One-sentence core summary, no more than 50 words
description: 2-3 sentences describing the document's purpose and main content
keyPoints:
  - Key point 1: specific, actionable insight
  - Key point 2: ...
  - Key point 3: ...
  - Key point 4: ...
  - Key point 5: ...
---

# <Document Title> — Detailed Analysis

## Document Overview
(Background, purpose, author/source info — not a simple repeat, provide context)

## Core Content
(Section-by-section analysis — synthesize and connect ideas, don't just paraphrase)

## Key Insights
(Beyond the source material: what deserves attention? what is debatable? what is actionable?)

## Structure Outline
(The document's chapter/section logical structure as a tree)
```

### Rules

- **Write the summary in the same language as the original document.**
- **Every frontmatter field is required.** If the document doesn't provide a title, infer a reasonable one.
- **keyPoints**: exactly 5 items, each a single concrete sentence.
- **tldr**: under 50 words, no line breaks.
- **description**: 2-3 complete sentences.
- **YAML quoting**: Don't quote simple strings. Only add double quotes when the value contains `:`, `#`, `"`, or starts with `{`/`[`/`&`/`*`/`!`/`|`/`>`.
- Placeholders like "..." or "N/A" are NOT acceptable — fill everything with real content.

---

## Step 4: Report to User

After all summaries are generated:

1. Print the Index.md table from `<project-root>/pdf-output/Index.md`
2. For each PDF, show the `tldr` from its summary
3. Mention any OCR-quality concerns if applicable (pages with 0 chars extracted, garbled sections)
