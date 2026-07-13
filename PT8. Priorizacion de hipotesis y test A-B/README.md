# 🧪 Prioridad de hipótesis y análisis de test A/B para tienda online

## 📝 Descripción del proyecto

En este proyecto se busca optimizar los ingresos de una tienda en línea mediante dos enfoques complementarios:

1. **Priorización de hipótesis de negocio** utilizando marcos de decisión estructurados.
2. **Análisis de un experimento A/B** para evaluar el impacto de cambios propuestos en la experiencia del usuario.

Se trabaja con datos reales de visitas, pedidos y resultados experimentales recopilados por el equipo de marketing.

---

## 📌 Parte 1 – Priorización de hipótesis

Se utilizaron nueve hipótesis formuladas por el equipo de marketing para mejorar los ingresos. Cada hipótesis está evaluada en base a:

- `Reach` (alcance de usuarios)
- `Impact` (impacto esperado)
- `Confidence` (nivel de certeza)
- `Effort` (esfuerzo o recursos necesarios)

Se aplicaron dos frameworks para priorizar:

- **ICE** (Impact × Confidence ÷ Effort)
- **RICE** (Reach × Impact × Confidence ÷ Effort)

Se compararon los resultados de ambas metodologías y se analizaron los cambios en el orden de prioridad para fundamentar decisiones estratégicas.

📁 **Archivo usado**: `hypotheses_us.csv`

---

## 📊 Parte 2 – Análisis del test A/B

Se analizaron los resultados de un test A/B implementado para evaluar el impacto de una nueva funcionalidad o estrategia sobre las métricas clave del negocio.

El análisis incluyó:

- Comparación del ingreso acumulado entre los grupos A y B
- Tamaño promedio de los pedidos
- Diferencias relativas y absolutas por día
- Tasas de conversión diarias
- Distribución de pedidos por usuario
- Detección y tratamiento de valores atípicos
- Cálculo de significancia estadística (con y sin datos filtrados)

El objetivo fue determinar si existe una diferencia significativa entre los grupos, y en función de ello, decidir si se debe implementar el cambio, seguir con la prueba o descartarla.

📁 **Archivos usados**:
- `orders_us.csv`  
- `visits_us.csv`

---

## 📁 Descripción de los datos

### `hypotheses_us.csv`
- `Hypothesis` — descripción de la hipótesis  
- `Reach` — alcance esperado  
- `Impact` — impacto esperado  
- `Confidence` — confianza en la hipótesis  
- `Effort` — esfuerzo estimado  

### `orders_us.csv`
- `transactionId` — ID del pedido  
- `visitorId` — ID del visitante  
- `date` — fecha del pedido  
- `revenue` — ingresos generados  
- `group` — grupo del test A/B (A o B)  

### `visits_us.csv`
- `date` — fecha  
- `group` — grupo del test A/B  
- `visits` — número de visitas por grupo y fecha  

---

# 🧪 Hypothesis Prioritization and A/B Test Analysis for Online Store

## 📝 Project Description

This project aims to increase the revenue of an online store through two main approaches:

1. **Business hypothesis prioritization** using structured decision-making frameworks.
2. **A/B test analysis** to measure the effect of experimental changes on key performance indicators.

Real datasets were used, containing information on user behavior, orders, and experimental visits.

---

## 📌 Part 1 – Hypothesis Prioritization

Nine business hypotheses were proposed by the marketing team to improve revenue. Each one was rated according to:

- `Reach` – user reach
- `Impact` – expected effect
- `Confidence` – level of certainty
- `Effort` – required resources

Two frameworks were applied:

- **ICE**: Impact × Confidence ÷ Effort  
- **RICE**: Reach × Impact × Confidence ÷ Effort

The priority order from both methods was compared to understand how the consideration of reach modifies strategic focus.

📁 **File used**: `hypotheses_us.csv`

---

## 📊 Part 2 – A/B Test Analysis

A complete evaluation was conducted on an A/B test to determine the impact of a change on sales performance.

The analysis included:

- Cumulative revenue by group
- Cumulative average order size
- Daily relative differences between groups
- Daily conversion rates
- Orders per user distribution
- Outlier detection (based on percentiles)
- Statistical significance testing (raw and filtered data)

The goal was to decide whether to implement the change, continue testing, or discard the variation.

📁 **Files used**:
- `orders_us.csv`  
- `visits_us.csv`

---

## 📁 Data Description

### `hypotheses_us.csv`
- `Hypothesis` — hypothesis description  
- `Reach` — estimated user reach  
- `Impact` — expected impact  
- `Confidence` — confidence level  
- `Effort` — required resources  

### `orders_us.csv`
- `transactionId` — order ID  
- `visitorId` — user ID  
- `date` — order date  
- `revenue` — order revenue  
- `group` — A/B test group (A or B)  

### `visits_us.csv`
- `date` — date  
- `group` — A/B test group  
- `visits` — number of visits per date and group  

