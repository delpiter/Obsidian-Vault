## Utente
- Visitatore
	- Email
	- Password
	- Dati anagrafici
		- Nome
		- Cognome
		- Anno nascita
		- Città
		- Nazione
		- Provincia
		- Cellulare (opzionale)
	- [[#Consenso]]
	- Motivo della visite
	- Tipologia
		- Operatore professionale
			- Azienda
			- Indirizzo
			- Cap
			- Attività
		- Appassionato
			- Passione (scelta multipla)

- Iscritto a un [[#Corsi|corso]]
	- Email
	- password
	- telefono
	- CF
	- nome
	- cognome
	- data nascita
	- [[#Consenso]]
	- residenza
		- Nazione
		- Provincia
		- Comune
		- Indirizzo
		- Cap
- Espositore (azienda)
	- Dati commerciali
		- Regione Nome,Cognome rappresentate azineda
		- Indirizzo
		- Città, Cap, Provincia, nazione, cellulare rappresentante
		- email pec
		- sitoweb
	- Espositori
		- Codice fiscale
		- nome cognome
		- Indirizzo citta cap provincia nazione
		- telefono email
		- partita iva

**RESPONSABILI**
- Marco
- Roberta
- Silvia
	- Descrizione
	- Numero
	- Email

## Consenso
Consensi:
- Profilazione Avanzata
- Marketing diretto
- Cessione dei dati a società terze
- Cessione dei dati a social network
## Fiera / Evento
- Data
- [[#Location]]
- Cosa si trova
	- [[#Corsi]]
	- [[#Mostre]]
	- [[#Espositori]]
	- Live Show
	- Merchandising
	- [[#Negozi]]

## Location
- Milano
- Torino
- Roma 
- Vicenza

## Corsi
Gratuiti o a pagamento
Online o nelle fiere
[[#"Campo" o "Mondo" (Tipologie di corsi/materiali/articoli)|tipologia]]
- Espositore
	- Docente
	- Orario
	- Tipo
- Accademy
	- Docente
	- Orario
	- Tipo

Numero minimo di persone
- Corso annullato se non si raggiunge
## Mostre
??
## Espositori
- Negozi principalmente

## Gruppi
- Fatti di [[#Utente|Visitatori]]
- Un responsabile (biglietto gratis)
- Minimo 15
	- Vari benefit per numeri incrementanti di persone
- Pubblici o privati
Attributi
- Referente (utente? / Stringa)
	- Telefono
	- nome 
	- città provenienza
	- Regione
	- Email
- Tappe (string)
- Note 
- Numero Persone
- Giorni di visita \[1-n\]

## Biglietti
- Comprati:
	- On line:
		- Pre
		- Durante l'evento
	- In cassa
- Diversi prezzi
	- Utente singolo
	- disabile e bambini <= 12 anni gratis
	- Codice promo
	- Gruppi

## Negozi
Attr:
- Nome
- URL
- Nome Referente
- Telefono
- Fax
- Email
- [[#"Campo" o "Mondo" (Tipologie di corsi/materiali/articoli)|categorie]] (una o più)
- posizione
	- Strada
	- Città
	- Provincia
	- Cap
	- Stato
- Dati aggiuntivi
	- Tipologia attività
	- Corsi (bool)
	- Descrizione aggiuntiva
- Consenso trattamento dati

Negozio di materiale
- Acquisti:
	- On-line
	- Nelle [[#Fiera / Evento]]
	- Negozi nelle città
Possibilità di inserire un negozio
- Online o no

## "Campo" o "Mondo" (Tipologie di corsi/materiali/articoli)
Quello che propone il sito
- Tipologia
	- Bijoux
	- Carta 
	- Cucito
	- Decorazione
	- Ricamo
	- Lifestyle

## News
Articoli circa i [[#"Campo" o "Mondo" (Tipologie di corsi/materiali/articoli)|"mondi"]]
- Tipologia
- Tags

## Storie
[[#"Campo" o "Mondo" (Tipologie di corsi/materiali/articoli)|sempre riguardo i mondi]]

## News Letter
- Iscriversi tramite nome e email (diverso account?)
	- Consenso trattamento dati (bool)