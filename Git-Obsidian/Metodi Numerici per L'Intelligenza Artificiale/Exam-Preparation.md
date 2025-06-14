## Utilities for Exam


```python
import numpy as np
import sympy as sim
import scipy as sp
import math
import matplotlib.pyplot as plt
import SolveTriangular as st
```

### Matrix Conditions
- The following blocks will display some function to check matrixes constraints.


```python
# Check if a matrix is positively defined
def is_positively_defined(A):
    return np.all(np.linalg.eigvals(A) > 0)

# Check if a matri is symmetric
def is_symmetric(A):
    return np.all(A==A.T)

# Check if the matrix has max rank
def has_max_rank(A):
    return A.shape[0]==np.linalg.matrix_rank(A)

# Check if its a square matrix
def is_square(A):
    return A.shape[0]==A.shape[1]

# Check if the matrix is well or ill conditioned
"""
Returns:
- 1 if the matrix is well conditioned
- 0 if is averagely poorly ill
- -1 if is ill conditioned
"""
def matrix_condition(A):
    cond=np.linalg.cond(A)
    if cond < 10**2:
        return 1
    elif cond>=10**2 and cond<=10**3:
        return 0
    else:
        return -1

# Check if the singularity of a matrix
def is_not_singular(A):
    return np.linalg.det(A)!=0
    
# Check if the matrix is dense
def density_Percentage(A):
    return np.count_nonzero(A)/(A.shape[0]*A.shape[1])

# Check if the matrix is strictly diagonally dominant
def is_diagonally_dominant(A):
    abs_A = np.abs(A)
    return np.all(2*np.diag(abs_A) > np.sum(abs_A, axis=1)) #|Aii| ≥ ∑j≠i |Aij|  =>  2|Aii| ≥ ∑j |Aij|.

# A (square) matrix is small if its dimension is in range of 10<x<100
# Its big if is in range of 300<x<500
```

## Roots of a Function
---
> Metodi:

1. Bisection.
2. Regula Falsi
3. Metodo delle Corde
4. Metodo delle Secanti
5. Newton, Newton Modified


```python
def order_valuation(xk,iterazioni):
     #Vedi dispensa allegata per la spiegazione

    k=iterazioni-4
    p=np.log(abs(xk[k+2]-xk[k+3])/abs(xk[k+1]-xk[k+2]))/np.log(abs(xk[k+1]-xk[k+2])/abs(xk[k]-xk[k+1]));
    
    ordine=p
    return ordine

```

### Bisection

> Key Operation:

$$x_{k+1}=a_{k} +\displaystyle\frac{b_k-a_k}{2}$$
If $f(a)*f(x_{k+1})<0$
- $b=x_{k+1}$

If $f(a)*f(x_{k+1})>0$
- $a=x_{k+1}$

> Ordine di Convergenza Lineare con $p=1$


```python
def bisection(f, a, b, tolx):
    fa=f(a)
    fb=f(b)
    
    if fa*fb >= 0:
        print("Failed to apply method")
        return None, None, None

    it = 0
    v_xk = []

    while abs(b-a)> tolx:
        xk = a+(b-a)/2 # key operation
        v_xk.append(xk)
        it+=1
        fxk=f(xk)
        if fxk==0:
            return xk, it, v_xk
        
        if fa*fxk < 0: # la radice si trova nell'intervallo [a, xk]
            b = xk
            fb=fxk
        elif fxk*fb < 0: # intervallo [xk, b]
            a=xk
            fa=fxk
    return xk, it, v_xk
```

### Regula Falsi

Algoritmo pressoché uguale alla bisezione:

> Key Operation

$$x_{k+1}=a_{k}-f(a_{k})\cdot \displaystyle{\frac{b_{k}-a_{k}}{f(b_{k})-f(a_{k})}}$$
> Perchè?

Il concetto sarebbe quello di **considerare** anche i **valori che la funzione assume negli estremi dell'intervallo**.
- Si considera come *nuova approssimazione* della soluzione la retta passante per $(a,f(a)), (b,f(b))$

> Ordine di Convergenza Superlineare con $p<1.5$ (generalmente)


```python
def falses(f, a, b, tolx, tolf, maxit):
    fa=f(a)
    fb=f(b)

    if fa*fb >= 0:
        print("Failed to apply method")
        return None, None, None
    
    it = 0
    v_xk=[]
    fxk=100
    error=100 # difference between 2 consecutive calculation
    xprec=a
    
    while it<maxit and abs(fxk)> tolf and error > tolx:
        xk = a-fa*(b-a)/(fb-fa) # key operation
        v_xk.append(xk)
        it+=1
        fxk=f(xk)
        if fxk==0:
            return xk, it, v_xk

        if fa*fxk < 0: # la radice si trova nell'intervallo [a, xk]
            b = xk
            fb=fxk
        elif fxk*fb < 0: # intervallo [xk, b]
            a=xk
            fa=fxk
        if xk!=0:
            error=abs(xk-xprec)/abs(xk)
        else:
            error=abs(xk-xprec)
        xprec=xk
    return xk, it, v_xk
```

### Linearizzazione
> Data $f(x),x_{0},f(x_{0})$: si ***approssima*** la funzione con una retta per $(x_{0},f(x_{0}))$.

- $x_{k+1}=x_{k}-\displaystyle\frac{f(x_{k})}{m_{k}}$

A seconda della scelta di $m_k$ abbiamo metodi diversi

#### Metodo delle Corde
> Il metodo assume la forma

$$x_{k+1}=x_{k}-\frac{f(x_{k})}{m}$$
- $m$ è dato all'inizio e viene usato per ***tutte le iterazioni***

Scelta classica: $m=\frac{f(b)-f(a)}{b-a}$
$$
x_{k+1}=x_{k}-\displaystyle{\frac{b-a}{f(b)-f(a)}}f(x_{k})
$$


