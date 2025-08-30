Esta pagina esta destinada a la sintesis y redaccion del proyecto investigativo del articulo: [[Sublinear_growth_HAL.pdf]] 

---

# Objetivo Inicial
Objetivo: generar simulaciones computacionales de los modelos descritos en el siguiente artículo. 
Idea: apoyar en la investigación del prof. Videla y colaboradores en la generación de simulaciones estocásticas.

# Comentarios e Ideas Claves
1. Los [[modelos de crecimiento sublineales]] se conocen de, al menos, medio siglo y el articulo que se considera como punto de partida, intenta dar respuesta al debate entre diversidad y estabilidad en modelos de dinamica ecologica mediante este tipo de modelos. Es importante destacar que los modelos sublineales son considerados inviables en este contexto por su forma de describir la extincion de una especie o el camino a esta misma. Aun asi, en este documento se busca estudiar las limitaciones y prospectos de la contraparte estocastica de estos modelos como modelos de fenomenos ecologicos.
2. Siguiendo como la motivacion del articulo, el panorama cambia un poco cuando introducimos la estocasticidad en el modelo.
   Definiremos dos primos cercanos de la ecuacion general del modelo sublineal
	1. [[Primera clase]]
	2. [[Segunda clase]]
	En ambos casos, estudiamos la casi segura exticion en tiempo finito y se muestra que esta propiedad depende fuertemente del valor del parametro y del tipo de modelo estocastico a considerar
3. Despues del analisis de los modelos anteriores se tiene que, el comportamiento estocastico sobre un modelo determinista dado puede cambiar drasticamente dependiendo del tipo de estocacidad y sus detalles añadido al sistema. Esta aproximacion proporciona una perspectiva adicional sobre apectos que un modelo determinista puede ignorar, como la escala de tiempo de extincion. Por otro lado, aun cunado el analisis realizado puede ser de interes matematicico debe ser considerado con cuidado cuando se utilice para el modelado de fenomenos biologicos puesto que considera supuestos estocasticos que se pueden interpretar como viables biologicamente o irreales en escalas de tiempo amplias. Dicho esto, una aproximacion difusa [[segundo]] puede ser una buena alternativa para este objetivo.

---

Este proyecto propone un estudio computacional exhaustivo que valide y complemente las predicciones teóricas recientes sobre la extincion y la viabilidad ecologica en modelos de crecimiento sublineal, en particular las conclusiones presentes en el manuscrito en que esta trabajando el académico Leonardo Videla et al. (2025). 
Se implementarán tres clases de modelos estocásticos 
(i) procesos de nacimiento-muerte individuales (discreto), 
(ii) difusión tipo Feller con ruido demográfico,
(iii) la aproximación difusiva (diffusion approximation)
para cuantificar tiempos medios de extinción, probabilidades de supervivencia y escalas temporales según el parámetro $\theta$, la capacidad de carga $K$, y la intensidad del ruido. 
Emplearemos métodos directos (Gillespie), esquemas SDE (Euler–Maruyama, Milstein), y técnicas de rare-event (Adaptive Multilevel Splitting, importance sampling, Fleming–Viot/cloning) **--Admito que estos metodos los sugirio el LLM que utilice para obtener recomendaciones de metodos de simulacion--** para estimar tiempos de extinción que escalan exponencialmente con $K$. 
Los resultados validarán (o matizarán) las proposiciones teóricas: extinción en escalas exponenciales para procesos discreto con $\theta\le 0$ (Proposición 1.4), umbral crítico en la difusión Feller ($\theta=-1$, Proposición 2.1) y extinción casi segura para la aproximación difusiva (Proposición 2.2). El código y rutinas de simulación se liberarán como paquete reproducible y GUIs/ notebooks para la comunidad ecológica, facilitando la exploración de escenarios prácticos para conservación.

Como contexto, aunque los modelos deterministas sublineales, se conocen hace medio siglo, hace poco han vuelto a la palestra como una respuesta al debate entre diversidad y estabilidad con el fin de explicar patrones macroecológicos recientes aunque su interpretación biológica es debatida debido a tasas per-cápita no acotadas cuando $x\to0$. En el documento donde el profesor Leonardo se encuentra trabajando presentan una caracterización teórica de versiones estocásticas (procesos nacimiento-muerte, difusión Feller y aproximación difusiva) y muestran que las propiedades de extinción dependen fuertemente del tipo de ruido y de $\theta$: por ejemplo, extinción casi segura/No extinción/tiempos exponenciales según el modelo y $\theta$. Estas proposiciones requieren una validación numérica robusta porque las implicancias ecológicas (predicción de colapsos, diseño de medidas de conservación) dependen de la escala temporal estimada —algo que la ecología aplicada necesita cuantificar con simulaciones reproducibles y herramientas accesibles.

# Objetivo general

Validar numéricamente y cuantificar las escalas temporales de extinción y la viabilidad ecológica en modelos estocásticos de crecimiento sublineal, contrastando resultados computacionales con las predicciones teóricas.

# Objetivos específicos

