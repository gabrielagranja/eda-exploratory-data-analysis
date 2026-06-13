# Estadística Descriptiva

## Introducción

La estadística descriptiva es la rama de la estadística encargada de organizar, resumir y describir las características principales de un conjunto de datos.

Dentro del Análisis Exploratorio de Datos (EDA), constituye una de las primeras etapas de análisis, ya que permite obtener una visión general del comportamiento de las variables antes de aplicar técnicas estadísticas más avanzadas o modelos de Machine Learning.

Su objetivo principal es transformar grandes volúmenes de datos en información comprensible mediante indicadores numéricos que faciliten la interpretación y la toma de decisiones.

La estadística descriptiva no busca explicar causas ni realizar predicciones, sino describir lo que ocurre en los datos observados.

---

## ¿Qué es la Estadística Descriptiva?

La estadística descriptiva consiste en un conjunto de técnicas matemáticas y estadísticas utilizadas para resumir, organizar y representar datos de manera significativa.

Estas técnicas permiten responder preguntas como:

- ¿Cuál es el valor promedio de una variable?
- ¿Qué tan dispersos están los datos?
- ¿Dónde se concentra la mayor parte de la información?
- ¿Existen valores extremos?
- ¿Cómo se distribuyen los datos?

Para ello utiliza diferentes medidas estadísticas agrupadas en tres grandes categorías:

- Medidas de tendencia central.
- Medidas de dispersión.
- Medidas de posición.

---

# 1. Medidas de Tendencia Central

Las medidas de tendencia central buscan identificar un valor representativo que describa el centro de una distribución de datos.

---

## Media (Promedio)

La media aritmética es la suma de todos los valores dividida entre el número total de observaciones.

### Fórmula

\[
\bar{x}=\frac{\sum x_i}{n}
\]

Donde:

- \(\bar{x}\) = media.
- \(x_i\) = cada observación.
- \(n\) = número total de observaciones.

### Ejemplo

```text
Edad:
20, 25, 30, 35, 40
```

Media:

```text
(20 + 25 + 30 + 35 + 40) / 5 = 30
```

### Ventajas

- Fácil de calcular.
- Utiliza toda la información disponible.

### Desventajas

- Muy sensible a valores atípicos.

Por ejemplo:

```text
20, 25, 30, 35, 200
```

La media aumenta considerablemente debido al valor extremo.

---

## Mediana

La mediana es el valor que ocupa la posición central cuando los datos se ordenan de menor a mayor.

Divide el conjunto de datos en dos partes iguales:

- 50% de los valores quedan por debajo.
- 50% de los valores quedan por encima.

### Ejemplo

```text
10, 15, 20, 25, 30
```

Mediana:

```text
20
```

### Ventajas

- Muy robusta frente a outliers.
- Representa mejor distribuciones asimétricas.

---

## Moda

La moda es el valor que aparece con mayor frecuencia dentro de un conjunto de datos.

### Ejemplo

```text
1, 2, 2, 3, 4, 4, 4, 5
```

Moda:

```text
4
```

### Característica importante

Es la única medida de tendencia central aplicable a variables categóricas nominales.

Ejemplo:

```text
Rojo
Azul
Rojo
Verde
Rojo
```

Moda:

```text
Rojo
```

---

# 2. Medidas de Dispersión

Las medidas de dispersión indican qué tan alejados o concentrados se encuentran los datos respecto a una medida central.

Permiten comprender si los datos son homogéneos o presentan gran variabilidad.

---

## Varianza

La varianza mide el promedio de las distancias al cuadrado entre cada dato y la media.

### Fórmula

\[
s^2=\frac{\sum (x_i-\bar{x})^2}{n-1}
\]

### Características

- Cuanto mayor sea la varianza, mayor será la dispersión.
- Sus unidades quedan elevadas al cuadrado.

Ejemplo:

```text
USD²
años²
kg²
```

Por ello suele ser difícil de interpretar directamente.

---

## Desviación Estándar

La desviación estándar es la raíz cuadrada de la varianza.

### Fórmula

\[
s=\sqrt{s^2}
\]

### Interpretación

Representa la distancia promedio entre los datos y la media.

- Desviación baja → datos agrupados.
- Desviación alta → datos dispersos.

### Ejemplo

Si la edad promedio es:

```text
30 años
```

y la desviación estándar es:

```text
2 años
```

los datos están bastante concentrados alrededor de la media.

---

## Rango

El rango representa la diferencia entre el valor máximo y el valor mínimo.

### Fórmula

\[
Rango = X_{max}-X_{min}
\]

### Ejemplo

```text
5, 10, 15, 20
```

