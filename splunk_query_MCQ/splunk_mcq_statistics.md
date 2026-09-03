# Splunk Search Reference MCQ Bank — Statistics

**Total questions:** 2499  
**Source:** Splunk Enterprise Search Reference 10.4.0 (`splunkSearchManual.pdf`, 983 pages)  
**Question set file:** `splunk_mcq_questions.json`

## Overall answer-letter distribution

| Letter | Count | % of total |
|---|---|---|
| A | 625 | 25.0% |
| B | 625 | 25.0% |
| C | 625 | 25.0% |
| D | 624 | 25.0% |

The correct answer is spread evenly across A/B/C/D (target 25% each); this was achieved by programmatically shuffling option order per question after generation, rather than relying on generation-time balance.

## Answer-length bias check

Measures how often the correct answer is the *N*th-longest of the 4 options, by character count. An unbiased bank should show ~25% at every rank; a bank where the correct answer is systematically the longest option lets test-takers guess without knowledge of the material.

| Rank (by option length) | % of questions where correct answer holds this rank |
|---|---|
| 1st (longest) | 32.7% |
| 2nd | 27.3% |
| 3rd | 21.5% |
| 4th (shortest) | 18.5% |

Before rebalancing, the correct answer was the longest option in **45.3%** of questions (vs. 25% expected by chance) — a strong exploitable bias from LLM generation tendencies. After a dedicated length-rebalancing edit pass (rewording ~800 flagged questions across all 21 topic batches) this was reduced to **32.7%**. The residual gap above 25% reflects a large number of individually small, content-driven length differences (e.g. a required-argument name that is genuinely a longer word than its siblings, or an exact literal value/config key quoted from the manual) that were deliberately left as-is rather than artificially padded, to avoid sacrificing factual accuracy for a marginal statistical gain. No single question in the final bank has a severe length skew (correct answer >40% longer than the runner-up) without that being a genuine, manual-grounded literal value.

## Distribution by chapter

Question counts are proportional to each chapter's page count in the manual.

| Chapter | Questions | % of total | Subtopics | A | B | C | D |
|---|---|---|---|---|---|---|---|
| Introduction | 18 | 0.72% | 3 | 6 | 3 | 5 | 4 |
| Quick Reference | 95 | 3.8% | 5 | 25 | 18 | 27 | 25 |
| Evaluation Functions | 395 | 15.81% | 13 | 94 | 110 | 89 | 102 |
| Statistical and Charting Functions | 147 | 5.88% | 5 | 31 | 37 | 37 | 42 |
| Time Format Variables and Modifiers | 34 | 1.36% | 2 | 9 | 14 | 6 | 5 |
| Search Commands | 1708 | 68.35% | 154 | 434 | 418 | 434 | 422 |
| Internal Commands | 86 | 3.44% | 10 | 22 | 24 | 21 | 19 |
| Search in the CLI | 16 | 0.64% | 2 | 4 | 1 | 6 | 5 |

## Distribution by subtopic

Every SPL command, eval-function category, and manual subsection got its own subtopic, sized by its page span in the manual.

### Introduction (18 questions, 3 subtopics)

| Subtopic | Questions | % of total |
|---|---|---|
| Understanding SPL syntax | 10 | 0.4% |
| How to use this manual | 5 | 0.2% |
| Welcome to the Search Reference | 3 | 0.12% |

### Quick Reference (95 questions, 5 subtopics)

| Subtopic | Questions | % of total |
|---|---|---|
| Commands by category | 31 | 1.24% |
| Command quick reference | 24 | 0.96% |
| Splunk SPL for SQL users | 21 | 0.84% |
| Command types | 16 | 0.64% |
| Splunk Quick Reference Guide | 3 | 0.12% |

### Evaluation Functions (395 questions, 13 subtopics)

