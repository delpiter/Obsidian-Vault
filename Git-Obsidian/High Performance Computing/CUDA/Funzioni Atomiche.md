>[!info]
>Le funzioni atomiche sono una serie di procedure di cui viene data la garanzia che l'operazione verrà eseguita in modo [[../../Sistemi Operativi/Teoria/9 - Condivisione di Risorse#Azioni Atomiche|atomico]].

Molte delle funzioni sono ***polimorfiche***
- Funzionano per *diversi tipi di dato*.
- `{c icon} atomicAdd()` funziona con `int`, `unsigned`, `float`, `double`.

Non tutte le funzioni supportano gli stessi tipi:
- [[https://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html#atomic-functions]]