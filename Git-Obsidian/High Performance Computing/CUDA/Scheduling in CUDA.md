## Scheduling dei Thread
---
>[!summary] `WARP`
> Un `WARP` [[CUDA]] è un gruppo di $32$ *thread* `CUDA` che eseguono simultaneamente.

L'hardware è usato in maniera più ***efficiente*** quando tutti i thread in un `WARP` eseguono istruzioni dallo stesso indirizzo.
- Se alcuni thread divergono, alcune **pipeline** di esecuzione sono *inutilizzate*.
- I *thread* in un `WARP` accedono a blocchi contigui e allineati di [[../../Architettura degli Elaboratori/Architettura del Calcolatore/RAM#RAM Dinamica|DRAM]].

>[!danger] Nota Bene
>Un `CUDA WARP` rappresenta la granularità minima di ***esecuzioni*** [[../../Architettura degli Elaboratori/Architetture a Confronto/Architetture Parallele#Classificazione di sistemi Paralleli|SIMD]] efficienti.

I singoli thread di un `WARP` partono insieme dallo *stesso indirizzo del programma*.
- Ogni thread ha il proprio `PC` (*program counter*).
	- Ogni thread è **libero** di dividersi e eseguire codice **indipendentemente**.
- Branch *divergenti* verranno ***eseguiti in maniera seriale***.

```c
int x;
AAA
if (x > 0) {
	XXX
} else {
	YYY
}
BBB
```

![[attachements/CUDA_WARP.png|600]]
