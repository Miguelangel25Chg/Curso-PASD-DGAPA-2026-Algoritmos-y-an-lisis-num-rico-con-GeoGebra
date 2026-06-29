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
  
  $$y_{n+1} = y_n + h \cdot f(t_n, y_n).$$
* **Método de Heun (Esquema Predictor-Corrector):** Equivalente a la regla del trapecio para integración numérica, alcanzando un orden $\mathcal{O}(h^2)$ global mediante el promedio de pendientes:
  $$\overline{y}_{n+1} = y_n + hf(t_n, y_n) \quad \text{(Predictor)}.$$
  
  $$y_{n+1} = y_n + \frac{h}{2}\left[f(t_n, y_n) + f(t_{n+1}, \overline{y}_{n+1})\right] \quad \text{(Corrector)}$$
  
* **Runge-Kutta de Cuarto Orden (RK4):** Utiliza cuatro evaluaciones del campo vectorial para cancelar términos de error de Taylor hasta el orden 4, vinculándose geométricamente con la Regla de Simpson:

  $$y_{n+1} = y_n + \frac{h}{6}(k_1 + 2k_2 + 2k_3 + k_4).$$

### 3. Teoría de Aproximación y Mínimos Cuadrados Generalizados
La aproximación por mínimos cuadrados se aborda desde el punto de vista del cálculo multivariable y la optimización se aborda desde la perspectiva del álgebra lineal, donde el ajuste de datos busca minimizar la distancia de las ordenadas provenientes de una nube de datos a una recta $y=Ax+B$ denominada recta de mínimos cuadrados.

* **Mínimos Cuadrados Polinomiales de Grado $n$:**
Dada una nube de puntos $\{(x_i, y_i)\}_{i=1}^m$, se busca el polinomio óptimo $P_n(x) = a_0 + a_1x + a_2x^2 + \dots + a_nx^n$ minimizando la norma del error cuadrático. Esto se traduce en la formulación y resolución explícita de las **Ecuaciones Normales** mediante la **matriz de momentos simétrica**:

$$\begin{pmatrix} m & \sum_{i=1}^m x_i & \sum_{i=1}^m x_i^2 & \dots & \sum_{i=1}^m x_i^n \\\\ \sum_{i=1}^m x_i & \sum_{i=1}^m x_i^2 & \sum_{i=1}^m x_i^3 & \dots & \sum_{i=1}^m x_i^{n+1} \\\\ \vdots & \vdots & \vdots & \ddots & \vdots \\\\ \sum_{i=1}^m x_i^n & \sum_{i=1}^m x_i^{n+1} & \sum_{i=1}^m x_i^{n+2} & \dots & \sum_{i=1}^m x_i^{2n} \end{pmatrix} \begin{pmatrix} a_0 \\\\ a_1 \\\\ \vdots \\\\ a_n \end{pmatrix} = \begin{pmatrix} \sum_{i=1}^m y_i \\\\ \sum_{i=1}^m x_i y_i \\\\ \vdots \\\\ \sum_{i=1}^m x_i^n y_i \end{pmatrix}$$
* **Aproximación Exponencial No Lineal:**
  Para ajustar modelos intrínsecamente no lineales de la forma $y = A e^{Bx}$, se aplica un proceso de **linealización** mediante transformaciones logarítmicas sobre el espacio de llegada:
  $$\ln(y) = \ln(A) + Bx$$
  Permitiendo resolver el problema transformado en el plano.

---

## 📂 Organización de las Carpetas en el Repositorio

* `EDO_Analisis_Numerico_con_GeoGebra_2026.pdf`: Presentación oficial en extenso con el aparato analítico y geométrico del curso.
* `/Modelos_GeoGebra/`: Archivos `.ggb` interactivos que muestran las *poligonales de Euler*, las matrices de momentos para polinomios de grado $n$, y los modelos de linealización logística/exponencial.
* Enlace del metodo de Euler: (https://www.geogebra.org/m/rucxsp8f)
* Método de Heun: (https://www.geogebra.org/m/wkmfh8cy)
* Método de Runge Kutta de orden cuatro: (https://www.geogebra.org/m/h9sk7hm3)
* Aproximación por mínimos cuadrados: (https://www.geogebra.org/m/gbhsurzw)
* Aproximación por polinomios grados dos por mínimos cuadrados (https://www.geogebra.org/m/pwexfg2n)
* Modelación por aproximación exponencial con mínimos cuadrados: (https://www.geogebra.org/m/vcz2st28)
* Modelación por aproximación logarítimica con mínimos cuadrados_ (https://www.geogebra.org/m/fgqnw7ws)
* Práctica de una aproximación logarítimica: (https://www.geogebra.org/m/pc5jntfx)
## 📂 Videos generados para el curso
* Video del 22/06/2026: (https://classroom.google.com/c/ODY3Nzg3Nzc2MzMx/m/ODY4NDQwMDMzOTgw/details)
* Video del 23/06/2026:(https://drive.google.com/file/d/1Iqp0z6QG68jXwNIhHtMN65jX9d8RzlIs/view?usp=drive_link)
* Video del 24/06/2026:(https://drive.google.com/file/d/1umD78TAkY5UYoWCZpx0FTHP5FuKfK4F1/view?usp=drive_link)
* Video del 25/06/2026:(https://drive.google.com/file/d/1rqGQ5Ihu79PzxXMIHcGYF5eM8lyjgZNt/view?usp=drive_link)
* Video del 26/06/2026:(https://drive.google.com/file/d/1KBr4M2MQAHnCfqT7gUN_FAQFNvV12rg-/view?usp=drive_link)
---

## 👥 Créditos y Desglose de Autoría Docente

En estricto cumplimiento de los principios de transparencia académica y propiedad de los contenidos desarrollados, se detalla la contribución específica de los instructores:

* **Mtro. Miguel Ángel Chávez García**  
  * *Diseño y desarrollo teórico-analítico, programación matemática de las poligonales e interactivos en GeoGebra, autor de contenido académico en $\LaTeX$.*
* **Mat. Alejandro Martínez Ireneo**  
  * *Ayudante en sesiones.*
