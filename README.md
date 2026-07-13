# 📊 data_analytics_yandex

Portafolio de proyectos realizados durante el bootcamp de Análisis de Datos de **Yandex Practicum**. Cada carpeta es un proyecto independiente con su propio notebook y README detallado (descripción, datos, análisis y conclusiones).

📖 **¿Buscas un fragmento de código que ya usaste antes?** → [APUNTES.md](APUNTES.md) reúne, organizados por tema (limpieza de datos, SQL, embudos, cohortes/LTV/CAC, tests A/B, machine learning, visualización...), los patrones de código reutilizables de los 13 proyectos, con enlace al proyecto de origen de cada uno.

---

## 📁 Proyectos

| # | Proyecto | Tema | Técnicas principales |
|---|----------|------|----------------------|
| [PT1](PT1) | Yandex Music | Comparación de hábitos musicales entre Moscú y San Petersburgo | Limpieza de datos, agrupamiento, funciones de filtrado |
| [PT2](PT2) | Riesgo de incumplimiento de prestatarios | Scoring crediticio de un banco | Imputación de nulos, categorización, tasas de morosidad por grupo |
| [PT3](PT3) | Precio de vehículos (Crankshaft List) | Qué factores influyen en el precio de un coche usado | Imputación por grupo, outliers (IQR), EDA |
| [PT4](PT4) | Operador Megaline | Qué tarifa (Surf o Ultimate) genera más ingresos | Agregación mensual, cálculo de tarifas con excedente, test t |
| [PT5](PT5) | Ice — ventas de videojuegos | Qué factores determinan el éxito de un videojuego | EDA, pruebas de hipótesis, visualización con Plotly |
| [PT6](PT6) | Taxis en Chicago | Actividad de compañías de taxi y efecto del clima en los trayectos | Consumo de datos pre-extraídos por SQL, test t (Welch) |
| [PT7](PT7) | Marketing para Y.Afisha | Rentabilidad de canales de marketing | Cohortes, LTV, CAC, ROMI, DAU/WAU/MAU |
| [PT8](PT8) | Priorización de hipótesis + test A/B | Optimizar ingresos de una tienda online | ICE/RICE, test A/B (Mann-Whitney), detección de anomalías |
| [PT9](PT9) | Café con camareros robot en LA | Estudio de mercado para un negocio nuevo | Limpieza de texto, parsing de direcciones, visualización |
| [PT10](PT10) | Dashboard en Tableau | Tendencias de vídeos en YouTube | Tableau Public (sin notebook) |
| [PT11](PT11) | Predicción de cancelación — gimnasio | Qué clientes tienen más riesgo de cancelar su membresía | Regresión logística, Random Forest, clustering (KMeans + dendrograma) |
| [Proyecto Integrado](Proyecto%20Integrado) | Test A/A/B — app de alimentos | Efecto de un cambio de fuente en el embudo de conversión | Embudo de conversión, test A/A/B, z-test de proporciones |
| [Proyecto Final Bootcamp](Proyecto%20Final%20Bootcamp) | Proyecto final (3 partes) | SQL sobre plataforma de lectura + test A/B de recomendaciones + predicción de cancelación (Model Fitness) | SQL (CTEs, window functions), test A/B, EDA + hipótesis |

> **Nota sobre PT11:** el README interno de esa carpeta describe por error un test A/A/B de una app de alimentos (contenido duplicado del Proyecto Integrado). El notebook real de PT11 es de predicción de cancelación de un gimnasio (clasificación + clustering) — la descripción de la tabla de arriba refleja el contenido real.

---

## 🛠️ Stack técnico

- **Python**: pandas, numpy, scipy, statsmodels, scikit-learn
- **Visualización**: matplotlib, seaborn, plotly
- **SQL**: PostgreSQL (SQLAlchemy)
- **BI**: Tableau Public
- **Entorno**: Jupyter Notebook

---

## 📖 English

Portfolio of projects completed during the **Yandex Practicum** Data Analytics bootcamp. Each folder is a standalone project with its own notebook and detailed README (description, data, analysis and conclusions).

**Looking for a code snippet you've used before?** → [APUNTES.md](APUNTES.md) collects reusable code patterns from all 13 projects, organized by topic (data cleaning, SQL, funnels, cohorts/LTV/CAC, A/B testing, machine learning, visualization...), each tagged with its source project.

See the table above for the full project index — folder names and links are the same in both languages.
