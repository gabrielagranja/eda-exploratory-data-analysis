# Tipos de Datos en un EDA

## Introducción

# Tipos de Datos en un EDA

## Introducción

Uno de los primeros pasos de cualquier Análisis Exploratorio de Datos (EDA) consiste en identificar correctamente los tipos de datos presentes en el conjunto de datos.

La clasificación adecuada de las variables es fundamental porque determina:

- Qué operaciones matemáticas son válidas.
- Qué métricas estadísticas pueden utilizarse.
- Qué visualizaciones son apropiadas.
- Qué algoritmos de Machine Learning pueden aplicarse.

Una interpretación incorrecta del tipo de dato puede conducir a conclusiones erróneas o a la aplicación de técnicas estadísticas inadecuadas.

---

## Clasificación General de los Datos

En estadística, los datos se clasifican según su escala de medición.

```text
                  ┌── Nominales (Categorías sin orden)
   ┌── Categóricos┼── Ordinales (Categorías con orden)
   │ (Cualitativos)└── Binarios (Solo dos opciones)
Datos
   │              ┌── Discretos (Conteos, números enteros)
   └── Numéricos ─┼── Continuos (Mediciones, decimales)
    (Cuantitativos)└── De Tipo Fecha/Tiempo (Instantes temporales)
```

Esta clasificación permite comprender la naturaleza de cada variable y seleccionar las técnicas de análisis adecuadas.

---

## 1. Datos Categóricos (Cualitativos)

Los datos categóricos describen cualidades, atributos o categorías.

No representan cantidades numéricas medibles, sino características que permiten clasificar observaciones.

### Datos Nominales

Son categorías mutuamente excluyentes que no poseen un orden lógico o jerarquía.

#### Ejemplos

- Estado civil.
- Nacionalidad.
- Color favorito.
- Ciudad de residencia.

```text
Soltero
Casado
Divorciado
Viudo
```

No tiene sentido afirmar que una categoría es "mayor" o "menor" que otra.

---

### Datos Ordinales

Son categorías que presentan una jerarquía o secuencia lógica.

Sin embargo, la distancia entre categorías no es cuantificable.

#### Ejemplos

- Nivel educativo.
- Grado de satisfacción.
- Nivel de prioridad.

```text
Bajo
Medio
Alto
```

Aunque existe un orden, no puede afirmarse que la diferencia entre "Bajo" y "Medio" sea igual a la diferencia entre "Medio" y "Alto".

---

### Datos Binarios o Dicotómicos

Son un caso particular de variable categórica que solo admite dos estados posibles.

#### Ejemplos

- Sí / No
- Verdadero / Falso
- Aprobado / Suspendido
- Pagado / Pendiente

```text
0 = No
1 = Sí
```

Son muy comunes en modelos de clasificación.

---

## 2. Datos Numéricos (Cuantitativos)

Los datos numéricos representan cantidades medibles.

Permiten realizar operaciones matemáticas como:

- Suma.
- Resta.
- Multiplicación.
- División.
- Promedios.

---

### Datos Discretos

Provienen de procesos de conteo.

Solo pueden tomar valores enteros específicos.

#### Ejemplos

- Número de hijos.
- Número de clientes.
- Número de pedidos.
- Número de incidencias.

```text
0
1
2
3
4
...
```

No tendría sentido obtener valores intermedios como 2.5 hijos.

---

### Datos Continuos

Provienen de procesos de medición.

Pueden tomar infinitos valores dentro de un rango.

#### Ejemplos

- Altura.
- Peso.
- Temperatura.
- Tiempo.

```text
72.5 kg
36.7 °C
1.78 m
```

Los decimales tienen significado real.

---

## 3. Datos de Fecha y Tiempo (Temporales)

Representan momentos específicos o intervalos temporales.

Aunque técnicamente suelen almacenarse como fechas, poseen características analíticas propias.

#### Ejemplos

- Fecha de compra.
- Fecha de registro.
- Hora de conexión.
- Fecha de envío.

```text
2025-01-15
2026-06-13 14:30:00
```

Este tipo de dato resulta fundamental para:

- Análisis de tendencias.
- Series temporales.
- Estacionalidad.
- Predicción temporal.

---

## Aplicación Práctica en Python

Pandas permite identificar automáticamente los tipos de datos de un DataFrame.

```python
import pandas as pd

df = pd.read_csv("datos.csv")

print(df.dtypes)
```

Salida de ejemplo:

```text
edad                 int64
ingresos           float64
genero             object
fecha_registro     datetime64
```

---

### Conversión de Tipos

En ocasiones los datos se cargan incorrectamente y es necesario convertirlos.

```python
# Convertir texto a número
df["edad"] = pd.to_numeric(df["edad"])

# Convertir texto a fecha
df["fecha_registro"] = pd.to_datetime(df["fecha_registro"])

# Convertir texto a categoría
df["genero"] = df["genero"].astype("category")
```

---

## Importancia de Identificar Correctamente los Tipos de Datos

Reconocer correctamente cada tipo de variable permite:

- Seleccionar gráficos adecuados.
- Aplicar estadísticas correctas.
- Detectar errores de calidad.
- Preparar datos para Machine Learning.
- Optimizar el rendimiento del análisis.

Por ejemplo:

| Tipo de dato | Gráfico recomendado |
|-------------|-------------------|
| Nominal | Barras |
| Ordinal | Barras ordenadas |
| Numérico continuo | Histograma |
| Numérico discreto | Barras |
| Temporal | Serie temporal |

---

## Conclusiones

La clasificación de los datos constituye una de las primeras tareas dentro de cualquier proceso de EDA.

Comprender la naturaleza de las variables permite seleccionar correctamente las técnicas estadísticas, los métodos de visualización y los algoritmos de análisis más adecuados.

Una correcta identificación de los tipos de datos facilita la comprensión del conjunto de datos y mejora significativamente la calidad de los análisis posteriores.

---

## Fuentes Consultadas

- Guía práctica de introducción al Análisis Exploratorio de Datos (Datos.gob.es, 2021)
- Pandas Documentation
- Tukey, J. W. (1977). Exploratory Data Analysis.