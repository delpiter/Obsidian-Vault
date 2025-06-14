# RETI
### Parte 1
- Throughput
    * Rate (bits/s) di trasmissione fra client e server
        + Instantaneo
        + Medio
    * Il throughput sarà sempre il rate minore fra quello del client e del server (bottleneck)

- Internet Protocol Stack
    * Levels
        + Application → Es: FTP, SMTP, HTTP..
        + Presentation (ISO/OSI) → Applicazione interpreta il significato dei dati, Es: encryptio, compression..
        + Session (ISO/OSI) → Synchronization, recovery of data
        + Transport → Comunicazione interprocesso, Es: TCP, UDP..
        + Network → Routing da sorgente a destinazione, Es: IP..
        + Link → Data transfer fra hardware vicino, Es: Ethernet, 802.111 (Wi-Fi)..
        + Physical → Cavo
    * Encapsulation
        + Application → Message
        + Transport → Segment
        + Network → Datagram [ROUTER]
        + Link → Frame [SWITCH, ROUTER]

- Network Security
    * Internet inizialmente era una cosa "intima", tutti si fidavano di tutti, ora no
    * Malwares
        + Virus → Autoreplicante, ricevuto tramite email
        + Worm → Autoreplicante, riceve file da eseguire
        + Spyware → Registra tastiera, siti visitati..
    * Botnet & DoS
    * Packet Sniffing
    * IP Spoofing → Manda pacchetti con IP sorgente arbitrario

### Parte 2

- Application Architectures
    * Client-Server
        + Server → Sempre on, IP permanente
        + Client → Parla con server, non sempre on, IP dinamico, non comunicano fra loro
        + Tempo di distribuzione di file (size F) a N client
            - Server → N * F / UploadCapacity
            - Client → F / MinCliDownRate
            - Totale → Max{Server, Client}
    * Peer to peer (P2P)
        + Non esiste un server sempre on
        + Tutti gli host parlano fra loro
        + I peer si scambiano servizi, più peer presenti, più "forza" ha la rete
        + IP dinamico
        + Tempo di distribuzione di file (size F) a N peer
            - "Server" → Almeno deve caricare una copia → F / UploadCapacity
            - "Client" → Ogni client deve scaricare una copia → F / MinCliDownRate
            - Clients → Tot download = N * F bits → MaxUpRate = UploadCapacity + sum(each_peer)
            - Totale → Max{"Server", "Client", N * F / Clients}
        + File Sharing (BitTorrent)
            - I file sono divisi in chunk da 256 Kb
            - Ogni peer manda/riceve i chunk di un file con tutta la lista dei peer del file
            - Un tracker gestisce le liste di peer
            - Richiedere chunk
                * Ogni peer ha una lista di chunk di un file
                * Periodicamente client A richiede la lista dei chunk ai peer
                * Client A richiede i chunk mancanti ai peer, i più rari per primi
            - Mandare chunk (tit-for-tat)
                * Client A manda chunk alla top 4 per velocità dei peer che gli sharano i file
                    + Agli altri niente (choke)
                    + Rivalutato ogni 10 secondi
                * Ogni 30 secondi scegli a caso un altro peer a cui mandare chunk
                    + Speri l'unchoke
                    + Potrebbe joinare la top 4

- Comunicazione fra processi
    * Same host → Inter process communications
    * Different host → Messaggi
        + P2P → Gli host hanno applicazione sia server che client
        + Client/Server → Client (processo che inizializza comunicazione), server (processo wait connection)

- Sockets (Porta fra processo applicazione e protocollo di trasporto)
    * Host A pusha messaggio a sua socket
    * Socket pusha messaggio a mezzo di trasporto esterno
    * Messaggio arriva a altra socket che lo "spacchetta"
    * Programmazione
        + UDP
            - Non esiste handshake
            - Sender → Ad ogni pacchetto attacho IP e porta destinazione
            - Receiver → Ad ogni pacchetto estraggo IP e porta sorgente
            - Client
                ```
                1) Creo la socket UDP
				2) Input del messaggio
				3) Attacho al messaggio IP e porta destinazione poi invio tramite socket
				4) Leggo la risposta dalla socket
				5) Chiudo socket
                ```
            - Server
                ```
                    1) Creo la socket UDP
                    2) Bindo la socket ad una porta locale
                       In loop:
                        3) Leggo quello che mi arriva dalla socket salvandomi IP e porta sender
                        4) Rispondo
                ```
        + TCP
            - Il server e la sua socket devono essere raggiungibili
            - Quando il client crea la socket specificando IP e porta destinazione la connessione parte
            - Quando il server riceve la richiesta di connessione crea una socket apposta per quel client
            - Client
                ```
                    1) Creo la socket TCP con porta destinazione e mi connetto all'IP destinazione
                    2) Mando il messaggio e mi arriva la risposta
                ```
            - Server
                ```
                    1) Creo la socket di benvenuto e mi metto in ascolto
                        In loop:
                         2) Quando mi arriva connessione creo socket dedicata
                         3) Leggo quello che mi è stato inviato
                         4) Chiudo la socket del client, non quella di benvenuto
                ```

