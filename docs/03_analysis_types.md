# Análisis Univariado, Bivariado y Multivariado

## Introducción

Uno de los principales objetivos del Análisis Exploratorio de Datos (EDA) es comprender cómo se comportan las variables dentro de un conjunto de datos.

Dependiendo del número de variables analizadas simultáneamente, el análisis puede clasificarse en:

- Análisis Univariado.
- Análisis Bivariado.
- Análisis Multivariado.

Cada uno proporciona distintos niveles de profundidad y permite responder preguntas específicas sobre los datos.

---

## 1. Análisis Univariado (1 Variable)

### Definición

El análisis univariado estudia una única variable de forma aislada.

Su objetivo principal es describir, resumir y comprender el comportamiento individual de una variable.

No busca relaciones entre variables.

---

### Preguntas que responde

- ¿Cuál es el promedio de edad?
- ¿Cuál es el producto más vendido?
- ¿Cómo se distribuyen los ingresos?
- ¿Existen valores atípicos?

---

### Métricas utilizadas

#### Tendencia central

- Media.
- Mediana.
- Moda.

#### Dispersión

- Varianza.
- Desviación estándar.
- Rango.

#### Posición

- Cuartiles.
- Percentiles.

---

### Gráficos habituales

- Histogramas.
- Diagramas de caja (Boxplots).
- Gráficos de barras.
- Diagramas de densidad.

---

## 2. Análisis Bivariado (2 Variables)

### Definición

El análisis bivariado estudia la relación existente entre dos variables.

Su objetivo es determinar si existe asociación, dependencia o correlación entre ambas.

---

### Preguntas que responde

- ¿Los clientes más jóvenes gastan más dinero?
- ¿La satisfacción influye en la fidelización?
- ¿Existe relación entre ingresos y edad?
- ¿El género afecta al nivel de gasto?

---

### Métricas utilizadas

#### Variables numéricas

- Correlación de Pearson.
- Correlación de Spearman.

#### Variables categóricas

- Tablas de contingencia.
- Chi-cuadrado.

---

### Gráficos habituales

- Diagramas de dispersión.
- Boxplots comparativos.
- Barras agrupadas.
- Heatmaps.

---

## 3. Análisis Multivariado (3 o más Variables)

### Definición

El análisis multivariado estudia simultáneamente tres o más variables.

Su objetivo es comprender cómo interactúan múltiples factores al mismo tiempo.

En la práctica, los fenómenos reales rara vez dependen de una única variable.

---

### Preguntas que responde

- ¿Cómo influyen conjuntamente la edad, los ingresos y la ubicación geográfica sobre una compra?
- ¿Qué factores explican el abandono de clientes?
- ¿Qué variables tienen mayor impacto en una predicción?

---

### Técnicas utilizadas

#### Modelos estadísticos

- Regresión lineal múltiple.
- Regresión logística.

#### Reducción de dimensionalidad

- PCA (Principal Component Analysis).

#### Agrupamiento

- Clustering.
- K-Means.

#### Machine Learning

- Árboles de decisión.
- Random Forest.
- Redes neuronales.

---

### Gráficos habituales

- Matrices de correlación.
- Pairplots.
- Heatmaps.
- Gráficos tridimensionales.

---

## Comparativa de los Tres Tipos de Análisis

| Tipo | Variables | Objetivo Principal |
|--------|--------|--------|
| Univariado | 1 | Describir una variable |
| Bivariado | 2 | Analizar relaciones |
| Multivariado | 3 o más | Comprender interacciones complejas |

---

## Aplicación Práctica en Python

### Análisis Univariado

```python
df["edad"].describe()
```

### Histograma

```python
df["edad"].hist()
```

---

### Análisis Bivariado

```python
df[["edad", "ingresos"]].corr()
```

### Scatterplot

```python
import seaborn as sns

sns.scatterplot(
    data=df,
    x="edad",
    y="ingresos"
)
```

---

### Análisis Multivariado

```python
sns.pairplot(
    df[
        [
            "edad",
            "ingresos",
            "gasto"
        ]
    ]
)
```

---

## Importancia dentro del EDA

Cada tipo de análisis aporta una perspectiva diferente:

- El análisis univariado ayuda a comprender variables individuales.
- El análisis bivariado permite descubrir relaciones.
- El análisis multivariado facilita comprender fenómenos complejos y dependencias simultáneas.

La combinación de los tres enfoques proporciona una visión completa del conjunto de datos.

---

## Conclusiones

El análisis univariado, bivariado y multivariado constituye una parte fundamental del proceso de Exploratory Data Analysis.

Cada nivel de análisis incrementa la profundidad del conocimiento obtenido sobre los datos, permitiendo pasar de la simple descripción de variables a la comprensión de relaciones e interacciones complejas.

La correcta aplicación de estos enfoques facilita la toma de decisiones y mejora la calidad de los análisis posteriores.

---

## Fuentes Consultadas

- Guía práctica de introducción al Análisis Exploratorio de Datos (Datos.gob.es, 2021)
- Pandas Documentation
- Seaborn Documentation
- Tukey, J. W. (1977). Exploratory Data Analysis.