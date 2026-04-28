#  PROYECTO FINAL: AD3005 - INTRODUCCIÓN A DATA ANALYTICS Y BIG DATA
##  UNIVERSIDAD DE INGENIERÍA Y TECNOLOGÍA (UTEC)
###  Administración & Negocios Digitales | Ciclo 2026-1

---

# CASO DE USO: CASO 3 - TURISMO DIGITAL Y PRECIOS DE ALOJAMIENTO EN NYC

## 1. PORTADA DEL EQUIPO

**CONSULTORA FICTICIA:** *SafeInvest NYC Analytics* (Consultora de Inversiones Inmobiliarias)

### **INTEGRANTES Y ROLES ASIGNADOS:**
* **Matias Amaya** - *Data Engineer & Lead Analyst*: Búsqueda de fuentes de enriquecimiento y ejecución técnica del EDA (limpieza de datos y pre-procesamiento).
* **Manuel Aguirre** - *Data Analyst & Integration Specialist*: Apoyo en búsqueda y limpieza de datos de enriquecimiento, y desarrollo de la primera mitad de las visualizaciones del EDA.
* **Giraldo Ruiz** - *Data Visualization Specialist*: Desarrollo de la segunda mitad de las visualizaciones interpretadas del EDA inicial.
* **Eurymar Umbria** - *Project Manager & Documentation*: Redacción del problema de negocio, objetivo principal, descripción de los datos, plan de trabajo Etapa 2 y gestión del repositorio.
* **Luciana Pacheco** - *Business Strategist*: Definición de objetivos específicos e hipótesis de negocio en formato de pregunta.

---

## 2. DESCRIPCIÓN DEL PROBLEMA DE NEGOCIO

Los inversionistas que buscan entrar al mercado de **Airbnb en Nueva York** se enfrentan a un dilema de rentabilidad y riesgo: las zonas con mayor valor de propiedad (como Manhattan) tienen precios de alquiler más altos pero costos de adquisición masivos. Por otro lado, zonas más económicas podrían parecer atractivas, pero presentan variaciones en la seguridad (**crime rate**) que pueden ahuyentar a la demanda o depreciar el valor del alquiler.

Actualmente, no existe una herramienta que cruce el costo de adquisición de la propiedad, la tasa de criminalidad del distrito y el precio potencial de alquiler para identificar el **"punto dulce" de inversión (ROI)** donde se maximice el ingreso minimizando el riesgo del entorno.

### **PREGUNTA CENTRAL:**
> ¿Cómo afecta la ubicación geográfica (medida a través del costo de mercado de la propiedad y el índice de criminalidad) en la fijación de precios de los alojamientos Airbnb en NYC, y en qué distritos se encuentra el mejor equilibrio entre seguridad y rentabilidad para un inversionista?

---

## 3. OBJETIVOS DEL PROYECTO

### **OBJETIVO PRINCIPAL:**
El objetivo de esta investigación es **identificar las zonas geográficas en la ciudad de Nueva York que ofrecen la mayor eficiencia de inversión inmobiliaria para alquileres de corto plazo (Airbnb)**. Esto se logrará mediante el análisis cruzado de la rentabilidad esperada (precios de alquiler), el riesgo del entorno (índice de criminalidad) y el costo de capital (valor de venta de mercado), permitiendo a los inversionistas de nuestra consultora tomar decisiones basadas en datos que equilibren la seguridad del huésped con el retorno de inversión (ROI).

### **OBJETIVOS ESPECÍFICOS:**
* Analizar la relación entre la ubicación geográfica (`neighbourhood_group`) y el precio de alquiler (`price`).
* Evaluar la relación entre precio (`price`) y demanda (`number_of_reviews`) como proxy de ocupación.
* Analizar cómo la disponibilidad (`availability_365`) refleja estabilidad de ingresos y ocupación.
* Evaluar el impacto del tipo de alojamiento (`room_type`) en el precio y la demanda.
* Analizar el efecto del nivel de criminalidad (`crime_rate`) sobre la demanda y estabilidad del alquiler.
* Evaluar la relación entre el valor de mercado de las propiedades (`average_sale_price`) y el precio de Airbnb.
* Identificar patrones de comportamiento entre anfitriones profesionales (`calculated_host_listings_count`) y anfitriones individuales.
* Determinar qué distritos presentan el mejor equilibrio entre ingreso potencial y riesgo, identificando el **“punto dulce”** de inversión.

