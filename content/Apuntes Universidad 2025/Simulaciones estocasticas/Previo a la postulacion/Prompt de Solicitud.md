¡Perfecto — vamos a armar una propuesta sólida, clara y lista para presentar a un concurso investigativo. A continuación tienes una **propuesta completa en español** —con resumen, objetivos, metodología computacional detallada, plan de trabajo, entregables abiertos y un presupuesto esquemático— basada y alineada con los resultados y proposiciones del manuscrito que adjuntaste (Champagnat _et al._, 2025). Incluiré referencias a los resultados teóricos clave para que el evaluador vea el puente directo entre teoría y simulación numérica.

---

# Título (propuesto)

**Simulaciones computacionales y validación numérica de tiempos de extinción en modelos estocásticos de crecimiento sublineal**

# Resumen ejecutivo (máx. 200–250 palabras)

Este proyecto propone un estudio computacional exhaustivo que valide y complemente las predicciones teóricas recientes sobre la extinción y la viabilidad ecológica en modelos de crecimiento sublineal, en particular las conclusiones de Champagnat _et al._ (2025). Se implementarán tres clases de modelos estocásticos —(i) procesos de nacimiento-muerte individuales (discreto), (ii) difusión tipo Feller con ruido demográfico, y (iii) la aproximación difusiva (diffusion approximation)— para cuantificar tiempos medios de extinción, probabilidades de supervivencia y escalas temporales según el parámetro θ\theta, la capacidad de carga KK, y la intensidad del ruido. Emplearemos métodos directos (Gillespie), esquemas SDE (Euler–Maruyama, Milstein), y técnicas de rare-event (Adaptive Multilevel Splitting, importance sampling, Fleming–Viot/cloning) para estimar tiempos de extinción que escalan exponencialmente con KK. Los resultados validarán (o matizarán) las proposiciones teóricas: extinción en escalas exponenciales para procesos discreto con θ≤0\theta\le 0 (Proposición 1.4), umbral crítico en la difusión Feller (θ=−1\theta=-1, Proposición 2.1) y extinción casi segura para la aproximación difusiva (Proposición 2.2). El código y rutinas de simulación se liberarán como paquete reproducible y GUIs/ notebooks para la comunidad ecológica, facilitando la exploración de escenarios prácticos para conservación.

---

# Antecedentes y justificación

Los modelos deterministas sublineales x˙=xθ(1−xθ)\dot x = \tfrac{x}{\theta}(1-x^\theta) han sido usados para explicar patrones macroecológicos recientes; sin embargo, su interpretación biológica es debatida debido a tasas per-cápita no acotadas cuando x→0x\to0. Champagnat _et al._ (2025) presentan una caracterización teórica de versiones estocásticas (procesos nacimiento-muerte, difusión Feller y aproximación difusiva) y muestran que las propiedades de extinción dependen fuertemente del tipo de ruido y de θ\theta: por ejemplo, extinción casi segura/No extinción/tiempos exponenciales según el modelo y θ\theta. Estas proposiciones requieren una validación numérica robusta porque las implicancias ecológicas (predicción de colapsos, diseño de medidas de conservación) dependen de la escala temporal estimada —algo que la ecología aplicada necesita cuantificar con simulaciones reproducibles y herramientas accesibles.

---

# Objetivo general

Validar numéricamente y cuantificar las escalas temporales de extinción y la viabilidad ecológica en modelos estocásticos de crecimiento sublineal, contrastando resultados computacionales con las predicciones teóricas de Champagnat _et al._ (2025).

# Objetivos específicos

1. Implementar y simular procesos de nacimiento-muerte discretos para rangos de θ\theta (incluyendo θ≤0\theta\le 0) y verificar la predicción de tiempos de extinción que escalan exponencialmente en KK (Proposición 1.4).
    
2. Implementar la difusión Feller dXt=Xt1−Xtθθdt+γXt dBtdX_t = X_t\frac{1-X_t^\theta}{\theta}dt + \sqrt{\gamma X_t}\,dB_t; comprobar numéricamente que:  
    a) para θ≥−1\theta\ge -1 la extinción ocurre casi seguramente en tiempo finito;  
    b) para θ<−1\theta < -1 la extensión de supremum/infimum implica que no ocurre extinción en tiempo finito (Proposición 2.1).
    
3. Implementar y simular la aproximación difusiva dZt=Zt1−Ztθθdt+ZtK∣θ∣(1+Ztθ) dBtdZ_t = Z_t\tfrac{1-Z^\theta_t}{\theta}dt + \sqrt{\tfrac{Z_t}{K|\theta|}(1+Z_t^\theta)}\,dB_t y verificar que la extinción casi segura se cumple para todo θ\theta (Proposición 2.2).
    
4. Estudiar la influencia de θ\theta en escalas de tiempo de extinción en el intervalo empírico θ∈[−2,2]\theta\in[-2,2] (por ejemplo, malla fina) y producir mapas de riesgo y curvas de escalamiento (ej.: log⁡E[Text]\log \mathbb{E}[T_{\mathrm{ext}}] vs KK).
    
5. Entregar un paquete de código abierto (Python), notebooks reproducibles, y una GUI simple para que ecólogos exploren parámetros y escenarios.
    

---

# Metodología (detallada)

## 1) Modelos y parámetros

- Parámetros a barrer: θ∈[−2,2]\theta\in[-2,2] (paso sugerido 0.1–0.2 para exploraciones iniciales, luego refinamiento alrededor de transiciones observadas), K∈{50,100,200,500,1000,2000}K\in\{50,100,200,500,1000,2000\}, γ\gamma (ruido demográfico en difusión Feller) en {0.1,0.5,1.0,2.0}\{0.1,0.5,1.0,2.0\}, α\alpha (si aplica) en {0,0.1,1}\{0,0.1,1\}.
    