- Addressing Processes
    * Per mandare messaggi ho bisogno di
        + Indirizzo IP host ricevente
        + Porta su cui il processo ricevente è bindato

- Definizione dei messaggi fra applicazioni
    * Tipo di messaggio → Richiesta/risposta
    * Sintassi messaggio → Campi del messaggio e loro disposizione
    * Semantica messaggio → Significato dei campi
    * Regole di invio richiesta/risposta

- Servizi di trasporto necessari
    * Integrità dei dati → File 100% integri, audio/video anche no
    * Timing → Videogiochi low delay
    * Throughput → Un film in 4K lo guardi se hai un buon throughput, una pagina web la scarichi in ogni caso
    * Sicurezza → Encryption, dati sani..

- Protocolli
    * TCP
        + Trasporto affidabile
        + Flow control → Sender non intasa receiver
        + Congestion control → Se congestione il sender rallenta
        + Connection oriented → Connessione fra host A e host B
        + No sicurezza
        + No throughput minimo garantito
    * UDP
        + Trasporto inaffidabile
        + No flow control
        + No congestion control→
        + No connessione
        + No sicurezza
        + No throughput minimo garantito

- Sicurezza TCP
    * SSL (livello applicazione)
        + Encryption
        + Dati sani
        + Autenticazione degli endpoint

- RTT (Round trip time) → Tempo che ci impiega un pacchetto di fare avanti e indietro fra client e server

- HTTP
    * Livello applicazione
    * Client (Browser richiede, riceve, visualizza) - Server (risponde con oggetti richiesti)
    * TCP → Connessione a porta 80, accettata, scambio messaggi, connessione chiusa
    * Stateless → Server non mantiene info sulle vecchie richieste del client
    * Connessione
        + Non-persistent → Un oggetto per ogni connessione TCP (pagina con 2 immagini = 3 connessioni)
            - Tempo di risposta → 1 RTT init connection + 1 RTT richiedo file + trasmetto file
            - Contro → 2 RTT per oggetto, sovralavoro per ogni connessione TCP..
        + Persistent → Oggetti multipli per una connessione TCP
    * Messages
        + Request 
            - Formato
                ```
                    Request line → Metodo URL Versione\r\n
                    Header lines → Header_field_name .. Value\r\n
                    \r\n
                    Body
                ```
            - Metodi
                * GET 
                * POST
                * HEAD → Lascia oggetto richiesto senza risposta
                * PUT (1.1) → Upload il file definito nel body nell'URL field
                * DELETE (1.1) → Deleta il file dell'URL field

            - Input forms
                * POST method → Il form input è uppato al server tramite il body
                * URL method → Usa GET e in URL field crafta la query di richiesta
        + Response
            - Formato
                ```
                    Status line → Protocol Status_code Status_phrase\r\n
                    Header lines
                    \r\n
                    Data
                ```
            - Status codes
                * 200 OK → Ok, data nel messaggio
                * 301 Moved Permanently → Object spostato, nuova location in messaggio
                * 400 Bad Request → Il server non ha capito
                * 404 Not Found 
                * 505 HTTP Version not SUpported
    * Cookies 
        ```
            1) Client richiede qualcosa a server
            2) Server risponde e nell'header di risposta mette "set-cookie: N" e salva in suo DB
            3) Client nella prossima richiesta incorpora cookie in header line e browser salva cookie
        ```
    * Web-caches (proxy server)
        + Funzionamento
            ```
                1) Client manda richiesta alla cache
                2) Se risorsa esiste → viene ritornata
                                else → contatti il server madre
            ```
        + La cache è installata dall'ISP (es: uni, ISP regionale..)
        + A cosa serve?
            - Riduci tempo risposta
            - Riduci il traffico
        + Solitamente 4/10 del traffico soddisfatto da cache (Latenza = 0.4 * tempo_cache + 0.6 * tempo_internet)
        + Conditional GET
            ```
                1) Cache richiede risorsa con header → If-modificed-since: data
                2) Server risponde: if non modificata → 304 Not Modified
                                                else → 200 OK
            ```

