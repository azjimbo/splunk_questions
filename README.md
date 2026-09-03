# Splunk Documentation MCQ Banks

Two independently-generated, documentation-grounded multiple-choice question banks covering
major areas of Splunk Enterprise: the Search Processing Language (SPL) and classic (Simple XML)
dashboard building. Together they total **4,999 questions**, each traceable to a specific page
or section of an official Splunk manual.

| Directory | Question bank | Questions | Source manual |
|---|---|---:|---|
| [`splunkQuestions/`](splunkQuestions/) | Splunk Search Reference MCQ Bank | 2,499 | *Splunk Enterprise Search Reference* 10.4.0 (983-page PDF) |
| [`xmlTest/`](xmlTest/) | Splunk Simple XML Dashboards MCQ Bank | 2,500 | *Simple XML dashboards* manual (help.splunk.com, 10.4) |

Each directory has its own `README.md` with full details — schema, build methodology,
limitations, and directory-specific use cases. This top-level file summarizes both so the two
can be browsed and understood together as one project.

## Splunk Search Reference MCQ Bank (`splunkQuestions/`)

Covers the full Search Processing Language: every SPL command, every eval/statistical/charting
function, time modifiers, quick-reference material, and CLI usage. Question allocation across
the manual's 8 chapters and 194 subtopics is proportional to each topic's page span in the
source PDF (e.g. the ~640-page Search Commands chapter accounts for ~68% of the bank).

- **Files**: `splunk_mcq_questions.json` (the bank), `splunk_mcq_statistics.md` (per-topic
  breakdown and answer-bias metrics), `splunkSearchManual.pdf` (the source manual),
  `work/` (build audit trail back to source text).
- **Traceability**: every question records a `source_page` (1-indexed page in the PDF).
- **Answer balance**: 625/625/625/624 across A/B/C/D (~25% each); answer-length bias was
  measured and reduced (from 45.3% to 32.7% "correct answer is the longest option") and the
  residual is reported transparently rather than hidden.

See [`splunkQuestions/README.md`](splunkQuestions/README.md) for the full write-up, including
detailed ideas for using it as an LLM benchmark (accuracy by chapter/subtopic, SPL-generation
eval extensions, regression gating for a Splunk-focused assistant).

## Splunk Simple XML Dashboards MCQ Bank (`xmlTest/`)

Covers classic (non–Dashboard Studio) Splunk dashboards built with Simple XML: dashboard/form
structure, every visualization type (tables, charts, maps, single values, gauges, trellis
layout), searches (inline, base, post-process), drilldown and interactivity, tokens, dashboard
management/sharing, and the complete Simple XML / Event Handler / Chart Configuration / Token
reference pages. Question allocation across the manual's 14 topics and 60+ subtopic pages is
proportional to each topic's word count in the source documentation.

- **Files**: `simple_xml_questions.json` (the bank), `simple_xml_question_statistics.md`
  (per-topic breakdown), `simple_xml_documentation_dependency_rework_report.md` (a report on a
  dedicated pass that reworded ~28% of questions that had been phrased as "per the
  documentation…", making them dependent on the exact source wording rather than testing
  standalone knowledge), plus `.html` renderings of all three Markdown docs.
- **Traceability**: every question records a `source_url` pointing to the exact
  help.splunk.com page it was drawn from.
- **Answer balance**: an exact 625/625/625/625 split across A/B/C/D; option lengths were
  checked to avoid the "longest/shortest answer is usually correct" bias.
- **Review passes**: beyond the documentation-dependency rework above, a systematic
  near-duplicate sweep also caught and rewrote questions that tested the same fact twice with
  slightly different wording.

See [`xmlTest/README.md`](xmlTest/README.md) for the full write-up, the original prompt that
kicked off the build, and the JSON schema.

## What the two banks have in common

- **Grounded, not invented.** Every question is built from the actual manual text for its
  topic, with a traceable pointer back to the source (page number or URL) — no facts beyond
  what the source documentation states.
- **Proportional coverage.** Questions are allocated across topics in proportion to how much
  the source manual itself says about that topic, so the bank's shape mirrors the
  documentation's own emphasis.
- **Bias-checked answer keys.** Both banks were built (or corrected) so the correct answer is
  evenly distributed across the four option letters and isn't reliably identifiable by option
  length alone — both being common failure modes in LLM-generated multiple choice.
- **LLM-built, LLM-reviewed.** Both banks were generated and reviewed by Claude working
  directly against the source manuals, with dedicated review passes for ambiguity, duplication,
  and (for the dashboards bank) documentation-dependent phrasing. Neither has been verified
  line-by-line by a human subject-matter expert.

## Possible uses (combined)

Everything listed in each sub-README applies on its own, but having both banks side by side
also enables:

- **A single "Splunk competency" benchmark.** Score an LLM, RAG chatbot, or support assistant
  across both SPL search-writing knowledge *and* classic dashboard-building knowledge in one
  pass, broken down by chapter/topic in either domain.
- **Certification study material spanning two exam-relevant domains.** SPL and Simple XML
  dashboards are both core topics for Splunk's Power User / Admin certification tracks — the
  combined ~5,000 questions give broad self-study coverage without leaving either domain thin.
- **A model/version regression suite.** Because both banks are static, versioned, and traceable
  to specific manual releases (Search Reference 10.4.0; Simple XML dashboards 10.4), they can
  be re-run after any change to a Splunk-focused assistant, prompt, or retrieval pipeline to
  watch for accuracy drops in either domain.
- **Cross-domain documentation-gap analysis.** Comparing where each bank's questions turned out
  hardest to write clearly (see each bank's review-pass reports) can highlight documentation
  pages — across both SPL and dashboards — that are unusually terse, ambiguous, or
  under-specified.

## Limitations (applies to both)

- Generated and reviewed by LLM agents against source text, not verified line-by-line by a
  human. Review passes materially improved quality (see each bank's statistics/report files for
  specifics), but spot-checking is advisable before high-stakes use.
- Each bank reflects a specific Splunk Enterprise 10.4.x documentation snapshot; SPL syntax,
  dashboard behavior, or defaults may differ in other versions.
- The Search Reference bank has a small residual answer-length bias (32.7% vs. an ideal 25%),
  documented transparently in its own statistics file rather than eliminated.
