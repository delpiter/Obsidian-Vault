>Di seguito vedremo come risolvere il problema della concorrenza [[10 - Sezioni Critiche#Approcci|modificando l'hardware]]

>[!tldr] Idea
>Si può pensare di fornire alcune *istruzioni hardware* speciali per semplificare la realizzazione di ***sezioni critiche***
>Nei sistemi uniprocessore, i processi concorrenti vengono "[[8 - Concorrenza#Multiprogramming|alternati]]" tramite il meccanismo degli ***interrupt***

>[!question] Risolve il problema, disabilitare gli interrupt?

Il sistema operativo deve lasciare ai processi la responsabilità di riattivare gli interrupt
>[!danger] Altamente Pericoloso!

Inoltre non funziona su ***sistemi multiprocessore***

###### Pro e Contro
>[!done] Vantaggi

- Concetti applicabili a qualsiasi numero di processi, sia su sistemi mono processore che multiprocessore
- Può essere usato per supportare sezioni ***critiche multiple***

>[!fail] Svantaggi

- Viene utilizzato il [[10 - Sezioni Critiche#Busy-Waiting|Busy-Waiting]]
- I problemi di [[9 - Condivisione di Risorse#Starvation|starvation]] ***non*** sono eliminati
- Complessi da programmare

![[../../Concurrent Systems/Critical Section/Soluzioni Hardware|Soluzioni Hardware]]