1. Implementar y simular procesos de nacimiento-muerte discretos para rangos de $\theta$ (incluyendo $\theta\le 0$) y verificar la predicción de tiempos de extinción que escalan exponencialmente en $K$ (Proposición 1.4).
2. Implementar la difusión Feller $dX_t = X_t\frac{1-X_t^\theta}{\theta}dt + \sqrt{\gamma X_t}\,dB_t$; comprobar numéricamente que:  
    a) para $\theta\ge -1$ la extinción ocurre casi seguramente en tiempo finito;  
    b) para $\theta < -1$ la extensión de supremum/infimum implica que no ocurre extinción en tiempo finito (Proposición 2.1).
3. Implementar y simular la aproximación difusiva $dZ_t = Z_t\tfrac{1-Z^\theta_t}{\theta}dt + \sqrt{\tfrac{Z_t}{K|\theta|}(1+Z_t^\theta)}\,dB_t$ y verificar que la extinción casi segura se cumple para todo $\theta$ (Proposición 2.2).
4. Estudiar la influencia de $\theta$ en escalas de tiempo de extinción en el intervalo empírico $\theta\in[-2,2]$ (por ejemplo, malla fina) y producir mapas de riesgo y curvas de escalamiento (ej.: $\log \mathbb{E}[T_{\mathrm{ext}}] vs K$).

## 1) Modelos y parámetros, extraidos de la informacion de soporte

- Parámetros a barrer: $\theta\in[-2,2]$ , $K\in\{50,100,200,500,1000,2000\}$, $\gamma$ (ruido demográfico en difusión Feller) en $\{0.1,0.5,1.0,2.0\}$, $\alpha$ (si aplica) en $\{0,0.1,1\}$.
- Condiciones iniciales: pequeñas poblaciones (por ejemplo $x_0=1/K$), densidades medias ($x_0=0.1,\,0.5$), y análisis de sensibilidad al estado inicial.
- Modelos a simular: 
	- (i) nacimiento-muerte discreto (Gillespie), 
	- (ii) SDE Feller (demográfico) con término $\sqrt{\gamma X_t}$, 
	- (iii) difusión aproximada (como en la ecuación propuesta). Todas las ecuaciones correspondientes y proposiciones están en Champagnat _et al._ (2025).

## 2) Algoritmos numéricos y técnicas especiales

### A. Procesos nacimiento-muerte (discreto)
### B. SDEs (Feller y aproximación difusiva)

### C. Estimación de tiempos de extinción y análisis estadístico

### D. Herramientas de reducción de varianza / rare event


## 3) Reproductibilidad y software

- Lenguaje principal: **Python 3.10+**. Librerías: NumPy, SciPy, Numba (para kernels rápidos), JAX opcional para paralelización en GPU, SDEint / custom solvers, matplotlib/plotly para visualizaciones.
- Código: paquete modular (simuladores, rare-event, análisis) con tests unitarios y notebooks Jupyter que reproducen figuras clave.
- Entrega: repositorio en GitHub/GitLab con CI (tests limitados, ejemplo small runs), DOI en Zenodo para release final.
- GUI/Notebooks: dashboards (Voila/Streamlit) con sliders para $\theta, K, \gamma$ y producción de mapas de riesgo.
    

## 4) Validación y contraste con teoría

- Comparar numéricamente:
    - Proposición 1.4 — comportamiento exponencial en K para θ≤0\theta\le 0 en el birth-death.
    - Proposición 2.1 — comportamiento de la difusión Feller con el umbral θ=−1\theta=-1.
    - Proposición 2.2 — extinción casi segura en la aproximación difusiva para todo θ\theta.
        
- Producción de curvas y mapas empíricos que muestren la región de parámetros donde cada modelo es “biológicamente creíble” desde el punto de vista de la escala temporal de extinción.

---

# Prompt de Investigacion
Estoy comenzando un proyecto de investigacion basado en el documento "" adjunto, este consiste en la simulacion de las ecuaciones estocasticas que se proponen en el documento, los modelos son los siguientes:

1. Procesos de nacimiento-muerte discretos, que verifican el escalado exponencial de la capacidad de carga relativo al parámetro negativo theta.

2. Difusión de Feller, que valida el umbral crítico (theta=-1) para la extinción.

3. Aproximación difusiva, que confirma la extinción casi segura de la especie en un tiempo finito para cualquier valor del parámetro.

. Este proyecto busca tener una duracion de dos meses y consiste en simulaciones utilizando metodos estocasticos propuestos en el libro adjunto como una forma de darle validez numerica a los resultados teorico, mediante graficos y visualizaciones de los resultados.

Necesito que examines el libro adjunto y catalogues los metodos de simulacion propuestos segun qué tan apropiados son para simular cada uno de los modelos, como minimo, cada modelo debe tener tres metodos de simulacion apropiados segun tiempo de ejecucion, complejidad y eficacia en un contexto realista.

Luego de realizar la clasificacion, es necesario que me proporciones un paso a paso para la implementacion en python de cada metodo de simulacion para cada uno de los modelos, propona fuentes de estudio externas para la correcta implementacion de estos datos y cita en formato APA cada una de ellas cuando sea necesario, tambien considera que los resultados deben ser visualizados mediante graficos y al ser simulaciones de gran calibre tambien propone metodos que involucren la utilizacion de tarjetas graficas