# Algoritmos y Análisis Numérico con GeoGebra — PASD DGAPA 2026

Este repositorio almacena el aparato analítico, las secuencias didácticas y las simulaciones en código desarrolladas para el Programa de Actualización y Superación Docente (**PASD 2026**), avalado por la Dirección General de Asuntos del Personal Académico (**DGAPA**) de la UNAM y dictado en la **FES Acatlán** los días 15 al 26 de junio de 2026.

El enfoque central del curso rompe con la enseñanza puramente operativa del software. En su lugar, propone una **interpretación geométrica del análisis numérico**, vinculando la teoría cualitativa de campos vectoriales con los esquemas de discretización clásicos y el álgebra lineal aplicada a la aproximación óptima de datos.

---

## 📐 Marco Teórico y Aparato Analítico

### 1. Fundamentos y Geometría de la EDO (Enfoque de V.I. Arnold)
Se modelan las Ecuaciones Diferenciales Ordinarias (EDO) de primer orden de la forma $\dot{x} = v(t,x)$ como campos vectoriales que asignan vectores de velocidad en el espacio de fases, garantizando la existencia y unicidad locales mediante el **Teorema de Picard-Lindelöf**:
$$\|f(t, y_1) - f(t, y_2)\|_2 \le L_K \|y_1 - y_2\|_2$$
Se aborda de forma gráfica el *Cono de Control Lineal* definido por la constante de Lipschitz $L_K$ para restringir el escape de las aproximaciones sucesivas sobre el operador de contracción.

### 2. Algoritmos de Aproximación Numérica para EDOs
* **Método de Euler (Aproximación Lineal):** Basado en el desarrollo de Taylor de primer orden, con un error de truncamiento local $\mathcal{O}(h^2)$:
  $$y_{n+1} = y_n + h \cdot f(t_n, y_n)$$
* **Método de Heun (Esquema Predictor-Corrector):** Equivalente a la regla del trapecio para integración numérica, alcanzando un orden $\mathcal{O}(h^2)$ global mediante el promedio de pendientes:
  $$\tilde{y}_{n+1} = y_n + hf(t_n, y_n) \quad \text{(Predictor)}$$
  $$y_{n+1} = y_n + \frac{h}{2}\left[f(t_n, y_n) + f(t_{n+1}, \tilde{y}_{n+1})\right] \quad \text{(Corrector)}$$
* **Runge-Kutta de Cuarto Orden (RK4):** Utiliza cuatro evaluaciones del campo vectorial para cancelar términos de error de Taylor hasta el orden 4, vinculándose geométricamente con la Regla de Simpson:
  $$y_{n+1} = y_n + \frac{h}{6}(k_1 + 2k_2 + 2k_3 + k_4)$$

### 3. Teoría de Aproximación y Mínimos Cuadrados Generalizados
El desmadre de la aproximación óptima se aborda desde la perspectiva del álgebra lineal abstracta, donde el ajuste de datos busca proyectar ortogonalmente un vector de observaciones sobre el subespacio generado por las funciones base.

* **Mínimos Cuadrados Polinomiales de Grado $n$:**
  Dada una nube de puntos $\{(xi, y_i)\}_{i=1}^m$, se busca el polinomio óptimo $P_n(x) = a_0 + a_1x + a_2x^2 + \dots + a_nx^n$ minimizando la norma del error cuadrático. Esto se traduce en la formulación y resolución explícita de las **Ecuaciones Normales** mediante la **Matriz de Vandermonde Modificada** (Matriz de Momentos):
  $$\begin{pmatrix} 
  m & \sum x_i & \sum x_i^2 & \dots & \sum x_i^n \\ 
  \sum x_i & \sum x_i^2 & \sum x_i^3 & \dots & \sum x_i^{n+1} \\ 
  \vdots & \vdots & \vdots & \ddots & \vdots \\ 
  \sum x_i^n & \sum x_i^{n+1} & \sum x_i^{n+2} & \dots & \sum x_i^{2n} 
  \end{pmatrix} 
  \begin{pmatrix} a_0 \\ a_1 \\ \vdots \\ a_n \end{pmatrix} = 
  \begin{pmatrix} \sum y_i \\ \sum x_i y_i \\ \vdots \\ \sum x_i^n y_i \end{pmatrix}$$

* **Aproximación Exponencial No Lineal:**
  Para ajustar modelos intrínsecamente no lineales de la forma $y = A e^{Bx}$, se aplica un proceso de **linealización** mediante transformaciones logarítmicas sobre el espacio de llegada:
  $$\ln(y) = \ln(A) + Bx$$
  Permitiendo resolver el PVI transformado en el plano linealizado antes de la restitución por el exponencial del operador inverso.

* **Aproximación Logística (Modelos de Crecimiento Sigmoidal):**
  Utilizado para acotar el crecimiento poblacional bajo un entorno con capacidad de carga $K$:
  $$y = \frac{K}{1 + A e^{-Bx}}$$
  La linealización requiere la manipulación analítica del recíproco y el logaritmo del cociente, forzando la linealización del término de perturbación:
  $$\ln\left(\frac{K - y}{y}\right) = \ln(A) - Bx$$
  Este esquema se programa dinámicamente en GeoGebra, permitiendo la estimación interactiva del techo de saturación $K$ mediante optimización visual de residuos.

---

## 📂 Organización de las Carpetas en el Repositorio

* `EDO_Analisis_Numerico_con_GeoGebra_2026.pdf`: Presentación oficial en extenso con el aparato analítico y geométrico del curso.
* `/Modelos_GeoGebra/`: Archivos `.ggb` interactivos que muestran las *poligonales de Euler*, las matrices de momentos para polinomios de grado $n$, y los modelos de linealización logística/exponencial.
* Enlace del metodo de Euler (https://www.geogebra.org/m/rucxsp8f)

---

## 👥 Créditos y Desglose de Autoría Docente

En estricto cumplimiento de los principios de transparencia académica y propiedad de los contenidos desarrollados, se detalla la contribución específica de los instructores:

* **Mtro. Miguel Ángel Chávez García**  
  * *Diseño y desarrollo teórico-A}analítico, Programación Matemática de las poligonales e interactivos en GeoGebra, y aaquetación del contenido académico en $\LaTeX$.*
* **Mat. Alejandro Martínez Ireneo**  
  * *Coautor intitucional.*
