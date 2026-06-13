# Matriz de Correlación

## Introducción

Una de las tareas más importantes dentro del Análisis Exploratorio de Datos (EDA) consiste en identificar relaciones entre variables.

La matriz de correlación es una herramienta estadística que permite medir y visualizar el grado de asociación existente entre variables numéricas dentro de un conjunto de datos.

Su uso facilita la detección de patrones, dependencias y relaciones que pueden resultar relevantes para la comprensión del negocio, la selección de variables o la construcción de modelos predictivos.

Dentro de un proceso de EDA, la matriz de correlación constituye uno de los mecanismos más utilizados para estudiar relaciones lineales entre variables.

---

## ¿Qué es una Matriz de Correlación?

Una matriz de correlación es una tabla que muestra los coeficientes de correlación entre todas las combinaciones posibles de variables numéricas de un conjunto de datos.

Cada celda representa la fuerza y dirección de la relación existente entre dos variables.

Por ejemplo:

| Variable | Edad | Ingresos | Gasto |
|-----------|--------|--------|--------|
| Edad | 1.00 | 0.45 | 0.30 |
| Ingresos | 0.45 | 1.00 | 0.80 |
| Gasto | 0.30 | 0.80 | 1.00 |

La diagonal principal siempre tiene valor:

```text
1.00
```

porque una variable está perfectamente correlacionada consigo misma.

---

## ¿Qué es la Correlación?

La correlación es una medida estadística que cuantifica el grado de relación entre dos variables.

No implica causalidad.

Es importante entender que:

> Correlación no significa necesariamente causa y efecto.

Dos variables pueden estar correlacionadas sin que una provoque cambios en la otra.

---

# Interpretación del Coeficiente de Correlación

La matriz utiliza habitualmente el **Coeficiente de Correlación de Pearson**, cuyos valores se encuentran entre:

\[
-1 \leq r \leq 1
\]

Donde:

- \(r\) = coeficiente de correlación.

---

## Correlación Positiva Perfecta (r = 1)

Cuando una variable aumenta, la otra también aumenta de forma proporcional.

### Ejemplo

- Horas de estudio.
- Calificación obtenida.

```text
Horas ↑
Notas ↑
```

---

## Correlación Negativa Perfecta (r = -1)

Cuando una variable aumenta, la otra disminuye proporcionalmente.

### Ejemplo

- Altitud.
- Temperatura.

```text
Altitud ↑
Temperatura ↓
```

---

## Ausencia de Correlación (r = 0)

No existe relación lineal entre las variables.

El comportamiento de una variable no permite predecir el comportamiento de la otra.

### Ejemplo

- Número de hermanos.
- Temperatura exterior.

---

## Escala General de Interpretación

| Valor absoluto de r | Interpretación |
|--------------------|----------------|
| 0.00 – 0.19 | Muy débil |
| 0.20 – 0.39 | Débil |
| 0.40 – 0.59 | Moderada |
| 0.60 – 0.79 | Fuerte |
| 0.80 – 1.00 | Muy fuerte |

Esta clasificación es orientativa y puede variar según el contexto del análisis.

---

# ¿Para Qué Sirve una Matriz de Correlación en el EDA?

Durante la fase exploratoria cumple varias funciones fundamentales.

---

## 1. Identificar Relaciones Relevantes

Permite detectar qué variables presentan asociaciones importantes.

### Ejemplo

En un análisis inmobiliario:

```text
Metros cuadrados ↔ Precio
```

podrían presentar una correlación elevada.

Esto indica que ambas variables evolucionan conjuntamente.

---

## 2. Detectar Multicolinealidad

La multicolinealidad ocurre cuando dos o más variables independientes están altamente correlacionadas entre sí.

### Ejemplo

```text
Ingresos mensuales
Ingresos anuales
```

Ambas contienen prácticamente la misma información.

---

### Problemas que genera

- Información redundante.
- Modelos menos interpretables.
- Inestabilidad en algoritmos predictivos.

Generalmente se considera problemática cuando:

```text
|r| > 0.80
```

---

## 3. Selección de Variables

La matriz ayuda a identificar qué variables aportan información relevante para el análisis.

Variables con correlaciones muy bajas pueden aportar poco valor predictivo.

Esto facilita procesos de:

- Selección de características (*Feature Selection*).
- Reducción de dimensionalidad.
- Optimización de modelos.

---

## 4. Comprender el Comportamiento del Dataset

La correlación proporciona una visión rápida de cómo interactúan las distintas variables.

Permite descubrir relaciones que podrían pasar desapercibidas mediante observación directa.

---

# Tipos de Correlación

Aunque Pearson es el coeficiente más utilizado, existen otros métodos de correlación.

---

## Correlación de Pearson

Mide relaciones lineales entre variables numéricas.

### Supuestos

- Variables numéricas.
- Relación lineal.
- Ausencia de valores extremos severos.

Es el método utilizado por defecto en Pandas.

---

## Correlación de Spearman

