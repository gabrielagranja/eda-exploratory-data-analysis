# Limpieza de Datos (Data Cleaning)

## Introducción

La limpieza de datos (*Data Cleaning*) es una de las etapas más importantes dentro del Análisis Exploratorio de Datos (EDA). Consiste en identificar, corregir o eliminar datos incompletos, incorrectos, inconsistentes o irrelevantes que puedan afectar la calidad del análisis.

En proyectos reales, los datos rara vez llegan en un estado perfecto. Es habitual encontrar registros duplicados, valores nulos, errores tipográficos, formatos inconsistentes o valores extremos que pueden distorsionar las conclusiones.

Por este motivo, la limpieza de datos constituye una fase crítica antes de realizar análisis estadísticos avanzados o entrenar modelos de Machine Learning.

---

## ¿Qué es la Limpieza de Datos?

La limpieza de datos es el proceso estadístico y técnico de identificar, corregir o eliminar datos corruptos, incorrectos, duplicados, incompletos o con formatos erróneos dentro de un conjunto de datos.

Su objetivo principal no es únicamente "ordenar" la información, sino garantizar la calidad del dato para que los análisis posteriores generen resultados fiables y representativos.

Una limpieza deficiente puede provocar:

- Conclusiones incorrectas.
- Sesgos en el análisis.
- Predicciones erróneas.
- Problemas de rendimiento en los algoritmos.
- Pérdida de confianza en los resultados.

---

# Principales Tareas de la Limpieza de Datos

## 1. Manejo de Valores Nulos (Missing Data)

Los valores nulos representan información ausente dentro del conjunto de datos.

Pueden aparecer como:

```text
NaN
None
Null
Vacío
```

### ¿Por qué aparecen?

- Errores durante la recolección de datos.
- Formularios incompletos.
- Fallos en sensores.
- Integraciones defectuosas entre sistemas.

### Ejemplo

| Nombre | Edad |
|----------|----------|
| Ana | 25 |
| Juan | NULL |
| Marta | 31 |

---

### Estrategias de tratamiento

#### Eliminación

Consiste en eliminar las filas o columnas afectadas.

Se recomienda cuando:

- El porcentaje de nulos es muy bajo.
- La información faltante no es relevante.

#### Imputación

Consiste en sustituir los valores faltantes por valores estimados.

Las técnicas más habituales son:

- Media.
- Mediana.
- Moda.
- Modelos predictivos.

---

## 2. Detección y Eliminación de Duplicados

Los registros duplicados aparecen cuando una misma observación se almacena más de una vez.

### Ejemplo

| Cliente | Compra |
|----------|----------|
| 101 | 500 |
| 101 | 500 |

---

### Problemas que generan

- Inflan estadísticas.
- Distorsionan promedios.
- Alteran distribuciones.
- Incrementan el tamaño del dataset innecesariamente.

Por norma general, los duplicados exactos deben eliminarse.

---

## 3. Errores de Formato y Consistencia

Una misma información puede registrarse de múltiples maneras.

### Ejemplo

```text
España
españa
ESPAÑA
España
Spain
```

Aunque representan el mismo concepto, para un ordenador son valores diferentes.

---

### Problemas asociados

- Incremento artificial de categorías.
- Resultados incorrectos en agrupaciones.
- Errores en análisis estadísticos.

---

### Soluciones habituales

- Convertir texto a minúsculas.
- Eliminar espacios innecesarios.
- Homogeneizar formatos.
- Corregir errores tipográficos.

---

## 4. Conversión de Tipos de Datos

Frecuentemente los datos se importan con tipos incorrectos.

### Ejemplo

Una columna de edades puede cargarse como:

```text
"25"
"31"
"40"
```

en lugar de:

```text
25
31
40
```

---

### Consecuencias

- Imposibilidad de realizar cálculos.
- Errores estadísticos.
- Problemas en visualizaciones.

---

### Casos habituales

#### Texto → Numérico

```text
"1500"
```

↓

```text
1500
```

---

#### Texto → Fecha

```text
"2025-01-15"
```

↓

```text
2025-01-15 00:00:00
```

---

#### Texto → Categoría

```text
Masculino
Femenino
```

↓

```text
Categorical
```

---

## 5. Tratamiento de Outliers

Los outliers son valores que se alejan significativamente del comportamiento general del conjunto de datos.

### Ejemplo

```text
20
22
25
28
30
500
```

El valor:

```text
500
```

es claramente anómalo respecto al resto.

---

### Posibles causas

#### Error de captura

```text
500
```

en lugar de:

```text
50
```

---

#### Error de medición

Fallos en sensores o sistemas automáticos.

---

#### Variabilidad real

Casos excepcionales pero legítimos.

Por ejemplo:

- Clientes VIP.
- Compras extraordinarias.
- Ingresos extremadamente altos.

---

### Opciones de tratamiento

#### Eliminación

Cuando el valor es claramente incorrecto.

#### Imputación

Sustituir por un valor estimado.

#### Winsorización

