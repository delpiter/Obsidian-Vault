## Parametri del comando Run
---
| Flag | Argomento | Descrizione |
|------|-----------|-------------|
| `-e` | `list` | Imposta variabili d'ambiente |
| `-d` | | Esegue il container in background e stampa l'ID |
| `-i` | | Mantiene STDIN aperto anche se non collegato |
| `--name` | `string` | Assegna un nome al container |
| `--network` | `string` | Connette il container a una rete (default: `"default"`) |
| `-p` | `list` | Pubblica le porte del container sull'host |
| `-h` | `string` | Hostname del container |
| `--ip` | `string` | Indirizzo IPv4 (es. `172.30.100.104`) |
| `--ip6` | `string` | Indirizzo IPv6 (es. `2001:db8::33`) |
| `-v` | `list` | Monta un volume |
| `--expose` | `list` | Espone una porta o un intervallo di porte |
| `--rm` | | Rimuove automaticamente il container all'uscita |
| `--restart` | `restart_policy` | Riavvia il container all'uscita (default: `"no"`) |
| `-w` | `workingdir` | Directory di lavoro nel container in cui viene eseguito il comando |
## Eseguire un comando in un Container
---
```sh
docker run -it -w / ubuntu echo I am in `pwd`
```

>[!question] Chi interpreta questa espressione?

Il comando `{docker icon} docker run` viene eseguito in una [[Interfaccia Utente|shell]] interattiva o in uno [[Esecuzione dei File|script bash]].
In entrambi i casi viene eseguito in una bash in esecuzione sull'host.
- Questa ***bash dell'host*** interpreta le espansioni del comando principale.

>[!danger] Se non quotate le espansioni del comando principale, queste vengono interpretate dalla `shell` dell'host, **non** del container.

L'output del comando iniziale sarà:
- `{sh icon} I am in /home/user`, la [[Command Substitution]] è stata effettuata dall'host.

Per produrre l'output corretto, è necessario utilizzare le quote (`''`).

> ***Non basta***

>[!warning] Nel container non è presente una bash che espande il comando.

È necessario eseguire la bash nel comando **docker**.

```docker
docker run -it -w / ubuntu /bin/bash -c 'echo I am in `pwd`'
```

Produce il corretto output:
- `I am in /`
- Il flag `-c` ordina alla bash di eseguire i comandi che seguono.

## Eseguire un comando interattivo in un container in background
> Supponiamo di aver eseguito il seguente comando:

```docker
docker run -d -it --name name ubuntu
```

Questo crea un [[Container]] in ***backgorund***.
- Per eseguire dei comandi, è necessario l'utilizzo del comando.

```sh
# docker exec [OPTIONS] container command [ARGS]
docker exec -it -u root:root -w /usr/local/ name find ./ -iname '*ma*'
```

Esegue il comando `{sh icon} find ./ -iname '*ma*'` all'interno del container `name`.

>[!info]
>Il comando `docker exec` consente di eseguire uno specifico comando all'interno di un container che **deve essere** già in esecuzione.