- Condiciones iniciales: pequeñas poblaciones (por ejemplo x0=1/Kx_0=1/K), densidades medias ( x0=0.1, 0.5x_0=0.1,\,0.5 ), y análisis de sensibilidad al estado inicial.
    
- Modelos a simular: (i) nacimiento-muerte discreto (Gillespie), (ii) SDE Feller (demográfico) con término γXt\sqrt{\gamma X_t}, (iii) difusión aproximada (como en la ecuación propuesta). Todas las ecuaciones correspondientes y proposiciones están en Champagnat _et al._ (2025).
    

## 2) Algoritmos numéricos y técnicas especiales

### A. Procesos nacimiento-muerte (discreto)

- Algoritmo: **Gillespie SSA** (algoritmo exacto) para trayectorias individuales.
    
- Problema: cuando la extinción ocurre en escalas exponenciales en KK (muy grandes), la simulación directa es ineficiente.
    
- Soluciones para rare events:
    
    - **Adaptive Multilevel Splitting (AMS)** / **Subset simulation** para estimar probabilidades de hitear 0 en horizontes largos.
        
    - **Importance sampling** con cambio de medida (exponencial tilting) para estimar tiempos medios.
        
    - **Fleming–Viot / Cloning** para estimar medidas quasi-estacionarias y tasas de salida.
        
- Verificación de convergencia y control de varianza con replicaciones y estimadores sesgo/varianza.
    

### B. SDEs (Feller y aproximación difusiva)

- Esquemas numéricos:
    
    - **Euler–Maruyama** para pruebas rápidas (paso adaptativo); comprobar estabilidad.
        
    - **Milstein** (cuando convenga) para reducir error de discretización en el término Xt\sqrt{X_t}.
        
    - Implementar reflect/absorb boundary handling con detección precisa del cruce de 0 para estimar tiempos de extinción.
        
- Para el caso θ<−1\theta< -1 en Feller (no extinción teórica), estudiar trayectorias, histogramas del mínimo alcanzado y comparar con la teoría (p. ej. funciones de escala).
    

### C. Estimación de tiempos de extinción y análisis estadístico

- Estimadores: tiempo medio E[Text]\mathbb{E}[T_{\mathrm{ext}}], mediana, distribución empírica de TextT_{\mathrm{ext}}, probabilidad de extinción antes de tmax⁡t_{\max}.
    
- Ajustes para escalamiento exponencial: ajustar log⁡E[Text]\log \mathbb{E}[T_{\mathrm{ext}}] vs KK para estimar constantes (pendiente ~ índice exponencial). Validar la Proposición 1.4 numéricamente.
    
- Cálculo de intervalos de confianza por bootstrap no paramétrico y verificación de dependencia de paso temporal (para SDEs).
    

### D. Herramientas de reducción de varianza / rare event

- Implementar y comparar: **AMS**, **splitting**, y **Fleming–Viot**; usar tests numéricos (coeficiente de variación) para elegir el método más eficiente por región de parámetros.
    
- Comparar resultados con aproximaciones asintóticas (p. ej. WKB / teoría de camino instantáneo para procesos Markovianos) cuando sea posible.
    

## 3) Reproductibilidad y software

- Lenguaje principal: **Python 3.10+**. Librerías: NumPy, SciPy, Numba (para kernels rápidos), JAX opcional para paralelización en GPU, SDEint / custom solvers, matplotlib/plotly para visualizaciones.
    
- Código: paquete modular (simuladores, rare-event, análisis) con tests unitarios y notebooks Jupyter que reproducen figuras clave.
    
- Entrega: repositorio en GitHub/GitLab con CI (tests limitados, ejemplo small runs), DOI en Zenodo para release final.
    
- GUI/Notebooks: dashboards (Voila/Streamlit) con sliders para θ,K,γ\theta, K, \gamma y producción de mapas de riesgo.
    

## 4) Validación y contraste con teoría

- Comparar numéricamente:
    
    - Proposición 1.4 — comportamiento exponencial en K para θ≤0\theta\le 0 en el birth-death.
        
    - Proposición 2.1 — comportamiento de la difusión Feller con el umbral θ=−1\theta=-1.
        
    - Proposición 2.2 — extinción casi segura en la aproximación difusiva para todo θ\theta.
        
- Producción de curvas y mapas empíricos que muestren la región de parámetros donde cada modelo es “biológicamente creíble” desde el punto de vista de la escala temporal de extinción.
    


---

# Métricas de éxito

- Reproducción numérica (con errores/IC) de las tres proposiciones teóricas citadas.
    
- Paquete con tests que permita a terceros reproducir al menos las figuras principales.
    
- Publicación(s) y workshop con asistencia de >30 personas.
    
- Transferencia de las herramientas a al menos un caso de estudio ecológico real (datos sintéticos o públicos).
    

---

# Riesgos, limitaciones y mitigaciones

- Riesgo: tiempos de extinción excesivamente grandes (simulaciones directas inviables). Mitigación: uso de técnicas rare-event (AMS, Fleming–Viot) y aproximaciones analíticas (WKB) para validar.
    
- Riesgo: discretización numérica que introduzca sesgo en SDE. Mitigación: uso de esquemas de orden superior (Milstein) y pruebas de convergencia de paso temporal; verificación con casos limitados de referencia.
    
- Riesgo: interpretación biológica de θ\theta ambigua. Mitigación: trabajo con ecólogo colaborador para traducir rangos de parámetros en escenarios realistas y reportar niveles de incertidumbre.
    

    
