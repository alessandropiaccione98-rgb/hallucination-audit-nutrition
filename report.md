# Hallucination Audit: Igiene, Alimentazione e Nutrizione Umana

**Confronto tra Claude, ChatGPT e Gemini su 20 domande di dominio nutrizionale/igienico-sanitario**

---

## 1. Executive Summary

Ho sottoposto 20 domande di igiene alimentare e nutrizione umana a tre modelli
LLM (Claude, ChatGPT, Gemini), valutando ogni risposta con la mia competenza
di dominio secondo una rubrica a 6 livelli. Su 60 risposte totali, **Claude e
ChatGPT sono risultati corretti nel 95% dei casi** (19/20, con un'unica
risposta "corretta ma incompleta" ciascuno), mentre **Gemini è risultato
corretto nel 55% dei casi**, con 5 errori fattuali specifici e verificabili
(25%) e altri 4 casi di risposte incomplete o con problemi di calibrazione
(20%). Il dato più interessante non è però la percentuale in sé, ma la
**natura sistematica** di alcuni errori di Gemini — spesso non invenzioni
grossolane, ma confusioni di categorizzazione normativa o meccanicistica che
richiedono competenza di dominio per essere individuate.

## 2. Metodologia

- **Dominio**: Igiene, Alimentazione e Nutrizione Umana, scelto come campo di
  competenza verificabile dall'autore (percorso di studi in Scienze
  Biologiche)
- **Modelli testati**: Claude, ChatGPT, Gemini (versioni free)
- **Domande**: 20, distribuite su 6 categorie tematiche (sicurezza alimenti,
  macronutrienti, micronutrienti, diete/intolleranze, etichettatura, linee
  guida nutrizionali)
- **Procedura**: ogni domanda posta in una chat nuova per ciascun modello,
  per evitare effetti di contesto tra domande; risposte raccolte
  integralmente prima della valutazione; raccolta condotta su più sessioni
  per rispettare i limiti dei piani free
- **Rubrica di valutazione**: Corretto / Corretto ma incompleto / Errore
  fattuale minore / Errore fattuale grave / Hallucination / Rifiuto-evasione,
  assegnata dall'autore come "ground truth" esperto, con verifica su fonti
  autorevoli (Reg. UE, OMS, LARN/SINU, EFSA) nei casi ambigui

## 3. Risultati Aggregati

| Modello | Corretto | Corretto ma incompleto | Nota di calibrazione | Errore fattuale minore |
|---|---|---|---|---|
| **Claude** | 19 (95%) | 1 (5%) | — | — |
| **ChatGPT** | 19 (95%) | 1 (5%) | — | — |
| **Gemini** | 11 (55%) | 3 (15%) | 1 (5%) | 5 (25%) |

Nessuno dei tre modelli ha prodotto una hallucination netta (invenzione di
uno studio, una linea guida o un dato inesistente) su questo set di domande —
un risultato di per sé degno di nota, che suggerisce che su un dominio ben
documentato e normato (nutrizione, etichettatura UE) i modelli attingono a
informazioni solide piuttosto che confabulare. Gli errori osservati sono
quasi sempre **errori di precisione o di categorizzazione**, non invenzioni.

## 4. Casi Degni di Nota

### 4.1 — Errore di categorizzazione: spinaci e ossalati (Domanda 9, Gemini)
Alla domanda su cosa inibisce l'assorbimento del ferro non eme, Gemini ha
classificato gli spinaci sotto "polifenoli e tannini", mentre il meccanismo
noto per cui gli spinaci inibiscono l'assorbimento del ferro è legato agli
**ossalati** — categoria chimica distinta. Claude ha classificato
correttamente gli ossalati come categoria a sé. Un errore di meccanismo, non
di superficie.

### 4.2 — Confusione normativa: soglie "senza" vs "a basso contenuto" (Domanda 15, Gemini)
Gemini ha fuso due claim nutrizionali UE distinti — "senza zuccheri" (soglia
reale: ≤0,5g/100g) e "a basso contenuto di zuccheri" (soglia reale:
≤5g/100g, dieci volte superiore) — sotto un'unica soglia di 0,5g, ripetendo
lo stesso errore per i grassi. Un errore verificabile con il testo del
Regolamento (CE) 1924/2006 alla mano.

