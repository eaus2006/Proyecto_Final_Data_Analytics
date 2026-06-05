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

Los inversionistas independientes y firmas boutique que buscan ingresar al mercado de alquileres temporales en la plataforma Airbnb en Nueva York se enfrentan a un complejo dilema estratégico que equilibra la rentabilidad potencial y el riesgo financiero. Las zonas tradicionales con un valor de propiedad masivo (como Manhattan) garantizan tarifas por noche elevadas, pero exigen un costo de adquisición de inmuebles prohibitivo, ralentizando el Retorno de Inversión (ROI). Por otro lado, los distritos periféricos ofrecen costos de entrada accesibles, pero exponen al inversor a una mayor volatilidad en la demanda turística y a riesgos de seguridad ciudadana que impactan directamente en la tasa de vacancia.

Actualmente, las decisiones de inversión se toman de forma aislada basándose en intuiciones o un solo dataset. La falta de una herramienta analítica centralizada que integre de manera limpia el costo de adquisición de la propiedad (Rolling Sales de la ciudad) con métricas operativas de turismo digital (Airbnb) impide identificar con precisión el "Punto Dulce" (Sweet Spot): zonas geográficas con precios de entrada moderados, tasas de delincuencia controladas y flujos de caja atractivos.

---

## 3. OBJETIVOS DEL PROYECTO

### **OBJETIVO PRINCIPAL:**
Desarrollar un framework de analítica de datos mediante la integración de fuentes de enriquecimiento públicas y privadas, con el fin de identificar las zonas geográficas óptimas en la ciudad de Nueva York que maximicen el rendimiento financiero para inversiones en Airbnb, minimizando simultáneamente el riesgo de adquisición inmobiliaria y los índices de inseguridad ciudadana.

### **OBJETIVOS ESPECÍFICOS:**
* OE1: Evaluar la relación económica entre el costo promedio de mercado de los bienes raíces por distrito y el precio de cotización diaria en la plataforma Airbnb.
  * Hipótesis 1 (H1): ¿Existe una correlación lineal positiva y fuerte ($r > 0.70$) entre el precio promedio de venta de las propiedades inmobiliarias (SALE PRICE) y la tarifa por noche (price) de los alojamientos en Airbnb a nivel de distritos?

* 0E2: Analizar el impacto de los niveles de seguridad ciudadana sobre las tarifas y la competitividad de los alojamientos turísticos.
  * Hipótesis 2 (H2): ¿Los distritos catalogados con niveles de criminalidad altos (como el Bronx) presentan una mediana de precio de alquiler significativamente menor y una menor densidad de ofertas en comparación con distritos considerados de alta seguridad (como Staten Island o Manhattan)?
 
* (OE3): Determinar la dinámica entre la política de precios por noche y la tasa de ocupación/disponibilidad anual del inmueble.
  * Hipótesis 3 (H3): ¿Existe una relación inversa entre el precio de alquiler (price) y la disponibilidad anual de la propiedad (availability_365), sugiriendo que los alojamientos con tarifas premium experimentan una menor rotación de huéspedes y mayor tiempo ociosos en el mercado?

* (OE4): Identificar el "Punto Dulce" de inversión inmobiliaria mediante un análisis de eficiencia multivariable (Costo - Seguridad - Retorno).
  * Hipótesis 4 (H4): ¿Existen vecindarios específicos en distritos periféricos (como Brooklyn o Queens) que registren un índice de eficiencia superior (Alta tarifa de Airbnb / Bajo costo de adquisición) manteniendo un nivel de criminalidad calificado como moderado o bajo?

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

## 6. PLAN DE TRABAJO ETAPA 2 (SEMANAS 7-14)

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

## 7. APÉNDICE DE USO DE IA

* **Herramientas:** ChatGPT / Gemini / Copilot
* **Uso:** Se utilizaron prompts para la estructuración del plan de trabajo, optimización de redacción ejecutiva y asistencia en el código de limpieza de datos en Python.

**Prompts para la Organización y Limpieza de Datos**:

"¿Cómo puedo tratar los valores nulos en la columna 'reviews_per_month' del dataset de Airbnb para que no afecten mis cálculos de promedios?" "Genera un código para mapear una lista de distritos de NYC (Manhattan, Brooklyn, Queens, Bronx, Staten Island) a una escala numérica de criminalidad del 1 al 5." 

**Prompts para la Búsqueda y Selección de Datasets**

"Estoy trabajando en un proyecto de Big Data sobre Airbnb en NYC. Necesito una fuente de enriquecimiento gratuita que me dé el valor de mercado de las casas en Nueva York para compararlo con los precios de alquiler. ¿Dónde puedo descargar esta data oficial?" 

"¿Qué variables del portal NYC Open Data son más útiles para analizar la seguridad ciudadana y cómo se relacionan con el turismo digital?" 

