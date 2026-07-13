# 📊 Análisis de rendimiento de marketing para Y.Afisha

## 📝 Descripción del proyecto

En este proyecto se analizaron datos de usuarios, pedidos y gastos publicitarios de la plataforma **Y.Afisha** entre enero de 2017 y diciembre de 2018. El objetivo fue entender el comportamiento de los usuarios, evaluar la rentabilidad de las campañas de marketing y aportar recomendaciones estratégicas basadas en métricas clave como conversión, LTV y ROMI.

Se trabajó con tres conjuntos de datos que contienen información sobre visitas al sitio web, transacciones realizadas y costos asociados a distintas fuentes de adquisición.

---

## 🎯 Objetivos del análisis

- Analizar cómo interactúan los usuarios con la plataforma: frecuencia de visitas, duración de sesiones y comportamiento de retorno.
- Evaluar el tiempo que tarda un usuario en convertirse en cliente.
- Calcular ingresos generados por usuario (LTV) y volumen de pedidos.
- Medir el impacto de las campañas de marketing: inversión, adquisición y retorno (CAC y ROMI).
- Identificar las plataformas más efectivas y rentables para futuras estrategias de inversión publicitaria.

---

## 📈 Métricas calculadas

### 🧍 Usuarios y sesiones
- Usuarios activos diarios, semanales y mensuales.
- Número de sesiones por día.
- Duración promedio de las sesiones.
- Frecuencia de retorno de usuarios.

### 💳 Ventas y comportamiento de compra
- Tiempo desde el registro hasta la conversión (por cohortes).
- Número total de pedidos y su evolución en el tiempo.
- Ticket promedio por compra.
- LTV (Valor de Vida del Cliente) acumulado por cohorte.

### 📣 Marketing y adquisición
- Inversión total y por fuente de adquisición.
- CAC (Costo de Adquisición de Cliente) por fuente.
- ROMI (Retorno de Inversión en Marketing) a lo largo del tiempo.
- Comparación de métricas según dispositivos y canales.

---

## 📁 Descripción de los datos

### `visits_log_us.csv`  
Registros de visitas al sitio web.  
Columnas:
- `uid`: ID único del usuario  
- `device`: tipo de dispositivo  
- `start_ts`: fecha y hora de inicio de la sesión  
- `end_ts`: fecha y hora de finalización  
- `source_id`: identificador de la fuente publicitaria  

### `orders_log_us.csv`  
Datos sobre pedidos realizados.  
Columnas:
- `uid`: ID del usuario que realizó el pedido  
- `buy_ts`: fecha y hora de la compra  
- `revenue`: ingreso generado por el pedido  

### `costs_us.csv`  
Gastos publicitarios por fuente.  
Columnas:
- `source_id`: identificador de la fuente  
- `dt`: fecha del gasto  
- `costs`: monto gastado ese día  

---

# 📊 Marketing Performance Analysis for Y.Afisha

## 📝 Project Description

This project analyzes user behavior, transactions, and marketing expenses on the **Y.Afisha** platform between January 2017 and December 2018. The goal is to evaluate how customers interact with the service, how much revenue they generate, and whether marketing investments are cost-effective.

Three datasets were used to assess user engagement, conversion timing, revenue per customer (LTV), and campaign profitability (ROMI).

---

## 🎯 Analysis Objectives

- Understand user interaction: session frequency, duration, and return behavior.
- Measure conversion time from registration to first purchase.
- Calculate total orders and average order value.
- Evaluate customer lifetime value (LTV).
- Assess marketing spend, customer acquisition cost (CAC), and return on investment (ROMI).
- Identify the most effective acquisition sources and advertising channels.

---

## 📈 Key Metrics

### 🧍 Users & Sessions
- Daily, weekly, and monthly active users.
- Number of sessions per day.
- Average session duration.
- User return frequency.

### 💳 Sales & Conversion
- Time to conversion by cohort.
- Total number of orders over time.
- Average order value.
- Customer lifetime value (LTV).

### 📣 Marketing & ROI
- Total and source-specific marketing spend.
- Customer acquisition cost (CAC) per source.
- ROMI over time.
- Performance by device and channel.

---

## 📁 Data Description

### `visits_log_us.csv`  
Website visit logs.  
Columns:
- `uid`: unique user ID  
- `device`: user device  
- `start_ts`: session start timestamp  
- `end_ts`: session end timestamp  
- `source_id`: ad source identifier  

### `orders_log_us.csv`  
Customer purchase data.  
Columns:
- `uid`: user ID who placed the order  
- `buy_ts`: timestamp of the purchase  
- `revenue`: revenue from the order  

### `costs_us.csv`  
Marketing costs.  
Columns:
- `source_id`: ad source identifier  
- `dt`: date of the expense  
- `costs`: amount spent that day  


