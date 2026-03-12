# Office 365 Skills for Claude Code — Research

**Date:** 2026-03-12  
**Scope:** PowerPoint, Excel, Word, and broader Office 365 integration for Claude Code  
**Goal:** Identify the smallest, highest-quality set of skills/MCPs worth building into `ent-skills`  

---

## TL;DR — Top Recommendations

| Rank | What | Type | Platform | Quality Signal |
|------|------|------|----------|----------------|
| 🥇 1 | **Anthropic Official Skills** (xlsx, pptx, docx) | Claude Code Skills | Cross-platform | First-party, proprietary, battle-tested |
| 🥈 2 | **sbroenne/mcp-server-excel** | MCP Server + CLI | Windows only | 25 tools / 225 ops, COM native, LLM-tested |
| 🥉 3 | **GongRzhe/Office-PowerPoint-MCP-Server** | MCP Server | Cross-platform | 34 tools / 11 modules, 2156 Smithery installs |
| 4 | **trsdn/mcp-server-ppt** (fork) | MCP Server + CLI | Windows only | 33 tools / 204 ops, COM native, sibling to #2 |
| 5 | **Softeria/ms-365-mcp-server** | MCP Server | Cloud/Graph API | Official MS Graph integration, auth required |
| 6 | **GongRzhe/Office-Word-MCP-Server** | MCP Server | Cross-platform | python-docx, broad doc manipulation |

**Key insight:** Anthropic already ships official, first-party skills for Excel, PowerPoint, and Word inside `anthropics/skills`. These should be the foundation — any custom skill built in `ent-skills` should wrap or extend them, not replace them.

---

## 1. Anthropic Official Skills (TIER 1 — Start Here)

