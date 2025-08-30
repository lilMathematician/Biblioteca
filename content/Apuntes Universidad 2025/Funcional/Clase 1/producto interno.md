Corresponde a un ![[semiproducto interno]]que adicionalmente satisface que: si $$\mu(x,x)=0\implies x=0$$
Algunos ejemplos de este tipo de operaciones son
- Tenemos el caso de $\mathbb{R}^n$ o $\mathbb{C}^n$, donde $$<x,y>=\sum x_i\bar{y_i}$$
- y una *generalizacion* consiste ocurre para las funciones continuas en $L^2(E,M,\mu)$, donde $$<f,g>=\int_Ef\cdot\bar{g}$$
## Desigualdad de cauchy-schwarz
Si $<\cdot,\cdot>$ es un [[semiproducto interno]], entonces $$|<x,y>|\le<x,x>^{1/2}\cdot<y,y>^{1/2}$$
donde de ahora en adelante **denotaremos** $<x,x>^{1/2}=||x||$.
Adicionalmente, la igualdad anterior se da siempre que existan $\alpha,\beta$ tales que
$$<\beta x+\alpha y,\beta x+\alpha y>=0$$
>La demostracion de esto se puede ver como los siguiente:
>![[demo-cs.png]]
>Ahora bien, aun falta demostrar la segunda parte de este resultado, el cual se demuestra en el siguiente bosquejo

En consecuencia al resultado anterior es que, *si $<\cdot,\cdot>$ es un P.I. sobre un espacio vectorial, entonces se tiene*
- $||x+y||\le||x||+||y||$
- $||\alpha x||=|\alpha|||x||$
- $||x||=0\implies x=0$
>Notemos que el primer punto es el unico que no parece estar tan claro intuitivamente, pero se resuelve notando que la **suma de un complejo y su conjugado es dos veces su parte real**, la cual es menor que el propio numero complejo.


 