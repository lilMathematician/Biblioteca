Este algoritmo funciona sobre las estructuras [[pilas o stacks]] para la representación de los grafos que toman como entrada. Estos últimos, no necesariamente son dirigidos y, ademas, consideran las listas de adyacencias de los mismos.
---
## Version Iterativa
Esta es la version *base* de este algoritmo y sigue la siguiente estructura
```pseudo
	\begin{algorithm}
	\caption{DFS-iterativa}
	\begin{algorithmic}
	\State Marcamos todos los vertices como no explorado
	\State $S$ corresponde a la pila que se inicializa con $s$
	\While{$S$ no esta vacia}
		\State $v$ es el vertice de $S$ y eliminamos $s$ con la operacion pop
		\If{$v$ no explorado}
			\State Marcamos $v$ como explorado
			\For{cada arista $(v,w)$ en la lista de adyacencia de $v$}
				\State añadir $w$ al frente de $S$ con la operacion push
	        \EndFor
        \EndIf
    \EndWhile
	\end{algorithmic}
	\end{algorithm}
```
## Version Recursiva
```pseudo
	\begin{algorithm}
	\caption{DFS-recursiva}
	\begin{algorithmic}
	\State Marcamos todos los vertices $v\in V$, fuera de la llamada, como no explorados 
	\State marcamos $s$ explorado
	\For{cada arista $(s,v)$ en la lista de adyacencia de $s$}
		\If{$v$ no explorado}
			\Procedure{DFS}{G,s}
            \EndProcedure
        \EndIf
    \EndFor
	\end{algorithmic}
	\end{algorithm}
```
---

Supongamos que tenemos el siguiente grafo con su lista:
![[DFS 2025-08-27 15.38.18.excalidraw|center|5000]]
una aplicacion de este algoritmo seria
```pseudo
	\begin{algorithm}
	\caption{Ejemplo}
	\begin{algorithmic}
	\Procedure{DFS}{G,s}
		\State marcamos $s$ como explorado
		\State examinamos $a$
		\Procedure{DFS}{G,a}
			\State marcamos $a$ como explorado
			\State examinamos $s \gets$ esta explorado
			\State examinamos $c$
			\Procedure{DFS}{G,c}
				\State marcamos $c$ como explorado
				\State examinamos $d$ 
				\Procedure{DFS}{G,d}
						\State marcamos $d$ como explorado
						\State examinamos $c \gets$  esta explorado
						\State examinamos $e$
						\Procedure{DFS}{G,e}
							\State marcamos $e$ como explorado
							\State examinamos $c \gets$ esta explorado
                        \EndProcedure
                        \State examinamos $b$
                        \Procedure{DFS}{G,b}
	                        \State marcamos $b$ como explorado
                        \EndProcedure
                \EndProcedure
            \EndProcedure
		\EndProcedure	
	\EndProcedure
	\end{algorithmic}
	\end{algorithm}
```
Con esto tenemos que la lista de vertices es $\{s,a,c,d,e\}$

---
# Aplicaciones 
Este algoritmo nos permite realizar implementaciones que realicen lo siguiente
- Busqueda segun orden topologico en un grafo dirigido
- Indentificacion de componentes fuertemente conexos en grafos dirigidos
	Esto ultimo se le conoce como el **algoritmo de Kosarg**

>[!info] **Teorema**
>El algoritmo DFS es correcto, su tiempo de ejecucion es $O(n_{s},m_{s})$
>>[!example]- **Demo**:
>>No necesariamente compete al curso segun el profe



