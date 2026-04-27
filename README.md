# Proyecto_Final_Data_Analytics

Caso de Uso: Caso 3 - Turismo digital y precios de alojamiento en NYC


Integrantes: 

- Luciana Pacheco
- Eurymar Umbria
- Giraldo Ruiz
- Matias Amaya
- Manuel Aguirre

# Roles sugeridos:
- Data Analyst: Encargado del Notebook y limpieza de datos.
- Business Strategist: Definición del problema e hipótesis.
- Documentation Lead: Redacción del informe y gestión de GitHub.2. Descripción del Problema de Negocio 

Contexto: Trabajamos para "Skyline Analytics", una consultora boutique que asesora a nuevos inversionistas de Real Estate en Nueva York.

El Problema: El mercado de alquileres de corto plazo en NYC es extremadamente competitivo y está sujeto a regulaciones estrictas y variaciones de demanda por zonas. Los nuevos propietarios no saben cómo fijar precios competitivos ni qué características (amenities, ubicación, tipo de habitación) garantizan una alta tasa de ocupación sin sacrificar el margen de ganancia.

Relevancia: Optimizar el precio basándose en datos puede incrementar los ingresos anuales de un anfitrión hasta en un 20-30% y reducir los periodos de propiedad vacía

# Descripción de los Datos Fuente Principal: 
New York City Airbnb Open Data (Kaggle). Contiene información sobre listados, disponibilidad, precios y ubicación geográfica de más de 48,000 registros en 2019.

Fuente de Enriquecimiento: Índice de Criminalidad por Vecindario de la Policía de Nueva York (NYPD Complaint Data) o Puntos de Interés (POIs) cercanos a estaciones de Metro.

Variables Clave: price (target), neighbourhood_group (Manhattan, Brooklyn, etc.), room_type, minimum_nights, number_of_reviews (proxy de ocupación).

# EDA inicial

Collab
5 visualizaciones concectadas al mercado digital y precios de alojamientos 
1. Precio de venta por precio de alquiler
2. Ubicación por precio de alquiler
3. Grado de criminalidad por precio de alquiler
4. Tipo de habitación por precio de alquiler
5. Evlauar la disponibilidad por precio de alquiler

# Hipótesis de Negocio 

- H1: "Las propiedades ubicadas a menos de 500 metros de una estación de metro principal en Manhattan tienen un precio por noche un 25% superior al promedio del distrito".
- H2: "Existe una correlación negativa entre el índice de criminalidad del vecindario y la tasa de ocupación (medida por el número de reseñas)".
- H3: "Los listados gestionados por 'Professional Hosts' (anfitriones con más de 3 propiedades) mantienen una disponibilidad anual menor pero precios más estables que los anfitriones individuales".


# Objetivo General
Desarrollar un análisis basado en el dataset de Airbnb NYC que permita identificar los principales factores que influyen en el precio y la demanda de alojamientos de corto plazo, con el fin de optimizar la fijación de precios y maximizar el ingreso potencial de los anfitriones.


# Objetivos Específicos
* Analizar la relación entre el precio (price) y la ubicación geográfica (neighbourhood_group).
* Evaluar el impacto del tipo de habitación (room_type) sobre el precio de los alojamientos.
* Analizar la relación entre la demanda del alojamiento (medida por number_of_reviews) y el precio.
* Evaluar cómo la disponibilidad anual (availability_365) se relaciona con el precio y la demanda.
* Identificar patrones de comportamiento entre anfitriones según la cantidad de propiedades (calculated_host_listings_count).
* Explorar la distribución de precios para detectar valores atípicos y rangos representativos del mercado.

# Hipótesis de Negocio
* H1 (Ubicación y precio): Las propiedades ubicadas en Manhattan presentan un precio promedio por noche significativamente mayor en comparación con otros distritos (neighbourhood_group).
* H2 (Tipo de habitación): Los alojamientos tipo “Entire home/apt” tienen precios más altos en promedio que los tipos “Private room” y “Shared room”.
* H3 (Precio vs demanda): Existe una relación inversa entre el precio (price) y la cantidad de reseñas (number_of_reviews), lo que indica que precios más altos tienden a reducir la demanda.
* H4 (Disponibilidad vs demanda): Las propiedades con menor disponibilidad anual (availability_365) presentan un mayor número de reseñas, lo que sugiere una mayor ocupación.
* H5 (Hosts profesionales): Los anfitriones con mayor número de propiedades (calculated_host_listings_count) tienden a manejar precios más homogéneos y presentan mayor cantidad de reseñas promedio que los anfitriones con pocas propiedades.
* H6 (Distribución de precios): La distribución del precio (price) presenta alta dispersión y presencia de valores atípicos, lo que indica un mercado heterogéneo con diferentes segmentos de oferta.
* H7 (Ubicación vs demanda): Los distritos con precios más altos (como Manhattan) no necesariamente presentan la mayor cantidad de reseñas, lo que sugiere una posible relación entre precio elevado y menor volumen de demanda.


Matias: Buscar data fuentes de enrequisimiento

Lu: Hipotesis y objetivos

Eurymar: Plan, descripcion del problema y datos

Giraldo y Manuel: 4. EDA Inicial: al menos 5 visualizaciones comentadas (distribuciones, valores nulos, primeras
correlaciones) Y LO DE IA
