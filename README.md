# Proyecto_Final_Data_Analytics

Caso de Uso: Caso 3 - Turismo digital y precios de alojamiento en NYC


Integrantes: 

- Luciana Pacheco
- Eurymar Umbria
- Giraldo Ruiz
- Matias Amaya
- Manuel Aguirre

# Roles sugeridos:
- Matias (Data Engineer & Lead Analyst): Búsqueda de fuentes de enriquecimiento y ejecución técnica del EDA (limpieza de datos y pre-procesamiento).
- Manuel (Data Analyst & Integration Specialist): Apoyo en búsqueda y limpieza de datos de enriquecimiento, y desarrollo de la primera mitad de las visualizaciones del EDA.
- Giraldo (Data Visualization Specialist): Desarrollo de la segunda mitad de las visualizaciones interpretadas del EDA inicial.
- Eurymar (Project Manager & Documentation): Redacción del problema de negocio, objetivo principal, descripción de los datos, plan de trabajo Etapa 2 y gestión del repositorio.
- Luciana (Business Strategist): Definición de objetivos específicos e hipótesis de negocio en formato de pregunta.

Empresa Ficticia: SafeInvest NYC Analytics (Consultora de Inversiones Inmobiliarias).

# El Problema:

Los inversionistas que buscan entrar al mercado de Airbnb en Nueva York se enfrentan a un dilema de rentabilidad y riesgo: las zonas con mayor valor de propiedad (como Manhattan) tienen precios de alquiler más altos pero costos de adquisición masivos. Por otro lado, zonas más económicas podrían parecer atractivas, pero presentan variaciones en la seguridad (crime rate) que pueden ahuyentar a la demanda o depreciar el valor del alquiler.

Actualmente, no existe una herramienta que cruce el costo de adquisición de la propiedad, la tasa de criminalidad del distrito y el precio potencial de alquiler para identificar el "punto dulce" de inversión (ROI) donde se maximice el ingreso minimizando el riesgo del entorno.

Pregunta Central:
¿Cómo afecta la ubicación geográfica —medida a través del costo de mercado de la propiedad y el índice de criminalidad— en la fijación de precios de los alojamientos Airbnb en NYC, y en qué distritos se encuentra el mejor equilibrio entre seguridad y rentabilidad para un inversionista?

# Objetivo Principal del Proyecto
El objetivo de esta investigación es identificar las zonas geográficas en la ciudad de Nueva York que ofrecen la mayor eficiencia de inversión inmobiliaria para alquileres de corto plazo (Airbnb).

Esto se logrará mediante el análisis cruzado de la rentabilidad esperada (precios de alquiler), el riesgo del entorno (índice de criminalidad) y el costo de capital (valor de venta de mercado), permitiendo a los inversionistas de nuestra consultora tomar decisiones basadas en datos que equilibren la seguridad del huésped con el retorno de inversión (ROI).


# Descripción de los Datos Fuente Principal: 
Para este proyecto, hemos integrado tres fuentes de datos distintas para obtener una visión multidimensional del mercado:

- Dataset Base: NYC Airbnb Open Data (2019):
Fuente base: Kaggle.
Descripción: Contiene información detallada sobre los listados de Airbnb en Nueva York, incluyendo geolocalización (latitud/longitud), tipo de habitación, precio por noche, noches mínimas y volumen de reseñas.
Variables clave utilizadas: neighbourhood_group, price, availability_365, latitude, longitude.

- Fuente de Enriquecimiento 1: NYC Rolling Sales Data:
Fuente: NYC Department of Finance.
Descripción: Registros de ventas de propiedades inmobiliarias en los cinco distritos de Nueva York.
Uso en el proyecto: Se calculó el average_sale_price por distrito para contrastar el costo de adquisición de una propiedad frente a su potencial de renta en Airbnb.

- Fuente de Enriquecimiento 2: Escala de Seguridad por Distrito (Crime Index):
Fuente: Elaboración propia basada en reportes históricos de criminalidad por condado.
Descripción: Una escala numérica (1 al 5) asignada a cada distrito donde 1 representa menor incidencia y 5 mayor incidencia.
Uso en el proyecto: Variable categórica (crime_rate) para analizar si la percepción de seguridad limita los precios de los alojamientos.

# EDA inicial

 EDA Inicial: al menos 5 visualizaciones comentadas (distribuciones, valores nulos, primeras
correlaciones).

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


# 6. Plan de Trabajo Etapa 2 (Semanas 7-14)

| Semana | Actividad Principal | Responsable(s) |
| :--- | :--- | :--- |
| **7 - 8** | **Analítica Diagnóstica:** Validación de las 3 hipótesis mediante análisis bivariado y multivariado. | Data Analytics Lead |
| **9 - 10** | **Construcción del Dashboard:** Diseño de visualizaciones interactivas que respondan a preguntas de negocio. | Visualization Expert |
| **11** | **Analítica Predictiva:** Implementación de un modelo simple (ej. regresión para predecir precios). | Data Analytics Lead |
| **12** | **Análisis Prescriptivo:** Creación de escenarios "¿qué pasaría si...?" y redacción de recomendaciones estratégicas. | Business Strategist |
| **13** | **Documentación Final y QA:** Consolidación del informe en GitHub y revisión de calidad del Notebook. | Documentation & QA Manager |
| **13** | **Preparación de la Presentación:** Diseño de diapositivas (máx. 12) y ensayo de la exposición oral. | Todo el Equipo |
| **14** | **Entrega PC2:** Carga de archivos finales y presentación ante el directorio de la empresa. | Todo el Equipo |


# Apéndice de uso de IA: 

si usaron IA generativa, detallar qué prompts usaron y cómo
validaron los resultados