| Subtopic | Questions | % of total |
|---|---|---|
| JSON functions | 74 | 2.961% |
| Conversion functions | 47 | 1.881% |
| Evaluation functions | 44 | 1.761% |
| Comparison and Conditional functions | 44 | 1.761% |
| Multivalue eval functions | 39 | 1.561% |
| Bitwise functions | 29 | 1.16% |
| Informational functions | 26 | 1.04% |
| Mathematical functions | 21 | 0.84% |
| Date and Time functions | 18 | 0.72% |
| Trig and Hyperbolic functions | 18 | 0.72% |
| Text functions | 17 | 0.68% |
| Statistical eval functions | 10 | 0.4% |
| Cryptographic functions | 8 | 0.32% |

### Statistical and Charting Functions (147 questions, 5 subtopics)

| Subtopic | Questions | % of total |
|---|---|---|
| Aggregate functions | 68 | 2.721% |
| Time functions | 29 | 1.16% |
| Statistical and charting functions | 21 | 0.84% |
| Event order functions | 21 | 0.84% |
| Multivalue stats and chart functions | 8 | 0.32% |

### Time Format Variables and Modifiers (34 questions, 2 subtopics)

| Subtopic | Questions | % of total |
|---|---|---|
| Time modifiers | 18 | 0.72% |
| Date and time format variables | 16 | 0.64% |

### Search Commands (1708 questions, 154 subtopics)

