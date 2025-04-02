
>[!definizione] Definizione
>La ***command substitution*** sostituisce a run time, in uno *script*, la riga di comando di un programma con l'[[File Descriptor#Stream di `I/O` dei processi|output]] su `stdout`
>>[!note] Comando
>>```OUT=`./example.exe` ```
>>L'**output** del comando `example.exe` viene inserito all'interno della variabile `OUT`
>
>>[!hint] Sintassi Alternativa
>>`OUT=$(./example.exe)`

### Quoting di Stringhe
>In una riga di comando, le eventuali [[Wildcards]], *variabili*, etc, vengono interpretate dalla shell e sostituite

>[!quote] Disabilitazione
>Per disabilitare (***escape***) la sostituzione delle *wildcards* si circonda la riga di comando con dei caratteri quote: `" "` e `’ ’`

>Double Quote per la disabilitazione di ***wildcards*** e ***spazi***

- **Impedisce** di usare il `;` come *separatore* di comandi
- **Impedisce** la sostituzione di *wildcard*
- *Permette* la sostituzione di variabili e esecuzione di comandi

>Single Quote per la disabilitazione di ***qualunque interpretazione***

- **Impedisce** `;` come *separatore* di comandi
- **Impedisce** la sostituzione di: *wildcards* e *variabili*
- **Impedisce** l'*esecuzione* di comandi

 >[!example] Esempio
 >Il comando: `find ~/ -name "*output*"`
 >- Cerca in tutto il *file system* a partire dalla directory dell'utente i file che contengono `output` all'interno del nome
 
 >[!warning] Attenzione
 >I doppi apici impediscono alla `shell` di interpretare il comando
 >- È come se il comando `find` ricevesse la *stringa* `*output*`
 >
 >>[!done] Conclusione
 >>I caratteri di *quoting* sono usati per passare a dei comandi delle stringhe contenente dei ***metacaratteri***