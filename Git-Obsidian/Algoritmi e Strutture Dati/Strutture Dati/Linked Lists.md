## Simple Linked List
---
>[!info] Descrizione
>Una *linked list* è una delle strutture migliori per quando si trattano un ***numero dinamico di dati***
>>[!tip] Concetto chiave
>>Una *linked list* consiste in un elemento chiamato **nodo** contenente due campi:
>>- Campo dei ***dati***
>>- **Indirizzo** al *nodo successivo*

```c
struct node{
	int elem;
	struct node *next;
};
```
 ![[attachements/Linked-List.webp]]
 
 >[!warning] Problema
 
 Il "**flusso di scorrimento**" è *unidirezionale*
 - Non è possibile *tornare indietro* di un nodo

>[!done] Soluzione
>*Doubly Linked List*

## Doubly Linked List
---
>[!info] Descrizione
>Concetto *simile* alla linked list semplice
>Una *doubly linked list* consiste in un elemento chiamato **nodo** contenente tre campi:
>- Campo dei ***dati***
>- **Indirizzo** al *nodo successivo*
>- **Indirizzo** al *nodo precedente*

```c
struct node{
	int elem;
	struct node *next;
	struct node *prev;
};
```
![[attachements/Doubly-Linked-List.png]]

## Operazioni
---
>[!info] Ricerca
>La ricerca di un elemento in una *linked list* **non è immediato** al contrario del vettore normale

```c
static struct node* NodeSearch(struct node *L, int i){
	struct node* pointer = L;
	while(pointer.elem != i && pointer.next != NULL){
		pointer = pointer.next;
	}
	return pointer;
}
```

>[!info] Inserimento
>Per l'**inserimento**, bisogna tenere particolarmente attenzione a non *alterare e perdere puntatori*

```c
static void NodeInsert(struct node *L, int elem){
	struct node *tmp = node_alloc(elem);

	tmp.next = L.next;
	tmp.prev = L;
	L.next = tmp;
	if(tmp.next != NULL)
		tmp.next.prev = tmp;
}
```

>[!info] Cancellazione
>La **rimozione di un nodo**, come per l'inserimento, è critica in termini di *perdita di informazione*

![[attachements/Doubly Linked List-Delete-1.png]]
![[attachements/Doubly Linked List-Delete-2.png]]

```c
static void NodeDelete(struct node *L){
	if(L.next != NULL)
		L.next.prev = L.prev;
	if(L.prev != NULL)
		L.prev.next = L.next;
	free(L);
}
```

### Costi computazionali
>[!tip] Ricerca
>Il *costo computazionale* della ricerca è $\Theta(n)$
>Poiché per sapere se un elemento *è nella lista o no* è necessario **scorrere tutti gli elementi**

>[!tip] Inserimento
>Il *costo computazionale* dell'inserimento è $\Theta(1)$
>Inserire un nuovo nodo è una operazione a *tempo costante*

>[!tip] Cancellazione
>Il *costo computazionale* della cancellazione è $\Theta(1)$
>**Senza considerare** la **ricerca** del nodo da *eliminare*, l'eliminazione di un nodo è una operazione a *tempo costante*

## Sentinelle
---
>[!info] Descrizione
>Una *sentinella* è un **oggetto artificiale** che *semplifica la gestione* dei **limiti dei dati**
>In una ***doubly linked list*** la *sentinella* punta al **primo** e all'**ultimo** elemento della lista
>- Non sarà più necessario tenere *due pointer separati* per la **testa** e la **coda**

La lista *vuota* utilizzando le *sentinelle* è la **sola sentinella**

## Alberi e Liste
---
### Alberi Binari
>[!info] Come rappresentare
>Per potere rappresentare un **albero binario** con una *linked list* è necessaria una struttura con 4 elementi:
>- *Dato*
>- **Puntatore** al *Padre*
>- **Puntatore** al $1^o$ *figlio*
>- **Puntatore** al $2^o$ *figlio*

```c
struct BinaryTreeNode{
	int value;
	BinaryTreeNode* Parent;
	BinaryTreeNode* lChild;
	BinaryTreeNode* rChild;
}
```
![[attachements/Binary-Tree.png]]

>[!warning] Problema

Non è possibile rappresentare un ***albero normale*** con questa configurazione

### Alberi Generici
>[!info] Come rappresentare
>Per potere rappresentare un **albero generico** con una *linked list* è necessaria una struttura con 4 elementi:
>- *Dato*
>- **Puntatore** al *Padre*
>- **Puntatore** al $1^o$ *figlio*
>- **Puntatore** al $1^o$ *fratello*

```c
struct TreeNode{
	int value;
	TreeNode* Parent;
	TreeNode* FirstChild;
	TreeNode* FirstSibling;
}
```

![[attachements/Linked-List-Tree.png]]