| Subtopic | Questions | % of total |
|---|---|---|
| timechart | 50 | 2.001% |
| tstats | 50 | 2.001% |
| chart | 44 | 1.761% |
| foreach | 44 | 1.761% |
| stats | 40 | 1.601% |
| mstats | 39 | 1.561% |
| transaction | 37 | 1.481% |
| streamstats | 35 | 1.401% |
| eval | 34 | 1.361% |
| search | 30 | 1.2% |
| makeresults | 29 | 1.16% |
| collect | 26 | 1.04% |
| spath | 25 | 1.0% |
| eventstats | 24 | 0.96% |
| join | 21 | 0.84% |
| predict | 21 | 0.84% |
| sendemail | 21 | 0.84% |
| rex | 20 | 0.8% |
| dbinspect | 18 | 0.72% |
| lookup | 18 | 0.72% |
| outputlookup | 18 | 0.72% |
| selfjoin | 18 | 0.72% |
| union | 17 | 0.68% |
| append | 16 | 0.64% |
| concurrency | 16 | 0.64% |
| datamodel | 16 | 0.64% |
| geom | 16 | 0.64% |
| geostats | 16 | 0.64% |
| iplocation | 16 | 0.64% |
| tojson | 16 | 0.64% |
| transpose | 16 | 0.64% |
| typeahead | 16 | 0.64% |
| untable | 16 | 0.64% |
| addtotals | 13 | 0.52% |
| anomalies | 13 | 0.52% |
| anomalousvalue | 13 | 0.52% |
| associate | 13 | 0.52% |
| convert | 13 | 0.52% |
| delta | 13 | 0.52% |
| erex | 13 | 0.52% |
| eventcount | 13 | 0.52% |
| fieldformat | 13 | 0.52% |
| fillnull | 13 | 0.52% |
| format | 13 | 0.52% |
| inputcsv | 13 | 0.52% |
| inputlookup | 13 | 0.52% |
| mcollect | 13 | 0.52% |
| metadata | 13 | 0.52% |
| meventcollect | 13 | 0.52% |
| mpreview | 13 | 0.52% |
| sort | 13 | 0.52% |
| tags | 13 | 0.52% |
| timewrap | 13 | 0.52% |
| top | 13 | 0.52% |
| xyseries | 12 | 0.48% |
| anomalydetection | 10 | 0.4% |
| bin | 10 | 0.4% |
| cluster | 10 | 0.4% |
| contingency | 10 | 0.4% |
| dedup | 10 | 0.4% |
| extract | 10 | 0.4% |
| from | 10 | 0.4% |
| head | 10 | 0.4% |
| history | 10 | 0.4% |
| map | 10 | 0.4% |
| mvcombine | 10 | 0.4% |
| outputcsv | 10 | 0.4% |
| rangemap | 10 | 0.4% |
| regex | 10 | 0.4% |
| rest | 10 | 0.4% |
| set | 10 | 0.4% |
| table | 10 | 0.4% |
| walklex | 10 | 0.4% |
| where | 10 | 0.4% |
| abstract | 8 | 0.32% |
| addcoltotals | 8 | 0.32% |
| cofilter | 8 | 0.32% |
| delete | 8 | 0.32% |
| fields | 8 | 0.32% |
| fieldsummary | 8 | 0.32% |
| folderize | 8 | 0.32% |
| gentimes | 8 | 0.32% |
| ingestpreview | 8 | 0.32% |
| kvform | 8 | 0.32% |
| loadjob | 8 | 0.32% |
| makecontinuous | 8 | 0.32% |
| multikv | 8 | 0.32% |
| mvexpand | 8 | 0.32% |
| pivot | 8 | 0.32% |
| rare | 8 | 0.32% |
| reltime | 8 | 0.32% |
| rename | 8 | 0.32% |
| replace | 8 | 0.32% |
| return | 8 | 0.32% |
| xpath | 8 | 0.32% |
| addinfo | 5 | 0.2% |
| analyzefields | 5 | 0.2% |
| appendcols | 5 | 0.2% |
| appendpipe | 5 | 0.2% |
| bucketdir | 5 | 0.2% |
| correlate | 5 | 0.2% |
| diff | 5 | 0.2% |
| fromjson | 5 | 0.2% |
| gauge | 5 | 0.2% |
| kmeans | 5 | 0.2% |
| localize | 5 | 0.2% |
| metasearch | 5 | 0.2% |
| multisearch | 5 | 0.2% |
| outlier | 5 | 0.2% |
| savedsearch | 5 | 0.2% |
| script | 5 | 0.2% |
| scrub | 5 | 0.2% |
| searchtxn | 5 | 0.2% |
| sendalert | 5 | 0.2% |
| sirare | 5 | 0.2% |
| sitimechart | 5 | 0.2% |
| sitop | 5 | 0.2% |
| strcat | 5 | 0.2% |
| tscollect | 5 | 0.2% |
| typer | 5 | 0.2% |
| xmlkv | 5 | 0.2% |
| makemv | 4 | 0.16% |
| accum | 3 | 0.12% |
| arules | 3 | 0.12% |
| autoregress | 3 | 0.12% |
| awssnsalert | 3 | 0.12% |
| bucket | 3 | 0.12% |
| ctable | 3 | 0.12% |
| dbxquery | 3 | 0.12% |
| entitymerge | 3 | 0.12% |
| filldown | 3 | 0.12% |
| findtypes | 3 | 0.12% |
| geomfilter | 3 | 0.12% |
| highlight | 3 | 0.12% |
| iconify | 3 | 0.12% |
| inputintelligence | 3 | 0.12% |
| localop | 3 | 0.12% |
| msearch | 3 | 0.12% |
| nomv | 3 | 0.12% |
| outputtext | 3 | 0.12% |
| overlap | 3 | 0.12% |
| require | 3 | 0.12% |
| reverse | 3 | 0.12% |
| rtorder | 3 | 0.12% |
| setfields | 3 | 0.12% |
| sichart | 3 | 0.12% |
| sistats | 3 | 0.12% |
| trendline | 3 | 0.12% |
| typelearner | 3 | 0.12% |
| uniq | 3 | 0.12% |
| x11 | 3 | 0.12% |
| xmlunescape | 3 | 0.12% |
| run | 1 | 0.04% |
| snowincident | 1 | 0.04% |

### Internal Commands (86 questions, 10 subtopics)

| Subtopic | Questions | % of total |
|---|---|---|
| noop | 18 | 0.72% |
| redistribute | 18 | 0.72% |
| mcatalog | 13 | 0.52% |
| makejson | 10 | 0.4% |
| prjob | 8 | 0.32% |
| dump | 5 | 0.2% |
| findkeywords | 5 | 0.2% |
| About internal commands | 3 | 0.12% |
| collapse | 3 | 0.12% |
| runshellscript | 3 | 0.12% |

### Search in the CLI (16 questions, 2 subtopics)

| Subtopic | Questions | % of total |
|---|---|---|
| Syntax for searches in the CLI | 13 | 0.52% |
| About searches in the CLI | 3 | 0.12% |
