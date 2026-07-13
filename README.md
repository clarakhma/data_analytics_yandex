# 📊 data_analytics_yandex

Portfolio of projects completed during the **Yandex Practicum** Data Analytics bootcamp. Each folder is a standalone project with its own notebook and detailed README (description, data, analysis and conclusions).

📖 **Looking for a code snippet you've used before?** → [APUNTES.md](APUNTES.md) collects reusable code patterns from all 13 projects, organized by topic (data cleaning, SQL, funnels, cohorts/LTV/CAC, A/B testing, machine learning, visualization...), each tagged with its source project.

## 📁 Projects

| # | Project | Topic | Main techniques |
|---|---------|-------|------------------|
| [PT1. Yandex Music](PT1.%20Yandex%20Music) | Yandex Music | Comparing music listening habits between Moscow and St. Petersburg | Data cleaning, grouping, filter functions |
| [PT2. Riesgo de incumplimiento de prestatarios](PT2.%20Riesgo%20de%20incumplimiento%20de%20prestatarios) | Borrower default risk | Credit scoring for a bank | Null imputation, categorization, default rate by group |
| [PT3. Precio de vehiculos](PT3.%20Precio%20de%20vehiculos) | Vehicle pricing (Crankshaft List) | What factors drive the price of a used car | Group-based imputation, IQR outliers, EDA |
| [PT4. Operador Megaline](PT4.%20Operador%20Megaline) | Megaline telecom | Which plan (Surf or Ultimate) generates more revenue | Monthly aggregation, overage billing logic, t-test |
| [PT5. Ventas de videojuegos](PT5.%20Ventas%20de%20videojuegos) | Ice — video game sales | What factors determine a game's success | EDA, hypothesis testing, Plotly visualization |
| [PT6. Taxis en Chicago](PT6.%20Taxis%20en%20Chicago) | Chicago taxi trips | Taxi company activity and weather's effect on trip duration | Consumes SQL-pre-extracted data, Welch's t-test |
| [PT7. Marketing Y.Afisha](PT7.%20Marketing%20Y.Afisha) | Y.Afisha marketing | Marketing channel profitability | Cohorts, LTV, CAC, ROMI, DAU/WAU/MAU |
| [PT8. Priorizacion de hipotesis y test A-B](PT8.%20Priorizacion%20de%20hipotesis%20y%20test%20A-B) | Hypothesis prioritization + A/B test | Increasing an online store's revenue | ICE/RICE, A/B test (Mann-Whitney), anomaly detection |
| [PT9. Cafe con camareros robot](PT9.%20Cafe%20con%20camareros%20robot) | Robot-café market study | Market research for a new business in LA | Text cleaning, address parsing, visualization |
| [PT10. Dashboard Tableau](PT10.%20Dashboard%20Tableau) | Tableau dashboard | YouTube video trends | Tableau Public (no notebook) |
| [PT11. Prediccion de cancelacion - gimnasio](PT11.%20Prediccion%20de%20cancelacion%20-%20gimnasio) | Gym churn prediction | Which customers are most likely to cancel their membership | Logistic regression, Random Forest, clustering (KMeans + dendrogram) |
| [Proyecto Integrado](Proyecto%20Integrado) | A/A/B test — food app | Effect of a font change on the conversion funnel | Conversion funnel, A/A/B test, z-test for proportions |
| [Proyecto Final Bootcamp](Proyecto%20Final%20Bootcamp) | Final project (3 parts) | SQL on a reading platform + recommendation A/B test + churn prediction (Model Fitness) | SQL (CTEs, window functions), A/B test, EDA + hypothesis testing |

> **Note on PT11:** that folder's own README mistakenly describes a food-app A/A/B test (duplicated content from Proyecto Integrado). The actual PT11 notebook is a gym-membership churn prediction project (classification + clustering) — the description above reflects the real content.

## 🛠️ Tech stack

- **Python**: pandas, numpy, scipy, statsmodels, scikit-learn
- **Visualization**: matplotlib, seaborn, plotly
- **SQL**: PostgreSQL (SQLAlchemy)
- **BI**: Tableau Public
- **Environment**: Jupyter Notebook

---

# 📊 data_analytics_yandex (Español)

Portafolio de proyectos realizados durante el bootcamp de Análisis de Datos de **Yandex Practicum**. Cada carpeta es un proyecto independiente con su propio notebook y README detallado (descripción, datos, análisis y conclusiones).

