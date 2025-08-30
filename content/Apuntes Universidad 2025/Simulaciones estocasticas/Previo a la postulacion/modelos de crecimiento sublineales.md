Luego de un tratamiento dimensional y temporal apropiado obtenemos la forma general de los modelos de crecimiento sublinear $$x'=\frac{x}{\theta}\left(1-x^{\theta}\right)$$ donde $x(t)\ge0$ es la densidad poblaconal en un tiempo y parametros $t\ge0\land\theta\in\mathbb{R}\setminus\{0\}$. 
Notemos lo siguiente:
- $\theta=1$ nos proporciona la clasica ecuacion logistica, donde la tasa entre la relacion de crecimiento per capita y la densidad es lineal
- $\theta=0$ obtenemos la ecuacion clasica del modelo de Gompertz $$x'=x\log(1/x)$$
- $-1<\theta<0$ es lo que llamamos como sublinealidad (SG)
- $\theta>0$ estan relacionado con el crecimiento lineal y la tasa superlineal de muerte asociado a la efectos de multitudes.

Siguiendo, como se señala en las referencias, 
> the per capita birth rate of the SG system tends to infinity as x goes to zero

[[Sublinear_growth_HAL.pdf#page=4&selection=0,23,5,12|Sublinear_growth_HAL, page 4]]
ademas que
> Although most often only values of θ between −1 and 1 are discussed in the literature, the range of values of θ estimated from population time series in [9] is broader than the interval [−2, 2]

[[Sublinear_growth_HAL.pdf#page=4&selection=22,0,40,2|Sublinear_growth_HAL, page 4]]

Dicho esto, tenemos que para todos los valores de $\theta$ se tiene solucion unica para todos los tiempos positivos en cualquier c.i. Ademas, los puntos de estabilidad para el modelo de crecimiento sublineal  son $$\begin{cases}
x&=0\\
x&=1
\end{cases}$$
donde la primera es inestable y la segunda es estabñe. Es mas, en general, el equilibrio en 1 es asintoticamente y globalmente estable, lo cual significa que para cualquier condicion inicial positiva la solucion converge a 1 cuando el tiempo es infinitamente grante. De este modo, para cualquier valor del parametro, el comportamiento _cualitativo asintotico_ es igual.