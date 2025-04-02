>La ***correttezza sintattica*** di uno stato di una relazione non è condizione sufficiente affinché i dati rappresentino un'*informazione possibile*.

>[!definizione] Definizione
>Un ***vincolo di integrità*** è una *funzione booleana* che associa un’[[Modello Relazionale#Data Base Relazionale|istanza]] $r$ di un *database* definito su uno **schema** a un ***valore di verità***.
>>[!done] Istanza Lecita
>>Un'***istanza lecita*** è una istanza che **soddisfa i vincoli definiti**

## Tipologie di vincoli
---
### Intra-Relazionali
>I vincoli ***intra-relazionali*** si applicano sulla *singola tabella*.

#### Vincoli di Tupla

>[!summary] Vincoli di Tupla
>I ***vincoli di*** [[Modello Relazionale#Relazione|tupla]] sono vincoli che esprimono condizioni su *ciascuna tupla*, indipendentemente dalle altre, tramite **espressioni booleane**

>Esempio: Schema $R(X)$
>- $R$ -> Esami
>- $X$ -> $\{$ Matricola, CodCorso, Voto, Lode$\}$

La **lode** si può assegnare solo se il voto è $30$.
$$(\text{Voto}=30) \text{ or not }(\text{Lode}=true) $$

#### Vincoli di Chiave

>[!help] Vincoli di Chiave
> I ***vincoli di chiave*** garantiscono l'unicità delle [[Modello Relazionale#Relazione|tuple]].
> - Vietano la presenza di ***tuple distinte*** che hanno lo *stesso valore* su uno o più attributi.

> Esempio:
- In una tabella "*Studenti*"
	- Un valore di **matricola** identifica univocamente uno *studente*
	- Analogo per il ***codice fiscale***.

##### Chiavi
>[!definizione] Definizione
>Una ***chiave*** è un *insieme di attributi* che consente di **identificare univocamente** una tupla di una relazione.

> Viene usata per:
- Avere *accesso* a ciascuna **tupla** della base di dati.
- **Correlazione** dei dati tra *relazioni diverse*.

![[NamesAndID.png]]

###### Superchiave
>Dato uno [[Modello Relazionale#Relazione|schema]] $R(X)$:

>[!info] Definizione
>Un sottoinsieme $K\subseteq X$ di *attributi* è detto ***superchiave*** se **NON** contiene due tuple distinte $t_{1}$ e $t_{2}$ tali che $t_{1}[K]=t_{2}[K]$

Poiché ogni istanza $r$ su $R(X)$ è un insieme, ne consegue che:
- L'insieme di $X$ è senz'altro una **superchiave** per $R(X)$
###### Chiave
>Dato uno schema $R(X)$

>[!cite] Definizione Formale
>Un sottoinsieme $K\subseteq X$ di *attributi* è detto ***chiave***
><u>se e solo se</u>
>è una superchiave minimale di $r$
>>[!done] Ovvero
>>Non esiste $K' \subset K$ con $K'$ **superchiave**

>Esiste sempre almeno una ***chiave***:
- Caso peggiore, si usano tutti gli attributi della relazione

>[!hint] Unicità
>Possono esistere più chiavi in una relazione

 >[!done] Chiave Primaria
 >Una ***chiave primaria*** è una chiave di una relazione su cui **non** sono ammessi valori `NULL`.
 >Ogni relazione **deve** averne una.
 >- Può essere composta da uno o più attributi.
 >

### Inter-Relazionali
>I vincoli ***inter-relazionali*** si applicano fra *più relazioni*.

>[!info] Concetto
>I vincoli ***inter-relazionali*** sono collegamenti tra relazioni espressi mediante *valori comuni in attributi replicati*.
>- Ogni riga della tabella *referenziante* si collega al **massimo** con **una** riga della tabella *referenziata*.

#### Vincolo di Integrità Referenziale
> Si considerino due schemi $R_{1}(X_{1})$ e $R_{2}(X_{2})$ di un *database* $R$, e sia $Y$ un insieme di attributi in $X_{2}$.

>[!definizione] Definizione
>Un vincolo di integrità referenziale su $Y$ impone che in **ogni istanza** $r=\{ r_{1},r_{2},\dots \}$ del *database* l'insieme dei valori di $Y$ in $r_{2}$ sia un sottoinsieme dell'insieme dei valori della chiave primaria di $R_{1}(X_{1})$.

>[!Foreign Key]
>L'insieme $Y$ viene detto ***foreign key***.
>**Impone** che i valori, diversi da `NULL`, su un attributo $X$ in $R_{1}$ compaiano come valori della *chiave primaria* di $R_{2}$.

Nei [[Git-Obsidian/DataBase/Introduzione#DBMS|DBMS]] un ***vincolo di integrità referenziale*** può anche esprimersi con riferimento a una generica chiave (anche *non primaria*)
### Errori

- Un’operazione di modifica su una relazione causa una violazione di VIR su altre relazioni.

### Soluzioni

- **Eliminazione a cascata**.
- **Non consentire l’operazione**.
- **Inserimento di valori NULL**.