📖 **¿Buscas un fragmento de código que ya usaste antes?** → [APUNTES.md](APUNTES.md) reúne, organizados por tema (limpieza de datos, SQL, embudos, cohortes/LTV/CAC, tests A/B, machine learning, visualización...), los patrones de código reutilizables de los 13 proyectos, cada uno etiquetado con su proyecto de origen.

## 📁 Proyectos

| # | Proyecto | Tema | Técnicas principales |
|---|----------|------|----------------------|
| [PT1. Yandex Music](PT1.%20Yandex%20Music) | Yandex Music | Comparación de hábitos musicales entre Moscú y San Petersburgo | Limpieza de datos, agrupamiento, funciones de filtrado |
| [PT2. Riesgo de incumplimiento de prestatarios](PT2.%20Riesgo%20de%20incumplimiento%20de%20prestatarios) | Riesgo de incumplimiento de prestatarios | Scoring crediticio de un banco | Imputación de nulos, categorización, tasas de morosidad por grupo |
| [PT3. Precio de vehiculos](PT3.%20Precio%20de%20vehiculos) | Precio de vehículos (Crankshaft List) | Qué factores influyen en el precio de un coche usado | Imputación por grupo, outliers (IQR), EDA |
| [PT4. Operador Megaline](PT4.%20Operador%20Megaline) | Operador Megaline | Qué tarifa (Surf o Ultimate) genera más ingresos | Agregación mensual, cálculo de tarifas con excedente, test t |
| [PT5. Ventas de videojuegos](PT5.%20Ventas%20de%20videojuegos) | Ice — ventas de videojuegos | Qué factores determinan el éxito de un videojuego | EDA, pruebas de hipótesis, visualización con Plotly |
| [PT6. Taxis en Chicago](PT6.%20Taxis%20en%20Chicago) | Taxis en Chicago | Actividad de compañías de taxi y efecto del clima en los trayectos | Consumo de datos pre-extraídos por SQL, test t (Welch) |
| [PT7. Marketing Y.Afisha](PT7.%20Marketing%20Y.Afisha) | Marketing para Y.Afisha | Rentabilidad de canales de marketing | Cohortes, LTV, CAC, ROMI, DAU/WAU/MAU |
| [PT8. Priorizacion de hipotesis y test A-B](PT8.%20Priorizacion%20de%20hipotesis%20y%20test%20A-B) | Priorización de hipótesis + test A/B | Optimizar ingresos de una tienda online | ICE/RICE, test A/B (Mann-Whitney), detección de anomalías |
| [PT9. Cafe con camareros robot](PT9.%20Cafe%20con%20camareros%20robot) | Café con camareros robot en LA | Estudio de mercado para un negocio nuevo | Limpieza de texto, parsing de direcciones, visualización |
| [PT10. Dashboard Tableau](PT10.%20Dashboard%20Tableau) | Dashboard en Tableau | Tendencias de vídeos en YouTube | Tableau Public (sin notebook) |
| [PT11. Prediccion de cancelacion - gimnasio](PT11.%20Prediccion%20de%20cancelacion%20-%20gimnasio) | Predicción de cancelación — gimnasio | Qué clientes tienen más riesgo de cancelar su membresía | Regresión logística, Random Forest, clustering (KMeans + dendrograma) |
| [Proyecto Integrado](Proyecto%20Integrado) | Test A/A/B — app de alimentos | Efecto de un cambio de fuente en el embudo de conversión | Embudo de conversión, test A/A/B, z-test de proporciones |
| [Proyecto Final Bootcamp](Proyecto%20Final%20Bootcamp) | Proyecto final (3 partes) | SQL sobre plataforma de lectura + test A/B de recomendaciones + predicción de cancelación (Model Fitness) | SQL (CTEs, window functions), test A/B, EDA + hipótesis |

> **Nota sobre PT11:** el README interno de esa carpeta describe por error un test A/A/B de una app de alimentos (contenido duplicado del Proyecto Integrado). El notebook real de PT11 es de predicción de cancelación de un gimnasio (clasificación + clustering) — la descripción de arriba refleja el contenido real.

## 🛠️ Stack técnico

- **Python**: pandas, numpy, scipy, statsmodels, scikit-learn
- **Visualización**: matplotlib, seaborn, plotly
- **SQL**: PostgreSQL (SQLAlchemy)
- **BI**: Tableau Public
- **Entorno**: Jupyter Notebook
