# Hallucination Audit — Hygiene, Food Safety & Human Nutrition

🇮🇹 [Italiano](#italiano) · 🇬🇧 [English](#english)

---

## Italiano

### Cos'è questo progetto
Un audit indipendente e verificabile sull'accuratezza di tre modelli LLM
(**Claude, ChatGPT, Gemini**) su domande di igiene alimentare e nutrizione
umana — un dominio su cui posso valutare le risposte con competenza diretta
(percorso di studi in Scienze Biologiche).

20 domande, 3 modelli, 60 risposte valutate una per una con una rubrica a 6
livelli (da "Corretto" a "Hallucination"), verificando ogni caso ambiguo
contro fonti autorevoli (Regolamenti UE, OMS, LARN/SINU, EFSA).

### Risultato principale
Claude e ChatGPT corretti nel 95% dei casi; Gemini nel 55%, con errori
concentrati non su invenzioni ma su **categorizzazioni normative o
meccanicistiche sbagliate** — il tipo di errore che richiede competenza di
dominio per essere individuato.

### Contenuto del repository
| File | Descrizione |
|---|---|
| [`report.md`](./report.md) | Report completo in italiano: metodologia, risultati aggregati, casi commentati, conclusioni |
| [`report_EN.md`](./report_EN.md) | Versione inglese dello stesso report |
| [`results.csv`](./results.csv) | Dataset completo delle 60 valutazioni |
| [`progetto1_hallucination_audit.md`](./progetto1_hallucination_audit.md) | Metodologia dettagliata e banca domande originale |
| [`raw-responses/`](./raw-responses) | Screenshot/testo integrale delle risposte dei tre modelli |

### Autore
Alessandro Piaccione — AI Evaluator & Red Teamer (Outlier.ai, OneForma).
[www.linkedin.com/in/alessandro-piaccione-5780aa203] · [alessandro.piaccione98@gmail.com]

---

## English

### About this project
An independent, verifiable accuracy audit of three LLMs (**Claude, ChatGPT,
Gemini**) on food hygiene and human nutrition questions — a domain I can
evaluate with direct subject-matter expertise (background in Biological
Sciences).

20 questions, 3 models, 60 responses individually scored against a 6-tier
rubric (from "Correct" to "Hallucination"), with ambiguous cases verified
against authoritative sources (EU Regulations, WHO, national/EU nutrition
reference bodies).

### Headline result
Claude and ChatGPT were correct in 95% of cases; Gemini in 55%, with errors
concentrated not in fabrications but in **incorrect regulatory or
mechanistic categorization** — the kind of error that requires domain
expertise to catch.

### Repository contents
| File | Description |
|---|---|
| [`report.md`](./report.md) | Full report in Italian: methodology, aggregate results, notable cases, conclusions |
| [`report_EN.md`](./report_EN.md) | English version of the same report |
| [`results.csv`](./results.csv) | Full dataset of all 60 evaluations |
| [`progetto1_hallucination_audit.md`](./progetto1_hallucination_audit.md) | Detailed methodology and original question bank |
| [`raw-responses/`](./raw-responses) | Screenshots / full text of all three models' responses |

### Author
Alessandro Piaccione — AI Evaluator & Red Teamer (Outlier.ai, OneForma).
[www.linkedin.com/in/alessandro-piaccione-5780aa203] · [alessandro.piaccione98@gmail.com]
