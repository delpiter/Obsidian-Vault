![[DockerArchitecture.png]]


### Stati di un Container
```mermaid
stateDiagram-v2
    direction LR
    [*] --> Created: docker create
    [*] --> Up: docker run
    Created --> Up: docker start
    Up --> Exited: Main program exit<br>docker stop
    Exited --> Up: docker start
    Exited --> Removed: docker rm
    Removed --> [*]
```

```sh
docker ps
# CONTAINER ID  | IMAGE | COMMAND | CREATED | STATUS | PORTS | NAMES
```
Lo status se è exit, mostra l'exit code del container, che molto spesso corrisponde all'[[Exit Status|Exit Code]] del processo principale.