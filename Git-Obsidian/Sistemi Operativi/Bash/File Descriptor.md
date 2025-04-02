>[!definizione] Definizione
>Il ***file descriptor*** è un'astrazione per permettere l'accesso ai file
>Ogni *file descriptor* è rappresentato da un ***integer***
>- Consente di utilizzare delle *funzioni* per accedere ai ***file***

### Tabelle dei File Aperti
>Il *sistema operativo* tiene una tabella di tutti i file aperti

>[!info] Tabella dei Processi
>I processi hanno una tabella dei ***propri file aperti***
>- I ***sotto-processi*** ereditano una *copia* della tabella

L'***integer*** che descrive il file aperto è l'indice che ha nella tabella del processo
- Il file aperto è ***identificato*** univocamente dal *processo* in cui è aperto e l'*indice*

### Stream di `I/O` dei processi
>Quando un programma entra in esecuzione, l'ambiente del sistema operativo si incarica di aprire 3 flussi di dati ***standard***:

>[!tl;dr] Standard Input
>`stdin`
>Serve per l'*input* normale (per default da tastiera)
>Viene identificato da una costante di valore numerico $0$

>[!abstract] Standard Output
>`stdout`
>Serve per l'*output* normale (per default da schermo)
>Viene identificato da una costante di valore numerico $1$

>[!error] Standard Error
>`stderr`
>Serve per *comunicare messaggi di errore* all'utente (per default da schermo)
>Viene identificato da una costante di valore numerico $2$

>I processi figli ereditano una copia dei 3 stream di `I/O` di default