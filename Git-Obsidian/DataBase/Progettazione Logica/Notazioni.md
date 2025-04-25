## Chiavi
---

>[!info] Chiave Primaria
>Convenzionalmente si <u>sottolineano</u> gli attributi che costituiscono la [[Vincoli di Integrità#Chiavi|chiave]].

>[!example] Esempio

**AGENZIE**(<u>Agenzia</u>, Luogo)
### Unique
>Per denotare che un *attributo* $A$ ammette solo **valori unici**, si usa scrivere:
- *Unique*($A$)

>[!example] Esempio

**AGENZIE**(<u>CodAgenzia</u>, Nome, Sede, Direttore: **IMPIEGATI**)
*Unique*(Direttore)
### Foreign Key
> Si usano diverse notazioni per indicare nella definizione di uno schema le *foreign key*

>[!abstract] Notazione 1

**AGENZIE**(<u>Agenzia</u>, Luogo)
**IMPIEGATI**(<u>CodImpiegato</u>, Cognome, Nome, CodAgenzia)
***FK***: CodAgenzia *REFERENCES* **AGENZIE**(Agenzia)
- Oppure
***FK***: CodAgenzia *REFERENCES* **AGENZIE**

>[!hint] Altra Notazione

**AGENZIE**(<u>Agenzia</u>, Luogo)
**IMPIEGATI**(<u>Agenzia</u>, Cognome, Nome, CodAgenzia:**AGENZIE**)

>[!nota]
>Queste notazioni sono da intendersi come semplificazioni rispetto alla sintassi del linguaggio [[SQL]].

## Valori Null
---
>Nella definizione di schemi relazionali a volte si usa il simbolo ***\****
- Per denotare che è ammesso `NULL` come [[Informazione Incompleta|valore]].

>[!example] Esempi

**IMPIEGATI**(<u>Codice</u>, Nome, Cognome, Agenzia\*: **AGENZIE**, DataInizio\*)

