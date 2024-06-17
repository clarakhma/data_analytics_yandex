## Operador de telecomunicaciones Megaline

### Descripcion del proyecto
La empresa ofrece a sus clientes dos tarifas de prepago, Surf y Ultimate. El departamento comercial quiere saber cuál de los planes genera más ingresos para poder ajustar el presupuesto de publicidad.

Vas a realizar un análisis preliminar de las tarifas basado en una selección de clientes relativamente pequeña. Tendrás los datos de 500 clientes de Megaline: quiénes son los clientes, de dónde son, qué tarifa usan, así como la cantidad de llamadas que hicieron y los mensajes de texto que enviaron en 2018. Tu trabajo es analizar el comportamiento de los clientes y determinar qué tarifa de prepago genera más ingresos.

### Descripción de las tarifas
Nota: Megaline redondea los segundos a minutos y los megabytes a gigabytes. Para llamadas, cada llamada individual se redondea: incluso si la llamada duró solo un segundo, se contará como un minuto. Para tráfico web, las sesiones web individuales no se redondean. En vez de esto, el total del mes se redondea hacia arriba. Si alguien usa 1025 megabytes este mes, se le cobrarán 2 gigabytes.

- Surf
Pago mensual: 20$
500 minutos al mes, 50 SMS y 15 GB de datos
Si se exceden los límites del paquete:
1 minuto: 3 centavos
1 SMS: 3 centavos
1 GB de datos: 10$

- Ultimate

Pago mensual: 70$
3000 minutos al mes, 1000 SMS y 30 GB de datos
Si se exceden los límites del paquete:
1 minuto: 1 centavo
1 SMS: 1 centavo
1 GB de datos: 7$

### Descricpcion de los datos
 Megaline redondea los segundos a minutos y los megabytes a gigabytes. Para llamadas, cada llamada individual se redondea: incluso si la llamada duró solo un segundo, se contará como un minuto. Para tráfico web, las sesiones web individuales no se redondean. En vez de esto, el total del mes se redondea hacia arriba. Si alguien usa 1025 megabytes este mes, se le cobrarán 2 gigabytes.


#### La tabla users (datos sobre los usuarios):

user_id — identificador único del usuario
first_name — nombre del usuario
last_name — apellido del usuario
age — edad del usuario (en años)
reg_date — fecha de suscripción (dd, mm, aa)
churn_date — la fecha en que el usuario dejó de usar el servicio (si el valor es ausente, la tarifa se estaba usando cuando se recuperaron estos datos)
city — ciudad de residencia del usuario
plan — nombre de la tarifa

#### La tabla calls (datos sobre las llamadas):

id — identificador único de la llamada
call_date — fecha de la llamada
duration — duración de la llamada (en minutos)
user_id — el identificador del usuario que realiza la llamada

#### La tabla messages (datos sobre los SMS):

id — identificador único del SMS
message_date — fecha del SMS
user_id — el identificador del usuario que manda el SMS

#### La tabla internet (datos sobre las sesiones web):

id — identificador único de la sesión
mb_used — el volumen de datos gastados durante la sesión (en megabytes)
session_date — fecha de la sesión web
user_id — identificador del usuario

#### La tabla plans (datos sobre las tarifas):

plan_name — nombre de la tarifa
usd_monthly_fee — pago mensual en dólares estadounidenses
minutes_included — minutos incluidos al mes
messages_included — SMS incluidos al mes
mb_per_month_included — datos incluidos al mes (en megabytes)
usd_per_minute — precio por minuto tras exceder los límites del paquete (por ejemplo, si el paquete incluye 100 minutos el operador cobrará el minuto 101)
usd_per_message — precio por SMS tras exceder los límites del paquete
usd_per_gb — precio por gigabyte de los datos extra tras exceder los límites del paquete (1 GB = 1024 megabytes)

## ENGLISH

## Megaline Telecommunications Operator

### Project Description
The company offers its customers two prepaid plans, Surf and Ultimate. The marketing department wants to know which plan generates more revenue to adjust the advertising budget accordingly.

You will conduct a preliminary analysis of the plans based on a relatively small sample of customers. You will have data for 500 Megaline customers: who they are, where they are from, which plan they use, as well as the number of calls they made and text messages they sent in 2018. Your task is to analyze customer behavior and determine which prepaid plan generates more revenue.

### Description of Plans
Note: Megaline rounds seconds to minutes and megabytes to gigabytes. For calls, each individual call is rounded up: even if the call lasted only one second, it will be counted as one minute. For internet traffic, individual web sessions are not rounded. Instead, the total for the month is rounded up. If someone uses 1025 megabytes this month, they will be charged for 2 gigabytes.

#### Surf
Monthly payment: $20
500 minutes per month, 50 SMS, and 15 GB of data
Exceeding the package limits:
1 minute: 3 cents
1 SMS: 3 cents
1 GB of data: $10

#### Ultimate
Monthly payment: $70
3000 minutes per month, 1000 SMS, and 30 GB of data
Exceeding the package limits:
1 minute: 1 cent
1 SMS: 1 cent
1 GB of data: $7

### Data Description
Megaline rounds seconds to minutes and megabytes to gigabytes. For calls, each individual call is rounded up: even if the call lasted only one second, it will be counted as one minute. For internet traffic, individual web sessions are not rounded. Instead, the total for the month is rounded up. If someone uses 1025 megabytes this month, they will be charged for 2 gigabytes.

- Users table (user data):

user_id — unique user identifier
first_name — user's first name
last_name — user's last name
age — user's age (in years)
reg_date — subscription date (dd, mm, yy)
churn_date — date when the user stopped using the service (if absent, the tariff was in use when this data was retrieved)
city — user's city of residence
plan — name of the plan
Calls table (call data):
id — unique call identifier
call_date — call date
duration — call duration (in minutes)
user_id — identifier of the user making the call

- Messages table (SMS data):
  
id — unique SMS identifier
message_date — SMS date
user_id — identifier of the user sending the SMS

- Internet table (web session data):
  
id — unique session identifier
mb_used — volume of data spent during the session (in megabytes)
session_date — web session date
user_id — user identifier

- Plans table (plan data):

plan_name — plan name
usd_monthly_fee — monthly payment in US dollars
minutes_included — included minutes per month
messages_included — included SMS per month
mb_per_month_included — included data per month (in megabytes)
usd_per_minute — price per minute after exceeding package limits (e.g., if the package includes 100 minutes, the operator will charge for minute 101)
usd_per_message — price per SMS after exceeding package limits
usd_per_gb — price per gigabyte of extra data after exceeding package limits (1 GB = 1024 megabytes)
