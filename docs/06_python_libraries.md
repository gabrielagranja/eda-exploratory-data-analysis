# Pandas, Matplotlib y Seaborn en el Análisis Exploratorio de Datos

## Introducción

El Análisis Exploratorio de Datos (EDA) combina técnicas estadísticas con herramientas de programación que permiten inspeccionar, transformar y visualizar la información de manera eficiente.

Dentro del ecosistema de Python, tres de las librerías más utilizadas para realizar EDA son:

- **Pandas**
- **Matplotlib**
- **Seaborn**

Estas herramientas cumplen funciones diferentes pero complementarias. Juntas permiten cargar datos, limpiarlos, analizarlos estadísticamente y representarlos gráficamente para facilitar su interpretación.

Su uso conjunto constituye uno de los flujos de trabajo más habituales en proyectos de Ciencia de Datos, Business Intelligence y Machine Learning.

---

## El Rol de Cada Librería en un EDA

Aunque suelen utilizarse juntas, cada librería tiene una función específica dentro del proceso de análisis.

### Resumen General

| Librería | Función Principal |
|----------|----------|
| Pandas | Manipulación y análisis de datos |
| Matplotlib | Construcción de gráficos |
| Seaborn | Visualización estadística avanzada |

De forma resumida:

> Pandas maneja y prepara los datos; Matplotlib construye los gráficos; y Seaborn facilita la creación de visualizaciones estadísticas de alta calidad.

---

# 1. Pandas

## ¿Qué es Pandas?

Pandas es una librería de código abierto especializada en manipulación y análisis de datos estructurados.

Su principal estructura de datos es el **DataFrame**, una tabla bidimensional similar a una hoja de cálculo o una tabla de base de datos.

Permite:

- Leer archivos.
- Limpiar datos.
- Filtrar registros.
- Agrupar información.
- Calcular estadísticas.
- Preparar datos para análisis posteriores.

---

## ¿Por qué es importante en el EDA?

Prácticamente todas las tareas iniciales del análisis exploratorio se realizan con Pandas.

Entre ellas:

- Carga de datasets.
- Inspección de variables.
- Gestión de valores nulos.
- Eliminación de duplicados.
- Conversión de tipos de datos.
- Estadística descriptiva.

---

## Ejemplo de uso

```python
import pandas as pd

df = pd.read_csv("datos.csv")

print(df.head())

print(df.info())

print(df.describe())
```

---

## Visualización rápida con Pandas

Aunque Pandas no es una librería de gráficos propiamente dicha, incorpora funciones de visualización basadas en Matplotlib.

```python
df["edad"].hist()
```

Este tipo de visualización es útil para inspecciones rápidas durante la fase de limpieza y exploración.

---

# 2. Matplotlib

## ¿Qué es Matplotlib?

Matplotlib es la librería de visualización más utilizada en Python.

Proporciona las herramientas básicas para construir gráficos personalizados.

Es considerada la librería madre sobre la que se apoyan muchas otras herramientas de visualización, incluida Seaborn.

---

## ¿Por qué es importante en el EDA?

Permite representar visualmente los datos para detectar:

- Tendencias.
- Distribuciones.
- Valores atípicos.
- Relaciones entre variables.

Además proporciona control absoluto sobre:

- Títulos.
- Etiquetas.
- Escalas.
- Colores.
- Diseño general del gráfico.

---

## Ejemplo de uso

```python
import matplotlib.pyplot as plt

plt.figure(figsize=(8, 4))

plt.title("Distribución de Edades")

plt.xlabel("Edad")

plt.ylabel("Frecuencia")

plt.grid(True)

plt.show()
```

---

## Ventajas

- Gran capacidad de personalización.
- Amplia variedad de gráficos.
- Base de numerosas librerías de visualización.

---

## Limitaciones

- Requiere más código que otras librerías.
- Algunas visualizaciones complejas resultan menos intuitivas.

---

# 3. Seaborn

## ¿Qué es Seaborn?

Seaborn es una librería de visualización estadística construida sobre Matplotlib.

Su objetivo es simplificar la creación de gráficos avanzados y mejorar la estética visual de las representaciones.

Está diseñada para trabajar directamente con DataFrames de Pandas.

---

## ¿Por qué es importante en el EDA?

Automatiza tareas que con Matplotlib requerirían múltiples líneas de código.

Facilita:

- Comparaciones entre grupos.
- Análisis de distribuciones.
- Visualización de correlaciones.
- Análisis multivariados.

