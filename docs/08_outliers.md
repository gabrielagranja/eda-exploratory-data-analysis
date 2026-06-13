# Outliers (Valores Atípicos)

## Introducción

Durante el Análisis Exploratorio de Datos (EDA) es habitual encontrar observaciones que se comportan de forma muy diferente al resto de los datos. Estos registros reciben el nombre de **outliers** o **valores atípicos**.

Los outliers pueden representar errores de captura, problemas de medición o eventos reales poco frecuentes. Debido a su capacidad para alterar promedios, correlaciones y modelos estadísticos, su identificación y tratamiento constituyen una de las tareas más importantes dentro de cualquier proceso de análisis de datos.

Detectar correctamente los valores atípicos permite mejorar la calidad del análisis y comprender mejor el comportamiento real del conjunto de datos.

---

## ¿Qué es un Outlier?

Un outlier es una observación que se encuentra significativamente alejada del comportamiento general del resto de los datos.

En términos prácticos, son registros que presentan valores excepcionalmente altos o bajos respecto a la distribución principal.

### Ejemplo

```text
20, 22, 25, 27, 29, 31, 34, 500
```

En este caso:

```text
500
```

es claramente un valor atípico respecto al resto de observaciones.

---

## ¿Por Qué Aparecen los Outliers?

La presencia de outliers puede deberse a diferentes causas.

### 1. Errores de Entrada o Captura de Datos

Son errores introducidos durante el registro manual de la información.

### Ejemplo

```text
Edad real: 35
Edad registrada: 350
```

Este tipo de errores suelen requerir corrección o eliminación.

---

### 2. Errores de Medición

Pueden producirse debido a:

- Sensores defectuosos.
- Equipos mal calibrados.
- Fallos de comunicación.
- Problemas en sistemas automáticos.

### Ejemplo

Un sensor de temperatura registra:

```text
250 °C
```

cuando el rango normal oscila entre:

```text
15 °C y 35 °C
```

---

### 3. Variabilidad Natural

No todos los outliers son errores.

Algunos representan eventos legítimos poco frecuentes.

### Ejemplos

- Clientes VIP.
- Compras extraordinarias.
- Ingresos muy elevados.
- Casos médicos excepcionales.

En estos casos eliminar el dato podría significar perder información valiosa.

---

# Impacto de los Outliers

Los valores atípicos pueden influir significativamente sobre múltiples métricas estadísticas.

---

## Media

La media es especialmente sensible a los outliers.

### Ejemplo

```text
20, 25, 30, 35, 40
```

Media:

```text
30
```

Si añadimos:

```text
500
```

La media pasa a ser:

```text
108.3
```

aunque la mayoría de observaciones siguen concentradas entre 20 y 40.

---

## Desviación Estándar

Los outliers aumentan artificialmente la dispersión del conjunto de datos.

Esto puede generar interpretaciones incorrectas sobre la variabilidad real de la población.

---

## Correlaciones

Los coeficientes de correlación pueden verse alterados significativamente por unos pocos valores extremos.

Esto afecta directamente a:

- Matrices de correlación.
- Modelos predictivos.
- Análisis bivariados.

---

## Modelos de Machine Learning

Muchos algoritmos son sensibles a los valores extremos.

Entre ellos:

- Regresión lineal.
- K-Means.
- Redes neuronales.

Por ello es habitual analizar los outliers antes de entrenar modelos.

---

# Métodos para Detectar Outliers

Existen diferentes enfoques para identificar valores atípicos.

---

## 1. Método del Rango Intercuartílico (IQR)

Es uno de los métodos más utilizados en EDA debido a su robustez frente a distribuciones no normales.

Se basa en los cuartiles estudiados en estadística descriptiva.

### Paso 1: Calcular los cuartiles

- Q₁ = Percentil 25.
- Q₃ = Percentil 75.

### Paso 2: Calcular el IQR

\[
IQR = Q_3 - Q_1
\]

---

### Paso 3: Calcular los límites

Límite inferior:

\[
Q_1 - 1.5 \times IQR
\]

Límite superior:

\[
Q_3 + 1.5 \times IQR
\]

---

### Interpretación

Todo valor fuera de estos límites se considera un posible outlier.

---

### Ventajas

- Fácil de implementar.
- No requiere distribución normal.
- Muy utilizado en EDA.

---

## 2. Método de la Puntuación Z (Z-Score)

La puntuación Z mide cuántas desviaciones estándar separan una observación de la media.

### Fórmula

\[
Z=\frac{X-\mu}{\sigma}
\]

Donde:

- \(X\) = valor observado.
- \(\mu\) = media.
- \(\sigma\) = desviación estándar.

---

### Interpretación

Generalmente se considera outlier cuando:

\[
|Z| > 3
\]

Es decir, cuando el dato se encuentra a más de tres desviaciones estándar de la media.

---

### Ventajas

- Muy utilizado en estadística clásica.
- Fácil de interpretar.

---

### Limitaciones

- Supone distribuciones aproximadamente normales.
- Sensible a otros outliers existentes.

---

## 3. Inspección Visual

La visualización constituye una de las herramientas más potentes dentro del EDA.

---

### Boxplot

Permite detectar automáticamente valores alejados del rango principal.

```text
Caja → 50% central de los datos
Puntos aislados → Posibles outliers
```