**Prompts para la Coherencia de Temas e Hipótesis**

"Revisa estas 9 hipótesis sobre el negocio de Airbnb y selecciona las 4 más impactantes para un inversionista inmobiliario que se preocupa por el balance entre seguridad y rentabilidad." 

"Ayúdame a mejorar mi 'Objetivo Principal' para que sea mas directo, profesional y que mencione específicamente el uso de analítica de datos para encontrar el 'punto clave' de inversión en NYC."

---

## 8. MARCO METODOLÓGICO Y AVANCE DE LA ETAPA 2 (DESARROLLO ANALÍTICO)

### 8.1. Analítica Diagnóstica y Validación Avanzada de Hipótesis (Semanas 7-8)
Para validar de forma cuantitativa las 4 hipótesis reformuladas y asegurar el rigor analítico exigido en la rúbrica de evaluación, el equipo ejecutará un Análisis Exploratorio de Datos (EDA) de nivel bivariado y multivariado sobre la base de datos unificada y enriquecida:

* **Validación de H1 (Precio vs. Costo Inmobiliario):** Se implementará un análisis de correlación lineal utilizando el coeficiente de Pearson ($r$) y gráficos de dispersión (`sns.scatterplot`) con líneas de tendencia. Esto determinará matemáticamente si el costo de adquisición del inmueble (`average_sale_price`) indexa proporcionalmente la tarifa de salida en Airbnb (`price`).
* **Validación de H2 (Precio vs. Criminalidad):** Se segmentarán los datos según el nivel de criminalidad corregido (escala 1 al 5 basada en el reporte NYPD). Mediante diagramas de caja y bigotes (`sns.boxplot`) y pruebas estadísticas de comparación de medianas (Kruskal-Wallis o ANOVA), se demostrará el impacto real y el "castigo financiero" que sufren los precios de los alojamientos en zonas con altos índices delictivos (como el Bronx).
* **Validación de H3 (Precio vs. Disponibilidad):** Se generará una matriz de correlación térmica (Heatmap) para evaluar si las propiedades con tarifas de alta gama experimentan una tasa de vacancia prolongada o si la disponibilidad (`availability_365`) se rige por factores estacionales ajenos al precio.
* **Validación de H4 (El "Punto Dulce" Inmobiliario):** Se cruzará de forma simultánea el costo, la seguridad y la tarifa mediante gráficos de burbujas multivariados, donde el color represente el nivel de riesgo y el tamaño represente la tarifa de alquiler, aislando los vecindarios periféricos más eficientes de Brooklyn o Queens.

### 8.2. Diseño de la Solución e Interactividad del Dashboard (Semanas 9-10)
Atendiendo al criterio crítico de la rúbrica que penaliza las visualizaciones estáticas, el equipo desarrollará un Dashboard Interactivo enfocado en el usuario final (inversionistas de la consultora *SafeInvest NYC Analytics*). 
* **Tecnología a usar:** El componente de visualización se construirá utilizando [Power BI / Streamlit en Python - *Coordinar con Giraldo*].
* **Funcionalidades Dinámicas:** El usuario podrá interactuar en tiempo real con filtros de presupuesto de capital, selección de distritos geográficos (`neighbourhood_group`) y niveles de tolerancia al riesgo. El núcleo de la interfaz incluirá un mapa interactivo basado en las coordenadas de latitud y longitud del dataset unificado, permitiendo una exploración visual directa del "Punto Dulce" de inversión.

### 8.3. Modelado Predictivo con Machine Learning (Semana 11)
El proyecto transicionará de la analítica descriptiva a la predictiva mediante el entrenamiento de modelos de aprendizaje supervisado en Python (Regresión Lineal Múltiple y Random Forest Regressor). El modelo estimará la tarifa óptima por noche ($Y$) de una nueva propiedad introducida al mercado basándose en variables predictoras ($X_i$) clave:
$$\text{Price} = \beta_0 + \beta_1(\text{average\_sale\_price}) + \beta_2(\text{crime\_rate}) + \beta_3(\text{room\_type}) + \epsilon$$
Para garantizar el nivel de excelencia técnica, el rendimiento del algoritmo no se asumirá a ciegas, sino que se medirá explícitamente a través del coeficiente de determinación ($R^2$) y el Error Absoluto Medio (MAE).

### 8.4. Enfoque Prescriptivo y Toma de Decisiones Estratégicas (Semana 12)
El cierre del proyecto articulará los hallazgos matemáticos con los objetivos de negocio de la consultora. Se construirán escenarios de simulación ("¿Qué pasaría si...?") para formular recomendaciones de inversión corporativa granulares. Estas prescripciones orientarán el capital hacia zonas específicas que mitiguen el riesgo de delincuencia y optimicen la tasa de ocupación anual, respondiendo de manera definitiva al problema de negocio planteado al inicio de la investigación.


