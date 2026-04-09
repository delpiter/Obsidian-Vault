>[!info] Sensore di Prossimità
>Un [[../Sensori e Azionatori#Sensori|sensore]] di ***prossimità*** è in grado di rilevare la presenza di un oggetto ad una certa distanza.

Si può basare su ***diverse tecnologie***:
- Sensori ultrasonici (*sonar*).
- Sensori ottici
- Sensori di [[../../../Fisica/Elettromagnetismo/Induzione|Induttivi]].
- Sensori [[../../../Fisica/Elettromagnetismo/Magnetismo|magnetici]].
- ...

Tipicamente usati per rilevare un oggetto ***senza misurare la distanza***.
## Sensori Ultrasonici
---
> Emittono un impulso *sonar* ($240KHz$) e rilevano l'***echo***.

>[!done] Pros
- Non sono disturbati dalle interferenze [[../../../Fisica/Elettromagnetismo/Elettromagnetismo|elettromagnetiche]].
- Può rilevare oggetti di materiale differente.
- Rileva oggetti *senza uno specifico setup*.

>[!fail] Cons
- Tempi di risposta lenti
- Può essere influenzato dalla superficie dell'oggetto.

#### HC-SR04
>[HC-SR04 Manuale](https://docs.google.com/document/d/1Y-yZnNhMYy7rwhAgyL_pfa39RsB-x2qR4vP8saG73rE/edit?pli=1&tab=t.0)

>[!caution] Utilizzo
- Un impulso è inviato dal ***Trig pin*** e viene misurato il tempo trascorso fino alla ricezione dell'impulso dal ***pin Echo***.
- Dato il tempo possiamo calcolare la **distanza** conoscendo la *velocità del suono*.
	- $ss\cdot \text{d}t = 2\cdot d$
	- $d=\displaystyle\frac{ss\cdot\text{d}t}{2}$ 
	- $\text{d}t = \displaystyle\frac{2\cdot d}{vs}$

>[!warning] Attenzione
>La velocità del suono dipende da alcuni fattori ambientali come la ***temperatura***.

## Sensori Ottici
---
> Basati sulla ***luce***

Anche chiamati ***sensori fotoelettrici***.

>[!done] Infrarossi
>***Non sono influenzati*** dalla luce dell'ambiente.

Il principio di base è quello della riflessione della luce.
- Altamente influenzato dall'***orientamento della superficie***.
- Distanza tipica: dai $10$ ai $100cm$.