>[!info] Se dice **conexo** a un grafo para el cual cada par de vertices $u,v\in V$ exite un camino entre estos vertices en G

Por lo tanto, un grafo **disconexo** es aquel que no es conexo.

## Componentes conexas
Estos elementos son subgrafos de $G$, lo cuales son **conexos maximales por inclusion**, en otras palabras, *todos los vertices contenidos en la componente estan conectadas entre si*.
>[!important] adicionalmente es poible estudiar las c.c, pues, si definimos una relación $R$ sobre $V$ talque $$aRb\Leftrightarrow\text{existe un camino entre a y b, entonces $R$ es relacion de equivalencia}$$ Asi las clases de equivalencia de $R$ serian las componentes conexas.

![[Conexidad 2025-08-20 14.32.41.excalidraw|5000]]

Ahora bien, es importante destacar que
>[!note]- **Prop:** Sea $G=(|V|=n,|E|=m)$, entonces tiene al menos $n-m$ componentes conexas. En particular, un grafo conexo tiene $2n-1$ aristas
>demo



