# 🧠 Proyecto Final Integral – Análisis, Predicción y Pruebas A/B

## 📝 Descripción general

Este proyecto final reúne tres estudios analíticos independientes enfocados en resolver problemas reales de negocio a través del uso de datos. A lo largo del proyecto se aplicaron técnicas de **exploración de datos (EDA)**, **SQL**, **pruebas de hipótesis**, **modelado predictivo** y **experimentos controlados (A/B testing)**.

El objetivo general es demostrar la capacidad de analizar y transformar datos en conocimiento accionable que permita tomar decisiones estratégicas fundamentadas. Cada parte incluye hipótesis específicas, análisis detallados y recomendaciones prácticas.

---

## 🧩 Componentes del proyecto

### 1. 📚 Análisis exploratorio con SQL – Plataforma de libros

**Objetivo del caso:**  
Evaluar el comportamiento de usuarios y el rendimiento de editoriales y autores en una plataforma de lectura digital durante la pandemia. El análisis busca sentar las bases para una propuesta de producto en el mercado editorial.

**Hipótesis planteadas:**  
- Los usuarios con más reseñas tienden a interactuar con los autores mejor valorados.  
- Algunas editoriales publican muchos libros, pero con baja valoración promedio.

**Técnicas utilizadas:**  
- Consultas SQL complejas (`JOIN`, `GROUP BY`, `HAVING`, `AVG`)  
- Agrupamiento de usuarios por nivel de actividad  
- Detección de patrones de publicación y valoración editorial  
- Identificación de autores de alto impacto

---

### 2. 🛍️ Evaluación de sistema de recomendaciones – A/B Test

**Objetivo del caso:**  
Determinar si un nuevo sistema de recomendaciones mejora la conversión en un e-commerce. Se analiza el comportamiento de los usuarios a través del embudo de conversión y se aplican pruebas estadísticas.

**Hipótesis principal:**  
- El nuevo sistema de recomendaciones mejora significativamente la conversión final del usuario (de vista a compra).

**Técnicas utilizadas:**  
- Análisis de embudo: `product_page → cart → purchase`  
- Comparación de conversiones entre grupos A y B  
- Pruebas de hipótesis con prueba z para proporciones  
- Evaluación de significancia estadística y decisión final basada en datos

---

### 3. 📞 Predicción de cancelación y eficiencia operativa – Model Fitness

**Objetivo del caso:**  
Predecir la cancelación de clientes de un gimnasio y analizar la eficiencia de operadores en una empresa de atención. Este módulo integra predicción, segmentación de usuarios y recomendaciones de retención.

**Hipótesis planteadas:**  
- Los clientes con contratos cortos, baja frecuencia de asistencia y sin interacción grupal tienen mayor probabilidad de cancelar.  
- La cancelación puede preverse mediante modelos supervisados simples.  
- Existen perfiles de usuarios distinguibles por características clave (edad, visitas, gastos adicionales).

**Técnicas utilizadas:**  
- Análisis exploratorio y visualización (EDA)  
- Modelos predictivos: regresión logística y random forest  
- Evaluación de precisión, *recall*, y exactitud  
- Clustering de usuarios con K-Means y análisis de clústeres  
- Detección de patrones de abandono y sugerencias de retención

---

## 📈 Herramientas y tecnologías utilizadas

- Python (Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn, SciPy, Statsmodels)
- SQL (PostgreSQL)
- Jupyter Notebook
- Pruebas de hipótesis estadísticas (z-test, U de Mann-Whitney)
- Segmentación y modelado supervisado
- Visualización interactiva y dashboards

---

## ✅ Resultados esperados

- Validación de hipótesis mediante pruebas estadísticas rigurosas.  
- Identificación de segmentos de clientes con comportamiento crítico.  
- Recomendaciones prácticas para negocios basadas en datos.  
- Presentación profesional de hallazgos y visualizaciones efectivas.

---

## 📁 Archivos del proyecto

- 📘 `SQL.pdf`: Estudio de base de datos de una app de lectura  
- 📘 `2. Proyecto de pruebas A_B.pdf`: Resultados de test A/B para recomendaciones  
- 📓 `Proyecto Final.ipynb`: Predicción de cancelación y segmentación de clientes  