- E-Mail
    * Componenti
        + User agent (mail reader) → Outlook, Thunderbird..
        + Mail servers
            - Mailbox → Contiene i messaggi
            - Message queue → ALL outgoing messages
        + SMTP 
            - TCP, port 25
            - Comando/risposta come HTTP
            - Connessione persistente
            - I messaggi devono essere in ASCII 7 bit
            - Client tells server A to send mail to server B, ogni passaggio in SMTP
            ```
                S: 220 hamburger.edu
                C: HELO crepes.fr
                S: 250  Hello crepes.fr, pleased to meet you
                C: MAIL FROM: <alice@crepes.fr>
                S: 250 alice@crepes.fr... Sender ok
                C: RCPT TO: <bob@hamburger.edu> 
                S: 250 bob@hamburger.edu ... Recipient ok 
                C: DATA 
                S: 354 Enter mail, end with "." on a line by itself
                C: Do you like ketchup? 
                C: How about pickles? 
                C: . (End = CRLF.CRLF)
                S: 250 Message accepted for delivery 
                C: QUIT 
                S: 221 hamburger.edu closing connection
            ```
            - Transfer → Handshaking, transfer of message, close
            - Formato mail
                ```
                    Header: 
                        To
                        From
                        Subject
                    Blank line
                    Body:
                        Caratteri ASCII
                ```
            - Protocolli di accesso
                * POP (Post office protocol) → Autorizzazione, download
                    + Download-and-delete → Appena scarichi il server non ha piu
                    + Download-and-keep → Scarichi e il server mantiene
                * IMAP (Internet mail access protocol) → Manipolo anche le mail sul server
                    + Tutto storato sul server, tu ci lavori sopra
                    + Cartelle
                * HTTP → Protonmail, Yahoo..

- DNS (Domain name system)
    * Database distribuito implementato gerarchicamente di tanti name servers
    * Servizi
        + Hostname to IP address translation
        + Host aliasing
        + Mail server aliasing
        + Load distribution → Tanti IP corrispondono ad un hostname
    * Tipologie
        + Root name server
            - Contattato dai local name server
            - Se non ha l'indirizzo lo richiede agli authoritative name server
        + Authoritative DNS server
            - Gestito da un azienda o un ISP (tipo DNS di Amazon)
        + Top level domain server (TLD)
            - com, org, net, edu, aero, jobs, museums, it, uk, nl..
        + Local DNS
            - Telecom, Uni..
            - Quello che riceve la richiesta dal client
    * Funzionamento
        ```
            Iterativo:
                1) Host contatta local DNS
                2) Local DNS contatta in ordine:
                    ° Root DNS
                    ° TLD DNS
                    ° Authoritative DNS
            Ricorsivo:
                1) Host contatta local DNS
                2) Local DNS contatta root DNS
                3) Root DNS contatta TLD DNS
                4) TLD DNS contatta authoritative DNS
                5) Ritorno il risultato riseguendo il percorso
        ```
    * DNS caching
        + Se un server acquisisce una risorsa la mantiene per un tot di tempo (TTL)
        + TLD DNS sono cachati nei local DNS, così la root non è sempre querata
    * DNS resource record (RR)
        + Formato → (name, value, type, ttl)
        + Tipi
            - A
                * Name = Hostname
                * Value = IP
            - NS 
                * Name = Domain (Es: foo.com)
                * Value = Hostname di authoritative DNS
            - CNAME
                * Name = Alias (Es: www.ibm.com)
                * Value = Canonical name (Es: servereast.backup2.ibm.com)
            - MX
                * Value = Name del mailserver associato con "Name"
    * Formato messaggi
        + Richieste e risposte hanno lo stesso formato
        + Header
            ```
                    2 Bytes     2 Bytes
                Identification    Flags
                
                Identification → ID richiesta/risposta
                Flags → Richiesta/risposta
                      → Ricorsione desiderata/possibile
                      → Risposta da authoritative
            ```
        + "Body"
            ```
                            4 Bytes each
                1) Nome, tipo di campi per una query
                2) Record raws (RRs) in risposta
                3) Record per server authoritative
                4) Additional info
            ```
    * Inserting records in DNS
        ```
            Es: Insert two RRs into .com TLD server: 
                (networkutopia.com, dns1.networkutopia.com, NS)
                (dns1.networkutopia.com, 212.212.212.1, A)
        ```
    * Attacking DNS
        + DDoS
            - Bombarda root → Molto difficile e in ogni caso ci sarebbero i TLD di ripiego
            - Bombarda TLD servers
        + Redirect
            - MITM → Intercetta le query al DNS
            - DNS poisoning → Manda richieste del cazzo al DNS che le cacha riempiendolo
        + Use DNS for DDoS
            - Manda query con IP spoofato, così chi hai spoofato viene dossato dal DNS