---

## 4. DESCRIPCIÓN DE LOS DATOS

Hemos integrado **tres fuentes de datos** para obtener una visión multidimensional (registros totales: **48,895**):

### **A. DATASET BASE: NYC AIRBNB OPEN DATA (2019)**
* **Fuente:** Kaggle.
* **Descripción:** Contiene información detallada sobre los listados de Airbnb en Nueva York, incluyendo geolocalización (latitud/longitud), tipo de habitación, precio por noche, noches mínimas y volumen de reseñas.
* **Variables Clave:** `neighbourhood_group`, `price`, `availability_365`, `latitude`, `longitude`.

### **B. FUENTE DE ENRIQUECIMIENTO 1: NYC ROLLING SALES DATA**
* **Fuente:** NYC Department of Finance.
* **Descripción:** Registros de ventas de propiedades inmobiliarias en los cinco distritos de Nueva York.
* **Uso:** Se calculó el `average_sale_price` por distrito para contrastar el costo de adquisición de una propiedad frente a su potencial de renta en Airbnb.

### **C. FUENTE DE ENRIQUECIMIENTO 2: ESCALA DE SEGURIDAD POR DISTRITO (CRIME INDEX)**
* **Fuente:** Elaboración propia basada en reportes históricos de criminalidad por condado.
* **Descripción:** Una escala numérica (1 al 5) asignada a cada distrito donde 1 representa menor incidencia y 5 mayor incidencia.
* **Uso:** Variable categórica (`crime_rate`) para analizar si la percepción de seguridad limita los precios de los alojamientos.

---

## 5. EDA INICIAL (EXPLORACIÓN DE DATOS)

Se han desarrollado **5 visualizaciones** conectadas al mercado digital y precios de alojamientos:
1.  **Precio de venta por precio de alquiler:** Relación entre el costo de inversión y la ganancia por noche.
2.  **Ubicación por precio de alquiler:** Comparativa de rentabilidad por distrito.
3.  **Grado de criminalidad por precio de alquiler:** Impacto de la seguridad en el costo del servicio.
4.  **Tipo de habitación por precio de alquiler:** Análisis de oferta (Entire home vs Private room).
5.  **Evaluación de disponibilidad por precio de alquiler:** Análisis de la oferta activa en el mercado.

---

## 6. HIPÓTESIS DE NEGOCIO (PREGUNTAS)

* **H1 (Ubicación premium y precio):** ¿Las propiedades ubicadas en Manhattan y cerca de estaciones de metro principales presentan precios por noche significativamente mayores (por ejemplo, al menos 25% por encima del promedio del distrito)?
* **H2 (Criminalidad vs demanda):** ¿Existe una relación negativa entre el índice de criminalidad del vecindario (`crime_rate`) y la demanda del alojamiento (`number_of_reviews`)?
* **H3 (Hosts profesionales):** ¿Los anfitriones con múltiples propiedades (más de 3 listings) presentan menor disponibilidad anual (`availability_365`) pero precios más estables en comparación con anfitriones individuales?
* **H4 (Precio vs demanda):** ¿Existe una relación inversa entre el precio de alquiler (`price`) y la cantidad de reseñas (`number_of_reviews`), indicando que precios más altos reducen la ocupación?
* **H5 (Criminalidad vs estabilidad):** ¿Los distritos con niveles altos de criminalidad (niveles 4 o 5) presentan mayor variabilidad en la disponibilidad (`availability_365`), reflejando menor estabilidad en la demanda?
* **H6 (Valor de propiedad vs precio Airbnb):** ¿Existe una correlación positiva entre el valor promedio de venta de las propiedades (`average_sale_price`) y el precio de alquiler diario (`price`)?
* **H7 (Rentabilidad vs costo de entrada):** ¿Los distritos con menor costo de adquisición presentan una mejor relación entre precio de alquiler y demanda, generando un retorno de inversión más atractivo que distritos de alto valor como Manhattan?
* **H8 (Tipo de propiedad y retorno):** ¿Los alojamientos tipo “Entire home/apt” generan mayor ingreso potencial a pesar de tener menor frecuencia de reseñas en comparación con habitaciones privadas o compartidas?
* **H9 (Punto dulce de inversión):** ¿Existe un conjunto de distritos que logran un equilibrio óptimo entre precio de alquiler, nivel de criminalidad y demanda, maximizando el ingreso esperado y minimizando el riesgo para el inversionista?

