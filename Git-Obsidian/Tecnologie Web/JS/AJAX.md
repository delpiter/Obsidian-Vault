## Asynchronous Javascript and Xml
---
>[!failure] AJAX
> Modello creato per sviluppare applicazioni web con *elevata dinamicità* delle pagine, grazie allo ***scambio di piccole quantità di dati***.

*AJAX*:
- Permette di cambiare il contenuto du una pagina web **senza ricaricare la pagina intera**.
- È una tecnologia **indipendente** dal software del server.
- È eseguito dentro il browser.
- È basato sul protocollo [[HTTP]].
- Trasferisce in modo **asincrono** tra il browser e il server attraverso `HTTP Requests`.
- Le request sono inviate da chiamate a script [[JavaScript]] senza dovere effettuare submit di form.

> Per usare `AJAX` in `js` occorre:
- Definire un oggetto per poter inviare una `request` e ottenere l'oggetto richiesto.
- Definire una funzione per **gestire** la `response`.
- Effettuare una request `GET` o `POST`, inviare i dati e gestire la **response**.
### JSON
>[!abstract] JavaScript Object Notation
>`{json icon} JSON` è un formato adatto all'**interscambio** di dati fra applicazioni client-server.

[Sintassi JSON](https://www.json.org/json-en.html)

```json title:Example
{
  "name": "Mikey",
  "surname": "Mouse",
  "address": {
     "street": "Via San Crispino, 12",
     "city": "Cesena",
     "country": "Italy"
   },
   "phones": [
      { "sede": "Cesena", "num": "0547 338892" },
      { "sede": "Bologna", "num": "051 2094880" }
   ]
}
```

Usato anche da ***MongoDB***.
- Supera la struttura relazionale a favore di documenti `{JSON icon} .json`
#### Usare JSON in JS
> L'interprete è in grado di eseguire il parsing da stringa a oggetto `{JSON icon} JSON` e viceversa tramite le chiamate:

```js
parse();
stringify();
```