- Multimedia
    * Video
        + Coding (decrease bits used to encode image)
            - Spatial coding → Manda il colore e quante volte è ripetuto
            - Temporal coding → Manda solo le differenze fra frame i e i+1
        + Bit rate
            - CBR → Constant bit rate
            - VBR → Variable bit rate → Usando spatial e temporal coding
        + Streaming 
            - DASH (Dynamic Adaptive Streaming over HTTP)
                * Server
                    + Divide il file in vari chunk
                    + Ogni chunk encodato con rate diverso
                    + Manifest → Da il link ai vari chunk
                * Client
                    + Periodicamente misura la banda
                    + Consultando il manifest sceglie in base alla banda il chunk da scaricare
                    + Intelligente, determina
                        - Quando richiedere un chunk in modo che non ci sia overflow/starvation
                        - Che encoding richiedere (in base alla banda)
                        - Dove richiedere il chunk in base al carico dei vari server
            - CDN (Content Distribution Networks)
                * Fornisci le copie dei contenuti da vari server sparsi per il mondo
                * Scegli il nodo del CDN migliore (più vicino, meno congestionato)
                * Funzionamento
                    ```
                        1) Client A si connette a NetCinema e trova url video (http://netcinema.com/6Y7B23V)
                        2) Risolvo l'URL tramite il DNS locale
                        3) Il DNS di NetCinema torna l'url che punta a KingCDN (http://KingCDN.com/NetC6y&B239
                        4) Risolvo l'URL tramite il DNS di KingCDN e mi torna l'url del video sui server di KingCDN
                    ```

### Parte 3