---

### Scatterplot

Especialmente útil en análisis bivariados.

Permite detectar observaciones que se alejan claramente del patrón general.

---

# Métodos para Tratar Outliers

El tratamiento de un outlier nunca debe realizarse de forma automática.

Antes de actuar es necesario comprender su origen.

---

## 1. Eliminación (Trimming)

Consiste en eliminar completamente las observaciones atípicas.

### Cuándo utilizarla

- Error de captura.
- Error de medición.
- Valor imposible.

### Ejemplo

```text
Edad = 350 años
```

---

### Ventajas

- Elimina distorsiones.

### Riesgos

- Puede eliminar información valiosa.

---

## 2. Imputación

Consiste en sustituir el valor extremo por otro valor estimado.

### Opciones habituales

- Media.
- Mediana.
- Moda.
- Predicción mediante modelos.

---

### Ventajas

- Conserva el registro.
- Reduce la influencia del valor extremo.

---

## 3. Winsorización

La Winsorización limita los valores extremos sustituyéndolos por los límites máximos o mínimos aceptables.

### Ejemplo

Si el límite superior calculado mediante IQR es:

```text
120
```

Todo valor superior se sustituye por:

```text
120
```

---

### Ventajas

- Mantiene todas las observaciones.
- Reduce la influencia de extremos.

---

## 4. Mantener y Transformar

Cuando el outlier representa una situación real del negocio, suele conservarse.

En estos casos puede aplicarse una transformación matemática para reducir el efecto de la escala.

### Transformaciones habituales

- Logaritmo.
- Raíz cuadrada.
- Box-Cox.

---

### Ejemplo

Ingresos:

```text
1000
5000
50000
500000
```

Aplicando logaritmos:

```text
3
3.7
4.7
5.7
```

La distribución se vuelve más manejable.

---

# Aplicación Práctica en Python

## Detección Visual mediante Boxplot

```python
import seaborn as sns
import matplotlib.pyplot as plt

sns.boxplot(
    data=df,
    x="ingresos"
)

plt.title(
    "Detección Visual de Outliers"
)

plt.show()
```

---

## Detección Analítica mediante IQR

```python
Q1 = df["ingresos"].quantile(0.25)

Q3 = df["ingresos"].quantile(0.75)

IQR = Q3 - Q1

limite_inferior = Q1 - 1.5 * IQR

limite_superior = Q3 + 1.5 * IQR
```

---

## Identificación de Outliers

```python
outliers = df[
    (df["ingresos"] < limite_inferior)
    |
    (df["ingresos"] > limite_superior)
]

print(
    f"Cantidad de outliers: {len(outliers)}"
)
```

---

## Eliminación de Outliers

```python
df_limpio = df[
    (df["ingresos"] >= limite_inferior)
    &
    (df["ingresos"] <= limite_superior)
]
```

---

## Winsorización

```python
df["ingresos_winsorizados"] = (
    df["ingresos"]
    .clip(
        lower=limite_inferior,
        upper=limite_superior
    )
)
```

---

## Detección mediante Z-Score

```python
from scipy.stats import zscore

df["z_score"] = zscore(
    df["ingresos"]
)

outliers_z = df[
    abs(df["z_score"]) > 3
]
```

---

# Buenas Prácticas

Antes de eliminar un outlier conviene preguntarse:

1. ¿Es un error o un dato real?
2. ¿Aporta información relevante?
3. ¿Afecta significativamente al análisis?
4. ¿Qué impacto tendrá eliminarlo?

En muchos proyectos profesionales la mejor decisión no es eliminar el outlier, sino comprender por qué existe.

---

## Importancia de los Outliers en el EDA

El análisis de valores atípicos permite:

- Detectar errores de calidad.
- Comprender eventos excepcionales.
- Mejorar la precisión estadística.
- Optimizar modelos predictivos.
- Evitar conclusiones engañosas.

Por esta razón constituye una de las etapas más importantes del proceso exploratorio.

---

## Conclusiones

Los outliers son observaciones que se alejan significativamente del comportamiento general de un conjunto de datos.

Pueden surgir debido a errores de captura, errores de medición o variaciones reales del fenómeno estudiado.

Su identificación mediante técnicas como el IQR, el Z-Score o la inspección visual permite mejorar la calidad del análisis y reducir distorsiones estadísticas.

No existe una única estrategia de tratamiento. La decisión entre eliminar, imputar, winsorizar o conservar un valor atípico debe basarse en el contexto del problema y en el conocimiento del dominio de negocio.

---

## Fuentes Consultadas

### Documentación Institucional

**Gobierno de España – Datos.gob.es**

*Guía práctica de introducción al Análisis Exploratorio de Datos (2021)*

https://datos.gob.es/sites/default/files/doc/file/analisis_exploratorio_de_datos_2021.pdf

### Documentación Oficial

- Pandas — https://pandas.pydata.org/docs/
- SciPy — https://docs.scipy.org/doc/scipy/
- Seaborn — https://seaborn.pydata.org/

### Bibliografía Académica

**Tukey, J. W. (1977)**  
*Exploratory Data Analysis.*  
Addison-Wesley.

**Montgomery, D. C. & Runger, G. C. (2018)**  
*Applied Statistics and Probability for Engineers.*  
Wiley.