# Hypothesis Testing (Pruebas de Hipótesis)

## Introducción

Las pruebas de hipótesis (*Hypothesis Testing*) constituyen uno de los pilares fundamentales de la estadística inferencial. Mientras que la estadística descriptiva permite resumir y describir un conjunto de datos, las pruebas de hipótesis permiten evaluar si los patrones observados en una muestra representan un fenómeno real en la población o si podrían explicarse simplemente por el azar.

Dentro del Análisis Exploratorio de Datos (EDA), las pruebas de hipótesis complementan la inspección visual y las métricas descriptivas, proporcionando evidencia estadística para validar o rechazar determinadas afirmaciones sobre los datos.

Su objetivo principal es transformar observaciones y sospechas en conclusiones respaldadas por métodos estadísticos formales.

---

## ¿Qué es una Prueba de Hipótesis?

Una prueba de hipótesis es un procedimiento estadístico que utiliza los datos de una muestra para evaluar una afirmación sobre una población.

Permite responder preguntas como:

- ¿Existe una diferencia real entre dos grupos?
- ¿Dos variables están relacionadas?
- ¿Una variable sigue una distribución determinada?
- ¿El efecto observado es estadísticamente significativo?

En lugar de aceptar una afirmación como verdadera o falsa de forma absoluta, las pruebas de hipótesis evalúan el grado de evidencia disponible para respaldarla.

---

# Fundamentos del Hypothesis Testing

Toda prueba de hipótesis se basa en la comparación de dos afirmaciones opuestas.

---

## Hipótesis Nula (H₀)

La hipótesis nula representa la situación de referencia o "estado normal".

Generalmente plantea que:

- No existe diferencia.
- No existe relación.
- No existe efecto.

### Ejemplos

```text
No existe diferencia de gasto entre hombres y mujeres.
```

```text
La región no influye en la suscripción de usuarios.
```

```text
La variable sigue una distribución normal.
```

---

## Hipótesis Alternativa (H₁ o Hₐ)

La hipótesis alternativa representa la afirmación que se desea demostrar.

Plantea que sí existe:

- Diferencia.
- Relación.
- Efecto.

### Ejemplos

```text
Existe diferencia de gasto entre hombres y mujeres.
```

```text
La región influye en la suscripción de usuarios.
```

```text
La variable no sigue una distribución normal.
```

---

# El Valor p (p-value)

El resultado más importante de una prueba de hipótesis es el valor p (*p-value*).

El valor p representa la probabilidad de observar unos resultados iguales o más extremos que los obtenidos, suponiendo que la hipótesis nula sea cierta.

---

## Regla de Decisión

La práctica estadística habitual consiste en comparar el valor p con un nivel de significancia previamente definido.

Normalmente:

\[
\alpha = 0.05
\]

---

### Caso 1: p < 0.05

Se rechaza la hipótesis nula.

Existe evidencia suficiente para considerar que el efecto observado es estadísticamente significativo.

```text
p = 0.02
```

Resultado:

```text
Se rechaza H₀
```

---

### Caso 2: p ≥ 0.05

No se puede rechazar la hipótesis nula.

No existe evidencia suficiente para afirmar que el efecto observado sea real.

```text
p = 0.12
```

Resultado:

```text
No se rechaza H₀
```

---

# Errores en las Pruebas de Hipótesis

Las decisiones estadísticas no son perfectas.

Existen dos tipos principales de error.

---

## Error Tipo I (Falso Positivo)

Consiste en rechazar una hipótesis nula que en realidad es verdadera.

### Ejemplo

Concluir que un medicamento funciona cuando realmente no produce ningún efecto.

---

## Error Tipo II (Falso Negativo)

Consiste en no rechazar una hipótesis nula que en realidad es falsa.

### Ejemplo

Concluir que un medicamento no funciona cuando sí tiene efecto.

---

## Relación con α

El nivel de significancia:

\[
\alpha = 0.05
\]

representa la probabilidad máxima aceptada de cometer un Error Tipo I.

---

# ¿Para Qué Sirve el Hypothesis Testing en el EDA?

Durante el Análisis Exploratorio de Datos es habitual detectar patrones visuales que podrían ser reales o simplemente producto del azar.

Las pruebas de hipótesis permiten validar científicamente estas observaciones.

---

## 1. Validar Diferencias Entre Grupos

Supongamos que un boxplot muestra que dos grupos tienen comportamientos distintos.

La prueba de hipótesis permite determinar si esa diferencia es estadísticamente significativa.

### Ejemplo

```text
Clientes Premium
vs
Clientes Estándar
```

---

## 2. Confirmar Relaciones Entre Variables

Una correlación observada puede ser consecuencia del azar.

Las pruebas de hipótesis permiten verificar si la relación observada es estadísticamente distinta de cero.

### Ejemplo

```text
Edad ↔ Ingresos
```

---

## 3. Evaluar Distribuciones

Muchos algoritmos estadísticos asumen que los datos siguen una distribución normal.

Las pruebas de hipótesis permiten verificar formalmente si esta condición se cumple.

---

## 4. Respaldar Decisiones Basadas en Datos

Permiten transformar observaciones subjetivas en conclusiones objetivas respaldadas por evidencia estadística.

---

# Principales Pruebas de Hipótesis Utilizadas en EDA

## 1. Prueba t de Student (T-Test)

Se utiliza para comparar las medias de dos grupos independientes.

### Hipótesis

#### H₀

Las medias son iguales.

#### H₁