---

## 7. PLAN DE TRABAJO ETAPA 2 (SEMANAS 7-14)

| SEMANA | ACTIVIDAD PRINCIPAL | RESPONSABLE(S) |
| :--- | :--- | :--- |
| **7 - 8** | **Analítica Diagnóstica:** Validación de las hipótesis mediante análisis bivariado y multivariado. | Matias y Eurymar |
| **9 - 10** | **Construcción del Dashboard:** Diseño de visualizaciones interactivas que respondan a preguntas de negocio. | Giraldo y Manuel |
| **11** | **Analítica Predictiva:** Implementación de un modelo simple (ej. regresión para predecir precios). | Matias |
| **12** | **Análisis Prescriptivo:** Creación de escenarios "¿qué pasaría si...?" y redacción de recomendaciones estratégicas. | Luciana |
| **13** | **Documentación Final y QA:** Consolidación del informe en GitHub y revisión de calidad del Notebook. | Eurymar |
| **13** | **Preparación de la Presentación:** Diseño de diapositivas (máx. 12) y ensayo de la exposición oral. | Todo el Equipo |
| **14** | **Entrega PC2:** Carga de archivos finales y presentación ante el directorio de la empresa. | Todo el Equipo |

---

## 8. APÉNDICE DE USO DE IA

* **Herramientas:** ChatGPT / Gemini.
* **Uso:** Se utilizaron prompts para la estructuración del plan de trabajo, optimización de redacción ejecutiva y asistencia en el código de limpieza de datos en Python.

**Prompts para la Organización y Limpieza de Datos**:
  
"Tengo un dataset de Airbnb con latitud y longitud, y otro dataset de ventas inmobiliarias por distrito en archivos Excel separados. Escribe un script en Python usando Pandas para cargar todos los archivos y crear una nueva columna en el dataset principal que contenga el precio promedio de venta por 'neighbourhood_group'." 

"¿Cómo puedo tratar los valores nulos en la columna 'reviews_per_month' del dataset de Airbnb para que no afecten mis cálculos de promedios?" "Genera un código para mapear una lista de distritos de NYC (Manhattan, Brooklyn, Queens, Bronx, Staten Island) a una escala numérica de criminalidad del 1 al 5." 

**Prompts para la Búsqueda y Selección de Datasets**

"Estoy trabajando en un proyecto de Big Data sobre Airbnb en NYC. Necesito una fuente de enriquecimiento gratuita que me dé el valor de mercado de las casas en Nueva York para compararlo con los precios de alquiler. ¿Dónde puedo descargar esta data oficial?" 

"¿Qué variables del portal NYC Open Data son más útiles para analizar la seguridad ciudadana y cómo se relacionan con el turismo digital?" 

**Prompts para la Coherencia de Temas e Hipótesis**

"Revisa estas 9 hipótesis sobre el negocio de Airbnb y selecciona las 4 más impactantes para un inversionista inmobiliario que se preocupa por el balance entre seguridad y rentabilidad." 

"Ayúdame a redactar un 'Objetivo Principal' para mi proyecto que sea directo, profesional y que mencione específicamente el uso de analítica de datos para encontrar el 'punto dulce' de inversión en NYC."

"Mejora la coherencia de este texto: quiero explicar por qué Manhattan tiene precios altos a pesar de tener un costo de adquisición masivo, usando un lenguaje de consultoría de negocios

