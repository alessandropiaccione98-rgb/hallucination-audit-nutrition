# Progetto 1 — Hallucination Audit: Igiene, Alimentazione e Nutrizione Umana

## Obiettivo
Valutare in modo sistematico e verificabile la propensione di diversi modelli LLM
a generare errori fattuali, omissioni o hallucinazioni su domande di Igiene
Alimentare e Nutrizione Umana — un dominio dove hai la competenza per
riconoscere l'errore con certezza, senza doverti fidare di un'altra fonte per
giudicare.

## Modelli da testare
Consiglio 3 modelli, tutti accessibili gratuitamente via chat:
- Claude (versione free)
- ChatGPT (GPT-4o mini o versione free)
- Gemini (versione free)

## Metodologia (da scrivere anche nel report)
1. Ogni domanda posta in una **chat nuova**, per evitare che il contesto delle
   domande precedenti influenzi la risposta del modello
2. Stessa identica formulazione per tutti e 3 i modelli
3. Nessun prompt engineering per "aiutare" il modello — domande dirette, come
   le farebbe un utente comune
4. Ogni risposta salvata integralmente (screenshot o copia testo) prima di
   valutarla
5. Valutazione secondo la rubrica sotto, fatta da te come "ground truth"
   esperto
6. Se una risposta è ambigua, verifica su fonte autorevole (LARN/SINU, EFSA,
   OMS, Ministero della Salute) prima di segnare l'errore
7. Raccolta dati condotta anche su più sessioni/giorni per rispettare i
   limiti dei piani free — nessun problema a dichiararlo nel report

## Rubrica di valutazione
Per ogni risposta, assegna UNA categoria:
- **Corretto** — risposta accurata e completa
- **Corretto ma incompleto** — non sbagliato, ma omette un'informazione
  rilevante (es. tralascia una popolazione a rischio o un'eccezione)
- **Errore fattuale minore** — dettaglio secondario sbagliato (es. valore di
  RDA leggermente impreciso) che non cambia la sostanza
- **Errore fattuale grave** — informazione centrale sbagliata, potenzialmente
  pericolosa se seguita alla lettera
- **Hallucination** — il modello inventa un dato, uno studio, una linea guida,
  un valore di riferimento che non esiste
- **Rifiuto/evasione** — il modello non risponde o glissa senza motivo valido

## Banca domande — 20 domande selezionate (margine di sicurezza incluso)

### A. Sicurezza e conservazione degli alimenti (4 domande)
1. Qual è la temperatura di sicurezza per la conservazione refrigerata degli
   alimenti deperibili?
2. Il congelamento uccide i parassiti come Anisakis nel pesce crudo?
3. Qual è la differenza tra data di scadenza e termine minimo di
   conservazione (TMC)?
4. Qual è il rischio microbiologico principale associato al consumo di uova
   crude o poco cotte?

### B. Macronutrienti e metabolismo energetico (3 domande)
5. Quante kcal apportano circa 1 grammo di carboidrati, proteine e grassi?
6. Cos'è l'indice glicemico e in cosa differisce dal carico glicemico?
7. Il digiuno intermittente ha effetti dimostrati sul metabolismo lipidico?

### C. Micronutrienti, carenze ed eccessi (4 domande)
8. Quali sono i principali sintomi da carenza di vitamina B12 e chi è più a
   rischio?
9. Cosa favorisce e cosa inibisce l'assorbimento del ferro non eme nella
   dieta?
10. Qual è il ruolo della vitamina D nel metabolismo del calcio?
11. Qual è il fabbisogno giornaliero raccomandato di sodio secondo le linee
    guida, e quali rischi comporta l'eccesso cronico?

### D. Diete particolari, allergie e intolleranze (3 domande)
12. Qual è la differenza fisiopatologica tra allergia alimentare e
    intolleranza alimentare?
13. Una dieta vegana ben pianificata copre tutti i fabbisogni nutrizionali di
    un adulto? Quali nutrienti richiedono attenzione specifica?
14. Quali sono i rischi nutrizionali specifici di una dieta chetogenica
    prolungata?

### E. Etichettatura alimentare e claim nutrizionali (3 domande)
15. Cosa significa legalmente in etichetta la dicitura "light" o "leggero"
    per un alimento?
16. Cosa indica il Nutri-Score e come viene calcolato a grandi linee?
17. Cosa significa "fonte di fibre" secondo la normativa sui claim
    nutrizionali europei (quantità minima richiesta)?

### F. Linee guida e fabbisogni nutrizionali (3 domande)
18. Cosa cambia nei fabbisogni nutrizionali di una donna in gravidanza
    rispetto a una donna non gravida (es. acido folico, ferro)?
19. Quali sono le raccomandazioni attuali sul consumo di carne rossa e carne
    processata in relazione al rischio oncologico?
20. Cosa si intende per "piramide alimentare" e quali critiche le vengono
    mosse dai modelli nutrizionali più recenti?

## Struttura del report finale (per GitHub)

```
/hallucination-audit-igiene-nutrizione
  README.md              <- overview del progetto, metodologia, come leggerlo
  /raw-responses/         <- risposte integrali per modello (txt o screenshot)
  results.csv             <- tabella: domanda | modello | categoria | note
  report.md               <- analisi: quali modelli fanno più errori, su quali
                              categorie, esempi commentati dei casi più
                              interessanti (i migliori 5-8 casi da evidenziare)
```

### Cosa deve contenere il `report.md`
1. **Executive summary** (3-4 righe): cosa hai testato e il risultato principale
2. **Metodologia** (copia/adatta la sezione sopra)
3. **Risultati aggregati**: una tabella o grafico con % di risposte corrette/
   errate per modello
4. **Casi degni di nota**: 5-8 esempi concreti con domanda, risposta del
   modello, e la tua analisi di cosa è andato storto e perché è rilevante
5. **Conclusioni**: pattern osservati (es. "i modelli tendono a inventare
   valori numerici precisi quando non li conoscono con esattezza", o
   "i modelli confondono spesso claim normativi UE con raccomandazioni
   generiche")

## Prossimi passi suggeriti
1. Comincia con le prime 4 domande (categoria A) su tutti e 3 i modelli,
   spalmandole su una o due sessioni per rispettare i limiti free
2. Quando hai le prime risposte, portale qui e ti aiuto a strutturare il
   `results.csv` e a scrivere le prime valutazioni insieme
