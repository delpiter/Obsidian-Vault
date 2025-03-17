>[!info]
>I seguenti dati sono stati raccolti tramite una analisi del sito: 
>[https://www.abilmente.org/it/](https://www.abilmente.org/it/)
>Numerose informazioni descritte potrebbero essere assunzioni.

Si vuole modellare una base di dati per un sito di esibizioni.

Il sito si occupa di ***programmare esibizioni*** riguardanti diversi campi:
- Cucito e Filato
- Carta, Scrap e Colore
- Bijoux e Accessori
- Ricamo e Tradizione
- Decorazione
- Etc...

La fiera si può svolgere in una di $4$ località (*Vicenza, Roma, Milano, Torino*) e dura un numero di giorni compreso tra $[4,7]$.
- Della location si vuole sapere l'indirizzo della fiera.
In un anno ci possono essere **più edizioni** in ciascuna delle località.
All'interno della fiera si possono trovare:
- Corsi educativi riguardanti uno specifico campo
- Mostre di vario tipo
- Live show

Inoltre si vuole dare la possibilità a ***piccoli produttori*** di poter diventare **espositori** della fiera.
- Un espositore dovrà fare richiesta di partecipazione alla fiera per poter esporre i propri prodotti.
- Per ciascun espositore si vuole salvare:
	- Il nome del referente diretto
	- Il link del sito dell'"azienda"
	- L'edizione di interesse in cui si vuole esporre
	- Un recapito telefonico
	- Un indirizzo email
	- Un messaggio aggiuntivo opzionale.

Inoltre si vogliono salvare i consensi per il trattamento dei dati.
- Profilazione avanzata (Do il consenso/nego il consenso)
- Marketing diretto.
- Cessione dei dati a società terze
- Cessione dei dati a piattaforme di social network

Le mostre possono essere di diverse categorie.
Ci possono essere più mostre per ogni esibizione.
- Di ciascuna mostra si vuole salvare:
	- Nome
	- Da chi è curata la mostra (Nome Azienda o Persona)
	- Eventuali sponsor.
	- Specifica di tecniche utilizzate (opzionale)
	- Una breve descrizione della mostra

I corsi possono essere sia on-line (in una area separata "*Accademy*") che direttamente nella **fiera**, in oltre possono essere gratuiti o a pagamento.
Un corso è incentrato su una delle tipologie di campi descritti in precedenza (*Cucito e filato, Carta, Bijoux, etc*)
- Per ciascun **corso** ci sono *più lezioni* (Il corso può essere **ripetuto in più date**).
	- Ciascuna lezione ha una data e un orario
- Ogni corso è tenuto da uno o più **docenti** dei quali si vogliono salvare:
	- Nome, Cognome, Recapito Telefonico, Email ed eventuali collegamenti a social network

Il sito propone anche una serie di corsi (masters) on-line "*Accademy*".

Ogni corso per partire deve avere un numero minimo di persone iscritte.
- Se il corso non raggiunge il minimo numero di iscritti, viene annullato e verrà rimborsata l'iscrizione

Di ciascun corso si vuole salvare:
- Un nome
- La location dove sarà svolto (se svolto in fiere), sottoforma di nome identificativo dello stand ("*Padiglione 7 stand 939*")
- Il docente che terrà il corso
- Il prezzo.
- Ciascun utente iscritto al corso.
- La categoria del corso
- Il livello del corso (Base, Intermedio o Avanzato)

Si vuole gestire la visita in gruppo di un evento.
Il gruppo è formato da un responsabile, il cui biglietto d'ingresso sarà gratuito, e almeno altri *14 partecipanti* (**minimo 15**)
- Più partecipanti al gruppo ci sono più si avrà accesso a benefit maggiori

Si vogliono memorizzare diversi tipi di utenti:
- Visitatore
	- Frequentante di un corso
- Gruppo Visitatori
- Espositore

I primi due tipi e il terzo avranno aree separate di interazione con il sito

Di ciascun utente visitatore si memorizzi:
- Email
- Password (cifrata)
- Dati anagrafici
	- Codice Fiscale
	- Nome
	- Cognome
	- Anno di nascita
	- Residenza
		- Nazione
		- Provincia
		- Città
		- Indirizzo
		- CAP
- Cellulare $[0..n]$
- Solito Consenso
- Motivo della Visita
- Tipologia del visitatore
	- Operatore Professionale
		- Nome Azienda
		- Indirizzo Azienda
		- Cap
		- Attività aziendale
	- Appassionato
		- Passione $[1,n]$

I gruppi possono essere **privati**, oppure **pubblici**
È possibile promuovere il gruppo "pubblico" e condividerlo sui social per trovare persone che si aggiungano al gruppo

Per ciascun gruppo si vuole salvare:
Se il gruppo verrà pubblicato e pubblicizzato, si memorizzano informazioni aggiuntive:
- Referente
	- Telefono
	- Email
	- Nome
- La regione di provenienza
- Città di provenienza 
- Nazione di Proveneinza
- L'identità del referente (Agenzia viaggi / Negozio / Associazione / Scuola / Privato)
- Un numero indicativo di persone partecipanti ( $[15,29],[30,49],[50,79], >80$ )
- Note aggiuntive
- Tappe
- I giorni in cui verrà effettuata la visita da parte del gruppo
- E gli stessi consensi per il trattamento dei dati di cui prima

Per gli espositori si vuole memorizzare:
I dati commerciali, fra cui:
- Dati del rappresentante aziendale
	- Nome Cognome, Regione, Cellulare, Email
- Indirizzo azienda
	- Città Cap, Provincia, Nazione
- Sito web aziendale $[0,1]$
- Una azienda può avere più co-espositori, si vogliono sapere:
	- Codice fiscale
	- Nome e Cognome
	- Telefono email
	- Indirizzo, città cap provincia e nazione
	- Partita Iva

Inoltre l'azienda organizzatrice degli eventi gestisce un blog, dove vengono riportate le seguenti informazioni:
- Negozi di materiali in città ***diverse da quelle della fiera***
- Negozi di materiali on-line
È possibile, inserire un nuovo negozio
In comune:
- Nome
- Sito web (URL)
- Email
- Telefono
- Descrizione
- Prevede Corsi?
- Consenso al trattamento dei Dati
- Categorie $[1,\dots n]$

- Normale:
	- Nome
	- Nome referente
	- Telefono
	- Sito
	- email
	- Fax
	- Posizione del negozio
		- Strada
		- Città
		- Provincia
		- CAP
		- Stato
	- Dati aggiuntivi
		- Tipologia di attività
		- Il negozio prevede corsi? (bool)
		- Descrizione aggiuntiva
	- Consenso al trattamento dei dati
- On-line
	- Specializzazione
	- Referente
		- Nome
		- Tipologia (produttore/distributore/artigiano, etc)
	- Il negozio tiene corsi?

Il blog contiene anche:
- Articoli
- Tutorial
- Storie creative
ciascuno riferite ad un campo (*Cucito e filato, Carta, Bijoux, etc*).
Di ciascuno di questi contenuti multimediali, si vuole memorizzare:
- Titolo
- Data uscita
- Autore
- Contenuto
- Serie di tag che descrivono il contenuto $[1,n]$