**Source:** [github.com/anthropics/skills](https://github.com/anthropics/skills/tree/main/skills)  
**License:** Proprietary (see LICENSE.txt in each skill)  
**Platform:** Cross-platform (Python + Node.js toolchain)  

These are Anthropic's own Claude Code skills, maintained in the official skills repo. They use SKILL.md files that Claude Code auto-discovers and loads. Each includes helper scripts, formatting standards, and QA workflows.

### 1a. `xlsx` Skill
**Trigger:** Any task where the user wants to open, read, edit, create, or convert `.xlsx`, `.xlsm`, `.csv`, or `.tsv` files.  
**Source:** [anthropics/skills/tree/main/skills/xlsx](https://github.com/anthropics/skills/tree/main/skills/xlsx)

**What it does:**
- **Data analysis:** Uses pandas (`pd.read_excel`, `df.to_excel`) for reading, analysis, statistics
- **Formula-first:** Enforces Excel formulas over Python-calculated hardcodes (`=SUM(B2:B9)` not `sheet['B10'] = 5000`)
- **Formatting engine:** Uses openpyxl for full formula, style, and chart control
- **Formula validation:** Ships a `scripts/recalc.py` that uses LibreOffice to recalculate and surface formula errors (`#REF!`, `#DIV/0!`, etc.)
- **Financial modeling standards:** Industry-standard color coding (blue=hardcode, black=formula, green=cross-sheet link, red=external), currency/percentage/multiple formatting rules
- **Documentation for hardcodes:** Forces citation format: "Source: Company 10-K, FY2024, Page 45, [URL]"

**Design philosophy:** Zero formula errors on delivery. Formulas stay dynamic. Financial models get blue/black/green/red coding automatically.

**Why it matters for ent-skills:** This is the canonical reference. Any custom Excel skill should follow its conventions and extend, not diverge.

---

### 1b. `pptx` Skill
**Trigger:** Any `.pptx` task — creation, editing, reading, templates, speaker notes.  
**Source:** [anthropics/skills/tree/main/skills/pptx](https://github.com/anthropics/skills/tree/main/skills/pptx)

**What it does:**
- **Reading:** `python -m markitdown presentation.pptx` for text extraction; `thumbnail.py` for visual overview
- **Editing:** Unpack → manipulate XML → repack workflow (for editing existing presentations)
- **Creating from scratch:** Uses **pptxgenjs** (JavaScript) for clean programmatic creation with full control
- **Design system:** Built-in color palettes (Midnight Executive, Coral Energy, Ocean Gradient, etc.), typography pairings, layout patterns (two-column, icon grid, half-bleed image)
- **QA requirements:** Mandates subagents for visual QA — converts slides to images and inspects for overlapping elements, overflow, color contrast failures
- **Anti-patterns enforcement:** Blocks accent lines under titles (classic AI tell), text-only slides, equal-weight colors, random spacing

**Key design guidance extracted:**
```
Dark/light contrast: Dark backgrounds for title+conclusion,
light for content ("sandwich" structure).
Commit to ONE visual motif and carry it across all slides.
Every slide needs a visual element — image, chart, icon, or shape.
Text-only slides are forgettable.
```

**Why it matters for ent-skills:** This skill has real visual taste. It won't produce generic AI slides. The QA-with-subagents pattern is gold.

---

### 1c. `docx` Skill
**Trigger:** Word documents — creation, editing, reports, memos, letters, templates.  
**Source:** [anthropics/skills/tree/main/skills/docx](https://github.com/anthropics/skills/tree/main/skills/docx)

**What it does:**
- **Reading:** `pandoc --track-changes=all document.docx -o output.md` for full content extraction including tracked changes
- **Creating:** Uses **docx-js** (JavaScript/npm) for clean document generation
- **Page size enforcement:** Explicitly sets US Letter (12240 × 15840 DXA) vs A4 — fixes the default-to-A4 bug
- **Style overrides:** Forces explicit heading style IDs so TOC works correctly (`id: "Heading1"` not inferred names)
- **List formatting:** Never uses unicode bullets — uses proper XML numbering structure
- **Legacy format conversion:** `soffice.py --convert-to docx document.doc` for `.doc` files
- **Tracked changes:** Includes `scripts/accept_changes.py` to produce clean final documents
- **Validation:** `scripts/office/validate.py` for XML validation after generation

**Why it matters for ent-skills:** Docx is underrated. Reports, SOWs, proposals, memos — all Word. This skill gets the formatting right and handles the annoying edge cases (US Letter vs A4, tracked changes, TOC heading IDs).

---

## 2. sbroenne/mcp-server-excel (TIER 1 — Windows)

**Source:** [github.com/sbroenne/mcp-server-excel](https://github.com/sbroenne/mcp-server-excel)  
**License:** MIT  
**Platform:** Windows only (COM automation)  
**Install:** `dotnet tool install --global Sbroenne.ExcelMcp.McpServer`  
**VS Code:** Available as one-click [VS Code extension](https://marketplace.visualstudio.com/items?itemName=sbroenne.excel-mcp)

**What makes this special:**
- **Native COM API** — controls the actual Excel application, not file manipulation. Zero corruption risk.
- **25 tools / 225 operations** covering: Power Query (M code), DAX measures, PivotTables, Charts, VBA, Tables, Connections (OLEDB/ODBC), Named Ranges, Conditional Formatting, Slicers, Screenshots
- **LLM-tested quality** — uses `pytest-aitest` framework to validate that LLMs correctly understand and use the tools (not just that tools work in isolation)
- **CLI mode for coding agents:** `excelcli` CLI uses 64% fewer tokens than MCP Server mode (single tool, no schema explosion). MCP sends 23 tool schemas per request (~100K+ tokens); CLI avoids this.
- **Visual feedback:** Shows Excel window side-by-side while AI works; progress in status bar
- **IRM/AIP-protected file support** — can work with enterprise-protected Excel files

**Key token efficiency insight:**
```
Metric    | CLI      | MCP Server
-------------------------------
Tokens    | ~59K     | ~163K
Winner    | CLI (64% fewer)
```
For Claude Code (coding agent mode), use the CLI interface. For conversational/interactive, use MCP.

**Install agent skills:**
```bash
npx skills add sbroenne/mcp-server-excel --skill excel-cli   # For coding agents
npx skills add sbroenne/mcp-server-excel --skill excel-mcp   # For conversational AI
```

**Why it matters for ent-skills:** If the target environment is Windows + Office, this is the best Excel automation available. The CLI skill is particularly well-suited for Claude Code's agentic coding mode.

---

## 3. GongRzhe/Office-PowerPoint-MCP-Server (TIER 1 — Cross-Platform)

**Source:** [github.com/GongRzhe/Office-PowerPoint-MCP-Server](https://github.com/GongRzhe/Office-PowerPoint-MCP-Server)  
**License:** MIT  
**Platform:** Cross-platform (python-pptx, no Office required)  
**Smithery:** 2,156 installs, 88/100 score, 89% uptime at 339ms P95  
**Install:** `npx -y @smithery/cli install @GongRzhe/Office-PowerPoint-MCP-Server --client claude`

**What it does (v2.1):**
- **34 tools across 11 modules:** Presentation management, content, templates, structural (tables/charts), professional design, hyperlinks, charts, connectors, slide masters, transitions
- **25 built-in slide templates:** title_slide, key_metrics_dashboard, before_after_comparison, timeline_slide, team_introduction, etc. — with dynamic sizing and auto-text-wrapping
- **4 professional color schemes:** Modern Blue, Corporate Gray, Elegant Green, Warm Red — applied consistently
- **Text extraction (v2.1):** `extract_slide_text` and `extract_presentation_text` for reading existing presentations
- **Image enhancement:** Pillow-based brightness/contrast/saturation + shadow/glow/reflection effects
- **Template support:** Reads `.pptx` and `.potx` template files, preserves themes and master layouts
- **Auto-generation:** `auto_generate_presentation` tool — full deck from topic in one call

**Key capability — template_sequence generation:**
```python
create_presentation_from_templates(
  template_sequence=[
    {"template_id": "title_slide", "content": {...}},
    {"template_id": "key_metrics_dashboard", "content": {...}},
    {"template_id": "before_after_comparison", "content": {...}},
  ],
  color_scheme="modern_blue"
)
```

**Why it matters for ent-skills:** Best cross-platform PowerPoint MCP. Works anywhere without Office installed. Template system is production-ready for enterprise reporting use cases.

---

## 4. trsdn/mcp-server-ppt — Windows COM Fork (TIER 1 — Windows)

**Source:** [github.com/trsdn/mcp-server-ppt](https://github.com/trsdn/mcp-server-ppt)  
**License:** MIT  
**Platform:** Windows only (COM automation)  
**Original upstream:** [sbroenne/mcp-server-ppt](https://github.com/sbroenne/mcp-server-ppt) by Stefan Broenner (same author as Excel MCP)  
**Install:** `dotnet tool install --global PptMcp.McpServer`

**What it does (sibling to Excel MCP):**
- **33 tools / 204 operations** across: Slides, Shapes (grouping/merge/flip/z-order), Text, Charts, Tables, Animations, Transitions, Design/Themes, Images, Notes, Sections, Hyperlinks, Slideshow control, Slide Masters, Export (PDF/video/MP4/print), VBA, Media (audio/video), Window, SmartArt, Shape Alignment, Custom Shows, Page Setup, Slide Import, Tags
- **Export to video (MP4)** — unique capability; creates presentation videos for distribution
- **Animations and transitions** — full control, can copy transitions across all slides
- **SmartArt support** — read diagram info, add nodes
- **Speaker notes management** — get/set/clear/append
- **Shared architecture with Excel MCP** — same CLI pattern, same token efficiency win

**Why different from GongRzhe's server:**
- COM API = controls live PowerPoint process (not file manipulation), sees all features
- Requires Windows + PowerPoint installation
- Far more complete: animations, transitions, video export, SmartArt — features python-pptx can't touch
- GongRzhe works everywhere but misses live-app features

**Why it matters for ent-skills:** If Windows is the target, use this paired with `mcp-server-excel`. They share the same architecture, skills format, and CLI approach. Animations, video export, and SmartArt are key enterprise use cases.

---

## 5. Softeria/ms-365-mcp-server — Graph API Integration (TIER 2)

**Source:** [github.com/Softeria/ms-365-mcp-server](https://github.com/Softeria/ms-365-mcp-server)  
**License:** (check repo)  
**Platform:** Cloud (Microsoft Graph API)  
**Auth:** Azure AD OAuth / Microsoft identity

**What it does:**
- Connects to Microsoft 365 via **Microsoft Graph API** — not local files, but cloud documents
- Access OneDrive, SharePoint, Excel Online, Word Online, Outlook, Teams, Calendar
- Read/write Excel workbooks stored in OneDrive/SharePoint using Graph Excel API
- Email integration via Outlook Graph
- Calendar read/write via Microsoft Calendar Graph

**Key distinction from local tools:**
This operates on cloud-hosted files, not local Office installations. Useful for enterprise environments where files live in SharePoint/OneDrive, not on disk.

**Anthropic native connector:** Anthropic also ships an official Microsoft 365 connector for Claude.ai Teams/Enterprise  
**Ref:** [support.claude.com/articles/12542951-enabling-and-using-the-microsoft-365-connector](https://support.claude.com/en/articles/12542951-enabling-and-using-the-microsoft-365-connector)  
This is a first-party integration available in Teams plans but operates at Claude.ai web level, not Claude Code.

**Why it matters for ent-skills:** Enterprise files often live in SharePoint, not locally. This is the only option for cloud-native Office file work. Requires Azure AD setup.

---

## 6. GongRzhe/Office-Word-MCP-Server (TIER 2)

**Source:** [github.com/GongRzhe/Office-Word-MCP-Server](https://github.com/GongRzhe/Office-Word-MCP-Server)  
**License:** MIT  
**Platform:** Cross-platform (python-docx)  
**Install:** `npx -y @smithery/cli install @GongRzhe/Office-Word-MCP-Server --client claude`

**What it does:**
- Create/read/edit Word documents without Office installed
- Add headings, paragraphs, tables, images, page breaks, footnotes/endnotes
- Rich text formatting: bold, italic, underline, color, font, size
- Table formatting: borders, header rows, shading, merging, alternating colors, column width control, cell padding
- Document operations: merge, split, copy, convert to PDF
- Document protection: password, restricted editing, digital signatures, signature verification
- Comment extraction: all comments, filter by author, per-paragraph comments
- Search and replace across entire document

**Why it matters for ent-skills:** Complements the official `docx` skill (which uses docx-js/Node). This is a pure Python option for environments without Node.js. Good for simpler document generation pipelines.

**Limitation vs official docx skill:** The official Anthropic `docx` skill uses docx-js and includes more sophisticated formatting guidance, page size handling, and validation. For complex enterprise documents, prefer the official skill.

---

## 7. jenstangen1/pptx-xlsx-mcp — Combined COM Server (TIER 3)

**Source:** [github.com/jenstangen1/pptx-xlsx-mcp](https://github.com/jenstangen1/pptx-xlsx-mcp)  
**License:** (check repo)  
**Platform:** Windows only (pywin32 COM)

**What it does:**
- Combined PowerPoint + Excel COM server in a single repo
- Financial focus: creates financial charts (line, bar, waterfall, comparison tables)
- Supports revenue, EBITDA, profit, assets, equity metrics
- Currently uses dummy data; designed for Proff API (Norwegian company data) integration
- Template system for both apps

**Why it matters:** Financial chart integration pattern is interesting for finance/consulting use cases. However, the codebase is less mature than sbroenne's tools, and sbroenne covers a superset of capabilities.

---

## Landscape: What's NOT Worth Including

### negokaz/excel-mcp-server
**Source:** [github.com/negokaz/excel-mcp-server](https://github.com/negokaz/excel-mcp-server)  
Python-based Excel server. Older, less complete than sbroenne. Superseded.

### socamalo/PPT_MCP_Server
**Source:** [github.com/socamalo/PPT_MCP_Server](https://github.com/socamalo/PPT_MCP_Server)  
Early-stage Python PowerPoint automation for Claude Desktop. Basic. Superseded by GongRzhe.

### alejandroBallesterosC/document-edit-mcp
Combined Word + Excel + PDF server. Simpler, less mature. Good proof-of-concept but superseded by dedicated tools.

### Smithery community `pptx` skills (pacphi, POBIM)
Generic SKILL.md wrappers pointing to python-pptx. Less opinionated than official Anthropic skill. Skip.

---

## Architecture Patterns and Key Insights

### Two Worlds: COM vs Library

| Approach | COM Automation | Library (python-pptx / openpyxl / docx-js) |
|----------|----------------|----------------------------------------------|
| Platform | Windows only | Cross-platform |
| Requires | Office installed | Nothing (self-contained) |
| Fidelity | 100% (live app) | ~80% (no animations/macros/transitions) |
| Use case | Desktop power users, live editing | Server-side generation, CI/CD |
| Token cost | MCP: high / CLI: low | Varies |
| Safety | Official COM API | Direct file manipulation |

**Rule of thumb:** If you need animations, video export, VBA, live Excel features (slicers, pivot interaction) → COM (Windows). If you need portable generation, CI/CD, server-side → library-based.

### Token Efficiency: MCP vs CLI for Coding Agents

The sbroenne tools surface a critical insight for Claude Code:

> **MCP Servers send all tool schemas to the LLM on every request.** For Excel MCP, that's ~100K tokens of schemas per call. The CLI alternative uses ~59K tokens total — 64% fewer.

For Claude Code's agentic/coding mode, prefer the CLI variant over MCP Server when available. This is the same tradeoff as using `bash` over `mcp:bash`.

### The Official Anthropic Skills Are Production-Ready

The `anthropics/skills` repo ships production-quality skills with:
- Opinionated formatting standards (financial modeling color codes, typography pairings)
- QA mandates (zero formula errors, visual QA with subagents for presentations)
- Helper scripts (`recalc.py`, `thumbnail.py`, `validate.py`, `soffice.py`)
- Cross-platform approach using standard Python/JS toolchains

These are the right foundation for `ent-skills`. Custom enterprise skills should:
1. Extend the official skills with org-specific templates, color schemes, or data sources
2. Add domain-specific formatting rules (branding, financial standards, legal templates)
3. Integrate with internal systems (SharePoint paths, template libraries, data APIs)

---

## Recommended Skill Architecture for ent-skills

Based on this research, a minimal high-quality skill set for Office 365 would be:

### Option A: Cross-Platform (Any OS)
```
ent-skills/
├── skills/
│   ├── excel/        # Extends anthropics/skills xlsx with enterprise conventions
│   ├── powerpoint/   # Extends anthropics/skills pptx + GongRzhe MCP
│   ├── word/         # Extends anthropics/skills docx with enterprise templates
│   └── ms365/        # Softeria MS Graph connector for cloud files
```

### Option B: Windows-First (Full Power)
```
ent-skills/
├── skills/
│   ├── excel/        # Extends anthropics/skills + wraps sbroenne excel-cli skill
│   ├── powerpoint/   # Extends anthropics/skills + wraps trsdn ppt-cli skill
│   ├── word/         # Extends anthropics/skills docx
│   └── ms365/        # Softeria MS Graph connector for cloud files
```

### Things to Build, Not Copy

The most valuable additions to these existing skills for an enterprise context:
1. **Corporate template loading** — skill that knows where org templates live (SharePoint path, local dir) and applies them automatically
2. **Brand enforcement** — inject org color schemes, fonts, and logo placement rules into the pptx skill
3. **Financial model conventions** — org-specific extensions to xlsx skill (e.g., GAAP vs IFRS formatting, fiscal year conventions)
4. **Deck-from-data pipeline** — a skill that takes a structured data source (CSV, JSON, database query) and generates a formatted report deck end-to-end
5. **Version-controlled templates** — skill that checks out the latest approved template before generating

---

## Reference: Complete Source List

| Tool | Source | License | Stars |
|------|--------|---------|-------|
| Official Anthropic xlsx skill | [anthropics/skills/skills/xlsx](https://github.com/anthropics/skills/tree/main/skills/xlsx) | Proprietary | — |
| Official Anthropic pptx skill | [anthropics/skills/skills/pptx](https://github.com/anthropics/skills/tree/main/skills/pptx) | Proprietary | — |
| Official Anthropic docx skill | [anthropics/skills/skills/docx](https://github.com/anthropics/skills/tree/main/skills/docx) | Proprietary | — |
| sbroenne/mcp-server-excel | [github.com/sbroenne/mcp-server-excel](https://github.com/sbroenne/mcp-server-excel) | MIT | — |
| GongRzhe/Office-PowerPoint-MCP-Server | [github.com/GongRzhe/Office-PowerPoint-MCP-Server](https://github.com/GongRzhe/Office-PowerPoint-MCP-Server) | MIT | 2156 Smithery installs |
| trsdn/mcp-server-ppt | [github.com/trsdn/mcp-server-ppt](https://github.com/trsdn/mcp-server-ppt) | MIT | — |
| Softeria/ms-365-mcp-server | [github.com/Softeria/ms-365-mcp-server](https://github.com/Softeria/ms-365-mcp-server) | — | — |
| GongRzhe/Office-Word-MCP-Server | [github.com/GongRzhe/Office-Word-MCP-Server](https://github.com/GongRzhe/Office-Word-MCP-Server) | MIT | — |
| jenstangen1/pptx-xlsx-mcp | [github.com/jenstangen1/pptx-xlsx-mcp](https://github.com/jenstangen1/pptx-xlsx-mcp) | — | — |
| Anthropic MS365 connector | [support.claude.com/articles/12542951](https://support.claude.com/en/articles/12542951-enabling-and-using-the-microsoft-365-connector) | Proprietary | — |
| awesome-claude-skills | [github.com/travisvn/awesome-claude-skills](https://github.com/travisvn/awesome-claude-skills) | — | — |
| obra/superpowers | [github.com/obra/superpowers](https://github.com/obra/superpowers) | — | — |

---

*Research compiled 2026-03-12 by Jarvis. All citations link to primary sources.*
