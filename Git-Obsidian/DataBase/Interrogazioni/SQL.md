## Structured Query Language
---
>[!definizione]
>**SQL** è il *linguaggio* per un [[Git-Obsidian/DataBase/Introduzione#DBMS|DBMS]] basato sul [[Modello Relazionale]] che riunisce funzionalità di:
>- *Creazione*
>- *Manipolazione*
>- *Controllo*

**SQL** è nato come un *linguaggio dichiarativo* (***non procedurale***)
- Non specifica la sequenza di operazioni da compiere per ottenere il risultato.

Il linguaggio è "***relazionalmente completo***"
- Ogni espressione dell'[[Algebra Relazionale]] può essere tradotta in **SQL**.

>[!hint] Differenze dal Modello Relazionale
>Il modello dei dati **SQL** è basato su **tabelle** e non *relazioni* 
>- Il *risultato* di una operazione **può restituire una tabella con righe duplicate**.
>- In alcuni casi l'*ordine delle colonne* ha **rilevanza**.

### Componenti SQL
>Il linguaggio si compone di 3 sotto categorie.

>[!abstract] ***D***ata ***D***efinition ***L***anguage
>Il [[DDL]] contiene costrutti per  la **creazione** e **modifica** dello schema di un *data base*.

>[!caution] ***D***ata ***M***anipulation ***L***anguage
>Il [[DML]] contiene costrutti per l'**interrogazione**, **eliminazione** e **modifica** dei dati di un *data base*.

>[!help] ***D***ata ***C***ontrol ***L***anguage
>Il `DCL` contiene i costrutti necessari per **fornire** o **revocare** agli utenti i *permessi* necessari per usare comandi di **DDL** e **DML**.