Se basa en rangos y no requiere relaciones estrictamente lineales.

Resulta útil cuando:

- Existen outliers.
- La relación es monotónica.
- Los datos no siguen distribución normal.

---

## Correlación de Kendall

Utilizada principalmente en muestras pequeñas o estudios con variables ordinales.

Es menos frecuente en EDA general.

---

# Aplicación Práctica en Python

## Cálculo de la Matriz de Correlación

Pandas permite calcular la matriz mediante el método `.corr()`.

```python
import pandas as pd

df = pd.read_csv("datos.csv")

matriz_corr = df.corr()

print(matriz_corr)
```

### Importante

El método:

```python
corr()
```

ignora automáticamente las variables categóricas y trabaja únicamente con columnas numéricas.

---

# Visualización Mediante Heatmap

La forma más habitual de representar una matriz de correlación es mediante un mapa de calor (*Heatmap*).

Para ello se utiliza Seaborn junto con Matplotlib.

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

matriz_corr = df.corr()

plt.figure(figsize=(10, 8))

sns.heatmap(
    matriz_corr,
    annot=True,
    cmap="coolwarm",
    fmt=".2f",
    vmin=-1,
    vmax=1
)

plt.title("Matriz de Correlación del Dataset")

plt.show()
```

---

## Interpretación del Heatmap

La intensidad del color representa la fuerza de la correlación.

### Colores cálidos

```text
Rojo
```

Indican correlaciones positivas.

---

### Colores fríos

```text
Azul
```

Indican correlaciones negativas.

---

### Colores neutros

```text
Blanco
```

Representan correlaciones cercanas a cero.

---

# Optimización Visual: Máscara Triangular

La matriz de correlación es simétrica.

Por ejemplo:

```text
Edad ↔ Ingresos
```

es idéntica a:

```text
Ingresos ↔ Edad
```

Por tanto, la mitad de la información aparece duplicada.

---

## Creación de una Máscara

```python
import numpy as np

mascara = np.triu(
    np.ones_like(
        matriz_corr,
        dtype=bool
    )
)

plt.figure(figsize=(10, 8))

sns.heatmap(
    matriz_corr,
    annot=True,
    cmap="coolwarm",
    fmt=".2f",
    mask=mascara,
    vmin=-1,
    vmax=1
)

plt.title(
    "Matriz de Correlación sin Duplicados"
)

plt.show()
```

Esta técnica mejora significativamente la legibilidad del gráfico.

---

# Limitaciones de la Correlación

Aunque es una herramienta muy útil, la correlación presenta ciertas limitaciones.

---

## Correlación no implica causalidad

Dos variables pueden estar correlacionadas sin que exista una relación causal.

### Ejemplo

```text
Ventas de helados
Ahogamientos
```

Ambas aumentan durante el verano, pero una no causa la otra.

---

## Solo mide relaciones lineales

Una correlación cercana a cero no implica necesariamente ausencia de relación.

Puede existir una relación no lineal que Pearson no sea capaz de detectar.

---

## Sensibilidad a Outliers

Los valores extremos pueden alterar significativamente los coeficientes de correlación.

Por este motivo suele ser recomendable analizar los outliers antes de interpretar una matriz de correlación.

---

# Importancia de la Matriz de Correlación en el EDA

La matriz de correlación constituye una herramienta fundamental para:

- Comprender relaciones entre variables.
- Detectar patrones.
- Identificar redundancias.
- Seleccionar variables relevantes.
- Preparar modelos predictivos.
- Reducir problemas de multicolinealidad.

Su interpretación adecuada permite obtener información valiosa sobre la estructura interna de un conjunto de datos.

---

## Conclusiones

La matriz de correlación es una herramienta estadística que permite medir y visualizar las relaciones existentes entre variables numéricas.

Dentro del Análisis Exploratorio de Datos, resulta especialmente útil para identificar asociaciones relevantes, detectar multicolinealidad y comprender el comportamiento general del dataset.

Combinada con herramientas de visualización como Seaborn y Matplotlib, proporciona una representación clara e intuitiva de las dependencias existentes entre variables.

Su correcta interpretación constituye una parte esencial de cualquier proceso de análisis de datos.

---

## Fuentes Consultadas

### Documentación Institucional

**Gobierno de España – Datos.gob.es**

*Guía práctica de introducción al Análisis Exploratorio de Datos (2021)*

https://datos.gob.es/sites/default/files/doc/file/analisis_exploratorio_de_datos_2021.pdf

### Documentación Oficial

- Pandas — https://pandas.pydata.org/docs/
- Matplotlib — https://matplotlib.org/stable/
- Seaborn — https://seaborn.pydata.org/

### Bibliografía Académica

**Tukey, J. W. (1977)**  
*Exploratory Data Analysis.*  
Addison-Wesley.

**James, G., Witten, D., Hastie, T. & Tibshirani, R. (2021)**  
*An Introduction to Statistical Learning.*  
Springer.