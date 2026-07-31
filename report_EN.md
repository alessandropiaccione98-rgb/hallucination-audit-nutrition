# Hallucination Audit: Hygiene, Food Safety, and Human Nutrition

**A comparison of Claude, ChatGPT, and Gemini across 20 domain-specific questions**

---

## 1. Executive Summary

I tested 20 questions covering food hygiene and human nutrition across three
LLMs (Claude, ChatGPT, Gemini), evaluating each response using my own domain
expertise against a 6-tier scoring rubric. Out of 60 total responses,
**Claude and ChatGPT were correct in 95% of cases** (19/20 each, with one
"correct but incomplete" answer apiece), while **Gemini was correct in 55%
of cases**, with 5 specific and verifiable factual errors (25%) and 4
further cases of incomplete answers or calibration issues (20%). The most
interesting finding isn't the raw percentage, though, but the **systematic
nature** of several of Gemini's errors — often not outright fabrications,
but regulatory or mechanistic categorization mistakes that require domain
expertise to catch.

## 2. Methodology

- **Domain**: Hygiene, Food Safety, and Human Nutrition, chosen as a field
  the author can independently verify (background in Biological Sciences)
- **Models tested**: Claude, ChatGPT, Gemini (free tiers)
- **Questions**: 20, spread across 6 thematic categories (food safety,
  macronutrients, micronutrients, special diets/intolerances, food
  labeling, nutritional guidelines)
- **Procedure**: each question was asked in a fresh chat per model, to
  avoid context effects between questions; responses were recorded in full
  before evaluation; data collection took place across multiple sessions to
  work within free-tier usage limits
- **Evaluation rubric**: Correct / Correct but incomplete / Minor factual
  error / Major factual error / Hallucination / Refusal-evasion, assigned
  by the author as the expert "ground truth," with verification against
  authoritative sources (EU regulations, WHO, national/EU nutrition
  reference bodies) in ambiguous cases

## 3. Aggregate Results

| Model | Correct | Correct but incomplete | Calibration note | Minor factual error |
|---|---|---|---|---|
| **Claude** | 19 (95%) | 1 (5%) | — | — |
| **ChatGPT** | 19 (95%) | 1 (5%) | — | — |
| **Gemini** | 11 (55%) | 3 (15%) | 1 (5%) | 5 (25%) |

None of the three models produced an outright hallucination (inventing a
nonexistent study, guideline, or figure) across this question set — a
notable result in itself, suggesting that on a well-documented and
well-regulated domain (nutrition, EU food labeling) these models draw on
solid underlying information rather than confabulating. The errors observed
were almost always **precision or categorization errors**, not
fabrications.

## 4. Notable Cases

### 4.1 — Categorization error: spinach and oxalates (Question 9, Gemini)
Asked what inhibits non-heme iron absorption, Gemini classified spinach
under "polyphenols and tannins," while the actual mechanism behind
spinach's iron-inhibiting effect is **oxalates** — a distinct chemical
category. Claude correctly classified oxalates as their own category. A
mechanism-level error, not a surface-level one.

### 4.2 — Regulatory confusion: "sugar-free" vs. "low-sugar" thresholds (Question 15, Gemini)
Gemini conflated two distinct EU nutrition claims — "sugar-free" (actual
threshold: ≤0.5g/100g) and "low sugar" (actual threshold: ≤5g/100g, ten
times higher) — under a single 0.5g threshold, repeating the same error for
fat claims. An error verifiable directly against the text of Regulation
(EC) No 1924/2006.

### 4.3 — Mechanism misapplied: "source of fiber" criteria (Question 17, Gemini)
The numeric values themselves were all correct (3g/100g, 1.5g/100kcal,
etc.), but Gemini presented the two criteria as specific to product type
(solids → g/100g, liquids → kcal), when the regulation actually offers them
as alternative routes available to any food. An error the numbers alone
don't reveal — it requires understanding how the rule is actually applied.

### 4.4 — Internal inconsistency on the highest-stakes figure in the set (Question 18, Gemini)
On folic acid in pregnancy — arguably the single most public-health-critical
figure in the entire dataset — Gemini stated the requirement "almost
doubles," but then cited the same baseline value (400 μg/day) as the
recommended pregnancy dose, never stating the actual increase to ~600
μg/day that both Claude and ChatGPT correctly reported.

### 4.5 — Wrong acronym (Question 19, Gemini)
The heterocyclic amines produced by high-temperature cooking were labeled
with the acronym "AHA" instead of the correct **HCA** (Heterocyclic
Amines) — a small but concrete notational error.

### 4.6 — Overconfidence on contested evidence (Questions 7 and 14, Gemini)
Two parallel cases: on intermittent fasting and on the ketogenic diet,
Gemini presented associations with genuinely mixed scientific evidence
(LDL cholesterol effects; the red meat–prostate/pancreatic cancer link)
with more certainty than current literature supports. These aren't
hallucinations in the strict sense — the phenomena described are real —
but a subtler failure mode: overconfidence about what remains scientifically
debated. Notably, **Claude fell into the same pattern once as well**
(hepatic steatosis from ketogenic diets, Question 14).

### 4.7 — A formatting bug, not a content error (Question 1, Gemini)
Worth flagging separately since it isn't a knowledge error: in the response
on food storage temperatures, Gemini displayed raw, unrendered LaTeX code
(`\textdegreeC`) — an interface issue, not an accuracy issue with the
underlying content (which was correct).

### 4.8 — A meaningful omission (Question 2, Claude)
Even the more reliable models had a weak moment: on the safety of raw fish
regarding Anisakis, Claude correctly flagged the limitations of home
freezers, but omitted the well-known practical alternative (-18°C for 96
hours) recommended by public health authorities specifically for people
without access to professional blast chillers — information that both
ChatGPT and Gemini provided correctly.

## 5. Conclusions

- On a well-regulated, well-documented domain like food hygiene and
  nutrition, **none of the three models produced genuine hallucinations**
  (invented data or nonexistent sources) across 60 tested responses.
- **Claude and ChatGPT showed essentially equivalent reliability** (95%
  correct responses), with differences that were minor and complementary
  in depth of detail rather than in correctness.
- **Gemini showed a significantly higher error rate** (25% minor factual
  errors), concentrated not in fabrications but in **categorization and
  mechanism/regulation-application errors** — a more insidious failure mode,
  since the surrounding content "sounds" competent and often includes
  accurate details in the very same response.
- A cross-cutting pattern worth noting: **overconfidence on scientifically
  contested topics** appeared both in Gemini (2 cases) and, once, in Claude
  — suggesting this failure mode isn't specific to a single model, but a
  structural risk whenever an LLM has to communicate genuine scientific
  uncertainty.
- The value of a domain-literate red teamer is clear throughout this audit:
  most of the errors identified (oxalate/polyphenol categorization, merged
  regulatory thresholds, regulatory criteria applied to the wrong product
  type) **would not have been catchable by a generic evaluator** without
  specific subject-matter knowledge.

---

*Full dataset (60 evaluated responses) available in `results.csv`.
Detailed methodology and question bank in
`progetto1_hallucination_audit.md`.*
