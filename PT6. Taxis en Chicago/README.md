# 🚕 Análisis de viajes en taxi en Chicago

## 📝 Descripción del proyecto

Este proyecto analiza el comportamiento del servicio de taxis en la ciudad de **Chicago** durante el mes de noviembre de 2017. Se utilizaron tres conjuntos de datos que contienen información sobre compañías de taxis, barrios donde finalizan los viajes y duración de trayectos bajo distintas condiciones climáticas.

El objetivo es identificar patrones clave que permitan entender qué empresas tienen mayor actividad, qué barrios son los más transitados y cómo influye el clima en los viajes hacia el aeropuerto O'Hare.

---

## 🔍 Análisis realizado

- Se identificaron las compañías con mayor número de viajes los días 15 y 16 de noviembre.
- Se examinaron los barrios con más finalizaciones de viajes durante el mes.
- Se generaron visualizaciones comparativas para analizar tendencias por empresa y por zona.
- Se investigó la duración de los viajes desde el Loop hasta el Aeropuerto Internacional O’Hare bajo distintas condiciones meteorológicas.
- Se probó la hipótesis de que **los sábados lluviosos afectan la duración promedio** de estos trayectos.

---

## 📁 Descripción de los datos

### `project_sql_result_01.csv`
Contiene el número de viajes realizados por cada compañía de taxis el 15 y 16 de noviembre de 2017.

- `company_name` — nombre de la empresa de taxis  
- `trips_amount` — cantidad total de viajes registrados  

### `project_sql_result_04.csv`
Promedio de viajes que terminaron en cada barrio durante noviembre de 2017.

- `dropoff_location_name` — nombre del barrio  
- `average_trips` — promedio de viajes finalizados en esa zona  

### `project_sql_result_07.csv`
Datos sobre viajes desde el Loop hacia el aeropuerto O’Hare.

- `start_ts` — fecha y hora del inicio del viaje  
- `weather_conditions` — condiciones climáticas al momento del viaje  
- `duration_seconds` — duración del viaje en segundos  

---

# 🚖 Chicago Taxi Trip Analysis

## 📝 Project Description

This project analyzes taxi service behavior in **Chicago** during November 2017. Three datasets were used, containing information about taxi companies, neighborhoods where trips ended, and travel durations under different weather conditions.

The main goal is to identify patterns in trip volume by company and neighborhood, and determine whether weather impacts travel time to O’Hare International Airport.

---

## 🔍 Analysis Overview

- Identified the most active taxi companies on November 15–16.
- Analyzed the neighborhoods with the highest number of trip drop-offs in November.
- Created visual comparisons of company activity and neighborhood traffic.
- Investigated trip durations from the Loop to O’Hare during varying weather.
- Tested the hypothesis that **rainy Saturdays affect average trip duration**.

---

## 📁 Data Description

### `project_sql_result_01.csv`  
Number of trips taken by each taxi company on November 15 and 16, 2017.

- `company_name` — taxi company name  
- `trips_amount` — total number of trips  

### `project_sql_result_04.csv`  
Average number of trips ending in each neighborhood during November.

- `dropoff_location_name` — neighborhood name  
- `average_trips` — average trip drop-offs  

### `project_sql_result_07.csv`  
Data on trips from the Loop to O’Hare International Airport.

- `start_ts` — trip start date and time  
- `weather_conditions` — weather at the time of trip  
- `duration_seconds` — trip duration in seconds  
