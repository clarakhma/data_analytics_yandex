## Factores que influyen en el precio de un vehiculo en Crankshaft List

### Descripción del proyecto
Cientos de anuncios gratuitos de vehículos se publican en tu sitio web cada día. se estudiarán los datos recopilados durante los últimos años y determinar qué factores influyen en el precio de un vehículo.

### Preprocesamiento de datos
Identifica y estudia los valores ausentes:

En algunos casos hay una forma obvia de reemplazar valores ausentes. Por ejemplo, si un campo booleano contiene solo valores True, es razonable asumir que los valores ausentes son False. Para otros tipos de datos no hay arreglos tan obvios, y hay casos en los que el hecho de que haya un valor ausente es significativo. En tales casos, no sustituyas los valores.
Cuando sea apropiado, sustituye los valores. Explica por qué has decidido hacerlo así y cómo has seleccionado los valores sustitutos.
Describe los factores que puedan haber resultado en valores ausentes.
Convierte los datos en los tipos necesarios:

Indica las columnas donde los tipos de datos necesitan ser cambiados y explica por qué.

### Calcula y añade a la tabla lo siguiente:
Día de la semana, mes y año en el que el anuncio se colocó
Los años del vehículo cuando el anuncio se colocó
La media de millaje del vehículo por año
En la columna condition, reemplaza los valores de cadena con una escala numérica:

nuevo = 5
como nuevo = 4
excelente = 3
bien = 2
bastante = 1
para rescate = 0

### Lleva a cabo el análisis exploratorio de datos siguiendo las siguientes instrucciones:

Estudia los siguientes parámetros: precio, años del vehículo cuando se colocó el anuncio, millaje, número de cilindrada y condición. Traza histogramas para cada uno de los parámetros. Estudia cómo los valores atípicos afectan a la forma y legitimidad de los histogramas.

Determina los límites superiores de los valores atípicos, elimina dichos valores y almacénalos en un DataFrame apartado, y continúa tu trabajo con los datos filtrados.

Utiliza los datos filtrados para plantear nuevos histogramas. Compáralos con los histogramas anteriores (aquellos con los valores atípicos incluidos). Obtén conclusiones de cada histograma.

Estudia cuántos días los anuncios fueron mostrados (days_listed). Traza un histograma. Calcula la media y la mediana. Describe la vida útil habitual de un anuncio. Determina cuándo se eliminan rápidamente los anuncios y cuándo son publicados por un tiempo anormalmente largo.

Analiza el número de anuncios y el precio medio para cada tipo de vehículo. Traza un gráfico mostrando la dependencia de los números de anuncios en cada tipo de vehículo. Selecciona los dos tipos con un mayor número de anuncios.
¿Qué factores impactan más sobre el precio? Toma cada uno de los tipos más populares que has detectado en la fase anterior y estudia si el precio depende de la edad, millaje, condición, tipo de transmisión y color. Para las variables categóricas (tipo de transmisión y color), traza gráficos de caja y bigotes, y crea gráficos de dispersión para el resto. Cuando analices variables categóricas, observa que las categorías deben tener al menos 50 anuncios; si no, sus parámetros no serán válidos para el análisis.

### Descripción de los datos
El conjunto de datos contiene los siguientes datos:

- price
- model_year
- model
- condition
- cylinders
- fuel — gasolina, diesel, etc.
- odometer — el millaje del vehículo cuando el anuncio fue publicado
- transmission
- paint_color
- is_4wd — si el vehículo tiene tracción a las 4 ruedas (tipo Booleano)
- date_posted — la fecha en la que el anuncio fue publicado
- days_listed — desde la publicación hasta que se elimina

## English

## Factors Influencing Vehicle Price on Crankshaft List

### Project Description
Hundreds of free vehicle listings are posted on your website every day. We will study data collected over the past years to determine which factors influence the price of a vehicle.

### Data Preprocessing
Identify and address missing values:

In some cases, there is an obvious way to replace missing values. For example, if a boolean field contains only True values, it is reasonable to assume that missing values are False. For other data types, there may not be such obvious fixes, and there are cases where the absence of a value is meaningful. In such cases, do not substitute the values.
Where appropriate, substitute values. Explain why you have chosen to do so and how you selected replacement values.
Describe factors that may have resulted in missing values.
Convert data into necessary types:

Specify columns where data types need to be changed and explain why.

Calculate and Add the following to the table:
Day of the week, month, and year the listing was posted.
Vehicle years when the listing was posted.
Average mileage per year for the vehicle.
In the condition column, replace string values with a numerical scale:

new = 5
like new = 4
excellent = 3
good = 2
fair = 1
salvage = 0

### Perform Exploratory Data Analysis (EDA) following these instructions:
Study the following parameters: price, vehicle years when listed, mileage, number of cylinders, and condition. Plot histograms for each parameter. Examine how outliers affect the shape and validity of histograms.

Determine the upper limits of outliers, remove those values, store them in a separate DataFrame, and continue your work with filtered data.

Use filtered data to plot new histograms. Compare them with previous histograms (those including outliers). Draw conclusions from each histogram.

Study how many days listings were displayed (days_listed). Plot a histogram. Calculate mean and median. Describe the typical lifespan of a listing. Determine when listings are quickly removed and when they are unusually long-lived.

Analyze the number of listings and average price for each vehicle type. Plot a graph showing dependency of listing numbers on each vehicle type. Select the two types with the highest number of listings.

Which factors most impact price? Take each of the popular types identified in the previous phase and study whether price depends on age, mileage, condition, transmission type, and color. For categorical variables (transmission type and color), plot box-and-whisker plots, and create scatter plots for the rest. When analyzing categorical variables, note that categories should have at least 50 listings for their parameters to be valid for analysis.

### Data Description
The dataset contains the following data:

price
model_year
model
condition
cylinders
fuel — gasoline, diesel, etc.
odometer — vehicle mileage when listed
transmission
paint_color
is_4wd — whether the vehicle is 4-wheel drive (Boolean type)
date_posted — date the listing was posted
days_listed — days from posting to removal  
