> Tipi di dati nello standard [[IA-32]]
![[attachements/DataTypeASM.png]]

## Range di Rappresentazione
---
>[!example] Unsigned

- `BYTE` *Unsigned Integer*  $0 \to255$
- `WORD` *Unsigned Integer*  $0\to 65535$
- `DOUBLE WORD` *Unsigned Integer*  $0\to 2^{32}-1$
- `QUAD WORD` *Unsigned Integer*  $0\to 2^{64}-1$

>[!example] Signed

- `BYTE` *Signed Integer*  $-128 \to127$
- `WORD` *Signed Integer*  $-32768\to 32767$
- `DOUBLE WORD` *Signed Integer*  $-2^{31}\to 2^{31}-1$
- `QUAD WORD` *Signed Integer*  $-2^{64}\to 2^{64}-1$

>[!example] Floating Point

- *Single Precision Floating Point*  $\pm1.18\cdot 10^{-38} \to\pm 3.4\cdot 10^{38}$
- *Double Precision Floating Point*  $\pm 2.23\cdot 10^{-308} \to\pm 1.79\cdot 10^{308}$
- *Double Extended Precision Floating Point* $\pm 3.37\cdot 10^{-4932} \to\pm 1.18\cdot 10^{4932}$

