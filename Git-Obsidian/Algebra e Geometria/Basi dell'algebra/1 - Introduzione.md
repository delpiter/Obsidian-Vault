La [[../../Analisi/Concetti Base#Insieme|terminologia]] degli insiemi è sempre la stessa

## Relazione
---
>[!info] Definizione
> Una **relazione** su un insieme $A$ è un sottoinsieme $R$ di $A\times A$
> Scrivo $a_{1}Ra_{2}$ se $(a_{1},a_{2}) \in R$ e dico: *"$a_{1}$ è in relazione con $a_{2}$"*

### Relazione di Equivalenza
Una relazione $R$ è una **relazione di equivalenza** se valgono le seguenti proprietà:
>[!tip] Proprietà Riflessiva
>$$aRa \qquad \forall a \in A$$
>
>>[!done] In Breve
>> Possiamo dire che ogni elemento è in **relazione con se stesso**

>[!tip] Proprietà Simmetrica
>$$aRb \implies bRa \ \ (\forall a,b \in A)$$
>
>>[!done] In Breve
>> Se un elemento è in **relazione con un altro** vale anche il viceversa, cioè che il secondo elemento è in **relazione** con il primo elemento

>[!tip] Proprietà Transitiva
>$$aRb, bRc \implies aRc \ \ (\forall a,b,c \in A)$$
>
>>[!done] In Breve
>>Considerando le due relazioni $aRb$ e $bRc$ di conseguenza vale anche la relazione $aRc$

- Essere uguali è una relazione di equivalenza

### Esempi
- Uguaglianza fra Numero
- Avere la stessa età in un gruppo di persone
- Parallelismo tra rette (*coincidenti*)
### Controesempi
- Disuguaglianza
- Gruppo di persone che abitano tutte a meno di 10 km di distanza
- L'amicizia
- Perpendicolarità

## Congruenza a Modulo $n$
---
>[!info] Definizione
>Sia $n\in\mathbb{Z}, n\geq2$, siano $a,b\in\mathbb{Z}$
>$$a \equiv b (n)$$
>Se $a-b$ è multiplo di $n$ cioè
>$$\exists h\in\mathbb{Z}:a-b=h(n)$$
>Si dice
>- "$a$ congruo a $b$ modulo $n$"

 Essere **congrui a modulo $n$** è una relazione di equivalenza 
 #### Dimostrazione
 >[!done] Proprietà Riflessiva
 $$\forall a \in\mathbb{Z}, a\equiv a (n) \implies a-a = 0 = 0\cdot n$$

>[!done] Proprietà Simmetrica
>Se $a\equiv b\ (n)$ allora $b\equiv a \ (n)$
>Se $a-b$ è multiplo di $n$ lo è anche $b-a$

>[!done] Proprietà Transitiva
>Se $a \equiv b \ (n)$, $b\equiv c\ (n)$ allora $a \equiv c \ (n)$
>Perchè se $a-b =hn$ e $b-c=kn$
>allora $a-c = (a-b)+(b-c) = (h+k)n$
>

## Funzione o Applicazione
---
### Definizione
>[!info] Applicazione o Funzione
>Siano $A$ e $B$ insiemi non vuoti una **funzione o applicazione** che va d a $A$ a $B$ è una legge che associa ad ogni elemento dell'insieme $A$ uno e un solo elemento dell'insieme $B$
### Proprietà

![[../../Analisi/Funzioni/Introduzione Funzioni#Funzione Surriettiva]]

![[../../Analisi/Funzioni/Introduzione Funzioni#Funzione Iniettiva]]

![[../../Analisi/Funzioni/Introduzione Funzioni#Funzione Biunivoca]]

## Insiemi Numerici
![[../../Analisi/Insiemi/Insiemi Numerici#Tipologie]]