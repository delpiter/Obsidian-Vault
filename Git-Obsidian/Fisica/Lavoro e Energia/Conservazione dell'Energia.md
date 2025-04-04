## Conservazione in Presenza di Forze non Conservative
---
>[!info]
>Partiamo dal [[Energia#Teorema dell'Energia Cinetica|teorema dell'energia cinetica]], che è valido indipendentemente dalla presenza di forze **conservative** e **non**.
>$$\Delta K=K_{f}-K_{i}=\mathscr{L}_{\text{tot}}$$

Se sono presenti sia forze *conservative* che *non conservative*, possiamo separare i due contributi al lavoro
$$\mathscr{L}_{\text{tot}}=\mathscr{L}_{\text{con}}+\mathscr{L}_{\text{n.c.}}$$
Per le forze conservative utilizzo la [[Energia#Energia Potenziale|definizione di energia potenziale]]:
$$
\mathscr{L}_{\text{con}}=-\Delta U=-(U_{f}-U_{i})
$$
- ***Quindi***
$$
K_{f}-K_{i}=\mathscr{L}_{\text{tot}}=\mathscr{L}_{\text{cons}}+\mathscr{L}_{\text{n.c.}}=-(U_{f}-U_{i})+\mathscr{L}_{\text{n.c.}}
$$
>[!tip] Conclusione
>$$K_{f}+U_{f}=K_{i}+U_{i}+\mathscr{L}_{\text{n.c.}}$$
>$$E_{f}=E_{i}+\mathscr{L}_{\text{n.c.}}$$
>>[!quote] A parole
>>La variazione di energia meccanica è pari al lavoro compiuto dalle forze non conservativo

## Legge di Conservazione dell'Energia
---
> Esempio: Una cassa con una certa velocità iniziale, striscia e rallenta ***fino a fermarsi***.

>[!question] Dove è andata l'energia meccanica?

Possiamo notare che cassa e pavimento si sono leggermente scaldati.

>[!done] L'energia meccanica si è trasformata in calore (in questo caso).

>[!info] Conversione dell'energia
>Possiamo interpretare questo fenomeno come un ***processo di conversione dell'energia***: da *meccanica* ad un *altra forma*.

$$
\Delta U+\Delta K +\Delta E_{\text{int}}=\mathscr{L}_{\text{ext}}
$$
> Nel sistema cassa-pavimento, l'attrito è una forza interna al sistema:
- Avrei quindi:
$$
\Delta U+\Delta K +\Delta E_{\text{int}}=0
$$

>[!definizione]
>In considerazione di ***sistemi isolati***, cioè non sono presenti forze esterne al sistema:
>***L'energia totale di un sistema isolato si conserva***.

>[!warning] Nota
>La "*dissipazione*" di energia meccanica è un processo ***irreversibile***.

### Punti di Vista
> Vediamo come posso usare diversi punti di vista per comprendere lo stesso fenomeno.

![[POV.png|450]]

>[!example] Esempio
>Considero un *blocco* connesso ad una molla, ***poggiato su un tavolo*** con [[Le Forze#Forze di Attrito|attrito]].

> 1. Il sistema è il blocco.

L'ambiente fa lavoro sul blocco per *mezzo della molla* ($\mathscr{L}_{k}$, $k\to$ *Costante elastica*) e per mezzo dell'*attrito* ($\mathscr{L}_{A}$).
$$
\Delta K+\Delta E_{\text{int}}=\mathscr{L}_{k}+\mathscr{L}_{A}
$$
Non c'è alcuna $\Delta U$: La molla ***non fa parte del sistema***.

> 2. Il sistema è il blocco e la molla.

C'è una energia potenziale (*molla*), e l'unica forza **esterna** è l'attrito:
$$
\Delta U+\Delta K + \Delta E_{\text{int}}=\mathscr{L}_{A}
$$

> 3. Il sistema è il blocco, la molla e il tavolo.

**Non** c'è nessuna forza esterna.
$$
\Delta U+\Delta K+\Delta E_{\text{int}}=0
$$
>[!quote] Tutti i trasferimenti di energia sono interni.