Las medias son diferentes.

---

### Ejemplo

```text
¿Existe diferencia de gasto entre hombres y mujeres?
```

---

### Aplicación en Python

```python
from scipy import stats

gasto_hombres = df[
    df["genero"] == "Masculino"
]["gasto"]

gasto_mujeres = df[
    df["genero"] == "Femenino"
]["gasto"]

stat, p_valor = stats.ttest_ind(
    gasto_hombres,
    gasto_mujeres,
    equal_var=False
)

print(f"Valor p: {p_valor}")

if p_valor < 0.05:
    print(
        "Rechazamos H0: existe una diferencia significativa."
    )
else:
    print(
        "No podemos rechazar H0."
    )
```

---

## 2. Prueba Chi-Cuadrado de Independencia (χ²)

Se utiliza para estudiar la relación entre dos variables categóricas.

---

### Hipótesis

#### H₀

Las variables son independientes.

#### H₁

Las variables están asociadas.

---

### Ejemplo

```text
¿La región influye en la suscripción de usuarios?
```

---

### Aplicación en Python

```python
import pandas as pd
from scipy import stats

tabla_contingencia = pd.crosstab(
    df["region"],
    df["suscrito"]
)

chi2, p_valor, dof, expected = (
    stats.chi2_contingency(
        tabla_contingencia
    )
)

print(f"Valor p: {p_valor}")

if p_valor < 0.05:
    print(
        "Existe una asociación significativa."
    )
else:
    print(
        "No existe evidencia suficiente de asociación."
    )
```

---

## 3. Prueba de Normalidad de Shapiro-Wilk

Permite verificar si una variable sigue una distribución normal.

---

### Hipótesis

#### H₀

Los datos siguen una distribución normal.

#### H₁

Los datos no siguen una distribución normal.

---

### Ejemplo

```text
¿La variable ingresos sigue una distribución normal?
```

---

### Aplicación en Python

```python
from scipy import stats

stat, p_valor = stats.shapiro(
    df["ingresos"].dropna()
)

print(f"Valor p: {p_valor}")

if p_valor < 0.05:
    print(
        "Los datos NO siguen una distribución normal."
    )
else:
    print(
        "No existe evidencia para rechazar la normalidad."
    )
```

---

# Flujo General de una Prueba de Hipótesis

```text
Planteamiento del problema
            │
            ▼
Definir H₀ y H₁
            │
            ▼
Seleccionar prueba estadística
            │
            ▼
Calcular estadístico y valor p
            │
            ▼
Comparar con α = 0.05
            │
            ▼
Tomar decisión
            │
            ▼
Interpretar resultados
```

---

# Limitaciones del Hypothesis Testing

Aunque es una herramienta extremadamente útil, presenta algunas limitaciones.

---

## Significancia ≠ Importancia

Un resultado puede ser estadísticamente significativo pero carecer de relevancia práctica.

### Ejemplo

```text
p = 0.001
```

Puede indicar una diferencia real pero económicamente irrelevante.

---

## Dependencia del Tamaño de la Muestra

Muestras muy grandes pueden detectar diferencias mínimas.

Muestras pequeñas pueden ocultar efectos reales.

---

## Sensibilidad a Supuestos Estadísticos

Algunas pruebas requieren:

- Normalidad.
- Independencia.
- Homogeneidad de varianzas.

Si estos supuestos no se cumplen, los resultados pueden resultar poco fiables.

---

# Importancia del Hypothesis Testing en el EDA

Las pruebas de hipótesis permiten complementar la exploración visual y descriptiva de los datos.

Gracias a ellas es posible:

- Validar diferencias observadas.
- Confirmar relaciones entre variables.
- Evaluar distribuciones estadísticas.
- Respaldar decisiones con evidencia cuantitativa.

Por ello constituyen una herramienta esencial tanto en análisis exploratorio como en investigación científica y desarrollo de modelos predictivos.

---

## Conclusiones

El Hypothesis Testing es un conjunto de procedimientos estadísticos diseñados para evaluar si las observaciones realizadas en una muestra reflejan fenómenos reales o simplemente variaciones aleatorias.

Su funcionamiento se basa en la comparación entre una hipótesis nula y una hipótesis alternativa mediante el análisis del valor p y el nivel de significancia.

Dentro del Análisis Exploratorio de Datos, estas pruebas permiten validar patrones observados, confirmar relaciones entre variables y fundamentar conclusiones con evidencia estadística objetiva.

La correcta aplicación de pruebas como el T-Test, Chi-Cuadrado o Shapiro-Wilk mejora significativamente la calidad y fiabilidad de cualquier análisis de datos.

---

## Fuentes Consultadas

### Documentación Institucional

**Gobierno de España – Datos.gob.es**

*Guía práctica de introducción al Análisis Exploratorio de Datos (2021)*

https://datos.gob.es/sites/default/files/doc/file/analisis_exploratorio_de_datos_2021.pdf

### Documentación Oficial

- SciPy — https://docs.scipy.org/doc/scipy/
- Pandas — https://pandas.pydata.org/docs/

### Bibliografía Académica

**Montgomery, D. C. & Runger, G. C. (2018)**  
*Applied Statistics and Probability for Engineers.*  
Wiley.

**James, G., Witten, D., Hastie, T. & Tibshirani, R. (2021)**  
*An Introduction to Statistical Learning.*  
Springer.

**Tukey, J. W. (1977)**  
*Exploratory Data Analysis.*  
Addison-Wesley.