- Transport Layer
    * Send-side → Divide il messaggio dell'app layer in segmenti passati al network layer 
    * Receive-side → Riassembla i segmenti ricevuti e li passa all'app layer
    * Transport vs Network layer
        + Network → Comunicazione logica fra host
        + Transport → Comunicazione logica fra processi
    * Multiplexing/Demultiplexing
        + Multiplexing → Raccogli i dati da socket multiple e aggiungi header di trasporto
        + Demultiplexing → Usa gli header per distribuire alle socket i corrispondenti pacchetti
            - Funzionamento
                * Host riceve IP datagram
                    + Ogni datagram ha l'IP sorgente e destinazione
                    + Ogni datagram trasporta un segmento del transport layer
                    + Ogni segmento ha la porta sorgente e destinazione
                    + Host usa gli IP e le porte per condurre il segmento alla socket corrispondente
                * Connectionless (UDP)
                    + Invio → Creo socket bindata a porta e ci faccio passare datagram in uscita (con dest IP e port)
                    + Ricezione → Leggo porta da datagram e lo spedisco a socket corretta (IP diversi, same socket)
                * Connection oriented (TCP)
                    + Socket TCP definite da quaterne
                        - Source IP
                        - Source port
                        - Dest IP
                        - Dest port
                    + Invio → Più o meno uguale a UDP
                    + Ricezione 
                        - Il ricevente usa tutte le 4 info per dirigere il segmento verso la sua socket
                        - Il ricevente puo supportare varie socket simultanee (ognuna definita da quaterna)
                        - Web server hanno socket diverse per ogni client (HTTP non pers → socket per ogni richiesta)
    * UDP (User Datagram Protocol)
        + Header
            ```
                         32 bit
                  16 bit         16 bit
                Source port     Dest port
                Length          Checksum
                        Payload
            ```
        + Checksum
            - Sender
                * Considera il segmento come una sequenza di interi a 16 bit
                * Checksum = Addizione a complemento a 1 del contenuto del segmento
            - Receiver
                * Calcola il checksum e lo compara al checksum del segmento, se non combacia errore
                * NB → Se riporto va tolto e +1
    * Principi di trasferimento reliable
        + Stop and wait (Sender manda pacchetto e aspetta risposta receiver)
            - Checksum
            - ACK → ACK for last packet received correct, duplicate ACK to retransmit current packet (No NAK) 
            - Sequence numbers
                * To solve ACK/NAK loss/corruption
                * 0, 1
            - Timeout
                * Il sender aspetta tempo x prima di ritrasmettere
            - Performance → Molto male poiche sendo solo un pacchetto alla volta
                * Link = R = 1 Gbps, Delay propag = 15 ms, L = 8000 bit
                * Tempo di trasporto = D = L / R = 8 microsec
                * Utilizzo del sender (U) = L / R / ((RTT = 2 * Delay propag) + R / L) = 0.00027
                * In pratica ho 27 Kb/s di throughput
        + Pipelining (Il sender concede multipli pacchetti in volo to be ACKed)
            - Maggior range sequence number + buffering
            - Con N pacchetti sendati contemporaneamente l'utilizzo (U) viene moltiplicato per N
            - Go Back N
                * Il sender può avere al massimo N pacchetti non ACKati (window di dimensione N)
                * Receiver manda ACK cumulativi (ACK(n) = ACK tutti i pacchetti fino ad n, NB: expectedseqnum)
                * Il sender ha timer per più vecchio pacchetto unACKato, quando scade ritrasmette tutti gli unACKed (timeout(n) = ritrasmetti n e tutti i pacchetti della window con sequence number maggiore di n)
                * Out-of-order-packets → Scartati e reACK dell'ultimo pacchetto integro in ordine
            - Selective Repeat
                * Il sender può avere al massimo N pacchetti non ACKati
                * Il receiver manda un ACK per ogni pacchetto, quindi buffer contiene pacchetti anche out of order
                * Il sender ha timer per ogni paccheto non ACKato, quando scade lo ritrasmette
                * Problema → Se io ho una window di N = 3, mando 3 pacchetti (0,1,2), arrivano, e l'ACK non torna indietro io rimanderò gli stessi 3 pacchetti (0,1,2), ma per il ricevitore saranno i 3 successivi (0,1,2,0,1,2)
    * TCP (Transmission Control Protocol)
        + Reliable protocol over unreliable channel
        + Point to point → Un sender, un receiver
        + Pipelined → In base alla congestione e al flow control viene definita la window size
        + Full duplex → Data flow bidirezionale sulla stessa connessione
        + Connection oriented
        + Flow controlled → Il sender non dossa il receiver
        + Struttura pacchetti
            ```
                            32 Bit
                Source_port     Destination_Port
                        Sequence_number                 → Numero del primo byte nel segmento data
                        ACK_number                      → Sequence number atteso del prossimo pacchetto, cumulativi
                Head_len Unused U A P R S F Rec_window  → U = urgent, A = ACK n. valid, P = PSH = push data now
                                                          R = RST S = SYN F = FIN (connection commands)
                Checksum        Urg_data_poiner
                        Options
                        Payload
            ```
        + Sequence number & ACKs
            ```
                                            TELNET

                Host A                                               Host B
                
                User scrive "c" -----------------------------------> 
                                    Seq = 42, ACK = 79, Data = c

                                <----------------------------------- Server ACKa la "c" e la ritorna
                                    Seq = 79, ACK = 43, Data = c
                
                User ACKa "c"   -----------------------------------> 
                                    Seq = 43, ACK = 80
            ```
        + Round trip time e timeout
            - La stima non deve essere troppo bassa rispetto originale (altrimenti ritrasmissioni continue inutili)
            - La stima non deve essere troppo alta rispetto originale (altrimenti reazione lenta alle perdite)
            - SampleRTT → Tempo da una trasmissione alla ricevuta del suo ACK
            - EstimatedRTT = (1 - a) * EstimatedRTT + a * SampleRTT (a = 0.125)
            - SafetyMargin → DevRTT = (1 - b) * DevRTT + b * |SampleRTT - EstimatedRTT| (b = 0.25)
            - Timeout totale = EstimatedRTT + 4 * SafetyMargin
        + Eventi del sender 
            - Dati ricevuti da app layer
                * Crea un segmento con un sequence number
                * Sequence number = Numero del primo byte nel segmento data
                * Start timer se non sta gia andando (il più vecchio pacchetto non ACKato)
            - Timeout
                * Ritrasmetti il segmento andato in timeout e restarta timer
            - ACK ricevuto
                * Se l'ACK corrisponde al precedente pacchetto non ACKato
                    + Aggiorna pacchetti ACKati, anche quelli precedenti saranno ACKati
                    + Restarta timer se ci sono pacchetti non ACKati
        + Scenario di ritrasmissione
            - Seq + Data = Ret ACK
            - Cumulative ACK = Sendo 2 pacchetti, ricevuti, ACK del primo lost, secondo ACK arriva, si continua
        + Fast retransmit
            - Se il sender riceve 3 ACK stesso pacchetto → Resenda pacchetto non ACKato con sequence number minore
            - Si fa questo perche il pacchetto non ACKato è sicuramente stato perso
        + Flow control
            - Il sender non intasa il receiver
            - Questo avviene perche il receiver controlla la quantità di dati mandata dal sender
                * Il receiver nell'header TCP attacha la "rwnd" value (lo spazio libero del buffer di ricezione) con cui il sender si autoregola
        + Connection management
            - Handshake
                * 2-way → A call B che risponde OK → Connessione stabilita
                    + Non efficace
                        - Half-open connection
                        - Apro connessione e finisco ma al server riarriva richiesta di apertura e i dati trasmessi
                * 3-way 
                    ```
                        Host A                                               Host B
                
                                    -----------------------------------> 
                                            SYNBit = 1, Seq = x

                                    <-----------------------------------
                                SYNbit = 1, Seq = y, ACKbit = 1, ACKnum = x + 1
                
                                    -----------------------------------> 
                                        ACKbit = 1, ACKnum = y + 1
                    ```
            - Closing connection
                ```
                        Host A                                               Host B
                
                                    -----------------------------------> 
                                            FINBit = 1, Seq = x

                                    <-----------------------------------
                                        ACKbit = 1, ACKnum = x + 1

                                    <-----------------------------------
                                            FINbit = 1, Seq = y
                
                                    -----------------------------------> 
                                        ACKbit = 1, ACKnum = y + 1
                ```
        + Principi di controllo di congestione
            - Congestione → La rete non riesce a gestire troppe sorgenti che mandano troppi dati troppo velocemente
                * Cause
                    + Delay grandi se il rate di arrivo si avvicina al rate della capacità della rete
                        - I pacchetti possono essere droppati a causa delle code dei router piene
                        - Il sender può andare in timeout prematuramente mandando dei duplicati
                * Costi
                    + Più lavoro poiche i pacchetti anche se "buoni" vengono ritrasmessi
                    + Questo fa si che la banda dedicata ai pacchetti "buoni" diminuisca
                    + Quando un pacchetto viene droppato le risorse usate per mandarlo sono sprecate
        + Congestion control
            - Il sender aumenta la trasmission rate (window size) per testare la banda finchè non avviene una perdita
                * Additive increase → Ingrandisci cwnd (current window) di 1 MSS (maximum segment size) ad ogni RTT
                * Multiplicative decrease → Dividi per due la cwnd quando rilevo una perdita
                * (Grafico a dente di sega)
            - LastByteSent - LastByteACKed >= cwnd → Dinamica in base alla congestione della rete percepita
            - Sending rate → Manda cwnd bytes, aspetta RTT per gli ACK, senda altri byte
                * Rate ~= cwnd / RTT bytes/s
            - Slow start
                * Inizialmente la cwnd = 1 MSS
                * Raddoppia la cwnd ad ogni RTT (ogni ACK ricevuto)
                * All'inizio il rate è basso ma sale molto velocemente
            - Detecting e reacting to loss
                * Loss indicata dal timeout
                    + Cwnd = 1
                    + Slow start fino a soglia e poi linearmente
                * Loss indicata da 3 ACK ripetuti (TCP RENO)
                    + L'arrivo degli ACK vuol dire che la rete non è congestionata
                    + Cwnd / 2 poi crescita lineare
                * TCP Tahoe in tutti e due i casi imposta la cwnd a 1
            - Passaggio da slow start a crescita lineare
                * Questo passaggio viene effettuato quando si raggiunge la ssthresh
                * Sshthresh → Quando avviene una perdita questa variabile viene settata a metà della cwnd
        + Throughput
            - Media → 3/4 * cwnd/RTT bytes/s
            - In funzione di segment loss probability (L) → 1.22 * MSS / RTT * sqrt(L)
        + Fairness → Se N host condividono banda R ognuno dovrebbe avere un rate medio di R/N
            - La fairness è data anche dal throughput, gli host si "alternano" in base ai loro momenti di picco
            - UDP → L'uso dell'UDP non rispetta la fairness, l'UDP ha sempre la precedenza
        + ECN (Explicit congestion notification)
            - Due bit nell'header IP (ToS field) vengono segnati dai router della rete se viene rilevata congestione
            - L'host ricevente nell'ACK di risposta comunica al sender la congestione tramite l'ECE bit

