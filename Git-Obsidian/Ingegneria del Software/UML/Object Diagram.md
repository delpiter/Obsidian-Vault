![[UML#^a4f60f]]
## Diagramma degli Oggetti
---
>[!info]
>Il ***diagramma degli oggetti*** è la il modo di rappresentare *una istanza* di un [[Class Diagram]].

L'utilizzo è limitato a mostrare ***esempi di strutture dati***.

Poiché il *diagramma delle classi* può contenere anche istanze, il diagramma degli oggetti può essere considerato come un ***caso particolare di diagramma delle classi***.
- Dove compaiono solo oggetti.
### Componenti
>[!Oggetto]
>Un ***Oggetto*** rappresenta una particolare istanza di una **classe**.

```mermaid
classDiagram
direction LR
	class Polygon{
		center
		vertices
		color
		borderColor
	}
	class Triangle["Triangle:Polygon"]{
		center = (0,0)
		vertices = ((0,0), (0,4), (4,3))
		color = black
		borderColor = white
	}
	Triangle ..> Polygon: Instance
```

- Il nome "triangle" deve essere sottolineato per indicare che è una istanza di poligono.