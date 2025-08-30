**"Simulaciones Computacionales de Modelos Estocásticos de Crecimiento Sublineal en Dinámicas Ecológicas"**  

---

Genera una propuesta investigativa para un fondo concursable investigativo que consiste en el estudio computacional que valide teóricamente los tiempos de extinción y la viabilidad ecológica de los modelos estocásticos sublineales. Esta solicitud debe considerar el siguiente contexto cientifico, modelos a modelar, objetivos e  impacto.
El proyecto en el cual trabajo consiste en el estudio de los modelos de crecimiento sublineal $\dot{x} = \frac{x}{\theta}(1 - x^\theta)$ que han resurgido para resolver debates ecológicos (ej. relación diversidad-estabilidad [Hatton et al., 2024]).  No obstante, los modelos deterministas poseen limitaciones tales como **tasa de natalidad per cápita no acotada** cuando $x \to 0$, considerada biológicamente irreal [Aguade-Gorgorio et al., 2025; Camacho-Mateu et al., 2025].  
Esto nos lleva a explorar versiones estocásticas: **propiedades de extinción** varían drásticamente según el tipo de estocasticidad y el parámetro $\theta$ [Champagnat et al., 2025].  

---

Basados en Champagnat et al. (2025), se implementarán tres modelos estocásticos:  

| **Modelo**                       | **Ecuación/Proceso**                                                                        | **Parámetros Críticos**                      |
| -------------------------------- | ------------------------------------------------------------------------------------------- | -------------------------------------------- |
| **Proceso de Nacimiento-Muerte** | Tasas $b(x)$, $d(x)$ definidas por $\theta$ (Sección 1, Info. Soporte)                      | $\theta$, $K$ (capacidad de carga), $\alpha$ |
| **Difusión de Feller**           | $dX_t = X_t \frac{1-X_t^\theta}{\theta}dt + \sqrt{\gamma X_t} dB_t$                         | $\theta$, $\gamma$                           |
| **Aproximación Difusiva**        | $dZ_t = Z_t \frac{1-Z_t^\theta}{\theta}dt + \sqrt{\frac{Z_t}{K\theta }(1+Z_t^\theta)} dB_t$ | $\theta$, $K$                                |

---

# **Objetivos de Investigación**  
Generar simulaciones computacionales para cuantificar **tiempos de extinción** y **viabilidad ecológica** de los modelos estocásticos sublineales, validando resultados teóricos de Champagnat et al. (2025).  

**Objetivos específicos:**  
1. Simular el proceso de nacimiento-muerte para $\theta \leq 0$ y verificar que la extinción ocurre en escalas de tiempo **exponenciales en $K$** (Proposición 1.4).  
2. Implementar la difusión de Feller y confirmar que:  
   - La extinción es **casi segura** si $\theta \geq -1$.  
   - **No ocurre extinción** si $\theta < -1$ (Proposición 2.1).  
1. Validar que la aproximación difusiva **siempre exhibe extinción en tiempo finito** para todo $\theta$ (Proposición 2.2).  
2. Analizar el impacto de $\theta$ en escalas de tiempo de extinción usando valores empíricos $[-2, 2]$, Hatton et al.).  

---

# **Impacto Esperado y Originalidad**  
Este proyecto busca llevar a cabo una representacion visual y una validacion empirica que respalde los modelos estocasticios propuestos y de proporciones predicciones teoricas sobre extincion, lo que representa un aporte crucial para el modelamiento ecologico realista.
Ademas, se busca prestar una herramienta de codigo abierto para que ecologos, tomando en cuenta las consideraciones ya descritas en las conclusiones del articulo base, exploren escenarios con distintos $\theta$ y tipos de estocacidad.

---
# **Conclusiones Clave para la Propuesta**  
- **Base teórica sólida:** Modelos ya caracterizados matemáticamente (Champagnat et al., 2025), pero sin validación numérica.  
- **Innovación:** Puente entre teoría estocástica y ecología computacional, con enfoque en extinción y escalas de tiempo realistas.  
- **Alcance social:** Herramientas para predecir colapsos poblacionales en conservación biológica.  

> **Cita central:**  
> *"Los modelos sublineales tienen atractivo matemático, pero deben usarse con cautela en fenómenos biológicos: dinámicas estocásticas que nunca se extinguen o lo hacen en escalas de tiempo irreales"* (Champagnat et al., 2025, p. 7). 