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

# Objetivos Específicos
- Analizar la relación entre la ubicación geográfica (neighbourhood_group) y el precio de alquiler (price).
- Evaluar la relación entre precio (price) y demanda (number_of_reviews) como proxy de ocupación.
- Analizar cómo la disponibilidad (availability_365) refleja estabilidad de ingresos y ocupación.
- Evaluar el impacto del tipo de alojamiento (room_type) en el precio y la demanda.
- Analizar el efecto del nivel de criminalidad (crime_rate) sobre la demanda y estabilidad del alquiler.
- Evaluar la relación entre el valor de mercado de las propiedades (average_sale_price) y el precio de Airbnb.
- Identificar patrones de comportamiento entre anfitriones profesionales (calculated_host_listings_count) y anfitriones individuales.
- Determinar qué distritos presentan el mejor equilibrio entre ingreso potencial y riesgo, identificando el “punto dulce” de inversión.

# Hipótesis de Negocio (preguntas)
- H1 (Ubicación premium y precio):
¿Las propiedades ubicadas en Manhattan y cerca de estaciones de metro principales presentan precios por noche significativamente mayores (por ejemplo, al menos 25% por encima del promedio del distrito)?
- H2 (Criminalidad vs demanda):
¿Existe una relación negativa entre el índice de criminalidad del vecindario (crime_rate) y la demanda del alojamiento (number_of_reviews)?
- H3 (Hosts profesionales):
¿Los anfitriones con múltiples propiedades (más de 3 listings) presentan menor disponibilidad anual (availability_365) pero precios más estables en comparación con anfitriones individuales?
- H4 (Precio vs demanda):
¿Existe una relación inversa entre el precio de alquiler (price) y la cantidad de reseñas (number_of_reviews), indicando que precios más altos reducen la ocupación?
- H5 (Criminalidad vs estabilidad):
¿Los distritos con niveles altos de criminalidad (niveles 4 o 5) presentan mayor variabilidad en la disponibilidad (availability_365), reflejando menor estabilidad en la demanda?
- H6 (Valor de propiedad vs precio Airbnb):
¿Existe una correlación positiva entre el valor promedio de venta de las propiedades (average_sale_price) y el precio de alquiler diario (price)?
- H7 (Rentabilidad vs costo de entrada):
¿Los distritos con menor costo de adquisición presentan una mejor relación entre precio de alquiler y demanda, generando un retorno de inversión más atractivo que distritos de alto valor como Manhattan?
- H8 (Tipo de propiedad y retorno):
¿Los alojamientos tipo “Entire home/apt” generan mayor ingreso potencial a pesar de tener menor frecuencia de reseñas en comparación con habitaciones privadas o compartidas?
- H9 (Punto dulce de inversión):
¿Existe un conjunto de distritos que logran un equilibrio óptimo entre precio de alquiler, nivel de criminalidad y demanda, maximizando el ingreso esperado y minimizando el riesgo para el inversionista?


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

