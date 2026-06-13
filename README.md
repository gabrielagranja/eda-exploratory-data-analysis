# 📊 Análisis Exploratorio de Datos (EDA)

![Python](https://img.shields.io/badge/Python-3.13-blue?logo=python)
![Pandas](https://img.shields.io/badge/Pandas-Análisis%20de%20Datos-150458?logo=pandas)
![NumPy](https://img.shields.io/badge/NumPy-Cálculo%20Numérico-013243?logo=numpy)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualización-orange)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualización%20Estadística-4C72B0)
![SciPy](https://img.shields.io/badge/SciPy-Cómputo%20Científico-8CAAE6?logo=scipy)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-Machine%20Learning-F7931E?logo=scikitlearn)
![Estado](https://img.shields.io/badge/Estado-En%20Desarrollo-yellow)

Introducción teórica y aplicación práctica del **Análisis Exploratorio de Datos (EDA)** utilizando Python y las principales librerías del ecosistema de Ciencia de Datos.

---

## 🎯 Descripción del Proyecto

Este repositorio contiene tanto la investigación teórica como la implementación práctica de un proceso de **Exploratory Data Analysis (EDA)** desarrollado dentro de un programa de formación en Data Analytics.

El objetivo es comprender cómo inspeccionar, limpiar, visualizar y analizar datos antes de aplicar modelos estadísticos o algoritmos de Machine Learning.

El proyecto se divide en dos grandes bloques:

- **Parte 1 – Investigación Teórica**
- **Parte 2 – Implementación Práctica**

---

## 📚 Contenido

### Parte 1 – Investigación Teórica

- [01. ¿Qué es el EDA y cuál es su propósito?](docs/01_what_is_eda.md)
- [02. Tipos de datos en un EDA](docs/02_data_types.md)
- [03. Análisis univariado, bivariado y multivariado](docs/03_analysis_types.md)
- [04. Estadística descriptiva](docs/04_descriptive_statistics.md)
- [05. Limpieza de datos](docs/05_data_cleaning.md)
- [06. Pandas, Matplotlib y Seaborn](docs/06_python_libraries.md)
- [07. Matriz de correlación](docs/07_correlation_matrix.md)
- [08. Detección y tratamiento de outliers](docs/08_outliers.md)
- [09. Hypothesis Testing](docs/09_hypothesis_testing.md)

### Parte 2 – Implementación Práctica

- Inspección del dataset
- Limpieza de datos
- Estadística descriptiva
- Visualización de datos
- Correlaciones
- Detección de outliers
- Conclusiones

---

## 🗂️ Estructura del Repositorio

```text
EDA-Exploratory-Data-Analysis/
│
├── README.md
│
├── docs/
│   ├── 01_what_is_eda.md
│   ├── 02_data_types.md
│   ├── 03_analysis_types.md
│   ├── 04_descriptive_statistics.md
│   ├── 05_data_cleaning.md
│   ├── 06_python_libraries.md
│   ├── 07_correlation_matrix.md
│   ├── 08_outliers.md
│   └── 09_hypothesis_testing.md
│
├── notebooks/
│   └── EDA_Practica.ipynb
│
├── data/
│
├── images/
│
├── requirements.txt
│
└── .gitignore
```

---

## 🛠️ Tecnologías Utilizadas

### Lenguaje de Programación

- Python 3

### Librerías Principales

- Pandas
- NumPy
- Matplotlib
- Seaborn
- SciPy
- KaggelHub
- Jupyter Notebook

---

## 📖 Parte 1 – Investigación Teórica

La parte teórica desarrolla los fundamentos del Análisis Exploratorio de Datos, proporcionando la base conceptual necesaria para comprender y preparar conjuntos de datos antes de realizar cualquier análisis avanzado.

### Temas desarrollados

- Fundamentos del EDA
- Tipos de datos y escalas de medición
- Análisis univariado, bivariado y multivariado
- Estadística descriptiva
- Limpieza y preparación de datos
- Visualización de datos
- Correlación entre variables
- Detección y tratamiento de outliers
- Pruebas de hipótesis

Toda la documentación se encuentra organizada dentro de la carpeta `docs`.

---

## 💻 Parte 2 – Implementación Práctica

La parte práctica aplica los conceptos estudiados durante la investigación teórica mediante un flujo completo de trabajo de EDA utilizando Python.

### Flujo de trabajo

- Carga del dataset
- Exploración inicial
- Identificación de valores nulos
- Limpieza de datos
- Estadística descriptiva
- Visualización de datos
- Matriz de correlación
- Detección de outliers
- Conclusiones finales

La práctica se desarrolló utilizando el dataset **Titanic**, con el objetivo de identificar los factores que influyeron en la supervivencia de los pasajeros.

## Objetivos del análisis

Responder a las siguientes preguntas:

1. ¿Quiénes tuvieron más probabilidad de sobrevivir?
2. ¿Qué factores fueron más importantes?
3. ¿Existió algún patrón relevante en los datos?

---

## 📈 Resultados obtenidos

### Tasa de supervivencia general

- Supervivencia total: **40.45%**

### Supervivencia por sexo

| Sexo | Tasa de supervivencia |
|--------|--------:|
| Mujeres | 75.29% |
| Hombres | 20.53% |

**Conclusión:** Las mujeres tuvieron una probabilidad de supervivencia significativamente superior a la de los hombres.

---

### Supervivencia por clase social

| Clase | Tasa de supervivencia |
|--------|--------:|
| Primera clase | 65.22% |
| Segunda clase | 47.98% |
| Tercera clase | 23.94% |

**Conclusión:** Los pasajeros de primera clase tuvieron una probabilidad de supervivencia considerablemente mayor.

---

### Supervivencia por edad

| Grupo | Tasa de supervivencia |
|--------|--------:|
| Niños | 53.98% |
| Adultos | 37.90% |

Edad promedio:

- Supervivientes: **28.19 años**
- No supervivientes: **30.63 años**

**Conclusión:** Los niños mostraron una mayor tasa de supervivencia que los adultos.

---

### Supervivencia según viajaba solo o acompañado

| Situación | Tasa de supervivencia |
|------------|--------:|
| Acompañado | 51.61% |
| Solo | 31.84% |

**Conclusión:** Viajar acompañado parece haber incrementado las probabilidades de supervivencia.

---

### Influencia del precio del billete

| Estado | Precio medio |
|---------|--------:|
| No supervivientes | 22.97 |
| Supervivientes | 51.65 |

**Conclusión:** Los pasajeros que sobrevivieron pagaron, en promedio, tarifas más elevadas, lo que sugiere una relación entre nivel socioeconómico y supervivencia.

---

## 🎯 Conclusiones finales

El análisis exploratorio realizado muestra que la supervivencia de los pasajeros del Titanic no fue aleatoria.

Los factores con mayor influencia fueron:

- Sexo.
- Clase social.
- Edad.
- Tamaño de la unidad familiar o acompañamiento durante el viaje.

Los resultados muestran que:

- Las mujeres tuvieron una tasa de supervivencia muy superior a la de los hombres.
- Los pasajeros de primera clase sobrevivieron con mayor frecuencia que los de tercera clase.
- Los niños presentaron mejores tasas de supervivencia que los adultos.
- Los pasajeros que viajaban acompañados sobrevivieron más que quienes viajaban solos.
- Los supervivientes pagaron tarifas significativamente más elevadas.

---

# 📓 Notebook

El desarrollo completo de la práctica puede consultarse en:

```text
notebooks/titanic_eda.ipynb
```

---

# 🧠 Aprendizajes Clave

El Análisis Exploratorio de Datos constituye una de las fases más importantes de cualquier proyecto basado en datos.

Antes de construir modelos predictivos o aplicar algoritmos de Machine Learning es imprescindible comprender:

- La estructura del dataset.
- La calidad de los datos.
- Las relaciones entre variables.
- La presencia de valores atípicos.
- Los patrones que pueden influir en los resultados.


---


## 📚 Fuentes Consultadas

### Documentación Institucional

**Gobierno de España – Datos.gob.es**

*Guía práctica de introducción al Análisis Exploratorio de Datos (2021)*

https://datos.gob.es/sites/default/files/doc/file/analisis_exploratorio_de_datos_2021.pdf

### Documentación Oficial

- Python — https://docs.python.org/
- Pandas — https://pandas.pydata.org/docs/
- NumPy — https://numpy.org/doc/
- Matplotlib — https://matplotlib.org/stable/
- Seaborn — https://seaborn.pydata.org/
- SciPy — https://docs.scipy.org/doc/scipy/
- Scikit-Learn — https://scikit-learn.org/stable/

### Bibliografía Académica

**Tukey, J. W. (1977)**  
*Exploratory Data Analysis.*  
Addison-Wesley.

**Wickham, H. & Grolemund, G. (2017)**  
*R for Data Science.*  
O'Reilly Media.

**James, G., Witten, D., Hastie, T. & Tibshirani, R. (2021)**  
*An Introduction to Statistical Learning.*  
Springer.

**Montgomery, D. C. & Runger, G. C. (2018)**  
*Applied Statistics and Probability for Engineers.*  
Wiley.

---

## 👩‍💻 Autor

**Gabriela Granja**

Business, Marketing & AI

Bootcamp de Data Analytics | Proyecto de Análisis Exploratorio de Datos
