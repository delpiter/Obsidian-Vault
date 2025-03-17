## Fase di Ristrutturazione
---
>[!def] Definizione
>La ***ristrutturazione*** è una fase della [[Progettazione Logica]] che consiste nell'eliminazione dallo [[Modello Entity-Relationship|schema E/R]] dei *costrutti* che **non possono** essere direttamente rappresentati nel ***modello logico target*** ([[Modello Relazionale]]).

Si pone l'obbiettivo di *semplificare* la traduzione e [[Analisi dell'Efficienza|ottimizzare le prestazioni]]

## Eliminazione delle generalizzazioni

### "Collasso" sull’entità padre

Introduce:
- **Valori nulli**
- Un attributo aggiuntivo che indica di quale entità figlia si tratta

✅ **Pro:** Accesso contestuale agli attributi del padre e della figlia.
❌ **Contro:** Spreco di memoria per valori null.

### "Collasso" sulle entità figlie

Possibile solo se la generalizzazione è totale.

✅ **Pro:**
- Conveniente quando si fanno operazioni che coinvolgono le singole entità figlie.
- Non introduce valori nulli.

❌ **Contro:** Possibile solo se la generalizzazione è totale.

### Sostituzione della generalizzazione con relazioni

- Relazioni tra le entità figlie e l’entità padre.
- Necessità di introdurre vincoli:
  - Un’occorrenza dell’entità "padre" non può partecipare contemporaneamente alle relazioni figlie.
  - Se la generalizzazione è totale, ogni occorrenza dell’entità padre deve appartenere ad almeno una e al massimo una delle entità figlie.

✅ **Pro:**
- Conviene quando la generalizzazione non è totale.
- Non si introducono valori nulli.
- Genera entità con pochi attributi.

❌ **Contro:** Aumenta il numero di accessi per mantenere i vincoli introdotti.

---

## Eliminazione degli attributi multi-valore

- Non presenti nel modello logico, quindi vanno rimossi.
- Possono essere sostituiti introducendo una relazione **uno a molti**.
- Aumenta il numero di entità.

---

## Partizionamento e accorpamento di concetti

### Obiettivo:
Ridurre il numero di accessi. È necessario conoscere il volume dei dati.

### Partizionamento
Separazione degli attributi di un concetto che vengono acceduti separatamente.
- **Partizionamento verticale**: Separazione di un’entità sulla base dei suoi attributi.

### Accorpamento
- Raggruppamento di attributi di concetti diversi che vengono acceduti insieme.
- Generalmente riguarda associazioni **uno a uno**.

---

## Scelta degli identificatori

In caso di entità con più identificatori:
- **Necessario sceglierne uno.**
- Evitare attributi con valori nulli.
- Scegliere l’identificatore minimale.
- Preferire identificatori interni.
- Preferire identificatori utilizzati da molte operazioni.

---

## Analisi delle ridondanze

### Definizione
Informazione significativa ma derivabile da altre già presenti (**attributi derivabili**).

✅ **Vantaggi:**
- Operazioni sui dati spesso più efficienti.

❌ **Svantaggi:**
- Maggiore occupazione di memoria.
- Maggiore complessità degli aggiornamenti.

### Decisione
- Si calcola il costo e l’occupazione di memoria di entrambi gli schemi (con e senza ridondanze).
- Necessario disporre di **tabelle dei volumi e delle operazioni**.
- Frequenza delle operazioni.
- **Pesi delle operazioni:**
  - Lettura: **1**
  - Scrittura: **2**

---

# TRADUZIONE SCHEMA E/R

Necessità di tradurre i costrutti del modello E/R in costrutti del modello relazionale per garantire l’equivalenza.

### Traduzione con identificatore interno
- Le entità del modello E/R si traducono in tabelle.
- L’identificatore diventa **chiave primaria**.

### Traduzione con identificatore esterno
- Le entità con identificatore esterno si traducono in una tabella che include tra le chiavi gli identificatori dell’entità esterna.

### Traduzione di relazioni **molti a molti**
- La relazione diventa una tabella con la chiave costruita dalle chiavi delle entità coinvolte.

### Traduzione di relazioni **uno a molti**
**Due possibilità:**
1. Tradurre la relazione come una **tabella separata** (come nel caso molti a molti).
2. **Inglobare** la relazione nell’entità con cardinalità massima 1.

### Traduzione di relazioni **uno a uno**
**Tre possibilità a seconda della cardinalità minima:**
1. **Partecipazione obbligatoria per entrambe le entità:**
   - Si traduce inglobando la relazione in una delle due entità.
2. **Partecipazione obbligatoria per una sola entità:**
   - Si traduce inglobando la relazione nell’entità con partecipazione obbligatoria.
3. **Partecipazione facoltativa per entrambe le entità:**
   - Analogamente al caso **uno a molti**.
