# 🤖 Estudio de mercado para un café con camareros robot en Los Ángeles

## 📝 Descripción del proyecto

Has decidido abrir un **café atendido por robots** en Los Ángeles. Aunque el concepto es innovador, también implica una inversión considerable. Para atraer financiamiento, es necesario presentar un estudio de mercado sólido que evalúe la viabilidad del negocio una vez superado el factor novedad.

Este análisis utiliza datos públicos sobre restaurantes en Los Ángeles, con el fin de comprender el panorama actual del mercado, identificar oportunidades de expansión y fundamentar decisiones sobre el tipo de local y la cantidad ideal de asientos.

---

## 🎯 Objetivos del análisis

- Examinar la distribución de tipos de establecimientos gastronómicos en LA.
- Evaluar la proporción de negocios independientes vs. cadenas.
- Investigar las características más comunes de las cadenas (número de locales vs. número de asientos).
- Analizar la capacidad promedio según el tipo de restaurante.
- Determinar las calles más populares para abrir restaurantes.
- Estudiar la distribución de asientos en zonas con alta densidad de restaurantes.
- Realizar recomendaciones sobre el tipo de establecimiento más adecuado y si conviene desarrollar una cadena.

---

## 📊 Análisis realizado

- Limpieza y transformación del dataset original.
- Segmentación por tipo de restaurante y pertenencia a cadena.
- Extracción de nombres de calles desde la dirección.
- Cálculo del promedio de asientos por tipo de restaurante.
- Visualización de:
  - Tipos de establecimientos
  - Proporción de cadenas
  - Calles con más restaurantes
  - Distribución de asientos en zonas concurridas

Se generaron gráficos descriptivos y se formularon recomendaciones de negocio basadas en tendencias claras del mercado.

---

## 📁 Descripción de los datos

### `rest_data_us_upd.csv`
Contiene información general sobre establecimientos gastronómicos en Los Ángeles.  
Columnas:

- `object_name` — nombre del restaurante o local  
- `chain` — si pertenece a una cadena (`TRUE`/`FALSE`)  
- `object_type` — tipo de establecimiento (ej. café, restaurante, bar)  
- `address` — dirección  
- `number` — número de asientos disponibles  

---


---

# 🤖 Market Study for a Robot Café in Los Angeles

## 📝 Project Description

You are planning to open a **robot-operated café** in Los Angeles. While the idea is original and attention-grabbing, it comes with a high financial cost. To secure investment, you’ve been tasked with preparing a detailed **market research study** that explores how sustainable the business would be once the novelty fades.

This project uses publicly available data on restaurants in Los Angeles to explore the current market landscape and identify promising business opportunities.

---

## 🎯 Analysis Objectives

- Analyze the distribution of different types of dining establishments.
- Compare independent businesses versus chain restaurants.
- Investigate whether chains tend to have more locations with fewer seats or the opposite.
- Calculate the average number of seats by restaurant type.
- Identify the most popular streets for restaurant placement.
- Explore seat distribution in high-density zones.
- Provide data-driven recommendations on the ideal restaurant type and expansion strategy.

---

## 📊 Key Analyses

- Data cleaning and preprocessing
- Classification by establishment type and chain affiliation
- Street name extraction from full addresses
- Average seat count by restaurant type
- Visualizations of:
  - Establishment types
  - Chain vs. non-chain ratios
  - Top streets by number of restaurants
  - Seat distribution across high-traffic areas

Business recommendations were made based on observed market trends.

---

## 📁 Data Description

### `rest_data_us_upd.csv`  
Includes data on dining establishments in Los Angeles.  
Columns:

- `object_name` — name of the restaurant or café  
- `chain` — whether it belongs to a chain (`TRUE`/`FALSE`)  
- `object_type` — type of establishment (e.g., café, restaurant, bar)  
- `address` — full street address  
- `number` — number of available seats  

---



