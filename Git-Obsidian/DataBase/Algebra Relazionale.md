# ALGEBRA RELAZIONALE

Linguaggio formale per interrogare un modello relazionale.

## Insieme di 5 operatori

### Unari (2)

#### Selezione (σ)
**Sintassi:**
```
σ_f(R)
```
- **f** → AθB / Aθc
- Permette di selezionare un sottoinsieme di tuple di una relazione attraverso un’espressione booleana.

#### Proiezione (π)
**Sintassi:**
```
π_y(R)
```
- Ortogonale alla selezione, seleziona un sottoinsieme **y** degli attributi di una relazione.

#### Ridenominazione (ρ) *(non fondamentale)*
**Sintassi:**
```
ρ y1←yR(X)
```
- Modifica lo schema di una relazione cambiando i nomi di uno o più attributi.

---

### Binari (3)

#### Join Naturale (⋈)
**Sintassi:**
```
R1(X1) ⋈ R2(X2)
```
- Combina le tuple di due relazioni sulla base dell’uguaglianza dei valori di attributi comuni.

#### Unione (∪)
**Sintassi:**
```
R1(X1) ∪ R2(X2)
```
- Applicato a relazioni con lo stesso insieme di attributi.
- Operazione che restituisce tutte le tuple presenti nelle relazioni A e B **senza ripetizioni**.

#### Differenza (-)
**Sintassi:**
```
R1(X1) - R2(X2)
```
- Applicato a relazioni con lo stesso insieme di attributi.
- Operazione che permette di **escludere** dalle tuple di una relazione le tuple uguali di un’altra relazione.

---

## Operatori derivati

### Theta Join (θ-join)
**Sintassi:**
```
r1 ⋈_F r2 = σ_F(r1 × r2)
```
- Combinazione fra join e selezione.

### Outer Join
Mantiene le tuple **dangling** aggiungendo i valori mancanti sotto forma di **NULL**.
- Una tupla di una delle relazioni operande che non fa “match” con alcuna tupla dell’altra relazione.

#### Tipi di Outer Join
- **Left Outer Join**
- **Right Outer Join**
- **Full Outer Join**

## Espressioni e viste

- Assegnare ad una soluzione un nome per facilitarne l’uso nelle query.