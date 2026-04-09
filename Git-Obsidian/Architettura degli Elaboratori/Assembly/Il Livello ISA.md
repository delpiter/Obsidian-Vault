## Instruction Set Architecture
---
>[!info] ISA
>Il livello ***ISA*** descrive l'architettura delle istruzioni che la `CPU` è in grado di eseguire in **Hardware** 

Scrivere programmi complessi utilizzando direttamente istruzioni **ISA** è difficile e spesso inutile
- In quasi tutti i calcolatori è possibile scrivere programmi utilizzando linguaggi di ***alto livello*** che vengono poi compilati da programmi chiamati **Compilatori**

>[!question] Perchè non progettare direttamente macchine in grado di comprendere linguaggi come il C?

I linguaggi di *alto livello* sono spesso molto complessi e la definizione di primitive **ISA** così articolate richiederebbe la realizzazione di `CPU` troppo complicate e costose
- Inoltre un programma in un linguaggio di alto livello può essere *teoricamente* compilato e eseguito su `CPU` diverse, utilizzando compilatori specifici per le `CPU`

### Differenze fra i Termini
>[!tip] Assembly Language
>Quando si parla di ***Assembly Language*** si intende un **linguaggio** costituito da *codici mnemonici* corrispondenti alle istruzioni ***ISA***
>Assembly fornisce altre *facilitazioni* al programmatore come etichette simboliche per variabili e indirizzi.

>[!info] Assembler
>Un programma "*semplice*" detto ***Assembler*** traduce i codici mnemonici nei codici numerici corrispondenti alle istruzioni ***ISA***
>L'insieme di questi codici costituisce i programmi eseguibili `.exe`

### Perché studiare ISA e Assembler 
>Un programma scritto in *Assembly Language* è solitamente dalle $2$ alle $3$ volte più veloce di un programma analogo scritto in `C`

L'ottimizzazione di piccole porzioni di codice, detta ***tuning*** è un'ottima tecnica per *migliorare radicalmente* le prestazioni di programmi con uno **sforzo** **contenuto**

![[attachements/TuningASM.png]]