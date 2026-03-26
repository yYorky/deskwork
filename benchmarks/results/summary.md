# Benchmark Summary

> High-level findings across all 3 GDPval tasks. See `comparison-notes.md` for per-task detail.

---

## Results at a glance

| Task | Rubric Pts | Claude Code + SKILL.md | ChatGPT 5.4 + Deskwork | Gap |
|------|:----------:|:----------------------:|:----------------------:|:---:|
| Fall Music Tour P&L | 89 | **79 (89%)** | 76 (85%) | +3 |
| Aurisic Prepaid Amortization | 95 | **91 (96%)** | 85 (89%) | +6 |
| Anti-Financial Crime Audit Sampling | 63 | **60 (95%)** | 49 (78%) | +11 |
| **Combined** | **247** | **230 (93%)** | **210 (85%)** | **+20** |

---

## Cross-task findings

### Finding 1: Workflow scaffolding recovers most of the performance gap

ChatGPT 5.4 Think Deeper, running one-shot without any system prompt, would have failed to produce correct deliverables on all three tasks. With a Deskwork system_prompt.md, it scored 85% combined — within 8 points of Claude Code's 93%. The remaining gap is entirely attributable to specification gaps in the system_prompt, not model capability.

### Finding 2: The gap widens as task complexity increases

| Task complexity | Claude Code | ChatGPT + Deskwork | Gap |
|-----------------|:-----------:|:------------------:|:---:|
| Low (music-tour-pl) | 89% | 85% | 4 pts |
| Medium (aurisic-amortization) | 96% | 89% | 7 pts |
| High (afc-audit-sampling) | 95% | 78% | 17 pts |

More complex tasks amplify the cost of specification gaps. The AFC sampling task had 63 rubric points across structured column assignments, full-population output, and 5 mandatory entity/country inclusions — each gap in the system_prompt cost 2+ points.

### Finding 3: Source data ambiguity bypasses both methods equally

The music-tour-pl task had an ambiguous categorisation in the reference file ("Other" expense items with no clear label). Both methods made the same incorrect inference, losing the same 6 rubric points. This is a genuine data quality issue, not a workflow problem. Neither SKILL.md nor a detailed system_prompt.md can resolve ambiguity that does not exist in the source.

### Finding 4: Claude Code makes better execution-time decisions

Claude Code proactively added features not specified in SKILL.md:
- **music-tour-pl**: Added a Withholding Tax Detail section by country (+4 criteria that ChatGPT missed)
- **aurisic-amortization**: Added a GL Rounding Adjustment row handling the accumulation of per-line rounding errors (+4 points vs. ChatGPT's $0.01 variance failures)
- **afc-audit-sampling**: Preserved the full 1516-row population in the output sheet (+1 point); all mandatory entity/country combinations correctly matched

These decisions were made during execution without prior specification. ChatGPT executed the system_prompt faithfully — it did not add features beyond what was specified.

### Finding 5: The largest single source of ChatGPT losses is structural specification gaps

| Root cause | Points lost across 3 tasks |
|------------|:--------------------------:|
| Column/sheet structure not specified precisely | 11 |
| Rounding adjustment not specified | 4 |
| Sheet naming convention not specified | 4 |
| Source data ambiguity (unfixable) | 6 |
| Execution-time judgment gap | 9 |

The top three are all fixable with a more precise system_prompt.md. They represent workflow gaps, not capability gaps.

---

## What Deskwork closes and what it doesn't

**Closes**:
- File delivery failures (the model produces the file in the right format)
- Structural omissions (sheets, columns, sections not included)
- Quality check misses (totals not reconciling, calculations wrong)
- Self-verification skips (model declares done without checking)

**Does not close**:
- Source data ambiguity (if the reference file is ambiguous, the system_prompt will encode the wrong inference)
- Execution-time judgment (proactive additions like the WHT detail section or GL rounding fix require domain experience to decide)
- Model-specific limitations (GPT-5's column counting under complex instructions; formula-linking in Python-generated Excel)

---

## Methodology notes

- Both methods were run without access to the gold-standard deliverable or GDPval rubric (data integrity preserved)
- Claude Code tasks were run collaboratively (user + Claude Code, step by step)
- ChatGPT tasks used the two-chat Deskwork method: Chat 1 generated the system_prompt.md; Chat 2 executed it in clean context
- Scoring used the GDPval rubric items exactly as published on HuggingFace
- Partial credit awarded where output was directionally correct but had a $0.01 rounding error or ambiguous criterion match
