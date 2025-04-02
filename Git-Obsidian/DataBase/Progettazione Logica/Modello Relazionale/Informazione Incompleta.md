>Le informazioni che si vogliono rappresentare mediante [[Modello Relazionale#Relazione|relazioni]] non sempre *corrispondono pienamente* allo **schema** prescelto
- Alcune **tuple** e per alcuni **attributi** potrebbe non essere possibile specificare un valore del [[Modello Relazionale#Dominio di un attributo|dominio]].

## Ennupla Senza Informazione
---
### Casi
> Ci sono 3 casi per cui un valore è senza informazione:

>[!example] Esempio
>Prendiamo come esempio la seguente tabella $R(X)$:
>- $R$ -> Persone
>- $X$ -> Codice, Cognome, Nome, DataMorte

Il valore "DataMorte" può non esserci per i seguenti motivi:

>[!question] Valore non noto
>Il valore è **applicabile ma ignoto**
>- "Bruno Bianchi" è deceduto ma ***non conosciamo*** la data di morte 

>[!missing] Valore inesistente
>Il valore **non è applicabile**
>- "Bruno Bianchi" è ***ancora vivo***

>[!summary] Valore senza informazione
>Il valore ha **ingnota applicabilità**
>- "Bruno Bianchi" è scomparso: ***Non sappiamo*** se è vivo o se è deceduto

### Soluzioni
>[!default] Applicare un valore di Default
>Ad ogni **mancanza di informazione** si applica un valore del [[Modello Relazionale#Dominio di un attributo|dominio]] di ***default***.
>>[!fail] Tecnica Sconsigliata


>[!quote] Valori Speciali
>Ad ogni **mancanza di informazione** si applicano ***valori speciali*** per ogni attributo.
>>[!fail] Sconsigliato
>>Valori inutilizzati **potrebbero diventare significativi**, e inoltre le applicazioni **devono essere al corrente** di questi valori.

#### Null
>Nel [[Modello Relazionale]] si adotta il concetto di **valore nullo** (`NULL`).

>[!definizione] Definizione
>Il ***valore nullo*** (`NULL`) denota *assenza di un valore* nel [[Modello Relazionale#Dominio di un attributo|dominio]].
>>[!attention] Attenzione
>>`NULL` ***non*** è un valore del domino.
>>Pertanto: $t[A]\in dom(A)\cup \{ \text{Null} \}$

Per definizione `NULL != NULL`.
- Due **tuple** uguali di una *relazione* che contengono un ***valore nullo*** **non** sono uguali per definizione.

>La presenza di valori nulli può **non** essere sempre tollerata.
- È necessario imporre delle [[Vincoli di Integrità|restrizioni]] al loro uso.