---

## Ejemplo de uso

```python
import seaborn as sns

sns.scatterplot(
    data=df,
    x="edad",
    y="ingresos"
)
```

Con una sola línea se genera un gráfico estadístico completo.

---

## Ventajas

- Menor cantidad de código.
- Integración nativa con Pandas.
- Gráficos más atractivos por defecto.
- Enfoque estadístico.

---

## Limitaciones

- Menor control detallado que Matplotlib.
- Algunas personalizaciones avanzadas requieren acceder a Matplotlib.

---

# Analogía: Construcción de una Casa

Una forma sencilla de comprender cómo interactúan estas librerías consiste en compararlas con la construcción de una vivienda.

### Pandas → Los materiales y los cimientos

Se encarga de traer los datos, organizarlos y prepararlos para su uso.

Sin Pandas no existiría la información sobre la que trabajar.

---

### Matplotlib → La estructura y las herramientas

Proporciona el lienzo, los ejes y todos los elementos básicos necesarios para construir un gráfico.

Permite modificar cualquier detalle de forma manual.

---

### Seaborn → El arquitecto y diseñador

Construye gráficos complejos utilizando la infraestructura de Matplotlib y los datos preparados por Pandas.

Automatiza gran parte del trabajo visual y proporciona mejores resultados con menos código.

---

# Cómo Trabajan Juntas en un EDA

En proyectos reales rara vez se utilizan de forma aislada.

Lo habitual es combinar las tres herramientas dentro de un mismo flujo de trabajo.

## Flujo General

```text
Dataset
   │
   ▼
Pandas
(Carga y limpieza)
   │
   ▼
Matplotlib
(Lienzo y configuración)
   │
   ▼
Seaborn
(Visualización estadística)
   │
   ▼
Interpretación
```

---

## Ejemplo Completo Integrado

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# 1. Cargar datos con Pandas
df = pd.read_csv("datos.csv")

# 2. Filtrar registros
df_filtrado = df[df["edad"] > 18]

# 3. Crear figura con Matplotlib
fig, ax = plt.subplots(figsize=(10, 6))

# 4. Generar gráfico con Seaborn
sns.boxplot(
    data=df_filtrado,
    x="categoria",
    y="ingresos",
    hue="genero",
    ax=ax
)

# 5. Personalización con Matplotlib
ax.set_title(
    "Distribución de Ingresos por Categoría y Género"
)

ax.set_xlabel("Categoría")

ax.set_ylabel("Ingresos")

# 6. Mostrar gráfico
plt.show()
```

---

# Importancia de Estas Librerías en el EDA

La combinación de Pandas, Matplotlib y Seaborn permite cubrir prácticamente todas las necesidades de un análisis exploratorio:

| Necesidad | Librería Principal |
|------------|------------|
| Carga de datos | Pandas |
| Limpieza de datos | Pandas |
| Estadística descriptiva | Pandas |
| Gráficos básicos | Matplotlib |
| Visualización estadística | Seaborn |
| Correlaciones | Seaborn |
| Análisis multivariado | Seaborn |

Por esta razón constituyen una parte esencial del ecosistema de Ciencia de Datos en Python.

---

## Conclusiones

Pandas, Matplotlib y Seaborn desempeñan funciones complementarias dentro del Análisis Exploratorio de Datos.

Pandas proporciona las herramientas necesarias para cargar, limpiar y analizar los datos. Matplotlib ofrece la infraestructura de visualización y el control detallado de los gráficos. Seaborn simplifica la creación de representaciones estadísticas avanzadas y mejora la calidad visual de los resultados.

El uso combinado de estas librerías permite desarrollar procesos completos de EDA de manera eficiente, facilitando la comprensión de los datos y la generación de conocimiento útil para la toma de decisiones.

---

## Fuentes Consultadas

### Documentación Oficial

- Python — https://docs.python.org/
- Pandas — https://pandas.pydata.org/docs/
- Matplotlib — https://matplotlib.org/stable/
- Seaborn — https://seaborn.pydata.org/

### Bibliografía Académica

**Tukey, J. W. (1977)**  
*Exploratory Data Analysis.*  
Addison-Wesley.

### Documentación Institucional

**Gobierno de España – Datos.gob.es**

*Guía práctica de introducción al Análisis Exploratorio de Datos (2021)*

https://datos.gob.es/sites/default/files/doc/file/analisis_exploratorio_de_datos_2021.pdf