```python
def corde(f, x0, coeff_ang, tolx, tolf, nmax):
    xk=[] # iterati successivi
    it=0
    errorex=1+tolx # Inizializziamo gli errori in modo che entri nel while almeno una volta
    erroref=1+tolf #

    while it<nmax and erroref>=tolf and errorex>=tolx :
        fx0=f(x0)       #|
        d=fx0/coeff_ang #| Key Operations
        x1=x0-d         #|
        fx1=f(x1)
        erroref=np.abs(fx1)
        if x1!=0:
            errorex=abs(d)/abs(x1)
        else:
            errorex=abs(d)
        x0=x1
        it=it+1
        xk.append(x1)
    if(it==nmax):
        print('Max Iteration Reached')
    return x1,it,xk
```

#### Metodo delle Secanti
> Il seguente metodo richiede **due iterati iniziali**

L'**approssimazione** della funzione $f$ nell'intervallo $[x_{k-1},x_{k}]$ è la retta che passa per i punti: $(x_{k-1}),f(x_{k-1}),(x_{k},f(x_{k}))$ con *coefficiente angolare*:
$$m_{k}=\frac{f(x_{k})-f(x_{k-1})}{x_{k}-x_{k-1}}$$

> La formula diventa:

$$
x_{k+1}=x_{k}-f(x_{k}) \displaystyle{\frac{x_{k}-x_{k-1}}{f(x_{k})-f(x_{k-1})}}
$$

La convergenza è ***garantita*** se le approssimazioni $x_{0}$ e $x_{1}$ si scelgono abbastanza **vicine alla soluzione**.

> Ordine di Convergenza Superlineare $p=\frac{1+\sqrt{ 5 }}{2}\approx1.618$


```python
def secanti(f, x0, x1, tolx, tolf, nmax):
    xk=[] # iterati successivi
    it=0
    errorex=1+tolx # Inizializziamo gli errori in modo che entri nel while almeno una volta
    erroref=1+tolf #

    while it<nmax and erroref>=tolf and errorex>=tolx :
        fx0=f(x0)                 #
        fx1=f(x1)                 # Key Operations
        d=fx1*((x1-x0)/(fx1-fx0)) #
        
        x1new=x1-d 
        
        fx1=f(x1new)
        
        xk.append(x1new)
        
        if x1new!=0:
            errorex=abs(d)/abs(x1new)
        else:
            errorex=abs(d)
            
        erroref=abs(fx1)
        
        x0=x1
        x1=x1new
        it=it+1
    if(it==nmax):
        print('Max Iteration Reached')
    return x1,it,xk
```

#### Newton
> Ad ogni passo $k$ si considera la retta passante per il punto $(x_{k},f(x_{k}))$ e *tangente alla curva* $f(x)$.

Si determina il nuovo iterato come il punto di incontro tra la **retta** e l'*asse* delle $x$.
- $m_k=f'(x_k)$

