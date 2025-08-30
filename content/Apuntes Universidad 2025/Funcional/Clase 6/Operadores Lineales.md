Vamos a recordar que un **operador** $T:\mathcal{H}\to \mathcal{H}$ entre dos espacios de Hilbert se dice *lineal* si 
$$
T(\alpha x\beta y)=\alpha T(x)+\beta T(y),\quad \alpha,\beta \in \mathbb{C}\text{ y }x,y\in \mathcal{H}
$$
Algunos ejemplos de este tipo de *operadores* son
- $A\in M_{n\times n}(\mathbb{C})\implies T(v)=Av$ es lineal
- $S$ un subespacio cerrado de  $\mathcal{H}$, entonces la proyección ortogonal $P_{s}$ es lineal

> [!definition] Operadores Lineal
> 1. $T:\mathcal{H}\to \mathcal{H}$ se dice **operador lineal acotado** si existe $M>0$tal que $$\lVert Tx \rVert _{\mathcal{H}_{2}}\leq M\lVert X \rVert _{\mathcal{H}_{1}}\forall x \in \mathcal{H}_{1}$$
> 2. la norma de $T$ se define como $$ \lVert T \rVert = \min M $$

> [!proposition] de lo anterior, podemos incluso afirmar lo siguiente
> $$ \lVert T \rVert = \sup_{f,g\in \mathcal{H}_{1}} \left\{ \langle Tf,g \rangle |\begin{cases} \lVert f \rVert &  \leq1  \\ \\ \lVert g \rVert  & \leq 1 \end{cases} \right\} $$

por lo tanto, podemos establecer que 
> [!proposition] 
> Un operador lineal $T:\mathcal{H}_{1}\to \mathcal{H}_{2}$ es acotado si y solo si es continuo


> [!definition] 
>El conjunto de los operadores lineales acotados de $\mathcal{H}_{1}$ a $\mathcal{H}_{2}$ se denota como $\mathcal{B}(\mathcal{H}_{1},\mathcal{H}_{2})$
>>[!exercise] **Tarea**: 
>>Pruebe que $\forall S,T\in\mathcal{B}(\mathcal{H}_{1})$ se cumplen las siguientes propiedades
>>1. $\lVert T+S \rVert\leq \lVert T \rVert+\lVert S \rVert$
>>2. $\lVert \alpha S \rVert=\lvert \alpha  \rvert\lVert S \rVert$
>>3. $\lVert TS \rVert\leq \lVert T \rVert\lVert S \rVert$


---
Algunos ejemplos de este tipo de operador lineal 
1. Tomemos la siguiente aplicación     
$$
\begin{align*}
T:\mathcal{l}_{2}(\mathbb{Z}) & \to \mathcal{l}_{2}(\mathbb{Z}) \\
T(a_{j}) & =b_{j},\quad b_{i}=a_{i+1}
\end{align*}
$$
Notemos que, como $\lVert a_{j} \rVert{^2}=\sum \lvert a_{i} \rvert{^2}$, entonces $\lVert Ta_{i} \rVert=\lVert b_{i} \rVert$, por tanto, la norma del operador es 1.

---
 
2. Considerando una función medible en $\mathbb{R}{^2}$ *kernel integral:* $K(x,y)$ el siguiente operador definido es lineal
$$
\begin{align*}  T:\mathcal{H}_{1} & \to \mathcal{H}_{2}\\
T(f)(x) & =\int_{\mathbb{R}}K(x,y)f(y)dy
\end{align*}
$$
puesto que, en $\mathcal{L}{^2}(\mathbb{R}{^2})$ 
$$
\begin{align}
\int_{\mathbb{R}}\left\lvert  \int_{\mathbb{R}}K(x,y)f(y)dy  \right\rvert{^2} dx  & \underbrace{ \leq }_{ holder } \int_{\mathbb{R}}  \int_{\mathbb{R}}\lvert K(x,y) \rvert ^2dy  \int_{\mathbb{R}}\lvert f(y)dy \rvert {^2}dx \\
 & =\left\lVert  f  \right\rVert \int_{\mathbb{R}}\int_{\mathbb{R}}\lvert K(x,y) \rvert {^2dydx} \\
 & =\lVert K \rVert {^2_{\mathcal{L}{^2(\mathbb{R}{^2})}}}\lVert f \rVert {^2_{\mathcal{L}{^2(\mathbb{R})}}}
\end{align}
$$
---
3.  El operador siguiente es lineal
$$
\begin{align*}
T:\mathcal{L}{^2([0,2\pi])} & \to \mathcal{l}{^2(\mathbb{Z})} \\
f & \to a_{n}=\int_{0}^{2\pi} \exp(inx)f(x) \, dx 
\end{align*}
$$
cuya norma
$$
\begin{align}
\lVert Tf \rVert \underbrace{ = }_{ def }\sum \lvert a_{n} \rvert {^2}\underbrace{ = }_{ parseval }\lVert f \rVert 
\end{align}
$$
Primero recordemos la identidad de Perceval 
   $$
\lVert f \rVert {^2}=\sum \lvert \langle f,e{^{inx}} \rangle  \rvert 
$$