### Parte 4

- Network Layer
    * Trasporta i segmenti dal sender al receiver
    * Dalla parte del sender incapsula i segmenti in datagrams
    * Dalla parte del ricevitore deploya i segmenti al trasnport layer
    * Il network layer è presente in ogni nodo in pratica e gli header di IP vengono esaminati ad ogni nodo
    * Funzioni
        + Forwarding → Trasporta i pacchetti dall'input del router all'appropriato output
            - Data plane → Definisce come il datagram in arrivo sulla porta di input viene mandato a quella di output
        + Routing → Definisce la strada presa dal pacchetto dalla sorgente alla destinazione (routing algorithms)
            - Control plane → Determina come il datagram è routato dall'host sorgente a quello destinazione
                * Traditional routing algorithms → Implementato in ogni router
                * Software defined networking → Implementato lato server
    * Router
        + Percorso del pacchetto: Layer fisico → Link layer → Network layer
            - Network layer → Decentralized switching
                * Usando header troviamo porta output cercando in forwarding table
                    + Destination-based → Tradizionale, forwarding basato solo sull'IP destinazione
                        - In forwarding table abbiamo dei range di IP (in) che corrispondono a interfacce di output
                        - Longest prefix matching → IP (in) corrisponda a più range, allora corrisponde al più lungo
                    + Generalized → Forwarding basato su ogni set di campi dell'header
                * Queuing → Se i datagram arrivano più velocemente della velocità di forwarding avviene il queuing
                    + Input
                        - Switch non regge se porte in input combinate → Delay and loss per input buffer overflow
                        - Head of the line blocking (HOL) → Datagram primi in fila bloccano successivi
                            * Cause
                                + Contendimento della output port fra due datagram in input
                                + Buffer out già occupato
                    + Output
                        - Switch di pacchetti più veloce dell'output rate → Delay and loss per output buffer overflow
                    + In generale causa perdita pacchetti anche la "mancanza" o "scarsità" (?) di buffer
                    + Buffering
                        - Average → Typical_RTT (250 ms) * Link_capacity (C)
                        - Con N flussi → RTT * C / sqrt(N)
                    + Scheduling → Selezione del prossimo pacchetto da mandare
                        - Network neutrality → Non ci sono priorità "economiche"
                        - FIFO
                            * Politica di drop
                                + Tail → Droppa l'ultimo che arriva
                                + Priority → Droppa in base alla priorità 
                                + Random
                        - Politiche
                            * Priority → Manda il pacchetto con priorità maggiore
                            * Round Robin → Controlla le code e manda pacchetto completo per ognuna, se possibile
                            * Weighted Fair Queuing → Ogni coda riceve una quantità di risorse pesata ad ogni ciclo
                * Switching
                    + Trasferisci i pacchetti dai buffer di input agli appropriati buffer di output
                    + Switching rate → Velocità a cui questo viene fatto
                        - Misurato in multipli della line rate
                        - N input → Switching rate = N * Line rate
                    + Tipi
                        - Memory → Computer che utilizzavano memoria come buffer e CPU per calcolare "output port"
                        - Bus → Datagram da input buf a output via bus condiviso (velocità limitata da banda del bus)
                        - Interconnection network → Divido il datagram in celle di dimensione definita che switcho
    * IP 
        + Datagram format
        ```
                                    32 Bit
                    16 Bit                         16 bit
            Ver Head_len Data_type                 Length
                Identifier                   Flags    Fragment_offset
            Time_to_live Upper_layer             Header_checksum
                                Source IP address
                            Destination IP address
                                    Options
                                    Payload
        ```
        + Fragmentation/Reassembly
            - I vari router di Internet hanno una MTU (dimensione più grande frame trasferibile) differente
                * Per questo avvengono varie frammentazioni durante la route di un pacchetto
                * Il riassemblamento viene fatto solo all'host di arrivo 
                * Nell'header IP ci sono informazioni dedicate a questo
            - Esempio
                ```
                    4000 byte datagram     →     Length = 4000, ID = x, fragflag = 0, offset = 0          
                    
                    MTU = 1500 bytes:
                                  Parte 1  →     Length = 1500 (1480 di dati), ID = x, fragflag = 1, offset = 0
                                  Parte 2  →     Length = 1500, ID = x, fragflag = 1, offset = 185 (1480/8 → 2 Word)
                                  Parte 3  →     Length = 1040, ID = x, fragflag = 0, offset = 370
                ```
        + IPv4 Addressing
            - IP address → ID 32-bit di interfaccia host/router (Interfaccia = Conn fra host/router e link fisico)
            - Subnets → Dispositivi con stessa parte "Subnet" in IP, possono parlare senza uso router
                * IP address
                    + Subnet → Bit di ordine alto
                    + Host → Bit di ordine basso
            - Classes interdomain routing (CIDR)
                * La porzione dell'IP address dedicata alla subnet ha lunghezza arbitraria
                * a.b.c.d/x → x = Numero di bit della parte subnet dell'indirizzo
            - Dynamic host configuration protocol (DHCP) → Va in UDP
                * Ricevi l'indirizzo dal server dinamicamente → Plug and play
                * Funzionamento
                    ```
                        Host → Boadcast: "DHCP Discover"
                        DHCP Server → Risposta: "DHCP offer"
                        Host → Richiedo IP: "DHCP Request" + Messaggio
                        DHCP Server → Mando IP: "DHCP ACK" + Messaggio
                    ```
                * Altre funzioni
                    + Indirizzo del primo router di "hop"
                    + Nome e indirizzo del server DNS
                    + Network mask (network vs host portion of IP)
                * Incapsulamento: DHCP → UDP → IP → 802.1 Ethernet e al contrario
            - L'addressing è gerarchico
                * ICANN (Internet corp for assigned names and numbers) 
                    + Alloca gli indirizzi (ecco come gli ISP ottengono la loro parte di indirizzi)
                    + Gestisce i DNS
                    + Assegna nomi di dominio e risolve dispute
                * L'ISP assegna alle organizzazioni iscritte una parte dei suoi indirizzi
                * L'ISP farà sempre da "intermediario" per la connessione fra l'esterno e una sua organizzazione
            - NAT (Network address translation)
                * Funzionamento
                    + Tutti i pacchetti in arrivo da internet hanno stessa destinazione, IP del NAT, ma porte diverse
                    + NAT "smista" pacchetti fra host connessi alla subnet del NAT (IP "virtuali") in base alla porta
                * Motivazioni
                    + Ogni network locale usa solo un indirizzo IP
                        - ISP non deve assegnare range di IP ma IP unico
                        - Indirizzi della rete locale modificabili senza notificare l'esterno
                        - ISP intercambiabile senza cambiare IP locali
                        - Dispositivi locali non direttamente indirizzabili da esterno (sicurezza)
                * Implementazione
                    + NAT deve
                        - Outgoing datagrams
                            * Source IP e port → NAT IP e port
                            * I server remoti risponderanno usando l'IP e la porta del NAT
                        - NAT translation table → ogni tupla di traduzione (Source IP-port/NAT IP-port)
                        - Incoming datagrams 
                            * NAT IP e port → Source IP e port
                            * In questo modo i pacchetti sono riconducibili ad un destinatario locale
                    + Porta → 16-bit number → 60000 connessioni con un singolo indirizzo
                * Il NAT rompe il sistema a livelli, dovrebbe processare solo fino al livello 3 ma arriva al 4 (TCP)
        + IPv6
            - Motivazioni
                * 32-bit address presto finiranno
                * Il formato dell'header aumenta la velocità di forwarding e la qualità del servizio
                    + Header → 40 bytes fissati
                    + Frammentazione non consentita
            - Formato
                ```
                                32 bit
                    Ver Priority        Flow_label
                    Payload_len      Next_hdr   Hop_limit
                            Source_addr (128 bit)

                            Dest_addr (128 bit)
                            
                            Data

                    Priority → Definisci una priorità dei datagram che scorrono
                    Flow label → Identifica i datagram in uno stesso "flow" (non definito)
                    Next header → Identifica il protocollo subito sopra per il segmento data
                ```
            - Cambiamenti da IPv4
                * Checksum → Rimosso per diminuire il tempo di processing ad ogni hop
                * Opzioni → Ammesse ma fuori dall'header, indicate da "Next header" field
                * ICMPv6
                    + Aggiunti tipi di messaggi, es "Packet too big"
                    + Aggiunte le funzioni di controllo gruppi del multicast
            - IPv4 → IPv6
                * Tunneling → IPv6 datagram trasportati come payload nei datagram IPv4 attraverso i router IPv4
                    ```
                        A   →   B   →   C   →   D   →   E   →   F
                        IPv6    IPv6    IPv4    IPv4    IPv6    IPv6

                        A → B (IPv6): Flow = x, Src = A, Dest = F, Data
                        B → C (IPv6 in IPv4): Src = B, Dest = E, Data = (Flow = x, Src = A, Dest = F, Data)
                        C → D (IPv4)
                        D → E (IPv6 in IPv4): B → C
                        E → F (IPv6): A → B
                    ```
    * Generalized forwarding e SDN
        + Ogni router contiene una flow table che è distribuita da un routing controller logicamente centralizzato
        + OpenFlow → communications protocol that gives access to the forwarding plane of a network switch or router
            - Packet handling
                * Pattern → Matcha i campi dell'header con campi tabella
                * Azione per pacchetti matchati → Drop, forward, modify, send to controller
                * Priorità → Disambigua pacchetti "simili" in base alla priorità della flow table
                * Counter → Numero bytes e numero pacchetti
                ```
                    Switch_port MAC_src MAC_dst Eth_type VLAN_ID IP_src IP_dst   IP_prot TCP_sport TCP_dport Action

                    *           *       *       *        *       *      51.6.0.8 *       *         *         port6

                    I datagram IP destinati a 51.6.0.8 sono forwardati alla porta di output del router n.6
                ```
            - Coportamenti      
                * Router
                    + Match → Il prefisso IP di destinazione più lungo
                    + Action → Forwarda out
                * Switch
                    + Match → Il MAC di destinazione
                    + Action → Forwarda o flooda
                * Firewall
                    + Match → IP e TCP/UDP ports
                    + Action → Concedi o no
                + NAT
                    + Match → IP e porta
                    + Action → Riscrivi indirizzo e porta
