# 🚕 Análisis de viajes en taxi en Chicago

## 📌 Descripción del proyecto

Este proyecto tiene como objetivo analizar los patrones de uso de servicios de taxi en la ciudad de Chicago durante noviembre de 2017. Para ello, se utilizarán tres conjuntos de datos provenientes de consultas SQL previas, que han sido proporcionados en formato CSV. Se buscará comprender qué empresas y barrios presentan mayor actividad y si las condiciones climáticas influyen en la duración de los viajes.

El proyecto incluye dos etapas principales: análisis exploratorio de datos y prueba de hipótesis.

---

## 🔍 Etapa 1: Análisis exploratorio de datos

Se analizarán dos archivos CSV:

- `/datasets/project_sql_result_01.csv`: contiene el número de viajes registrados por distintas compañías de taxis los días 15 y 16 de noviembre de 2017.
- `/datasets/project_sql_result_04.csv`: muestra el promedio de viajes que terminaron en cada barrio de Chicago durante todo noviembre de 2017.

El análisis incluye:
- Carga e inspección de los datos
- Validación de tipos de datos
- Identificación de los 10 barrios con más viajes finalizados
- Visualización de:
  - Empresas de taxi y cantidad de viajes
  - Barrios principales por promedio de finalizaciones

Se obtendrán conclusiones específicas a partir de los gráficos generados.

---

## 🧪 Etapa 2: Prueba de hipótesis

Se utilizará el archivo:

- `/datasets/project_sql_result_07.csv`: contiene registros de viajes realizados desde la zona Loop hasta el Aeropuerto Internacional O'Hare, incluyendo la hora de inicio, condiciones climáticas y duración del trayecto.

Se probará la siguiente hipótesis:

**“La duración promedio de los viajes desde el Loop hasta el Aeropuerto O’Hare cambia los sábados lluviosos.”**

Se establecerá un nivel de significación (alfa) y se explicarán:
- La formulación de las hipótesis nula y alternativa
- El criterio estadístico utilizado para validar la hipótesis
- Las conclusiones obtenidas

---

## 📝 Evaluación del proyecto

El proyecto será evaluado considerando:

- La correcta recuperación y carga de datos
- El uso adecuado de slicing, agrupaciones y combinaciones
- La formulación y prueba de hipótesis
- La calidad de las conclusiones
- Comentarios claros y explicativos en el código

---

# 🚕 Chicago Taxi Trip Analysis

## 📌 Project Description

This project aims to analyze taxi service usage patterns in the city of Chicago during November 2017. The analysis is based on three CSV datasets resulting from previous SQL queries. The goal is to identify which companies and neighborhoods show the highest activity, and whether weather conditions affect trip durations.

The project consists of two main stages: exploratory data analysis and hypothesis testing.

---

## 🔍 Stage 1: Exploratory Data Analysis

Two CSV files are analyzed:

- `/datasets/project_sql_result_01.csv`: number of trips recorded by various taxi companies on November 15 and 16, 2017.
- `/datasets/project_sql_result_04.csv`: average number of trips ending in each Chicago neighborhood throughout November 2017.

The analysis includes:
- Loading and inspecting the datasets
- Verifying data types
- Identifying the top 10 neighborhoods with the most trip drop-offs
- Visualizations:
  - Taxi companies and number of trips
  - Top neighborhoods by average drop-offs

Clear conclusions will be drawn from the visualizations.

---

## 🧪 Stage 2: Hypothesis Testing

Using the file:

- `/datasets/project_sql_result_07.csv`: includes trips from the Loop to O'Hare International Airport with start time, weather conditions, and trip duration in seconds.

We test the following hypothesis:

**“The average duration of trips from the Loop to O’Hare International Airport changes on rainy Saturdays.”**

The significance level (alpha) will be defined, and the following will be explained:
- Null and alternative hypotheses
- Statistical criteria used to test the hypothesis
- Conclusions obtained

---

## 📝 Project Evaluation

The project will be evaluated based on:

- Proper data retrieval and loading
- Correct use of slicing, grouping, and merging
- Hypothesis formulation and testing
- Clarity and relevance of conclusions
- Clear and helpful comments throughout the code

