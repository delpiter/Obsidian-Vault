>*Durante la memorizzazione in [[Le Memorie|memoria]] si possono occasionalmente commettere errori a causa di picchi di tensione o altri difetti*
>*Questi errori possono essere prevenuti utilizzando dei **Error Correction Code***

## Distanza di Hamming
---
>[!info] Definizione
>La ***distanza di Hamming*** indica il numero di `BIT` corrispondenti che ***differiscono*** in due sequenze di `BIT`
>>[!example] Trade Off
>>Aggiungo una ridondanza dei `BIT` per essere sicuro che quello che leggo è corretto
>>- ***Trade Off***: *space*-*reliability* 

***D. Hamming*** $=2$
- `10011100`
- `11010100`

***D. Hamming*** $=4$
- `11111110`
- `01100111`
### Codeword
>[!tldr] Parola di Codice
>La ***codeword*** indica un insieme di `BIT` $n$ formato da $m$ `BIT` di dati (***word***) r $r$ `BIT` di *controllo*

Se due ***codeword*** hanno distanza di ***hamming*** $H$
- Sono necessari $H$ errori (*cambiamenti di stato* di 1 `BIT`) per convertirne una nell'altra

Utilizzando ***codeword*** di lunghezza $n$ con $m$ `BIT` di dato
- Sono disponibili solo $2^m$ delle $2^n$ possibili combinazioni di `BIT` saranno ***valide***

>[!done] Identificazione di un Errore

Il calcolatore **identifica la presenza di un errore** quando:
- Nel leggere una parola dalla memoria, ***incontra una codeword non valida*** rispetto al codice di correzione degli errori utilizzato

### Distanza di un Codice di Correzione
>[!info] Definizione
>La ***distanza di Hamming di un codice di correzione*** è data dalla *minima* distanza tra *tutte le codeword valide*

Il codice di correzione degli errori ***più semplice*** è quello che si ottiene utilizzando un [[../../Definizioni/Definizioni_Architettura#Parity Bit|bit di parità]].
#### Individuazione di Errore
>[!abstract] Requisiti
>Per ***individuare*** $d$ errori di un `BIT` serve un codice con distanza $d+1$
>>[!done] ‎ 
>>*Non esiste alcun modo che consente con $d$ errori singoli di cambiare una codeword in un'altra*

##### Esempio
`00`$\to$`000000`
`01`$\to$`000111`
`10`$\to$`111000`
`11`$\to$`111111`

**Distanza di hamming del codice**: $3$
- Posso individuare al massimo 2 errori singoli senza che una *codeword* **valida** diventi un'altra *codeword* **valida**

#### Correzione di Errore
>[!abstract] Requisiti
>Per ***correggere*** $d$ errori di un `BIT` serve un codice con distanza $2d+1$
>>[!done] ‎ 
>>*Le parole sono abbastanza lontane per poter consentire anche nel caso di $d$ errori di ricondursi alla parola più vicina originaria*

