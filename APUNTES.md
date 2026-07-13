# 📖 Apuntes de código — Cheatsheet del bootcamp

Referencia rápida de patrones de código reutilizados a lo largo de los 13 proyectos del bootcamp (PT1–PT11, Proyecto Final Bootcamp, Proyecto Integrado). El objetivo de este documento es que puedas buscar "¿cómo hacía yo X?" sin tener que abrir cada notebook uno por uno.

Cada snippet incluye una etiqueta `[PT_N]` que indica en qué proyecto(s) aparece originalmente, por si necesitas ver el contexto completo. Índice por tema, no por proyecto.

## Índice

1. [Carga de datos](#1-carga-de-datos)
2. [Diagnóstico y exploración inicial](#2-diagnóstico-y-exploración-inicial)
3. [Limpieza de datos](#3-limpieza-de-datos)
4. [Fechas y columnas derivadas](#4-fechas-y-columnas-derivadas)
5. [Agregación, pivote y agrupamiento](#5-agregación-pivote-y-agrupamiento)
6. [SQL](#6-sql)
7. [Embudos de conversión y eventos](#7-embudos-de-conversión-y-eventos)
8. [Cohortes, LTV, CAC, ROMI](#8-cohortes-ltv-cac-romi)
9. [Priorización de hipótesis (ICE/RICE)](#9-priorización-de-hipótesis-icerice)
10. [Test A/B y pruebas de hipótesis estadísticas](#10-test-ab-y-pruebas-de-hipótesis-estadísticas)
11. [Preprocesamiento para Machine Learning](#11-preprocesamiento-para-machine-learning)
12. [Modelos de clasificación y regresión](#12-modelos-de-clasificación-y-regresión)
13. [Clustering](#13-clustering)
14. [Métricas de evaluación de modelos](#14-métricas-de-evaluación-de-modelos)
15. [Visualización](#15-visualización)
16. [Funciones utilitarias varias](#16-funciones-utilitarias-varias)

---

## 1. Carga de datos

**Carga robusta local vs. plataforma (try/except)**
```python
try:  # local / Anaconda
    df = pd.read_csv('vehicles_us.csv')
except FileNotFoundError:  # plataforma Practicum
    df = pd.read_csv('/datasets/vehicles_us.csv')
```
Patrón usado en casi todos los proyectos para que el mismo notebook funcione tanto en local como en la plataforma del bootcamp, sin tocar rutas a mano. `[PT2, PT3, PT4, PT6, PT7, PT8, PT9, PT11, Proyecto Final]`

**Conexión a PostgreSQL con SQLAlchemy + pandas**
```python
from sqlalchemy import create_engine

db_config = {
    'user': 'praktikum_student', 'pwd': 'Sdf4$2;d-d30pp',
    'host': 'rc1b-wcoijxj3yxfsf3fs.mdb.yandexcloud.net',
    'port': 6432, 'db': 'data-analyst-final-project-db'
}
connection_string = 'postgresql://{}:{}@{}:{}/{}'.format(
    db_config['user'], db_config['pwd'], db_config['host'], db_config['port'], db_config['db'])
engine = create_engine(connection_string)

query = "SELECT * FROM books LIMIT 5"
results = pd.io.sql.read_sql(query, con=engine)
```
Conexión directa a una base de datos y ejecución de queries devolviendo un DataFrame. `[Proyecto Final Bootcamp - SQL]`

---

## 2. Diagnóstico y exploración inicial

**Función `data_info()` — resumen exploratorio "todo en uno"**
```python
def data_info(df):
    print('Filas y columnas: \n{}'.format(df.shape))
    print('Informacion general:'); print(df.info())
    print('Primeras cinco filas: \n{}'.format(df.head()))
    print('Detalles estadisticos: \n{}'.format(df.describe()))
    print('Hay {} datos duplicados.'.format(df.duplicated().sum()))
    print('Valores ausentes ?'); print(df.isna().sum(), '\n')
    print('Porcentaje de valores ausentes \n'); print(df.isna().mean().reset_index())
    print((df.isna().sum().sort_values(ascending=False).reset_index()
           .rename(columns={'index': 'Variables', 0: 'Missing'})).T)
```
Función repetida (casi idéntica) en la mayoría de los proyectos: primer vistazo estándar a cualquier dataset — shape, tipos, duplicados, % de nulos. Vale la pena tenerla en un módulo propio para no reescribirla cada vez. `[PT4, PT6, PT7, PT8, PT9, PT11, Proyecto Final]`

**Tabla ordenada de valores ausentes (sin función)**
```python
(df.isna()
 .sum()
 .sort_values(ascending=False)
 .reset_index()
 .rename(columns={'index': 'Variables', 0: 'Missing'})
).T
```
Versión suelta del mismo patrón — muestra qué columnas tienen más ausentes, ordenadas de mayor a menor. `[PT2, PT3]`

---

## 3. Limpieza de datos

**Normalizar todo el DataFrame a minúsculas (contenido + nombres de columnas)**
```python
def convertir_a_minusculas(df):
    df = df.applymap(lambda s: s.lower() if type(s) == str else s)
    df.columns = df.columns.str.lower()
    return df
```
Evita duplicados implícitos por diferencia de mayúsculas/minúsculas de una sola pasada. `[PT4, PT7, PT8, PT9, PT11]`

**Corregir duplicados implícitos en una columna categórica**
```python
def replace_wrong_genres(wrong_genres, correct_genre):
    for wrong_genre in wrong_genres:
        df['genre'] = df['genre'].replace(wrong_genre, correct_genre)

replace_wrong_genres(['hip', 'hop', 'hip-hop'], 'hiphop')
```
Unifica variantes distintas de una misma categoría (typos, mayúsculas, sinónimos). `[PT1]`

**Renombrar columnas a snake_case**
```python
df = df.rename(columns={'  userID': 'userid', 'Track': 'track', '  City  ': 'city', 'Day': 'day'})
```
`[PT1]`

**Reemplazar valores inválidos por rangos plausibles**
```python
data["children"] = data["children"].replace({20: 2, -1: 1})  # typos evidentes (-1 hijo, 20 hijos)
data['days_employed'] = data['days_employed'].abs()          # negativos por error de signo
data['gender'] = data['gender'].replace({"XNA": "F"})        # categoría inválida → la más frecuente
```
Estrategia caso por caso para corregir valores que violan reglas de negocio obvias (edad negativa, categoría inexistente, etc.). `[PT2]`

**Reemplazar "cero disfrazado de ausente" por NaN y luego imputar por grupo**
```python
df.loc[df['odometer'] == 0, 'odometer'] = np.nan
df['odometer'] = df.groupby(['model', 'type'])['odometer'].apply(lambda x: x.fillna(x.median()))

# Si algunos grupos no tenían suficientes datos para calcular la mediana, quedan NaN residuales:
df = df.dropna(subset=['odometer'], axis=0).reset_index(drop=True)
```
Cuando un valor "técnicamente presente" (0 km) en realidad significa "dato faltante", conviene convertirlo primero a NaN y luego imputar con la mediana del grupo relevante (mismo modelo/tipo), en vez de usar la mediana global. `[PT3]`

**Imputación de nulos por mediana/media agrupada (`groupby().transform()`)**
```python
# Imputar el ingreso mensual usando la mediana del subgrupo (género, educación, tipo de ingreso)
data_not_nan_avg = data_not_nan.groupby(['gender', 'education_id', 'income_type'])['total_income'].transform("median")
data['total_income'] = data['total_income'].fillna(data_not_nan_avg)
```
`transform` conserva el índice original, por lo que el resultado se puede pasar directo a `fillna()`. Mejor que imputar con la media/mediana global cuando existe una variable categórica que correlaciona con el valor ausente. `[PT2]`

**Imputación de valores faltantes vía diccionario derivado de una relación calculada**
```python
odometer_per_year_dict = df.groupby(['model', 'type'])['odometer_per_year'].median().to_dict()

def fill_in_model_year(row):
    if np.isnan(row['model_year']):
        row['dif_years'] = row['odometer'] / odometer_per_year_dict[(row['model'], row['type'])]
        row['model_year'] = row['year_posted'] - row['dif_years']
    return row

df = df.apply(fill_in_model_year, axis=1)
```
Cuando no se puede imputar directamente, a veces se puede *despejar* el valor faltante a partir de una relación matemática entre otras columnas (aquí: año del modelo = año del anuncio − antigüedad estimada por kilometraje/año típico del modelo). `[PT3]`

**Capar valores extremos por percentil/cuartil**
```python
data.loc[data['days_employed'] > 5537, 'days_employed'] = 5537   # capar al valor del Q3

def calcular_percentiles(tabla, columns, percentil):
    return {column: np.percentile(tabla[column], percentil) for column in columns}

percentiles = calcular_percentiles(dataset, ['calls_count', 'call_duration', 'total_call_duration'], 99)
dataset = dataset[(dataset['calls_count'] <= percentiles['calls_count']) &
                   (dataset['call_duration'] <= percentiles['call_duration'])]
```
Dos variantes del mismo patrón: capar (winsorize) un valor puntual, o filtrar filas completas que excedan el percentil 99 en varias columnas a la vez. `[PT2, Proyecto Final]`

**Detección y filtrado de outliers por rango intercuartílico (IQR)**
```python
inferior_limit = np.zeros(len(df), dtype=bool) + True
for feature in ['price', 'odometer', 'age_in_years_posted']:
    q25, q75 = df[feature].quantile(0.25), df[feature].quantile(0.75)
    iqr = q75 - q25
    upper = q75 + iqr * 1.5
    inferior_limit[np.where(df[feature] > upper)] = False

df_filtered = df[inferior_limit].reset_index(drop=True)
```
Método clásico de detección de outliers (1.5×IQR) aplicado a varias columnas simultáneamente con una máscara booleana acumulada. `[PT3]`

**Categorización de texto libre por palabras clave**
```python
def purpose_groups(row):
    if 'car' in row['purpose']:
        return 'car'
    if 'hous' in row['purpose'] or 'prop' in row['purpose'] or 'real est' in row['purpose']:
        return 'house'
    if 'wedd' in row['purpose']:
        return 'wedding'
    if 'educ' in row['purpose'] or 'uni' in row['purpose']:
        return 'education'

data['purpose_groups'] = data.apply(purpose_groups, axis=1)
```
Agrupa texto libre en categorías de negocio buscando substrings — útil cuando `purpose`/`comentario` tiene muchas variantes de redacción para la misma idea. `[PT2]`

**Categorización numérica por cuantiles**
```python
def income_class(income):
    q_rico, q_alto, q_medio, q_bajo = (data['total_income'].quantile(q) for q in (0.99, 0.85, 0.6, 0.25))
    if income < q_bajo: return 'pobre'
    if income < q_medio: return 'clase media baja'
    if income < q_alto: return 'clase media'
    if income < q_rico: return 'clase media alta'
    return 'rico'

data['income_class'] = data['total_income'].apply(income_class)
```
Convierte una variable continua en categorías de negocio basadas en su propia distribución (cuantiles), en vez de umbrales fijos arbitrarios. `[PT2]`

**Tasa de un evento binario por categoría (tabla de "morosidad"/conversión)**
```python
pivot = data.pivot_table(index='family_status', columns='debt', values='days_employed', aggfunc='count')
pivot['defaulter_percent'] = pivot[1] / (pivot[1] + pivot[0]) * 100
pivot.sort_values(by='defaulter_percent')
```
Patrón muy reutilizable: cuenta ocurrencias de una variable binaria (0/1) por categoría vía `pivot_table` y calcula el % directamente. Sirve igual para tasa de cancelación, de impago, de conversión, etc. `[PT2]`

**Validación cruzada de reglas de negocio entre columnas**
```python
inconsistencia = np.logical_and(dataset['is_missed_call'] == True, dataset['call_duration'] > 0)
dataset['is_missed_call'] = dataset['is_missed_call'].mask(inconsistencia, False)
```
`np.logical_and` + `.mask()` para corregir filas donde dos columnas se contradicen lógicamente (ej. "llamada perdida" con duración > 0). `[Proyecto Final]`

**Eliminar duplicados considerando solo un subconjunto de columnas**
```python
duplicates_mask = dataset.duplicated(subset=['user_id', 'date', 'direction', 'operator_id', 'calls_count'])
dataset.drop_duplicates(inplace=True)
```
`[Proyecto Final]`

---

## 4. Fechas y columnas derivadas

**Función `get_date()` — detectar columna de fecha y derivar mes/año**
```python
def get_date(df):
    columns = df.columns.tolist()
    idx = [columns.index(x) for x in columns if 'date' in x][0]
    df[columns[idx]] = pd.to_datetime(df[columns[idx]])
    df['month'] = df[columns[idx]].dt.month_name()
    df['year'] = df[columns[idx]].dt.year
```
Busca automáticamente la primera columna cuyo nombre contenga "date" y deriva mes/año — evita hardcodear el nombre de columna en cada proyecto. `[PT4, PT5, PT7, PT8, PT9, PT11]`

**Conversión de fecha a datetime + descomposición día/mes/semana/día de semana**
```python
dataset['date'] = pd.to_datetime(dataset['date']).dt.tz_convert(None).astype('datetime64[D]')
dataset['day']       = dataset['date'].dt.day
dataset['month']     = dataset['date'].dt.month
dataset['week']      = dataset['date'].dt.week
dataset['dayofweek'] = dataset['date'].dt.dayofweek
```
`[Proyecto Final]`

**Orden categórico de meses (para que los gráficos no queden alfabéticos)**
```python
df['month'] = pd.Categorical(df['month'],
    categories=['January', 'February', 'March', 'April', 'May', 'June', 'July',
                'August', 'September', 'October', 'November', 'December'], ordered=True)
```
Sin esto, `groupby('month')` y los gráficos de barras ordenan los meses alfabéticamente en vez de cronológicamente. `[PT4]`

**Extraer un ID embebido dentro de otra columna con regex vectorizado**
```python
extract_id = np.vectorize(lambda x: re.sub('.*_', '', x))
calls['id'] = extract_id(calls['id'])   # '1000_125' -> '125'
```
`[PT4]`

---

## 5. Agregación, pivote y agrupamiento

**Pivot table con conteo de únicos (`nunique`) como aggfunc**
```python
conversions = new_df.pivot_table(index='event_name', values='user_id', columns='exp_id',
                                  aggfunc=lambda x: x.nunique())
```
Cuenta usuarios únicos (no filas) por combinación de categorías — el patrón base de cualquier tabla de embudo o comparación de grupos A/B. `[Proyecto Integrado, PT8]`

**Combinar varios DataFrames mensuales con `reduce` + `merge`**
```python
from functools import reduce

data_frames = [calls_per_month, mins_per_month, messages_per_month, internet_per_month]
df = reduce(lambda left, right: pd.merge(left, right, on=['user_id', 'month'], how='outer'), data_frames)
```
Encadena múltiples `merge` sin escribirlos uno por uno, útil cuando hay 3+ tablas agregadas para unir por las mismas claves. `[PT4]`

**Aplicar una función de negocio fila a fila para calcular un importe (facturación)**
```python
def monthly_pay(row):
    plan = row['plan']
    fix_cost, call_limit, minut_fee = (20, 500, 0.03) if plan == 'surf' else (70, 3000, 0.01)
    call_revenue = max(0, row['minutes spent'] - call_limit) * minut_fee
    return fix_cost + call_revenue  # + lógica análoga para SMS/datos

df['revenue_pm'] = df.apply(monthly_pay, axis=1)
```
Patrón para modelar reglas de tarifas con excedentes (plan base + cobro por exceso sobre el límite incluido), aplicado fila a fila con `apply(axis=1)`. `[PT4]`

**Porcentaje sobre el total tras un `groupby().agg()`**
```python
in_out = dataset.groupby('direction').agg({'calls_count': 'sum'}).reset_index()
in_out['percentage'] = round(in_out['calls_count'] / in_out['calls_count'].sum() * 100, 2)
```
`[Proyecto Final]`

**Combinar varios criterios calculados por separado con `merge(how='outer')` + `isin` en AND**
```python
inefficient = out_ineff.merge(waiting_ineff, on='operator_id', how='outer').merge(missed_ineff, on='operator_id', how='outer')
inefficient_filtered = inefficient[
    inefficient['operator_id'].isin(out_ineff['operator_id']) &
    inefficient['operator_id'].isin(waiting_ineff['operator_id']) &
    inefficient['operator_id'].isin(missed_ineff['operator_id'])
]
```
Útil para quedarte solo con las filas que cumplen *todos* los criterios de "ineficiencia"/"riesgo" calculados en pasos separados. `[Proyecto Final]`

---

## 6. SQL

**JOIN + GROUP BY + COUNT DISTINCT + AVG**
```sql
SELECT books.book_id, books.title, authors.author AS author_book,
       COUNT(DISTINCT review_id) AS number_review,
       AVG(rating) AS rating_avg
FROM books
    LEFT JOIN reviews ON books.book_id = reviews.book_id
    LEFT JOIN ratings ON books.book_id = ratings.book_id
    LEFT JOIN authors ON books.author_id = authors.author_id
GROUP BY books.book_id, authors.author_id
ORDER BY rating_avg DESC
```
`[Proyecto Final Bootcamp - SQL]`

**Window function (`COUNT() OVER PARTITION BY`)**
```sql
SELECT DISTINCT publishers.publisher_id, publishers.publisher,
       COUNT(books.book_id) OVER (PARTITION BY publishers.publisher_id) AS count_books
FROM books
    INNER JOIN publishers USING (publisher_id)
WHERE books.num_pages > 50
ORDER BY count_books DESC
LIMIT 1
```
Cuenta sin colapsar filas — alternativa a `GROUP BY` cuando necesitas conservar el detalle. `[Proyecto Final Bootcamp - SQL]`

**CTE (`WITH`) + filtro por subquery**
```sql
WITH books_rating(book_id, title, author, count_marks, avg_rating) AS (
    SELECT DISTINCT book_id, books.title, authors.author,
           COUNT(rating_id) OVER (PARTITION BY book_id) AS count_marks,
           ROUND(AVG(rating) OVER (PARTITION BY book_id), 2) AS avg_rating
    FROM books
        LEFT JOIN ratings USING (book_id)
        LEFT JOIN authors USING (author_id)
)
SELECT book_id, title, author, avg_rating
FROM books_rating
WHERE count_marks > 50 AND avg_rating = (
    SELECT avg_rating FROM books_rating WHERE count_marks > 50 ORDER BY avg_rating DESC LIMIT 1
)
```
`[Proyecto Final Bootcamp - SQL]`

**Doble CTE encadenada (`HAVING` + join entre CTEs)**
```sql
WITH users_rated_50_plus (username) AS (
    SELECT username FROM ratings GROUP BY username HAVING COUNT(rating_id) > 50
),
users_count_reviews (username, count_reviews) AS (
    SELECT DISTINCT username,
           COUNT(review_id) OVER (PARTITION BY username) AS count_reviews
    FROM users_rated_50_plus INNER JOIN reviews USING (username)
)
SELECT ROUND(AVG(count_reviews), 2) AS avg_reviews FROM users_count_reviews
```
Primero filtra con `HAVING` sobre un agregado, luego calcula una métrica sobre ese subconjunto ya filtrado. `[Proyecto Final Bootcamp - SQL]`

> Nota: `PT6` (taxis de Chicago) usa datos ya extraídos por SQL en 3 CSVs, pero el notebook en sí no contiene sentencias SQL.

---

## 7. Embudos de conversión y eventos

**Conversión paso a paso de un embudo (con `shift`)**
```python
users_by_event = new_df.groupby("event_name")["user_id"].nunique().sort_values(ascending=False).reset_index()
users_by_event["users_in_previous_step"] = users_by_event["user_id"].shift(1)
users_by_event["conversion_previous_step"] = users_by_event["user_id"] / users_by_event["users_in_previous_step"]
users_by_event["dropoff_rate"] = 1 - users_by_event["conversion_previous_step"]
```
`shift(1)` trae el valor del paso anterior a la misma fila, permitiendo calcular la conversión y el abandono paso a paso. `[Proyecto Integrado]`

**Visualización de embudo (Plotly)**
```python
import plotly.graph_objects as go
import plotly.express as px

fig = go.Figure(go.Funnel(y=['MainScreenAppear', 'OffersScreenAppear', 'CartScreenAppear', 'PaymentScreenSuccessful'],
                           x=[7419, 4593, 3734, 3539]))
fig.show()

# Alternativa rápida directo desde un DataFrame:
fig = px.funnel(embudo, x='user_id', y='event_name', color='exp_id')
```
`[Proyecto Integrado]`

**Detectar usuarios "contaminados" en más de un grupo experimental**
```python
usuarios_en_ambos_grupos = df[df.groupby('user_id')['exp_id'].transform('nunique') > 1]
df_limpio = df[~df['user_id'].isin(usuarios_en_ambos_grupos['user_id'].unique())]
```
`transform('nunique') > 1` identifica usuarios que aparecen en más de un grupo (A y B a la vez) — hay que excluirlos antes de testear. `[Proyecto Integrado, PT8]`

**Filtrar filas por rango de fechas del experimento**
```python
def eliminar_filas_por_rango_de_fechas(df, columna_fecha, fecha_inicio, fecha_fin):
    df[columna_fecha] = pd.to_datetime(df[columna_fecha])
    return df.loc[(df[columna_fecha] >= fecha_inicio) & (df[columna_fecha] <= fecha_fin)]
```
Recorta el dataset al periodo de estudio real del experimento, excluyendo ruido de antes/después. `[Proyecto Final de pruebas AB]`

---

## 8. Cohortes, LTV, CAC, ROMI

**Retención por cohorte mensual**
```python
first_activity_date = visits.groupby('uid')['start_ts'].min().rename('first_activity_date')
user_activity = visits[['uid', 'start_ts']].join(first_activity_date, on='uid')

user_activity['activity_month'] = user_activity['start_ts'].astype('datetime64[M]')
user_activity['first_activity_month'] = user_activity['first_activity_date'].astype('datetime64[M]')
user_activity['cohort_lifetime'] = (
    (user_activity['activity_month'] - user_activity['first_activity_month']) / np.timedelta64(1, 'M')
).round().astype('int')

cohorts = user_activity.groupby(['first_activity_month', 'cohort_lifetime']).agg({'uid': 'nunique'}).reset_index()
initial = cohorts[cohorts['cohort_lifetime'] == 0][['first_activity_month', 'uid']].rename(columns={'uid': 'cohort_users'})
cohorts = cohorts.merge(initial, on='first_activity_month')
cohorts['retention'] = cohorts['uid'] / cohorts['cohort_users']
```
Patrón estándar: agrupar por mes de primera actividad ("cohorte") y "edad" de la cohorte en meses, luego dividir usuarios activos entre usuarios iniciales. `[PT7]`

**Heatmap de retención (o LTV/CAC/ROMI) por cohorte**
```python
pivot = cohorts.pivot_table(index='first_activity_month', columns='cohort_lifetime', values='retention', aggfunc='sum')

plt.figure(figsize=(14, 6))
sns.heatmap(pivot, annot=True, fmt='.1%', linewidths=1, linecolor='skyblue', cmap='BuPu', vmin=0, vmax=0.1
).set_yticklabels(pivot.index.strftime('%d-%m-%Y'))
plt.title('Cohorts: User Retention')
plt.show()
```
Mismo patrón de visualización reutilizado para LTV/CAC/ROMI, solo cambia la métrica en `values` y el `fmt`/rango de color. `[PT7]`

**Días hasta la conversión (primera visita → primera compra)**
```python
conversion = order.groupby('uid').agg({'buy_ts': 'first'}).reset_index().join(first_activity_date, on='uid')
conversion['conversion_days'] = (conversion['buy_ts'].dt.date - conversion['first_activity_date'].dt.date).apply(lambda x: x.days)
conversion.loc[conversion['conversion_days'] < 0, 'conversion_days'] = 0  # ruido de datos
```
`[PT7]`

**LTV (Lifetime Value) por cohorte**
```python
cohort_users = order.groupby('first_order_month').agg({'uid': 'nunique'}).rename(columns={'uid': 'cohort_users'})
ltv_cohorts = order.groupby(['first_order_month', 'order_month']).agg({'revenue': 'sum'}).rename(columns={'revenue': 'gross_profit'})
ltv_cohorts = ltv_cohorts.merge(cohort_users, on='first_order_month')
ltv_cohorts['ltv'] = ltv_cohorts['gross_profit'] / ltv_cohorts['cohort_users']

# LTV acumulado en el tiempo:
ltv_pivot = ltv_cohorts.pivot_table(index='first_order_month', columns='age_month', values='ltv', aggfunc='mean').cumsum(axis=1)
```
LTV = ingresos de la cohorte en un mes dado / usuarios que empezaron en esa cohorte. `[PT7]`

**CAC (Customer Acquisition Cost) y ROMI**
```python
ltv_cohorts = ltv_cohorts.merge(cost.groupby('month').agg({'costs': 'sum'}), left_on='first_order_month', right_on='month')
ltv_cohorts['cac'] = ltv_cohorts['costs'] / ltv_cohorts['cohort_users']
ltv_cohorts['romi'] = ltv_cohorts['ltv'] / ltv_cohorts['cac']
```
CAC = gasto de marketing del mes / nuevos usuarios captados. ROMI = LTV / CAC (>1 = la inversión se recupera con ganancia). Se puede agrupar por `source_id` en vez de por mes para obtener CAC/ROMI por canal de adquisición. `[PT7]`

**DAU / WAU / MAU**
```python
visits['visits_month'] = visits['start_ts'].astype('datetime64[M]')
visits['visits_week']  = visits['start_ts'].astype('datetime64[W]')
visits['visits_date']  = visits['start_ts'].dt.date

dau = visits.groupby('visits_date')['uid'].nunique().mean()
wau = visits.groupby('visits_week')['uid'].nunique().mean()
mau = visits.groupby('visits_month')['uid'].nunique().mean()
```
`[PT7]`

**Duración de sesión + filtro de outliers imposibles**
```python
visits['session_length'] = (visits['end_ts'] - visits['start_ts']).dt.total_seconds() / 60
visits = visits.query('0 < session_length <= 120')  # descarta sesiones de 0 min o > 2h
```
`[PT7]`

---

## 9. Priorización de hipótesis (ICE/RICE)

```python
hypotheses['ICE']  = (hypotheses['impact'] * hypotheses['confidence']) / hypotheses['effort']
hypotheses['RICE'] = (hypotheses['reach'] * hypotheses['impact'] * hypotheses['confidence']) / hypotheses['effort']

hypotheses[['hypothesis', 'ICE', 'RICE']].sort_values(by='RICE', ascending=False)
```
RICE añade el factor "Reach" (alcance de usuarios) frente a ICE — compara ambos rankings para ver cómo cambia la prioridad al considerar el alcance. `[PT8]`

**Comparación visual ICE vs RICE con anotaciones**
```python
ax = hypotheses[['hypothesis', 'ICE', 'RICE']].plot(kind='bar', figsize=(8, 6))
for p in ax.patches:
    ax.annotate(str(p.get_height().round()), (p.get_x() * 1.005, p.get_height() * 1.005), rotation=90)
```
`[PT8]`

---

## 10. Test A/B y pruebas de hipótesis estadísticas

**Test Z de proporciones "manual" (fórmula explícita)**
```python
def check_hypothesis(grp1, grp2, event, alpha=0.01):
    p1 = success[grp1] / trials[grp1]
    p2 = success[grp2] / trials[grp2]
    p_combined = (success[grp1] + success[grp2]) / (trials[grp1] + trials[grp2])
    z_value = (p1 - p2) / math.sqrt(p_combined * (1 - p_combined) * (1/trials[grp1] + 1/trials[grp2]))
    p_value = (1 - stats.norm(0, 1).cdf(abs(z_value))) * 2
    print('Rechazar H0' if p_value < alpha else 'No se rechaza H0')
```
`[Proyecto Integrado]`

**Mismo test con `statsmodels` (más limpio, aplicado en bucle a todo el embudo)**
```python
from statsmodels.stats.proportion import proportions_ztest

def test_hypothesis(grp1, grp2, alpha, event):
    count = [success[event][grp1], success[event][grp2]]
    nobs = [trials[grp1], trials[grp2]]
    z_value, p_value = proportions_ztest(count, nobs)
    print('Se rechaza H0' if p_value < alpha else 'No se rechaza H0', 'para', event)

for event in test_groups.event_name.unique():
    test_hypothesis('A', 'B', 0.05, event)
```
`[Proyecto Final de pruebas AB]`

**Test Mann-Whitney U (no paramétrico, robusto a outliers)**
```python
p_value = st.mannwhitneyu(sampleA, sampleB)[1]
print("Diferencia relativa:", sampleB.mean() / sampleA.mean() - 1)
print('Se rechaza H0' if p_value < 0.05 else 'No se rechaza H0')
```
Preferible al t-test cuando los datos de conversión/ingresos tienen outliers marcados o no siguen una normal — muy común en tests A/B de e-commerce. `[PT8]`

**t-test de dos muestras independientes**
```python
from scipy.stats import ttest_ind

t_stat, p_val = ttest_ind(grupo_a, grupo_b, equal_var=True)   # equal_var=False → test de Welch
print('Rechazamos H0' if p_val < 0.05 else 'No podemos rechazar H0')
```
Usar `equal_var=False` (test de Welch) cuando no se puede asumir que ambos grupos tienen varianza igual. `[PT5, PT6, PT4]`

**t-test de una muestra contra la media poblacional**
```python
t_statistic, p_value = stats.ttest_1samp(muestra, poblacion.mean())
```
Compara la media de un subgrupo (ej. llamadas perdidas los viernes) contra la media general. `[Proyecto Final]`

**ANOVA de un factor (3+ grupos)**
```python
statistic, p_value = stats.f_oneway(plan_A, plan_B, plan_C)
```
Alternativa a hacer múltiples t-tests por pares cuando hay que comparar 3 o más grupos a la vez. `[Proyecto Final]`

**Detección de anomalías por percentil antes de re-testear un A/B**
```python
usersWithManyOrders = ordersByUsersA[ordersByUsersA['orders'] > 2]['userId']
usersWithExpensiveOrders = orders[orders['revenue'] > 830]['visitorId']
abnormalUsers = pd.concat([usersWithManyOrders, usersWithExpensiveOrders]).drop_duplicates()

sampleFiltered = ordersByUsersA[~ordersByUsersA['userId'].isin(abnormalUsers)]['orders']
```
Vuelve a correr el test excluyendo usuarios con comportamiento anómalo (compradores compulsivos, pedidos gigantes) para comprobar si el resultado es robusto. `[PT8]`

---

## 11. Preprocesamiento para Machine Learning

**Escalado estándar + train/test split (sin fuga de datos)**
```python
from sklearn.preprocessing import StandardScaler
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=0)

scaler = StandardScaler()
scaler.fit(X_train)                 # ajustar SOLO con train
X_train_st = scaler.transform(X_train)
X_test_st = scaler.transform(X_test)
```
Clave: `fit` únicamente sobre el set de entrenamiento; `test` solo se transforma, nunca se usa para ajustar el escalador. `[PT11]`

---

## 12. Modelos de clasificación y regresión

**Regresión logística**
```python
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score, precision_score, recall_score

lr_model = LogisticRegression(random_state=42)
lr_model.fit(X_train_st, y_train)
predictions = lr_model.predict(X_test_st)
probabilities = lr_model.predict_proba(X_test_st)

print('Exactitud: {:.2f}'.format(accuracy_score(y_test, predictions)))
print('Precisión: {:.2f}'.format(precision_score(y_test, predictions)))
print('Recall: {:.2f}'.format(recall_score(y_test, predictions)))
```
`[PT11]`

**Random Forest (mismo flujo, para comparar contra logística)**
```python
from sklearn.ensemble import RandomForestClassifier

rf_model = RandomForestClassifier(random_state=42)
rf_model.fit(X_train_st, y_train)
predictions = rf_model.predict(X_test_st)
```
`[PT11]`

---

## 13. Clustering

**Flujo completo: dendrograma + KMeans + silhouette score**
```python
from scipy.cluster.hierarchy import dendrogram, linkage
from sklearn.cluster import KMeans
from sklearn.metrics import silhouette_score

x_sc = StandardScaler().fit_transform(X)          # 1. estandarizar (obligatorio para KMeans)

linked = linkage(x_sc, method='ward')              # 2. dendrograma para decidir n° de clusters
dendrogram(linked, orientation='top')

km = KMeans(n_clusters=5, random_state=0)          # 3. entrenar KMeans con el n decidido
labels = km.fit_predict(x_sc)

sil_score = silhouette_score(x_sc, labels)         # 4. validar calidad de la separación

df['cluster'] = labels                             # 5. perfilar cada cluster
cluster_profile = df.groupby('cluster').mean()
```
`[PT11]`

**Distribución de una feature por cluster (histograma con `hue`)**
```python
for col in ['age', 'lifetime', 'avg_class_frequency_total']:
    sns.histplot(data=df, x=col, hue='cluster', kde=True, palette="tab10")
    plt.show()
```
`[PT11]`

**Tasa de un evento binario por cluster**
```python
churn_rate = (df.query('churn == 1').groupby('cluster')['churn'].count() /
              df.groupby('cluster')['churn'].count())
```
Reutiliza el mismo patrón de "tasa de evento por categoría" de la sección 3, ahora usando el cluster como categoría — útil para priorizar qué segmento retener. `[PT11]`

---

## 14. Métricas de evaluación de modelos

**Matriz de correlación (detectar multicolinealidad antes de modelar)**
```python
plt.figure(figsize=(15, 9))
sns.heatmap(df.corr(), annot=True, square=True)
```
`[PT11]`

**Comparar la media de cada feature entre clases del target (proxy de importancia de variables)**
```python
df.groupby('churn').mean()
```
Forma rápida de intuir qué variables separan mejor las clases antes de entrenar cualquier modelo. `[PT11]`

**Histogramas por clase objetivo (EDA previo a clasificación)**
```python
for feature in columnas_numericas:
    sns.histplot(data=df, x=feature, hue='churn')
    plt.show()
```
`[PT11]`

---

## 15. Visualización

**Heatmap con formato/escala fija (cohortes, correlación, tendencias)**
```python
sns.heatmap(pivot, annot=True, fmt='.2f', linewidths=1, linecolor='black', vmin=4, vmax=13)
```
`vmin`/`vmax` fijos permiten comparar el color entre varios heatmaps del mismo informe (ej. LTV de distintos meses). `[PT7]`

**Serie temporal con línea de referencia en la media**
```python
dau.plot(figsize=(8, 4))
plt.hlines(int(dau.mean()), visits['visits_date'].min(), visits['visits_date'].max(), color='red', linestyle='dotted')
```
`[PT7]`

**Top-N en barras horizontales**
```python
top_n = df.sort_values(by='average_trips', ascending=False).head(10)
top_n.plot(x='dropoff_location_name', y='average_trips', kind='barh', figsize=(20, 6))
```
`[PT6]`

**Barras con el valor anotado encima de cada una**
```python
ax = sns.barplot(data=df.sort_values('avg_seats', ascending=False), x='type', y='avg_seats')
for p in ax.patches:
    ax.annotate(format(p.get_height(), '.2f'), xy=(p.get_x() + p.get_width()/2, p.get_height()),
                ha='center', va='center', xytext=(0, 10), textcoords='offset points')
```
`[PT9, PT5, Proyecto Final]`

**Barras/histograma de densidad comparando dos grupos (`sns.kdeplot` superpuesto)**
```python
sns.kdeplot(df_surf['minutes spent'], shade=True, label='surf')
sns.kdeplot(df_ultimate['minutes spent'], shade=True, label='ultimate')
plt.legend()
```
`[PT4]`

**Barras/áreas/boxplot interactivos con Plotly Express (mismo dato, distinta vista)**
```python
import plotly.express as px

px.bar(genre_comp, x="genre", y=['eu_sales', 'jp_sales', 'na_sales'], barmode='group')
px.area(platform, x="year_of_release", y="total_sales", color="platform", line_group="platform")
px.box(filtered, x="platform", y="total_sales", color='platform')
px.imshow(trend.T)  # heatmap interactivo sobre una tabla pivotada (año x categoría)
```
Plotly Express da interactividad (zoom, hover) prácticamente gratis sobre los mismos DataFrames que ya usarías con matplotlib/seaborn — útil para dashboards o exploración rápida. `[PT5]`

**Gráfico de pastel con porcentaje automático**
```python
plt.pie(df['counts'], labels=df['type'], autopct='%0.f%%')
```
`[PT9]`

**Múltiples subplots en bucle**
```python
fig, axs = plt.subplots(len(columnas), figsize=(10, 6 * len(columnas)))
for i, col in enumerate(columnas):
    axs[i].bar(data.index, data.values)
    axs[i].set_title(f'Distribución de {col}')
plt.tight_layout()
```
`[Proyecto Final]`

**Función reutilizable de barras agrupadas con conteo y etiquetas automáticas**
```python
def plot_snsbar(df, x, y, title):
    data = df.groupby([x])[y].count().sort_values(ascending=False).reset_index()
    ax = sns.barplot(x=x, y=y, data=data)
    ax.set_title(title)
    ax.set_xticklabels(data[x], rotation=90)
```
`[PT5]`

**Función reutilizable de barras con filtro opcional + anotaciones de valor**
```python
def plot_distribution(df, x, y, column='', value='', func=np.sum):
    plot_df = df[df[column] == value] if column else df
    plot_df = plot_df.pivot_table(index=x, values=y, aggfunc=func)
    ax = plot_df.plot(kind='bar', figsize=(12, 6), rot=45, edgecolor='silver', legend=False)
    for p in ax.patches:
        ax.annotate(str(round(p.get_height(), 2)), (p.get_x(), p.get_height()))
```
La más completa de las funciones de graficado del repo: agrega, filtra opcionalmente por una categoría, grafica y anota — vale la pena reutilizarla tal cual en vez de reescribir la lógica de barras cada vez. `[PT5]`

---

## 16. Funciones utilitarias varias

**Filtro parametrizado envuelto en función (evita copiar/pegar el mismo filtro)**
```python
def number_tracks(day, city):
    track_list = df[(df['day'] == day) & (df['city'] == city)]
    return track_list['userid'].count()
```
`[PT1]`

**Filtro + agrupamiento + top-N envuelto en función**
```python
def genre_weekday(df, day, time1, time2):
    genre_df = df[(df['day'] == day) & (df['time'] >= time1) & (df['time'] <= time2)]
    return genre_df.groupby('genre')['genre'].count().sort_values(ascending=False)[:15]
```
`[PT1]`

**Extracción de nombre de calle desde una dirección completa (parsing de texto en cadena)**
```python
def get_streetname(x):
    return ' '.join(w for w in x.replace("#", "").replace("/", "").split() if not w.isdigit())

def filter_streetname(direccion):
    partes, sufijos = [], ['BLVD', 'ST', 'AVE', 'RD', 'DR', 'WAY']
    for palabra in direccion.split(' '):
        if palabra in sufijos:
            partes.append(palabra)
            return " ".join(partes)
        partes.append(palabra)
    return " ".join(partes)

df['street_name'] = df['address'].apply(get_streetname).apply(filter_streetname)
```
Parsing en dos pasos encadenado con `.apply().apply()`: primero quita números, luego corta en el primer sufijo de tipo de vía (Blvd, St, Ave...). `[PT9]`

---

## Nota sobre proyectos sin snippets de ML

En `Proyecto Final.ipynb` (CallMeMaybe / Model Fitness, dentro de `Proyecto Final Bootcamp/`) se importan `StandardScaler`, `train_test_split`, `LogisticRegression`, `RandomForestClassifier`, `GradientBoostingClassifier`, `KMeans` y métricas de clasificación, pero no llegan a usarse en el cuerpo del notebook — el análisis terminó siendo EDA + detección de operadores ineficientes por percentiles + pruebas de hipótesis (ANOVA/t-test), no un modelo entrenado. Si buscas el flujo real de clasificación/clustering con gimnasios, está en `PT11/10. Pronostico y Prediccion.ipynb` (secciones 11-14 de este documento).
