> Si mappano i costrutti residui in elementi del [[Modello Relazionale]]

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
