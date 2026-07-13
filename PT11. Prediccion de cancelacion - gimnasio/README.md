# 📱 Análisis del comportamiento de usuarios y test A/A/B en una app de alimentos

## 📝 Descripción del proyecto

Trabajas en una empresa emergente que comercializa productos alimenticios a través de una aplicación. Tu objetivo es estudiar cómo los usuarios interactúan con la app, identificar en qué etapa del embudo de conversión abandonan el proceso y evaluar los resultados de un **test A/A/B** diseñado para medir el impacto de un cambio en la fuente tipográfica del diseño.

---

## 🎯 Objetivos del análisis

- Analizar el recorrido de los usuarios a lo largo del embudo de eventos hasta llegar a la compra.
- Determinar en qué etapas del embudo se pierden más usuarios.
- Evaluar si los dos grupos de control (A/A) son estadísticamente similares.
- Comparar el desempeño del grupo de prueba (B) frente a los grupos de control.
- Tomar decisiones basadas en pruebas de hipótesis sobre los efectos del rediseño.

---

## 🧪 Descripción del experimento

El experimento está dividido en tres grupos:

- **Grupo 246**: control A  
- **Grupo 247**: control A  
- **Grupo 248**: grupo de prueba (fuente nueva)

El diseño A/A/B permite validar la confiabilidad del experimento y entender el impacto del rediseño en la experiencia del usuario.

---

## 📊 Análisis realizado

- Limpieza y transformación de los datos
- Generación de columnas de fecha y hora
- Exploración de la frecuencia de eventos
- Análisis del embudo de conversión
- Comparación de tasas de participación por evento entre los grupos
- Pruebas estadísticas para verificar diferencias significativas
- Ajuste del nivel de significancia con corrección por comparaciones múltiples

---

## 📁 Descripción de los datos

### `logs_exp_us.csv`  
Registros de acciones de usuarios en la app.  
Columnas:

- `EventName` — nombre del evento (ej. login, view_product, purchase)  
- `DeviceIDHash` — identificador único de usuario  
- `EventTimestamp` — fecha y hora del evento  
- `ExpId` — ID del grupo experimental:  
  - 246: grupo de control A  
  - 247: grupo de control A  
  - 248: grupo de prueba (fuente nueva)

---

# 📱 User Behavior and A/A/B Test Analysis in a Food App

## 📝 Project Description

You work at a food-focused startup with a mobile app. Your goal is to analyze user behavior, determine how users progress through the event funnel, and evaluate the results of an **A/A/B test** that measures the effect of a font redesign on user engagement and performance.

---

## 🎯 Analysis Objectives

- Track user behavior through the app’s funnel to identify drop-off points.
- Determine the conversion rate from the first event to purchase.
- Evaluate whether the two control groups (A/A) are statistically similar.
- Assess the effect of the new font (group B) on user engagement.
- Base recommendations on statistically sound A/B testing methodology.

---

## 🧪 Experiment Description

The experiment is divided into three groups:

- **Group 246**: Control A  
- **Group 247**: Control A  
- **Group 248**: Test group (new font)

The A/A/B design helps validate the experiment setup and evaluate the font’s impact.

---

## 📊 Key Analyses

- Data cleaning and timestamp processing
- Event frequency and funnel drop-off analysis
- Funnel conversion ratio calculations between steps
- Control group consistency check (A vs. A)
- Statistical comparison between control and test groups
- Adjustment for multiple hypothesis testing

---

## 📁 Data Description

### `logs_exp_us.csv`  
User action logs from the mobile app.  
Columns:

- `EventName` — name of the event (e.g., login, view_product, purchase)  
- `DeviceIDHash` — unique user ID  
- `EventTimestamp` — event timestamp  
- `ExpId` — experimental group ID:  
  - 246: control group A  
  - 247: control group A  
  - 248: test group (new font)