Rango:

```text
20 - 5 = 15
```

Es una medida sencilla, aunque muy sensible a valores extremos.

---

# 3. Medidas de Posición

Las medidas de posición permiten dividir los datos ordenados en diferentes segmentos para comprender mejor su distribución.

---

## Percentiles

Los percentiles dividen los datos en 100 partes iguales.

El percentil \(N\) indica el valor por debajo del cual se encuentra el \(N\%\) de los datos.

### Ejemplo

Percentil 90:

```text
P90
```

Significa que el 90% de los valores se encuentra por debajo de ese punto.

---

## Cuartiles

Los cuartiles son casos particulares de percentiles.

Dividen los datos en cuatro partes iguales.

### Primer Cuartil (Q₁)

Corresponde al percentil 25.

```text
25% de los datos por debajo
```

---

### Segundo Cuartil (Q₂)

Corresponde al percentil 50.

Es exactamente la mediana.

```text
50% de los datos por debajo
```

---

### Tercer Cuartil (Q₃)

Corresponde al percentil 75.

```text
75% de los datos por debajo
```

---

## Relación con los Outliers

Los cuartiles son fundamentales para el método IQR (*Interquartile Range*) utilizado en la detección de valores atípicos.

Este método será estudiado en profundidad en el apartado dedicado a Outliers.

---

## Aplicación Práctica en Python

Pandas permite calcular automáticamente gran parte de estas métricas mediante el método `.describe()`.

```python
import pandas as pd

df = pd.read_csv("datos.csv")

print(df["ingresos"].describe())
```

Salida típica:

```text
count      1000
mean      24500
std        3500
min       18000
25%       22000
50%       24000
75%       27000
max       35000
```

El método proporciona:

- Número de observaciones.
- Media.
- Desviación estándar.
- Valor mínimo.
- Cuartiles.
- Valor máximo.

---

## Cálculos Individuales

Pandas también permite calcular cada métrica por separado.

```python
media = df["ingresos"].mean()

mediana = df["ingresos"].median()

moda = df["ingresos"].mode()[0]

varianza = df["ingresos"].var()

desviacion_estandar = df["ingresos"].std()
```

---

## Percentiles Personalizados

```python
percentil_90 = df["ingresos"].quantile(0.90)

percentil_99 = df["ingresos"].quantile(0.99)

print(percentil_90)
```

---

## Relación Visual: El Boxplot

El diagrama de caja (*Boxplot*) representa gráficamente varias medidas de posición.

```python
import seaborn as sns
import matplotlib.pyplot as plt

sns.boxplot(data=df, x="ingresos")

plt.title("Representación Visual de Cuartiles y Mediana")

plt.show()
```

Interpretación:

- Línea central → Mediana (Q₂).
- Borde inferior → Primer Cuartil (Q₁).
- Borde superior → Tercer Cuartil (Q₃).
- Altura de la caja → 50% central de los datos.

Además, permite detectar visualmente posibles valores atípicos.

---

## Importancia de la Estadística Descriptiva en el EDA

La estadística descriptiva constituye el primer nivel de comprensión de los datos.

Permite:

- Detectar errores de calidad.
- Comprender distribuciones.
- Identificar valores extremos.
- Comparar variables.
- Preparar análisis posteriores.

Sin este paso, resulta difícil interpretar correctamente los resultados obtenidos en fases más avanzadas del análisis.

---

## Conclusiones

La estadística descriptiva proporciona las herramientas necesarias para resumir y comprender un conjunto de datos mediante indicadores numéricos y visualizaciones.

Las medidas de tendencia central permiten identificar valores representativos; las medidas de dispersión muestran el grado de variabilidad de los datos; y las medidas de posición ayudan a comprender cómo se distribuye la información dentro del conjunto analizado.

Dentro del Análisis Exploratorio de Datos, estas métricas constituyen la base para detectar patrones, anomalías y oportunidades de análisis antes de aplicar técnicas estadísticas más complejas.

---

## Fuentes Consultadas

### Documentación Institucional

**Gobierno de España – Datos.gob.es**

*Guía práctica de introducción al Análisis Exploratorio de Datos (2021)*

https://datos.gob.es/sites/default/files/doc/file/analisis_exploratorio_de_datos_2021.pdf

### Documentación Oficial

- Pandas — https://pandas.pydata.org/docs/

### Bibliografía Académica

**Tukey, J. W. (1977)**  
*Exploratory Data Analysis.*  
Addison-Wesley.

**Montgomery, D. C. & Runger, G. C. (2018)**  
*Applied Statistics and Probability for Engineers.*  
Wiley.