# Splunk Search Reference MCQ Bank

A 2,499-question multiple-choice question bank generated from the **Splunk Enterprise Search Reference 10.4.0** manual (`splunkSearchManual.pdf`, 983 pages), covering the full Search Processing Language (SPL): every command, every eval/statistical/charting function, time modifiers, quick-reference material, and CLI usage.

Originally intended to test various LLMs innate ability to generate Splunk queries.  But there might be other use cases.

## Creation
Generated using Sonnet 5 on August 28th 2026
-The Prompt:
Using the pdf manual here: splunkSearchManual.pdf (local file name for the Aug 16th 2026 version 10.4.0) create 2500 multiple choice questions (four options for each question, A-D) based on the material in this document.  Distribute the questions proportionally across topics based on the size of the topic in the manual. Ensure the output does not have answer length bias and the correct answer choice is dispersed across the four options.  
Output the questions in a json report in the same directory.  Review the questions once complete and ensure there are no ambiguous questions and that all questions can be answered by a human or machine. Last, create a second document that provides statistics about the questions just created broken down by topic.   


## Files

| File | Description |
|---|---|
| `splunk_mcq_questions.json` | The question bank — 2,499 questions as a JSON array. |
| `splunk_mcq_statistics.md` | Breakdown of question counts by chapter/subtopic, plus answer-distribution and answer-length-bias metrics. 


## Question schema

Each entry in `splunk_mcq_questions.json`:

```json
{
  "id": 1327,
  "chapter": "Search Commands",
  "subtopic": "highlight",
  "source_page": 545,
  "question": "Why can't the highlight command be used with a command like stats?",
  "options": {
    "A": "Because stats removes the _raw field entirely from every event",
    "B": "Because stats produces calculated results, not raw events",
    "C": "Because stats runs only on the search head",
    "D": "Because stats always requires a BY clause to run"
  },
  "correct_answer": "B",
  "explanation": "The manual says you cannot use highlight with commands like stats \"which produce calculated or generated results,\" since highlight requires a search that keeps the raw events."
}
```

`source_page` is the 1-indexed physical page in Splunk Search Manual (10.4.0 16 August 2026) the question was drawn from, so every answer can be traced back to the manual text.  Download the pdf to align the pages to the document.  

## How it was built

- Questions were allocated across the manual's 8 chapters and 194 subtopics (individual SPL commands, function categories, etc.) in proportion to each topic's page span, so coverage roughly mirrors how much the manual itself says about a topic (e.g. the ~640-page Search Commands chapter accounts for ~68% of the bank; the 6-page CLI chapter accounts for ~0.6%).
- Each question is grounded in its source excerpt only — no facts beyond what the manual states.
- Correct-answer letter position was programmatically rebalanced after generation (final distribution: 625/625/625/624 across A/B/C/D, i.e. ~25% each).
- Answer *length* was checked for bias (an LLM's tendency to write the correct answer as the most detailed/longest option, letting a test-taker guess without knowledge) and corrected through a dedicated editing pass, cutting the "correct answer is the longest option" rate from 45.3% to 32.7%. See `splunk_mcq_statistics.md` for the full methodology and honest reporting of the residual gap.
- A separate review pass re-checked every question against the source manual text for ambiguity, factual correctness, and grammatical coherence, fixing issues introduced by earlier edit passes.

## Potential uses

**LLM knowledge benchmarking.** The most direct use: run the question bank through one or more LLMs (with or without the manual in context) and score accuracy, broken down by `chapter`/`subtopic`. Because coverage is proportional to the manual's structure and the answer distribution is unbiased, aggregate and per-topic accuracy scores are meaningful for comparing models, comparing a model with and without retrieval/context, or tracking regressions across model versions or system-prompt changes for a Splunk-focused assistant.

**Testing an LLM's ability to *generate* SPL, not just recognize it.** This bank tests comprehension and recall (multiple-choice), which is a different — and easier — skill than writing correct SPL from scratch. It's a good complement to, not a substitute for, a generation-focused eval. Two ways to extend it in that direction:
- **Prompt-from-explanation**: take a question's `explanation` (or the underlying manual passage at `source_page`) describing a command's behavior or a worked example, and ask the LLM to write the SPL that produces that behavior/result, then compare against the manual's actual example query. Many questions in the `subtopic`s under "Search Commands" are built directly from the manual's own worked examples, so the ground-truth query is often recoverable from `source_page`.
- **Distractor-as-bug-detection**: present the LLM with the question stem and the *incorrect* options as candidate SPL snippets or claims, and ask it to identify what's wrong — a proxy for whether a model can catch subtly incorrect SPL rather than just recall correct syntax.

**Regression / eval-harness gate.** Because it's static, versioned, and traceable to a specific manual release, it can serve as a repeatable regression check for any pipeline that answers Splunk questions (a RAG chatbot, a fine-tuned support model, a documentation search feature) — run it on every change and watch for score drops in specific chapters/subtopics.

**Human learning material.** Usable as-is for Splunk SPL study/certification prep, quiz-style training modules, or onboarding material for new Splunk users — organized by exactly the topic structure of the official manual, so weak areas map directly back to the relevant manual section via `chapter`/`subtopic`/`source_page`.

**Topic-coverage analysis.** The per-subtopic counts in `splunk_mcq_statistics.md` double as a map of how much material each SPL command or function category has in the manual — useful on its own for prioritizing documentation, training, or support-content work.

## Limitations

- Questions and answers were generated and reviewed by LLM agents against the source text, not human-verified line by line. The review pass materially improved quality (see `splunk_mcq_statistics.md` for what it caught), but spot-checking before high-stakes use (e.g. certification-adjacent training) is still advisable.
- A small residual answer-length bias remains (32.7% vs. an ideal 25% "correct answer is the longest option" rate), documented transparently rather than eliminated, because closing the gap further would have required padding literal manual values (config keys, exact defaults, argument names) in ways that risk misrepresenting the source text.
- Reflects Splunk Enterprise 10.4.0 as of the manual's 2026-08-16 revision; SPL syntax, defaults, or command availability may differ in other versions.
