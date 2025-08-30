## Def
Un Hilbert $\mathcal{H}$ es un espacio vectorial dotado de [[producto interno]] tal que la métrica inducida $$d(x,y)=||x-y||$$ lo convierte en un espacio métrico **completo**

Ahora bien, aunque la definición indica qué es un hilbert, se puede dar el caso donde la métrica inducida no sea completa, a esto lo denominaremos un **Pre-Hilbert**.
Un ejemplo de esto podria ser:
- Consideremos el espacio de funciones continuas de soporte compacto, esto quiere decir que todos estos bichos están en $L^2(\mathbb{R})$. Asi, si consideramos una sucesión de funciones continuas $L^2(\mathbb{R})$, es decir, son densas. Ahora bien, al ser densas existe una funcion que converge a una funcion discontinua y eso no es $L^2(\mathbb{R})$. **Por lo tanto, este subconjunto es espacio metrico, pero su metrica no es continua. Es decir, es un hilbert**

Sin embargo, podemos elevar este espacio simplemente completando su medida:
- Sea $$\mathcal{H}=\{\{x_n\}:\mathbb{N}\to V/\{x_n\}\text{ es de cauchy}\}$$y decimos que $x_n\sim y_n$ si $$\lim||x_n-y_n||=0$$
- Luego, tomamos el siguiente espacio vectorial $$\mathcal{H}'=\mathcal{H}/\sim$$, que basta definir la suma como $\{x_n+y_n\},\{x_n',y_n'\}$ y la ponderación de forma similar
- Ademas, el limite recien definido cuenta como producto interno, ya que ![[IMG_20250818_181721.jpg]]y este limite resulta en la clase de equivalencia del $0$, lo que verifica la condición de producto interno. Ademas hereda las propiedades del espacio $\mathcal{H}$ que se mantienen con el limite. 