Limitar los valores extremos.

#### Conservación

Cuando representan información real y valiosa.

---

# Escalamiento de Datos

Cuando las variables poseen escalas muy diferentes, algunos algoritmos pueden verse afectados.

### Ejemplo

| Variable | Rango |
|----------|----------|
| Edad | 18 - 80 |
| Salario | 1.000 - 200.000 |

El salario domina matemáticamente a la edad debido a su magnitud.

Para evitarlo se aplican técnicas de escalamiento.

---

## Normalización (Min-Max Scaling)

Transforma todos los valores a un rango fijo, generalmente entre 0 y 1.

### Fórmula

\[
Valor_{Normalizado}=
\frac{X-X_{min}}
{X_{max}-X_{min}}
\]

### Ventajas

- Escala uniforme.
- Fácil interpretación.

### Limitaciones

- Sensible a outliers.

---

## Estandarización (Z-Score Scaling)

Transforma los datos para que tengan:

```text
Media = 0
Desviación Estándar = 1
```

### Fórmula

\[
Valor_{Estandarizado}
=
\frac{X-\mu}
{\sigma}
\]

Donde:

- \(\mu\) = media.
- \(\sigma\) = desviación estándar.

### Ventajas

- Muy utilizada en Machine Learning.
- Más robusta frente a distribuciones complejas.

---

# Aplicación Práctica en Python

## Identificación de Valores Nulos

```python
import pandas as pd

df = pd.read_csv("datos.csv")

print(df.isnull().sum())
```

---

## Eliminación de Valores Nulos

```python
df_sin_nulos = df.dropna()
```

---

## Imputación con la Mediana

```python
df["ingresos"] = df["ingresos"].fillna(
    df["ingresos"].median()
)
```

---

## Imputación con la Moda

```python
df["ciudad"] = df["ciudad"].fillna(
    df["ciudad"].mode()[0]
)
```

---

## Identificación de Duplicados

```python
print(df.duplicated().sum())
```

---

## Eliminación de Duplicados

```python
df = df.drop_duplicates()
```

---

## Limpieza de Texto

```python
df["pais"] = (
    df["pais"]
    .str.strip()
    .str.lower()
)
```

---

## Conversión de Tipos

```python
df["edad"] = pd.to_numeric(
    df["edad"],
    errors="coerce"
)

df["fecha_registro"] = pd.to_datetime(
    df["fecha_registro"]
)
```

---

## Winsorización mediante IQR

```python
Q1 = df["ingresos"].quantile(0.25)
Q3 = df["ingresos"].quantile(0.75)

IQR = Q3 - Q1

limite_superior = Q3 + 1.5 * IQR
limite_inferior = Q1 - 1.5 * IQR

df["ingresos"] = df["ingresos"].clip(
    lower=limite_inferior,
    upper=limite_superior
)
```

---

## Normalización

```python
from sklearn.preprocessing import MinMaxScaler

scaler = MinMaxScaler()

df["edad_normalizada"] = scaler.fit_transform(
    df[["edad"]]
)
```

---

## Estandarización

```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()

df["ingresos_estandarizados"] = scaler.fit_transform(
    df[["ingresos"]]
)
```

---

# Beneficios de la Limpieza de Datos

Una adecuada limpieza de datos proporciona múltiples ventajas:

- Mayor precisión en el análisis.
- Reducción de errores estadísticos.
- Mejora de la calidad de los modelos predictivos.
- Mayor velocidad de procesamiento.
- Resultados más fiables y reproducibles.

En proyectos profesionales, una parte significativa del tiempo suele dedicarse a esta etapa debido a su impacto directo en la calidad final del análisis.

---

## Conclusiones

La limpieza de datos constituye una fase esencial dentro del Análisis Exploratorio de Datos.

Su objetivo es garantizar que la información utilizada sea consistente, completa y adecuada para el análisis.

El tratamiento de valores nulos, duplicados, errores de formato, tipos de datos incorrectos y outliers permite mejorar significativamente la calidad de los resultados obtenidos.

Además, técnicas como la normalización y la estandarización facilitan la aplicación de algoritmos de Machine Learning y modelos estadísticos avanzados.

Una limpieza adecuada no solo mejora la calidad del análisis, sino que aumenta la fiabilidad de cualquier decisión basada en datos.

---

## Fuentes Consultadas

### Documentación Institucional

**Gobierno de España – Datos.gob.es**

*Guía práctica de introducción al Análisis Exploratorio de Datos (2021)*

https://datos.gob.es/sites/default/files/doc/file/analisis_exploratorio_de_datos_2021.pdf

### Documentación Oficial

- Pandas — https://pandas.pydata.org/docs/
- Scikit-Learn — https://scikit-learn.org/stable/

### Bibliografía Académica

**Tukey, J. W. (1977)**  
*Exploratory Data Analysis.*  
Addison-Wesley.

**James, G., Witten, D., Hastie, T. & Tibshirani, R. (2021)**  
*An Introduction to Statistical Learning.*  
Springer.