### 4.3 — Meccanismo applicato in modo scorretto: criteri "fonte di fibre" (Domanda 17, Gemini)
I valori numerici erano tutti corretti (3g/100g, 1,5g/100kcal, ecc.), ma
Gemini ha presentato i due criteri come specifici per tipo di prodotto
(solidi → g/100g, liquidi → kcal), quando la normativa li offre come
alternativi per qualsiasi alimento. Un errore che i soli numeri non
rivelano — serve capire come la regola si applica.

### 4.4 — Incongruenza interna sul dato più critico (Domanda 18, Gemini)
Sull'acido folico in gravidanza — probabilmente il singolo dato nutrizionale
con più impatto sulla salute pubblica nell'intero dataset — Gemini ha
dichiarato che il fabbisogno "raddoppia quasi", ma poi ha citato lo stesso
valore di partenza (400 μg/die) come dose raccomandata, senza mai indicare
l'aumento reale a ~600 μg/die che sia Claude che ChatGPT hanno riportato
correttamente.

### 4.5 — Acronimo errato (Domanda 19, Gemini)
Le ammine eterocicliche prodotte dalla cottura ad alte temperature sono
state etichettate con l'acronimo "AHA" invece del corretto **HCA**
(Heterocyclic Amines) — un piccolo ma concreto errore notazionale.

### 4.6 — Overconfidence su evidenza dibattuta (Domande 7 e 14, Gemini)
Due casi paralleli: sul digiuno intermittente e sulla dieta chetogenica,
Gemini ha presentato associazioni con evidenza scientifica mista (effetto
sul colesterolo LDL; legame carne rossa-tumori a prostata/pancreas) con più
sicurezza di quanto la letteratura attuale giustifichi. Non sono
hallucination in senso stretto — i fenomeni descritti esistono — ma un tipo
di errore più sottile: la sovra-sicurezza su ciò che è ancora dibattuto.
Interessante notare che **anche Claude è caduto nello stesso pattern una
volta** (steatosi epatica da dieta chetogenica, Domanda 14).

### 4.7 — Bug di formattazione, non di contenuto (Domanda 1, Gemini)
Da segnalare separatamente perché non è un errore di conoscenza: nella
risposta sulle temperature di conservazione degli alimenti, Gemini ha
mostrato codice LaTeX grezzo non renderizzato (`\textdegreeC`) — un problema
di interfaccia, non di accuratezza del contenuto sottostante (che era
corretto).

### 4.8 — Un'omissione informativa rilevante (Domanda 2, Claude)
Anche i modelli più affidabili hanno avuto un momento debole: sulla
sicurezza del pesce crudo rispetto all'Anisakis, Claude ha correttamente
segnalato i limiti dei freezer domestici, ma ha omesso l'alternativa pratica
nota (-18°C per 96 ore) raccomandata dal Ministero della Salute proprio per
chi non ha un abbattitore professionale — un'informazione che sia ChatGPT
che Gemini hanno fornito correttamente.

## 5. Conclusioni

- Su un dominio ben normato e documentato come nutrizione/igiene alimentare,
  **nessuno dei tre modelli ha prodotto hallucination vere e proprie**
  (invenzione di dati/fonti inesistenti) su 60 risposte testate.
- **Claude e ChatGPT hanno mostrato affidabilità sostanzialmente equivalente**
  (95% di risposte corrette), con differenze minime e complementari nella
  profondità di dettaglio più che nella correttezza.
- **Gemini ha mostrato un tasso di errore significativamente più alto**
  (25% di errori fattuali minori), concentrato non su invenzioni ma su
  **errori di categorizzazione e applicazione di meccanismi/normative** —
  un tipo di errore più insidioso perché il contenuto "suona" competente e
  spesso include anche dettagli accurati nella stessa risposta.
- Un pattern trasversale rilevante: la **sovra-sicurezza (overconfidence)
  su temi scientificamente dibattuti** è emersa sia in Gemini (2 casi) sia,
  una volta, in Claude — suggerendo che questo tipo di errore non è
  specifico di un modello, ma un rischio strutturale quando un LLM deve
  comunicare incertezza scientifica genuina.
- Il valore di un red teamer con competenza di dominio emerge chiaramente
  in questo audit: la maggior parte degli errori individuati (categorizzazione
  ossalati/polifenoli, soglie normative fuse, criteri normativi applicati al
  tipo sbagliato di prodotto) **non sarebbe stata rilevabile da un
  valutatore generico** senza conoscenza specifica della materia.

---

*Dataset completo (60 risposte valutate) disponibile in `results.csv`.
Metodologia dettagliata e banca domande in `progetto1_hallucination_audit.md`.*
