Análisis de viajes en taxi en Chicago
Descripción del proyecto
En este proyecto se analizaron los patrones de uso de taxis en la ciudad de Chicago durante el mes de noviembre de 2017. Para ello se utilizaron tres conjuntos de datos con información sobre compañías de taxis, barrios donde finalizaron los viajes y condiciones climáticas.

Se buscó identificar qué empresas tuvieron mayor actividad, en qué barrios finalizaron más viajes y si las condiciones climáticas afectan la duración de los trayectos hacia el aeropuerto O’Hare.

Análisis realizado
Se identificaron las compañías de taxis con mayor número de viajes registrados el 15 y 16 de noviembre.

Se analizaron los barrios con más finalizaciones de viaje en todo el mes de noviembre.

Se generaron gráficos comparativos para visualizar la actividad por empresa y por barrio.

Se examinó la duración de los viajes desde el Loop al aeropuerto O'Hare en diferentes condiciones climáticas.

Se probó la hipótesis de que los sábados lluviosos afectan la duración promedio de estos viajes.

Descripción de los datos
project_sql_result_01.csv
Contiene el número de viajes registrados por cada empresa de taxis durante el 15 y 16 de noviembre.
Columnas:

company_name: nombre de la empresa

trips_amount: cantidad de viajes

project_sql_result_04.csv
Contiene el promedio de viajes que finalizaron en cada barrio durante noviembre de 2017.
Columnas:

dropoff_location_name: nombre del barrio

average_trips: viajes promedio finalizados en esa zona

project_sql_result_07.csv
Incluye datos de viajes desde el Loop al Aeropuerto Internacional O’Hare.
Columnas:

start_ts: fecha y hora del viaje

weather_conditions: condiciones climáticas al inicio

duration_seconds: duración del viaje en segundos

🇬🇧 English
Chicago Taxi Trip Analysis
Project Description
This project analyzes taxi usage patterns in the city of Chicago during November 2017. Three datasets were used, providing information on taxi companies, neighborhoods where trips ended, and weather conditions.

The goal was to identify which companies had the highest number of trips, the neighborhoods with the most drop-offs, and whether weather conditions affected travel duration to O’Hare Airport.

Analysis Performed
Identified the most active taxi companies on November 15–16.

Analyzed neighborhoods with the highest number of trip drop-offs throughout November.

Created comparative charts showing company activity and top neighborhoods.

Examined trip durations from the Loop to O’Hare under varying weather conditions.

Tested the hypothesis that rainy Saturdays affect the average duration of these trips.

Data Description
project_sql_result_01.csv
Includes the number of trips by taxi company on November 15 and 16.
Columns:

company_name: name of the taxi company

trips_amount: number of trips

project_sql_result_04.csv
Includes the average number of trips that ended in each neighborhood during November.
Columns:

dropoff_location_name: neighborhood name

average_trips: average number of trip drop-offs

project_sql_result_07.csv
Contains data on trips from the Loop to O’Hare International Airport.
Columns:

start_ts: pickup date and time

weather_conditions: weather at trip start

duration_seconds: trip duration in seconds



