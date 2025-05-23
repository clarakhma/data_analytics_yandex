# 🕹️ Ice – Análisis de ventas de videojuegos

## 📌 Descripción del proyecto

Trabajas para **Ice**, una tienda online que vende videojuegos en todo el mundo. Tu objetivo es identificar patrones que determinan si un videojuego tendrá éxito comercial, utilizando datos históricos como puntuaciones de usuarios y críticos, géneros, plataformas (por ejemplo, Xbox, PlayStation), y ventas por región. Esta información permitirá predecir futuros lanzamientos prometedores y optimizar campañas de marketing.

Los datos disponibles llegan hasta diciembre de 2016. El proyecto simula una situación en la que estás planificando estrategias para el año 2017, usando los datos históricos como base de análisis.

## 🧠 Objetivos

- Preparar y limpiar el conjunto de datos.
- Analizar tendencias de ventas por plataforma, año y género.
- Evaluar el impacto de las reseñas de usuarios y expertos en las ventas.
- Comparar las plataformas líderes y su evolución a lo largo del tiempo.
- Generar perfiles de usuario por región: Norteamérica, Europa y Japón.
- Comprobar hipótesis estadísticas sobre calificaciones y géneros.

## 🧾 Descripción de los datos

El conjunto de datos incluye las siguientes columnas:

- `name`: nombre del videojuego  
- `platform`: plataforma de lanzamiento (ej. PS4, Xbox One)  
- `year_of_release`: año de lanzamiento  
- `genre`: género del juego  
- `na_sales`: ventas en Norteamérica (millones USD)  
- `eu_sales`: ventas en Europa (millones USD)  
- `jp_sales`: ventas en Japón (millones USD)  
- `other_sales`: ventas en otras regiones (millones USD)  
- `critic_score`: puntuación media de críticos (sobre 100)  
- `user_score`: puntuación media de usuarios (sobre 10)  
- `rating`: clasificación ESRB (adolescente, adulto, etc.)

**Nota:** Los datos de 2016 pueden estar incompletos. Algunos valores como "TBD" (por determinar) requieren tratamiento especial.

## 🧪 Pruebas de hipótesis

Se analizan y prueban las siguientes hipótesis:

- Las calificaciones promedio de los usuarios para las plataformas Xbox One y PC son iguales.
- Las calificaciones promedio de los usuarios difieren entre los géneros de Acción y Deportes.

---

# 🕹️ Ice – Video Game Sales Analysis

## 📌 Project Description

You work for **Ice**, an online video game retailer operating worldwide. Your task is to identify patterns that predict whether a video game will be commercially successful. You will analyze historical data, including user and critic ratings, genres, platforms (e.g., Xbox, PlayStation), and regional sales. These insights will help forecast promising projects and support marketing decisions for 2017.

The data goes up to December 2016. This project assumes you are planning the upcoming year based on historical trends.

## 🧠 Objectives

- Clean and prepare the dataset.
- Analyze sales trends by platform, year, and genre.
- Evaluate the impact of user and critic reviews on sales.
- Compare top-performing platforms and their life cycles.
- Create user profiles by region: North America, Europe, and Japan.
- Test statistical hypotheses on ratings and genres.

## 🧾 Data Description

The dataset includes the following columns:

- `name`: name of the video game  
- `platform`: release platform (e.g., PS4, Xbox One)  
- `year_of_release`: year of release  
- `genre`: game genre  
- `na_sales`: North American sales (in millions of USD)  
- `eu_sales`: European sales (in millions of USD)  
- `jp_sales`: Japanese sales (in millions of USD)  
- `other_sales`: sales in other regions (in millions of USD)  
- `critic_score`: average critic score (out of 100)  
- `user_score`: average user score (out of 10)  
- `rating`: ESRB rating (e.g., Teen, Mature)

**Note:** Data from 2016 may be incomplete. Some values such as "TBD" (to be determined) require specific handling.

## 🧪 Hypothesis Testing

The following hypotheses are tested:

- The average user ratings for Xbox One and PC are the same.
- The average user ratings for Action and Sports genres are different.

