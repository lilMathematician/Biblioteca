Esta variacion del algoritmo introducido en la [[Clase 4 (25-08)]] consiste en la busqueda o exploracion de las longitudes del $s,v$-camino mas corto, en particular, la **busqueda en anchura** busca $dist(s,v)$ entre dos vertices: 
- $s\in V$ explorado
- $v\in V$ sin explorar

---
## Formas de representación de grafos para BFS
Vimos dos, 
- [[Lista de Adyacencia]]
- [[Matriz de adyacencia]]
---
## Psudocodigo e implementacion
Este algoritmo, al menos, esta forma de implementacion, funciona mediante el uso de [[Colas o Queues]] para el trabajo sobre las [[Lista de Adyacencia]].
Primero, consideraremos como **entrada** un grafo *dirigido o no* representado por una [[Lista de Adyacencia]]. Sobre esto, consideraremos que un vertice es *alcanzable* ssi cuando terminemos la ejecucion este se denomina explorado.
Segundo, de las aristas elegibles, elegimos una arista cuya cola es un vertice explorado y continuaremos el proceso de exploracion mediante capas
- $C_{0}$ corresponde a la inicial y solo contiene al vertice $s$
- $C_{k}\ \forall k \in \{1,\dots,i-1\}$ son las capas tales que $C_{i}$ es la capa donde los vertices $w \not\in(C_{0}\lor C_{1}\lor ,\dots, C_{i-1})$.
Luego, el proceso se lleva a cabo mediante el siguiente pseudocodigo
```pseudo
	\begin{algorithm}
	\caption{BFS}
	\begin{algorithmic}
	\State marcamos $s$ como explorado
	\State $Q$ cola inicializada en $s$
	\While{$Q$ no esté vacia}
		\State $v:=$ extraemos $v$ de la cola
		\For{cada arista $(v,w)$ en la lista de adyacencia de $v$}
		\If{$w$ no explorado}
			\State marcamos $w$ como explorado
			\State añadimos $w$ al final de la cola
        \EndIf
        \EndFor
    \EndWhile
	\end{algorithmic}
	\end{algorithm}
```
Imagen de referencia: [[Pasted image 20250830172922.png]]

---
Por ultimo, del siguiente grafo 
![[BFS 2025-08-27 14.59.58.excalidraw|center|500]]
y comentarios anteriores existen algunas observaciones que vale la pena considerar

>[!note]- **Prop** Sea $(v,w)\in E$ con $v\in G\text{ y }w\in C_{i,j}, j\ge1$ entonces $j=1$
>En cristiano, **las aristas hacia adelante solo se mueven por capas consecutivas**

>[!note]- **Prop** Sean $C_0=\{2\},C_1,C_2,...,C_k$ las capas de $G$. Entonces $v_i\in C_i$ ssi $dist(s,v)=1$
>demo


