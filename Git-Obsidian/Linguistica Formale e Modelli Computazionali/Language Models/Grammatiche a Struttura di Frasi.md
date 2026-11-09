> Introdotte da [[../Linguistica Formale/Forma Normale di Chomsky|Noam Chomsky]] per riferirsi alle grammatiche come le [[../Linguistica Formale/Grammatiche e Linguaggi Liberi dal contesto|CFG]].

Le categorie sintattiche, come le ***frasi nominali*** (`NP` o *noun phrase*) o le ***locuzioni verbali*** (`VP` o *verbal phrase*), dei *linguaggi naturali* sono le ***variabili della grammatica***.
- Denotano le parti della frase e sono chiamati ***costituenti***.

> [!info] Grammatica
> Una grammatica quindi esprime la ***struttura della frase***, la relazione tra nodi di un albero sintattico.

> [!hint] Tutti gli esempi saranno basati sulla lingua inglese

Una frase *inglese* (radice $S$) è formata da una ***noun phrase*** (figlio sinistro dell'albero `NP`) seguita da una ***verb phrase*** (figlio destro `VP`).

> [!question] E i simboli terminali?
> 

## Tokenization
---
> [!quote] Definizione
> Il processo di divisione di un testo in una sequenza di parole è chiamato ***tokenization***.

Viene segmentata una sequenza di caratteri in ***token***, per esempio la frase

"From the start, it took a person with great qualities to succeed"

> ***Diventa***

"From | the | start |,|it | took | a | person | with | great | qualities | to | succeed"

Per un testo inglese è relativamente semplice.
- Si divide il testo ad un ***carattere whitespace*** (spazio, tab o newline).

Si assume che i token appartengano ad un insieme finito.
- Le parole che appartengono ad un ***vocabolario di un linguaggio***.
- La punteggiatura.
- Etc...

> [!hint] Vocabolario vs Dizionario
> Le parole che appartengono al ***vocabolario*** di un linguaggio è l'insieme di tutte le ***parole lessicalmente corrette*** rispetto al suo *dizionario*.

Quello che prima era un simbolo dell'alfabeto ***ora è un token***.
- I ***token*** sono il nuovo alfabeto di simboli $\Sigma$ usate per rappresentare frasi come sequenze di $\Sigma$

Esempio la frase precedente ("*From | the | start |,*" ...) è rappresentata usando una sequenza di token:
$$
\begin{align}
&\Sigma =\{  \\
&[\text{a}],[\text{from}],[\text{great}],[\text{it}],\\
&[\text{person}],[\text{qualities}],[\text{start}],\\
&[\text{succeed}],[\text{the}],[\text{to}], [\text{took}],[\text{with}],[,],\dots\}
\end{align}
$$

> [!attention] Normalizzazione
> Possono esserci alcune normalizzazioni, per esempio "From" e "from" sono rappresentate dallo ***stesso token*** $[\text{from}]$.

### Ambiguità
> [!abstract] Info
> I ***linguaggi naturali sono ambigui***.

È normale per una frasi avere diversi [[../Linguistica Formale/Grammatiche e Linguaggi Liberi dal contesto#Alberi Sintattici|alberi sintattici]].

###### Esempio
> Consideriamo la `CFG`

$$
\begin{align}
& S\to NP \ \ VP \\
& NP \to \text{Noun} \mid \text{Pronoun} \\
& VP \to \text{Verb }VP \mid \text{Modal Verb}  \\
&  \\
& \text{Noun} \to [fish] \mid \dots \\
& \text{Pronoun} \to [I] \mid [they] \mid \dots \\
& \text{Verb} \to [can]\mid[fish]\mid\dots \\
& \text{Modal}\to[can] \mid \dots
\end{align}
$$

La frase "***I can fish***" ha due alberi sintattici:

![[attachements/Pasted image 20261108182906.png]]


> [!done] Soluzione
> L'ambiguità è gestita usando un approccio probabilistico, ***assegnando delle probabilità alle produzioni della grammatica***.

Selezionando infine l'albero sintattico ***più probabile***.