$$
x_{k+1}=x_{k}-\frac{f(x_{k})}{f'(x_{k})}
$$

> Ordine di convergenza Quadratica con $p=2$

A meno che la funzione $f$ abbia una molteplicità nello zero $\alpha$: $m>1$,
- Il metodo di *Newton* non ha più convergenza *Quadratica* ma **Lineare**.

Soluzione:
- Applicare il metodo di newton modificato:
$$x_{k+1}=x_{k}-m \displaystyle{\frac{f(x_{k})}{f'(x_{k})}}$$

Che si dimostra avere convergenza $p=2$
- Dove $m$ è la molteplicità dello zero


```python
def newton(f,d_f,x0,tolx,tolf,nmax):
  
    xk=[]
    
    it=0
    errorx=1+tolx
    errorf=1+tolf
    
    while it<nmax and errorf>=tolf and errorx >= tolx:
        fx0=f(x0)
        if abs(d_f(x0))<=np.spacing(1):
            print("First Derivate = 0 in x0")
            return None, None, None
        
        d=f_x0/d_f(x0)
        x1=x0-d # Key operations
        
        fx1=f(x1)
        errorf=np.abs(fx1)
        if x1!=0:
            errorx=abs(d)/abs(x1)
        else:
            errorx=abs(d) 
        
        it=it+1
        x0=x1
        xk.append(x1)
      
    if it==nmax:
        print('Max Iteration Reached')
        
    
    return x1,it,xk

def newton_molteplicity(f,d_f,m,x0,tolx,tolf,nmax):    
    xk=[]
    
    it=0
    errorx=1+tolx
    errorf=1+tolf
    
    while it<nmax and errorf>=tolf and errorx >= tolx:
        fx0=f(x0)
        if abs(d_f(x0))<=np.spacing(1):
            print("First Derivate = 0 in x0")
            return None, None, None
        
        d=f_x0/d_f(x0)
        x1=x0-m*d # Key operations
        
        fx1=f(x1)
        errorf=np.abs(fx1)
        if x1!=0:
            errorx=abs(d)/abs(x1)
        else:
            errorx=abs(d)
        
        it=it+1
        x0=x1
        xk.append(x1)
      
    if it==nmax:
        print('Max Iteration Reached')  
    return x1,it,xk
```

## Systems
---

### Non-Linear System Solution

#### Newton Rapshon
> Il metodo consiste nel trasformare la **funzione non lineare** nel corrispondente *sviluppo di taylor*.

Ricavando il sistema:
$$
\begin{cases}
\displaystyle 0 = f_1\left(x_1^{(k)}, x_2^{(k)}\right) + \frac{\partial f_1}{\partial x_1}\left(x_1^{(k)}, x_2^{(k)}\right)(x_1 - x_1^{(k)}) + \frac{\partial f_1}{\partial x_2}\left(x_1^{(k)}, x_2^{(k)}\right)(x_2 - x_2^{(k)}) \\
\displaystyle 0 = f_2\left(x_1^{(k)}, x_2^{(k)}\right) + \frac{\partial f_2}{\partial x_1}\left(x_1^{(k)}, x_2^{(k)}\right)(x_1 - x_1^{(k)}) + \frac{\partial f_2}{\partial x_2}\left(x_1^{(k)}, x_2^{(k)}\right)(x_2 - x_2^{(k)})
\end{cases}
$$
Che espresso in forma matriciale:
$$
\begin{array}
\ 0=F(X_{k})+J(X_{k})(X-X_{k}) \\
J(X_{k})(X-X_{k})=-F(X_{k}) \\
\end{array}
$$
Sotto l'ipotesi che la Jacobiana sia invertibile:
- $\cancel{ J^{-1}(X_{k})J(X_{k}) }(X-X_{k})=-J^{-1}(X_{k})F(X_{k})$

Possiamo notare che $-J^{-1}(X_{k})F(X_{k})$ è la soluzione del sistema lineare
$$J(X_{k})s_{k}=-F(X_{k})$$

> Schematizzazione dell'algoritmo:
1. Valutare $J(X_{k-1})$
2. Risolvere il sistema lineare $J(X_{k-1})s_{k-1}=-F(X_{k-1})$
3. Porre $X_k=X_{k-1}+s_{k-1}$

> Convergenza

Metodo a convergenza **Locale** e ordine di convergenza **Quadratica**


```python
def newton_rapshon(init_guess,f,J,tolx,tolf,nmax):
    X=np.array(init_guess, dtype=float)
    
    it=0
    errorf=1+tolf
    errorx=1+tolx
    error=[]

    while it<nmax and errorf>=tolf and errorx>=tolx:
        jx=J(X[0],X[1])
        
        if np.linalg.det(jx)==0:
            print("J-Matrix does not have max rank")
            return None,None,None
        
        fx=np.array(f(X[0],X[1]))
        fx=fx.squeeze()
        
        s=np.linalg.solve(jx,-fx)

        Xnew=X+s
        XnNorm=np.linalg.norm(Xnew,1)

        if XnNorm!=0:
            errorx=np.linalg.norm(s,1)/XnNorm
        else:
            errorx=np.linalg.norm(s,1)

        error.append(errorx)
        fnew=f(Xnew[0],Xnew[1])
        errorf=np.linalg.norm(fnew.squeeze(),1)

        X=Xnew
        it=it+1
    return X,it,error
```

#### Newton Rapshon Corde
> Concetto chiave
- La Jacobiana viene ***valutata solo la prima volta*** e si usa sempre lo *stesso valore*


```python
def newton_rapshon_corde(init_guess,f,J,tolx,tolf,nmax):
    X=np.array(init_guess)
    
    it=0
    errorf=1+tolf
    errorx=1+tolx
    error=[]
    
    jx=J(X[0],X[1]) # calculate jx only one time
    
    if np.linalg.det(jx)==0:
        print("J-Matrix does not have max rank")
        return None,None,None

    while it<nmax and errorf>=tolf and errorx>=tolx:
        fx=np.array(f(X[0],X[1]))
        fx=fx.squeeze()
        
        s=np.linalg.solve(jx,-fx)

        Xnew=X+s
        XnNorm=np.linalg.norm(Xnew,1)

        if XnNorm!=0:
            errorx=np.linalg.norm(s,1)/XnNorm
        else:
            errorx=np.linalg.norm(s,1)
        error.append(errorx)
        fnew=f(Xnew[0],Xnew[1])
        errorf=np.linalg.norm(fnew.squeeze(),1)

        X=Xnew
        it=it+1
    return X,it,error
```

#### Newton Rapshon-Shamaskii
> Concetto chiave
- La Jacobiana viene ***valutata ogni*** $m$ ***iterazioni***.


```python
def newton_rapshon_sham(init_guess,f,J,tolx,tolf,nmax,counter):
    X=np.array(init_guess)
    
    it=0
    errorf=1+tolf
    errorx=1+tolx
    error=[]

    while it<nmax and errorf>=tolf and errorx>=tolx:
        
        if it % counter == 0: # Calculate jx only once every "counter" steps
            jx=J(X[0],X[1])
        shamCounter=shamCounter + 1
        
        if np.linalg.det(jx)==0:
            print("J-Matrix does not have max rank")
            return None,None,None
        fx=np.array(f(X[0],X[1]))
        fx=fx.squeeze()
        
        s=np.linalg.solve(jx,-fx)

        Xnew=X+s
        XnNorm=np.linalg.norm(Xnew,1)

        if XnNorm!=0:
            errorx=np.linalg.norm(s,1)/XnNorm
        else:
            errorx=np.linalg.norm(s,1)
        error.append(errorx)
        fnew=f(Xnew[0],Xnew[1])
        errorf=np.linalg.norm(fnew.squeeze(),1)

        X=Xnew
        it=it+1
    return X,it,error
```

#### Minimum of Non Linear Function
> Concetto Chiave

Occorre esaminare la matrice Hessiana $H(X)$
Il sistema riscritto in **termini matriciali** diventa:
$$
0=\nabla f(X_{k})+H(X_{k})(X-X_{k})
$$

Sotto l'ipotesi che $\det H(X_{k})\neq0$ si ricava:
$$
X-X_{k}=-H^{-1}(X_{k})\nabla f(X_{k})
$$

> Schematizzazione dell'algoritmo:
1. Valutare $H(X_{k-1})$
2. Risolvere il sistema lineare $ H(X_{k})s_{k}=-\nabla f(X_{k})$
3. Porre $X_k=X_{k-1}+s_{k-1}$


```python
def newton_rapshon_min(init_guess,grad_f_num,H_num,tolx,tolf,nmax):
    X=np.array(init_guess)
    
    it=0
    errorf=1+tolf
    errorx=1+tolx
    error=[]

    while it<nmax and errorf>=tolf and errorx>=tolx:
        Hx=H_num(X[0],X[1])
        if np.linalg.det(Hx)==0:
            print("H-Matrix does not have max rank")
            return None,None,None
        
        gfx=grad_f_num(X[0], X[1])
        gfx=gfx.squeeze()
        
        s=np.linalg.solve(Hx,-gfx)

        Xnew=X+s
        XnNorm=np.linalg.norm(Xnew,1)
        
        # Criteri di arresto
        if XnNorm!=0:
            errorx=np.linalg.norm(s,1)/XnNorm
        else:
            errorx=np.linalg.norm(s,1)

        gradf_xnew=grad_f_num(Xnew[0],Xnew[1])
        errorf=np.linalg.norm(gradf_xnew.squeeze(),1)
        
        error.append(errorx)

        X=Xnew
        it=it+1
    return X,it,error
```

### Linear Systems

#### Iterative Methods

> Metodi che generano una ***successione di soluzioni*** che sotto *opportune ipotesi*, convergono alla **soluzione**.

I metodi si basano tutti sullo stesso ***principio di decomposizione***.
- Si decompone $A$ in due matrici tali che: $A=M-N$ con $\det(M)\neq 0$

$$(M-N)x=b\implies Mx=Nx +b$$
Il metodo suggerisce le soluzioni successive:
$$x^{(k)}=M^{-1}Nx^{(k-1)}+M^{-1}b\quad k=1,2,\dots$$

> Si parte da un vettore $x^{(0)}$ arbitrario e si costruisce la soluzione tramite il processo iterativo:

$$x^{(k)}=Tx^{(k-1)}+q\qquad k=1,2,\dots$$
**Dove** 
- $T=M^{-1}N$ è detta ***matrice di iterazione*** del metodo iterativo.
- $q=M^{-1}b$

Nei prossimi metodi si considera la seguente decomposizione:
$$A=D+E+F$$
$$
D=\begin{bmatrix}
a_{11} &  \\
 & \ddots \\
&  & a_{nn}
\end{bmatrix},
E=\begin{bmatrix}
0 & 0 & \dots & 0 & 0 \\
a_{21} & 0  & \dots & 0 & 0\\
a_{31} &  a_{32} &  \ddots & 0 & 0 \\
\vdots  & \vdots & \ddots & \ddots & \vdots\\
a_{n1} & a_{n2} &  \dots& a_{nn-1} & 0
\end{bmatrix},
F=\begin{bmatrix}
0 & a_{12} & a_{13} & \dots & a_{1n} \\
0 & 0 & a_{23} & \dots & a_{2n} \\
\vdots & \vdots & \ddots & \ddots & \vdots \\
0 & 0 & 0 & \ddots & a_{n-1n} \\
0 & 0 & 0 & \dots & 0
\end{bmatrix}
$$
- $D$ Matrice *diagonale*
- $E$ Matrice *Triangolare Inferiore*
- $F$ Matrice *Triangolare Superiore*

###### Teorema Convergenza
La condizione ***necessaria e sufficiente*** per la *convergenza* del procedimento iterativo, comunque si scelga il vettore iniziale $x^{(0)}$, al vettore soluzione $x$ del sistema $Ax=b$ , è che:
>$$\rho(T)<1$$

Più il raggio spettrale è *piccolo* più è **veloce la convergenza**

##### Jacobi
> Nel metodo di Jacobi la *decomposizione* di $A$ nella forma $A=M-N$ si ottiene scegliendo $M=D$ e $N=-(E+F)$

Il procedimento iterativo diventa:
$$x^{(k)}=-D^{-1}(E+F)x^{(k-1)}+D^{-1}b_{1}\quad k=1,2,\dots$$
- Raccogliendo $D^{-1}$
$$x^{k}=D^{-1}(\underbrace{ N }_{ -(E+F) }x^{(k-1)}+b)$$

Ogni elemento dell'iterato $(k)$ è ***indipendente dagli altri***:
- Ottimo metodo per la parallelizzazione.


```python
def jacobi(A,b,x0,toll,it_max):
    errore=1000
    d=np.diag(A)
    n=A.shape[0]
    E=np.tril(A,-1)
    F=np.triu(A,1)
    N=-(E+F)

    # Convergencee Check (||T|| < 1 or sr < 1)
    T=np.dot(np.diag(1/d),N)
    eigenvalues=np.linalg.eigvals(T)
    spectralradius=np.max(np.abs(eigenvalues)) # sprad < 1 -> Converge
    # print("Norm:",np.linalg.norm(T,2))
    
    it=0
    er_vet=[]
    while it<=it_max and errore>=toll:
        x=(b+N@x0)/d.reshape(n,1)
        errore=np.linalg.norm(x-x0)/np.linalg.norm(x)
        er_vet.append(errore)
        x0=x.copy()
        it=it+1
    return x,it,er_vet
```

##### Gauss Seidel
> La *decomposizione* di $A$ si ottiene scegliendo $M=E+D$ e $N=-F$

La soluzione al passo $k$ si ottiene come:
$$x^{(k)}=-(E+D)^{-1}Fx^{(k-1)}+(E+D)^{-1}b\quad k=1,2,\dots$$

In termini di componenti:
$$Mx^{(k)}=Nx^{(k-1)}+b$$

Sostituendo ad $M$ la matrice $E+D$ e ad $N$ la matrice $-F$, otteniamo:
$$
\begin{array}
\ (E + D)\,x^{(k)} = -F\,x^{(k-1)} + b \qquad k = 1, 2, \dots \\
\end{array}
$$

- Questo passaggio suggerisce che la soluzione al passo $(k)$ si ottiene risolvendo il sistema ***triangolare inferiore*** avente $(E+D)$ come matrici dei coefficienti e termine noto $b-Fx^{(k-1)}$.
$$Mx^{(k)}=b+Nx^{(k-1)}$$


```python
def gauss_seidel(A,b,x0,toll,it_max):
    errore=1000
    d=np.diag(A)
    D=np.diag(d)
    E=np.tril(A,-1)
    F=np.triu(A,1)
    M=D+E
    N=-F

    # Convergence check
    invM=np.linalg.inv(M)
    T=invM@N
    eigenvalues=np.linalg.eigvals(T)
    spectralradius=np.max(np.abs(eigenvalues))
    # print("raggio spettrale Gauss-Seidel ",raggiospettrale)

    # print("Norm:", np.linalg.norm(T,2))
    
    it=0
    er_vet=[]
    while it<=it_max and errore>=toll:
        x,flag=st.Lsolve(M,b+N@x0) # Key Operation
        errore=np.linalg.norm(x-x0)/np.linalg.norm(x)
        er_vet.append(errore)
        x0=x.copy()
        it=it+1
    return x,it,er_vet
```

##### Gauss Seidel SOR
> Accelerazione di un Metodo Iterativo

Partendo dal metodo di **Gauss Seidel**:
$$
x^{(k)} = -D^{-1}(E\,x^{(k)} + F\,x^{(k-1)} - b)
$$
Può essere riscritto nella forma:
- $x^{(k)}=x^{(k-1)}+r^{(k)}$

*Dove*
$$
r^{(k)}=x^{(k)}-x^{(k-1)}=-D^{-1}[Ex^{(k)}+Fx^{(k-1)}-b]-x^{(k-1)}
$$

> Modificando il *metodo di Gauss-Seidel* otteniamo:

$$
x^{(k)}=x^{(k-1)}+\omega r^{(k)}
$$

Scegliendo opportunamente il parametro $\omega>0$ si può ***accelerare la convergenza in modo significativo***.

Il metodo **SOR** si ottiene sostituendo (1) con (2):
$$x^{(k)} = (1 - \omega)x^{(k-1)} - \omega D^{-1}[E x^{(k)} + F x^{(k-1)} - b]$$

Da cui si ricava:

$$x^{(k)} = (1 - \omega)x^{(k-1)} + \omega[-D^{-1}[E x^{(k)} + F x^{(k-1)} - b]]$$



```python
def gauss_seidel_sor(A,b,x0,toll,it_max,omega):
    errore=1000
    d=np.diag(A)
    D=np.diag(d)
    Dinv=np.diag(1/d)
    E=np.tril(A,-1)
    F=np.triu(A,1)

    # Iteration Matrix
    Momega=D+omega*E
    Nomega=(1-omega)*D-omega*F
    T=np.dot(np.linalg.inv(Momega),Nomega)

    # Convergence Check
    eigenvalues=np.linalg.eigvals(T)
    spectralradius=np.max(np.abs(eigenvalues))
    # print("raggio spettrale Gauss-Seidel SOR ", raggiospettrale)
    
    M=D+E
    N=-F
    it=0
    xold=x0.copy()
    xnew=x0.copy()
    er_vet=[]
    while it<=it_max and errore>=toll:
        xtilde,flag=Lsolve(M, b-F@xold)
        xnew=(1-omega)*xold+omega*xtilde
        errore=np.linalg.norm(xnew-xold)/np.linalg.norm(xnew)
        er_vet.append(errore)
        xold=xnew.copy()
        it=it+1
    return xnew,it,er_vet
```

#### Direct Methods
#####  Fattorizzazione
>Obbiettivo

L'obbiettivo della ***fattorizzazione*** $A=BC$ è quello di trasformare il sistema lineare $Ax=b$ in un sistema lineare *equivalente*.
$$BCx=b$$
- Si può spezzare in due problemi:
$$\begin{cases}By=b \\ Cx=y\end{cases}$$

##### Stabilità di un Algoritmo di Fattorizzazione
> Consideriamo la fattorizzazione $A=BC$

Consideriamo:
- $\mathcal{B}=B+\delta B$
- $\mathcal{C}=C+\delta C$

>I fattori $\mathcal{B},\mathcal{C}$ possono essere pensati come fattorizzazione esatta di una *matrice perturbata*.

$$
A+\delta A=\mathcal{B}\cdot\mathcal{C}
$$
Quindi
$$
A+\delta A=\underbrace{ (B+\delta B)\cdot(C+\delta C) }_{ BC+B\delta C+\delta BC+\delta B\delta C }
$$
La relazione non dipende solo dalle perturbazioni, ma è tanto più grande quanto sono più grandi gli elementi dei fattori $B$ e $C$.

###### Stabilità di un Algoritmo di Fattorizzazione
>Data una matrice $A$ i cui elementi sono tutti minori o uguali a $1$, si dice che un *algoritmo di fattorizzazione* è ***numericamente stabile in senso forte***, se esistono delle costanti positive $a$ e $b$ indipendenti dall'ordine e dagli elementi di $A$ tali che:
>$$\mid b_{ij}\mid\leq a\quad \mid c_{ij}\mid\leq b$$

Se le costanti $a,b$ dipendono dall'ordine di $A$ si dice che la fattorizzazione è ***stabile in senso debole***.

##### Gauss with Pivot
> Il metodo di eliminazione Gaussiana si basa sulla fattorizzazione $A=LU$

> Teorema

Data $A\in\mathbb{R}^{n\times n}$ sia $A_{k}$ la sottomatrice principale di testa di $A$ considerando le prime $k$ righe e colonne di $A$.
Se $A_{k}$ ***non è singolare*** per ogni $k=1,\dots,n-1$ allora esiste ed è unica la fattorizzazione $LU$ di $A$

Dove:
- $L$ è una matrice **triangolare inferiore**.
- $U$ è una matrice **triangolare superiore**.

Data una qualunque matrice $A$ non singolare, esiste una matrice di permutazione $P$ non singolare t.c. $PA=LU$
- Una ***matrice di permutazione*** è una matrice ottenuta dalla *matrice identità* **scambiando** due righe tra di loro. Effettuare $P\cdot A$ equivale a scambiare le stesse due righe della matrice $A$.
- La **matrice di permutazione** è sempre una matrice ortogonale, cioè: $PP^T=I$

> Gauss con Pivotaggio

Al passo $k$, prima di calcolare $l_{ik}$, se $a_{kk}=0$ si cerca dalla colonna $k$-*esima* a partire dalla riga $k$-*esima*, la posizione di riga $s$ in cui si trova il ***primo elemento diverso da zero***.

Sfruttando questo concetto la soluzione del sistema diventa:
$$
\begin{cases}
Ly=P\cdot b \\
Ux=y
\end{cases}
$$

> Algoritmo ***Stabile in Senso Debole***

$$|l_{ij}|\leq 1\qquad \mid u_{ij}\mid\leq 2^{n-1}\max\mid a_{ij}\mid$$


```python
def LUsolve(A,b):
    PT,L,U=sp.linalg.lu(A) #Returns P,L,B : A=P@L@U => P.T@A=L@U
    P=PT.T.copy()
    y,flag=st.Lsolve(L,P@b)
    if flag==0:
        x,flag=st.Usolve(U,y)
        if flag!=0:
            return [],flag
    else:
        return [],flag
    return x,flag
```

##### Householder Method ($QR$)
Se $A\in\mathbb{R}^{m\times n}$, con $m\geq n$ e $\text{rank}(A)=n$.
***Allora***
Esistono una matrice $Q\in\mathbb{R}^{m\times m}$ **ortogonale** e una matrice $R=\begin{pmatrix}R_{1} \\ 0\end{pmatrix}\in \mathbb{R}^{(m-n)\times n}$ dove $R_{1}\in\mathbb{R}^{n\times n}$, è una matrice triangolare superiore ***non singolare***, e $0\in \mathbb{R}^{(m-n)\times n}$ è una matrice di zeri tali che $A=QR$ 

Usando questa **fattorizzazione** la soluzione si riduce a:
$$
\begin{cases}
Qy=b \implies y=Q^Tb\\
Rx=y
\end{cases}
$$

> Algoritmo ***stabile in senso debole***, ma più stabile di Gauss

$$\mid q_{ij}\mid\leq 1\qquad \mid r_{ij}\mid\leq \sqrt{ n }\max\limits_{ij}\mid a_{ij}\mid$$


```python
def QRsolve(A,b):
    Q,R=sp.linalg.qr(A)
    y=Q.T@b
    x,flag=st.Usolve(R,y)
    if flag != 0:
        return [], flag
    else:
        return x
```

##### Cholesky

> Solo per matrici simmetriche e definite positive

Esiste una matrice triangolare inferiore $L$ con elementi *diagonali positivi*. ($l_{ii}>0,i=1,\dots,n$) tale che:
$$A=L\cdot L^T$$

La soluzione si riduce a:
$$
\begin{cases}
Ly=b \\
L^Tx=y
\end{cases}
$$

> Algoritmo ***Stabile in senso Forte***

$$\max\limits_{ij}\mid l_{ij}\mid\leq\sqrt{ \max\limits_{ij}\mid a_{ij}\mid }$$


```python
def solve_cholesky(A,b):
    if is_positively_defined(A) and is_symmetric(A):
        L=sp.linalg.cholesky(A,lower=True)
        y,flag=st.Lsolve(L,b)
        x,flag=st.Usolve(L.T,y)
        return x
    else:
        print('Matrix does not meet requirements')
```

#### Overdetermined Systems

##### Normal Equations
Definiamo il vettore residuo come:
$$r(x):=Ax-b$$
Cerchiamo il vettore $x^* \in \mathbb{R}^n$ che rende minima la norma 2 al ***quadrato del residuo***.
$$x^*=\arg\min\limits_{x\in\mathbb{R}^n }\|Ax-b\|_{2}^2=x^TA^TAX-2x^TA^Tb+b^Tb$$
- Poniamo $G=A^TA$

> Poichè $G$ è **Matrice Simmetrica** e **Definita Positiva** possiamo usare la fattorizzazione di Cholesky.

$$F(x)=x^TGx-2x^TA^Tb+b^Tb$$

Per calcolare il valore di $x^*$ che rende minimo $F(x)$ calcoliamo il gradiente di $F(x)$ e *poniamo che si annulli*.
$$\nabla F(x)=2Gx-2A^Tb=0$$

Il vettore $x^*$ che annulla il gradiente della funzione $F(x)$ è la soluzione del sistema lineare:
$$Gx=A^Tb$$

> Teorema

Dato il ***sistema lineare sovradeterminato*** $Ax=b$ dove $A\in\mathbb{R}^{m\times n},\quad x\in\mathbb{R}^n, \quad b\in\mathbb{R}^m,\quad m>n$
$\arg\min\limits_{x\in\mathbb{R}^n }\|Ax-b\|_{2}^2\iff$ è la *soluzione* di $A^TAx=A^Tb$
- La soluzione è unica se e solo se la matrice $A$ ha ***rango massimo***

> Condizionamento:
$$K_{2}(A^TA)=(K_{2}(A))^2$$

Se il problema è mediamente mal condizionato, il metodo è **numericamente pericoloso**


```python
def eqnorm(A,b):
    G=A.T@A
    
    print("Condition Number of G: ", np.linalg.cond(G))

    f=A.T@b

    L=sp.linalg.cholesky(G,lower=True)
    U=L.T

    z,flag=Lsolve(L,f)

    if flag==0:
        x,flag=Usolve(U,z)

    return x
```

##### QR Least Squares
> Una volta calcolata la fattorizzazione $QR$ di una matrice $A$.

Considerando che il prodotto di un vettore per una matrice ortogonale ***mantiene la norma euclidea***.
$$\|Q^T(Ax-b)\|_{2}^2=\|Q^TAx-Q^Tb\|_{2}^2=\|R_{1}x-Q^Tb\|_{2}^2$$

Posto $h=Q^Tb=\begin{bmatrix}\underbrace{ h_{1} }_{ n \text{ componenti} }\\ \underbrace{ h_{2} }_{ m-n \text{ componenti}}\end{bmatrix}$

Quindi si ha che il minimo sarà ottenuto per $x^*$ che risolve il sistema lineare $R_1x=h_1$

> Stabilità

1. Si lavora **sempre** solo sulla matrice $A$, senza passare da $A^TA$
2. La fattorizzazione $QR$ è *abbastanza stabile*.


```python
def qrLS(A,b):
    n=A.shape[1]
    Q,R=sp.linalg.qr(A)
    
    h=Q.T@b
    
    x, flag =st.Usolve(R[:n,:],h[:n])
    r=np.linalg.norm(h[n:])
    return x,r
```

##### Singular Value Decomposition Least Squares
Sia $A\in\mathbb{R}^{m\times n}$ a rango $k\leq\min(m,n)$, allora esistono due **matrici ortogonali** $U\in\mathbb{R}^{m\times n}$ e $V\in\mathbb{R}^{m\times n}$ tali che:
$$U^TAV=\Sigma=diag(\sigma_{1},\sigma_{2},\dots,\sigma_{k},0,\dots,0)$$

I valori della diagonale $\sigma$ sono detti valori singolari di $A$ e soddisfano:
$$\sigma_{1}\geq \sigma_{2}\geq\dots\geq\sigma_{k}\geq0$$

Il rapporto $\displaystyle\frac{\sigma_{\max}}{\sigma_{\min}}$ ci fornisce l'***indice di condizionamento*** della *matrice* $A$.

> Bisogna aggiungere una condizione sulla soluzione cercata:

$$\|Ax-b\|_{2}^2=\|U^T(Ax-b)\|_{2}^2=\|U^TAVV^Tx-U^Tb\|_{2}^2=\|\Sigma V^Tx-U^Tb\|_{2}^2$$
- $c=V^Tx$
- $d=U^Tb$


$$\underset{ x\in\mathbb{R}^n }{ \arg\min }\|Ax-b\|_{2}^2=\underset{ c\in\mathbb{R}^n }{ \arg\min }\|\Sigma c-d_{1}\|_{2}^2+\|d_{2}\|_{2}^2$$
Per rendere minimo il residuo:
- Si deve *annullare* $\Sigma c-d_{i} \implies \Sigma c=d_i$

Poniamo quindi $c_i=0$ per $i=k+1,\dots,n$ che rappresenta una condizione aggiuntiva per ottenere la **soluzione di minima norma**.

La soluzione del sistema diventa quindi:
$$x=Vc=\sum_{i=1}^kc_{i}v_{i}$$

- dove $v_{i}, i=1,\dots,n$ indicano le *colonne* della matrice $V$


```python
def SVDLS(A,b):
    m,n=A.shape  #numero di righe e  numero di colonne di A
    U,s,VT=spLin.svd(A)  
    
    V=VT.T
    thresh=np.spacing(1)*m*s[0] ##Calcolo del rango della matrice, numero dei valori singolari maggiori di una soglia
    k=np.count_nonzero(s>thresh)
    
    d=U.T@b
    d1=d[:k].reshape(k,1) # Seleziono i primi k elementi di d
    s1=s[:k].reshape(k,1) # Seleziono i primi k elementi di s
    
    c=d1/s1
    x=V[:,:k]@c
    r=np.linalg.norm(d[k:])**2 
    return x,r
```

## Descent Methods
---
> Concetti Generali

Sia $A\in\mathbb{R}^{n\times n}$, matrice *simmetrica* e *definita positiva*, $b,x\in\mathbb{R}^n$
<u>Allora</u>
La soluzione del sistema lineare $Ax=b$ coincide con il punto di minimo della seguente ***funzione quadratica***.
$$F(x)=\frac{1}{2}<Ax,x> - <b,x> =\frac{1}{2}x^TAx-b^Tx=\frac{1}{2}\sum_{i=1}^n\sum_{j=1}^na_{ij}x_{i}x_{j}-\sum_{i=1}^nb_{i}x_{i}$$
Dove la forma quadratica $Q(x)= <Ax,x\geq x^TAx$ è positiva per $x\neq0$

>Il teorema afferma che il vettore che risolve il sistema lineare coincide con il vettore che ***minimizza la forma quadratica***.


### Steepest Descent
> Caratterizzato dalla scelta ad ogni passo $k$ , della direzione $p^{(k)}$ come l'***antigradiente*** della funzione $F$ calcolato nell'iterato $k$-esimo:

$$p^{(k)}=-\nabla F(x^{(k)})=-Ax^{(k)}+b=-r^{(k)}$$

> Passaggi Iterativi:

1. Determina la direzione $p^{(k)}$
2. Scegli lo Step-Size $\alpha^{(k)}=-\displaystyle{\frac{<r^{(k)},p^{(k)}>}{<Ap^{(k)},p^{(k)}>}}$
3. Aggiorna l'iterato $x^{(k+1)}=x^{(k)}+\alpha^{(k)}p^{(k)}$
4. Aggiorna il residuo $r^{(k+1)}=r^{(k)}+\alpha Ap$

> Ordine di Convergenza

Il metodo ha ordine di convergenza lineare con fattore:
$$\rho=\displaystyle{\frac{K(A)-1}{K(A)+1}}$$


```python
def steepestdescent(A,b,x0,itmax,tol):
    x=x0.copy()
    r=A@x-b
    it=0
    p=-r
    normb=np.linalg.norm(b)

    error=np.linalg.norm(r)/normb

    vec_sol=[]
    vec_sol.append(x.copy())
    vec_r=[]
    vec_r.append(error)

    while error>=tol and it<itmax:
        it=it+1
        
        Ap=A@p
        alpha=(r.T@r)/(p.T@Ap)
        
        x=x+alpha*p
        r=r+alpha*Ap

        vec_sol.append(x.copy())
        error=np.linalg.norm(r)/normb
        vec_r.append(error)
        p=-r # Max descent (Opposite of gradient)
        
    iterates=np.vstack([arr.T for arr in vec_sol]) # Only for graphical purpose

    return x,vec_r, iterates, it
```

#### Conjugate Gradient
> Si sceglie la **nuova direzione di discesa** come quella *appartenente al piano* $\pi_{k}$ passante per $x^{(k)}$e individuato da $r^{(k)}$ e $p^{(k-1)}$.

$$p^{(k)}=-r^{(k)}+\gamma_{k}p^{(k-1)}\qquad k=1,2,\dots$$

- $\gamma$ è scelto in modo che la direzione $p$ punti verso il *centro dell'ellisse*.

Scegliamo $\gamma$ come:
$$\gamma^{(k)}=\displaystyle{\frac{<r^{(k)},r^{(k)}>}{<r^{(k-1)},r^{(k-1)}>}}$$

- Molto efficiente poichè il calcolo $<r^{(k-1)},r^{(k-1)}>$ è già stato fatto per calcolare lo step size.
  


> Ordine di Convergenza

Il metodo ha Ordine di Convergenza lineare con fattore:
$$\rho=\displaystyle{\frac{\sqrt{ K(A) }-1}{\sqrt{ K(A) }+1}}$$


```python
def conjugateGradient(A,b,x0,itmax,tol):
    
    x=x0.copy()
    r=A@x-b
    p=-r
    it=0
    errore=np.linalg.norm(r)/np.linalg.norm(b)
    
    vec_sol=[]
    vec_sol.append(x.copy())
    vec_r=[]
    vec_r.append(errore)

    while errore>=tol and it<itmax:
        it=it+1
        
        Ap=A@p

        save=(r.T@r)
        alpha=save/(Ap.T@p)
        
        x=x+alpha*p
        r=r+alpha*Ap

        vec_sol.append(x.copy())
        errore=np.linalg.norm(r)/normb
        vec_r.append(errore)

        gamma=(r.T@r)/save
        p=-r+gamma*p # Max descent (Opposite of gradient)
        
    iterates=np.vstack([arr.T for arr in vec_sol]) # Only for graphical purpose

    return x,vec_r, iterates, it
```

## Interpolation
---
Note le coppie (**nodi**) $(x_{i},y_{i})$ con $i=0,\dots,n$ e $x_{i}\neq x_{k}\quad i\neq k$ e $y_{i}$ il problema dell'***interpolazione polimoniale*** consiste nell'individuare i coefficienti $\alpha_{i}$ del polinomio $P_{n}(x)$ tale che sia soddisfatta la ***condizione di interpolazione***.
$$P_{n}(x_{i})=y_{i}$$

$P_{n}(x_{i})=y_{i}$ significa imporre:
$$P_{n}(x_{i})= \alpha_{0}+\alpha_{1}x_{i}+\alpha_{2}x_{i}^2+\dots+\alpha_{n}x_{i}^n=y_{i}$$

Se scriviamo questa relazione per ogni $i$, ricaviamo il seguente sistema lineare:
$$
\begin{cases}
\alpha_{0}+\alpha_{1}x_{0}+\alpha_{2}x_{0}+\dots+\alpha_{n}x_{0}^n=y_{0} \\
\alpha_{1}+\alpha_{1}x_{1}+\alpha_{2}x_{1}+\dots+\alpha_{n}x_{1}^n=y_{1} \\
\dots \\
\alpha_{n}+\alpha_{1}x_{n}+\alpha_{2}x_{n}+\dots+\alpha_{n}x_{n}^n=y_{n} \\
\end{cases}
$$
Dove la matrice dei coefficienti $A$ del sistema è la matrice di dimensione $(n+1)\times(n+1)$

### Lagrange Polynome
> Cambiamento necessario per via del mal condizionamento della matrice costruita con la base canonica dello spazio vettoriale dei polinomi

Gli $n+1$ ***polinomi di Lagrange***, $L_{j}^{(n)}$ sono polinomi di grado $n$ che rappresentano una base per lo spazio dei polinomi $\mathbb{P}_{n}[x]$ e *soddisfano le condizioni*:
$$
L_{j}^{(n)}(x_{i})=\begin{cases}
1\qquad \text{se }i=0 \\
0\qquad \text{se }i\neq0
\end{cases}
$$

Sarà quindi della forma:
$$L_{j}^{(n)}(x)=c(x-x_{0})(x-x_{1})\dots(x-x_{j-1})(x-x_{j+1})\dots(x-x_{n})$$

> Determiniamo $c$ in maniera tale che $L_{j}^{(n)}(x_{j})=1$

*Impongo*:
$$
L_{j}^{(n)}(x_{j})=c\prod_{\begin{array}\ k=0 \\ k\neq j\end{array}}^{n}(x_{j}-x_{k})=1
$$
***Quindi***:
$$
L_{j}^{(n)}(x)=\prod_{\begin{array}\ k=0 \\ k\neq j\end{array}}^{n} \frac{(x-x_{k})}{(x_{j}-x_{k})}
$$

> Ricorda:


```python
# np.poly(zeros)
# Ritorna i coefficienti del polinomio che si annulla nei punti dati
# np.polyval(coeff,val)
# Ritorna la valutazione del polinomio con i coefficienti coeff nel valore val
```

### Interpolation With Lagrange Polynome
Il polinomio $P_{n}(x)=\alpha_{0}L_{0}^{(n)}(x)+\alpha_{1}L_{1}^{(n)}(x)+\dots+\alpha_{n}L_{n}^{(n)}(x)$.
- Imponendo le ***condizioni di interpolazione***, ricaveremo il seguente sistema lineare:

$$
\begin{bmatrix}
L_0^{(n)}(x_0) & L_1^{(n)}(x_0) & \dots & L_n^{(n)}(x_0) \\
L_0^{(n)}(x_1) & L_1^{(n)}(x_1) & \dots & L_n^{(n)}(x_1) \\
\vdots & \vdots & \ddots & \vdots \\
L_0^{(n)}(x_n) & L_1^{(n)}(x_n) & \dots & L_n^{(n)}(x_n)
\end{bmatrix}
\begin{bmatrix}
\alpha_0 \\
\alpha_1 \\
\vdots \\
\alpha_n
\end{bmatrix}
=\begin{bmatrix}
y_0 \\
y_1 \\
\vdots \\
y_n
\end{bmatrix}
$$

Che per la proprietà dei ***polinomi base di Lagrange*** si riduce a:
$$
\begin{bmatrix}
1 & 0 & \dots & 0 \\
0 & 1 & \dots & 0 \\
\vdots & \vdots & \ddots & \vdots \\
0 & 0 & \dots & 1
\end{bmatrix}
\begin{bmatrix}
\alpha_0 \\
\alpha_1 \\
\vdots \\
\alpha_n
\end{bmatrix}=\begin{bmatrix}
y_0 \\
y_1 \\
\vdots \\
y_n
\end{bmatrix}
$$


```python
def plagr(nodes,j):
    n=nodes.size
    zeros=np.zeros_like(nodes)
    
    zeros=np.append(nodes[:j],nodes[j+1:]) # one-line based programming.

    num=np.poly(zeros) # Per trovare il polinomio che si annulla in tutti i valori tranne il valore j
    den=np.polyval(num,nodes[j]) # Per far sì che il polinomio trovato, dove non si annulla, valga 1

    p=num/den # Trovo il Polinomio (!! Coefficienti del Polinomio !!)
    
    return p
```


```python
def InterpL(x, y, xx):
     
     n=x.size
     m=xv.size
     L=np.zeros((m,n))
     for j in range(n):
        p=plagr(x,j)
        L[:,j]=np.polyval(p,xx)
         
     return L@y # Rappresenta il Polinomio
```
