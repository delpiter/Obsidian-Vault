>[!info] Regole
>Le ***At Rules*** sono regole [[Cascading Style Sheets|CSS]] precedute dal carattere `@` e servono per specificare determinati comportamenti.

Si dividono in:
- Regular Rules
- Nested Rules

>[!summary] Regular Rules

- `{CSS} @keyword (RULE)`

>[!failure] Nested Rules

- `@keyword { css Rules }`


## Transizioni
---
>[!abstract] Transition
>Le ***transizioni*** sono effetti che permettono di applicare *passaggi graduali* da uno stile all'altro per un determinato elemento.

Le transizioni sono gestibili tramite la proprietà `{css icon} transition`, abbreviazione delle proprietà:
- `{css} transition-propriety`: Proprietà modificata (*required*).
- `{css} transition-duration`: Durata della transizione (*required*).
- `{css}transition-timing-function`:  Velocità di esecuzione (*optional*).
- `{css} transition-delay`: (*optional*).

È possibile specificare più transizioni per elementi diversi, è sufficiente separarli con una `,` nella proprietà `{css} transition`.

## Animazioni
---
>[!help] `{CSS icon} keyframe`
>Con la regola `@keyframe` è possibile definire delle ***animazioni***, che coinvolge una o più proprietà.

```css title:sintax
@keyframes name {
	selectorKeyFrame{
		...
	}
}
```

Dove:
- `name`: Nome della **animazione**.
- `selectorKeyFrame`: Percentuale dell'animazione.
	- Consistono in valori da `0%` a `100%` o nelle keyword `{css icon} from(0%)` e `{css icon} to(100%)`.

> Una volta applicata una animazione è necessario definire a quale elemento applicarla usando la proprietà `animation`.

```css
div {
	animation: animationName 3s;
}
```

- `{css} animation-name`: nome dell’animazione da applicare.
- `{css} animation-duration`: durata totale dell’animazione (es: `2s`, `500ms`).
- `{css} animation-timing-function`: velocità di esecuzione dell’animazione, ovvero la curva di accelerazione. Valori comuni:
	  - `linear`, `ease`, `ease-in`, `ease-out`, `ease-in-out`, `cubic-bezier(...)`
- `{css} animation-delay`: tempo di attesa prima dell’inizio dell’animazione (es: `1s`, `200ms`).
- `{css} animation-iteration-count`: numero di volte che l’animazione deve essere ripetuta. Può essere:
	- Un numero (es: `3`)
	- `infinite` (per ripetere all’infinito)
- `{css} animation-direction`: direzione di esecuzione dell’animazione. Valori:
	- `normal`, `reverse`, `alternate`, `alternate-reverse`
- `{css} animation-play-state`: stato di esecuzione dell’animazione. Valori:
	- `running` (animazione attiva), `paused` (animazione in pausa)
- `{css} animation-fill-mode`: definisce come applicare gli stili dell’animazione prima, durante o dopo l’esecuzione. Valori:
	- `none`, `forwards`, `backwards`, `both`.

