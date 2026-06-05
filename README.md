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

## 6. PLAN DE TRABAJO PARA LA ETAPA 2 (CRONOGRAMA DE ACTIVIDADES)

El equipo ha estructurado el desarrollo de la fase final del proyecto de acuerdo con el siguiente cronograma de hitos académicos, garantizando una transición ordenada de la analítica descriptiva hacia la predictiva y prescriptiva:

| Semana | Actividad Principal | Responsable(s) |
| :--- | :--- | :--- |
| **7 - 8** | **Analítica Diagnóstica:** Validación de las 4 hipótesis mediante análisis de datos bivariado y multivariable en Python. | Matias Amaya, Eurymar Umbria |
| **9 - 10** | **Construcción del Dashboard:** Diseño de visualizaciones interactivas y dinámicas enfocadas en la toma de decisiones. | Giraldo Ruiz, Manuel Aguirre |
| **11** | **Analítica Predictiva:** Implementación de modelos de aprendizaje supervisado (Machine Learning) para la estimación de tarifas. | Matias Amaya |
| **12** | **Análisis Prescriptivo:** Simulación de escenarios de inversión y formulación de recomendaciones corporativas finales. | Luciana Pacheco, Eurymar Umbria |
| **13** | **Documentación Final y QA:** Consolidación del informe técnico en GitHub y control de calidad del código. | Eurymar Umbria |
| **13** | **Preparación de la Presentación:** Diseño de diapositivas finales y ensayo de la sustentación oral colectiva. | Todo el Equipo |
| **14** | **Cierre del Proyecto:** Entrega del repositorio final y evaluación de desempeño del equipo consultor. | Todo el Equipo |

---

## 7. APÉNDICE: BITÁCORA DE USO DE INTELIGENCIA ARTIFICIAL (IA GENERATIVA)

En cumplimiento con las directrices académicas del curso, el equipo de *SafeInvest NYC Analytics* declara haber utilizado herramientas de Inteligencia Artificial Generativa (ChatGPT-4 y Gemini) exclusivamente como soporte metodológico, optimización de consultas en lenguaje DAX/Python y refinamiento de la redacción técnica. Su uso se limitó a acelerar los procesos de desarrollo sin sustituir el criterio analítico ni estratégico del equipo.

### **Muestras de Prompts Clave Utilizados por el Equipo:**

* **Prompts para la Organización y Limpieza de Datos:**
  > *"¿Cómo puedo tratar los valores nulos en la columna 'reviews_per_month' del dataset de Airbnb para que no afecten mis cálculos de promedios en Pandas sin sesgar la distribución?"*
  > *"Genera una función en Python para limpiar espacios en blanco ocultos (trailing spaces) en una columna de texto antes de realizar un pd.merge entre dos DataFrames."*

* **Prompts para la Búsqueda y Selección de Datasets de Enriquecimiento:**
  > *"Estoy trabajando en un proyecto de Big Data sobre Airbnb en NYC. Necesito una fuente de enriquecimiento gratuita que me dé el valor histórico de venta de mercado de las casas en Nueva York para compararlo con los precios de alquiler. ¿Dónde puedo descargar esta data oficial?"*

* **Prompts para la Coherencia de Temas e Hipótesis de Negocio:**
  > *"Revisa estas hipótesis sobre el negocio de Airbnb y selecciona las 4 más impactantes para un inversionista inmobiliario que se preocupa por el balance entre seguridad ciudadana, costo de adquisición y rentabilidad por noche."*
  > *"Ayúdame a mejorar mi 'Objetivo Principal' para que adopte un enfoque de consultoría de negocios digitales y mencione explícitamente el uso de fuentes de enriquecimiento."*

---

## 8. DESARROLLO DE LA ETAPA 2 (DIAGNÓSTICA, PREDICTIVA Y PRESCRIPTIVA)

A partir de la base de datos unificada en el entorno de desarrollo (Google Colab), el equipo ejecutará las siguientes fases metodológicas siguiendo el cronograma establecido:

### 8.1. Fase Diagnóstica y Análisis Multivariable (Semanas 7-8)
* **Objetivo:** Validar cuantitativamente las 4 hipótesis de negocio planteadas en la Sección 4, cruzando las variables del dataset base de Airbnb con las variables de enriquecimiento inmobiliario y seguridad.
* **En el Código:** Se utilizarán las librerías `seaborn` y `matplotlib` en Python para generar gráficos de dispersión (`sns.scatterplot`) con líneas de tendencia que midan la correlación de Pearson ($r$) entre el precio de Airbnb (`price`) y el costo de la propiedad (`average_sale_price`). Asimismo, se analizará estadísticamente el impacto del riesgo usando diagramas de cajas (`sns.boxplot`) segmentados por el nivel de criminalidad corregido (escala 1 al 5).

### 8.2. Implementación de la Solución Interactiva (Semanas 9-10)
* **Objetivo:** Construir el Dashboard interactivo para que los inversionistas de la consultora puedan explorar los datos dinámicamente y localizar visualmente el "Punto Dulce" de inversión.
* **Herramienta:** El despliegue se definirá mediante Power BI o Streamlit para asegurar que la visualización sea completamente dinámica, incorporando filtros por distrito (`neighbourhood_group`), rangos de presupuesto de capital y mapas interactivos basados en latitud y longitud.

### 8.3. Fase Predictiva con Machine Learning (Semana 11)
* **Objetivo:** Entrenar un algoritmo de aprendizaje supervisado (Regresión Lineal Múltiple / Árboles de Decisión) que permita predecir la tarifa óptima por noche ($Y$) de una nueva propiedad introducida al mercado basándose en variables predictoras clave ($X_i$):
  Price = beta_0 + beta_1(average\_sale\_price) + beta_2(text{crime\_rate) + beta_3(room\_type) + \epsilon$$
* **Métricas de Éxito:** Se evaluará rigurosamente el rendimiento del modelo utilizando el coeficiente de determinación ($R^2$) y el Error Absoluto Medio (MAE) para cumplir con el estándar técnico exigido.

### 8.4. Fase Prescriptiva y Conclusiones (Semana 12)
* **Objetivo:** Traducir las métricas estadísticas y las predicciones del modelo en recomendaciones estratégicas de negocio ("¿Qué pasaría si...?").
* **Impacto:** Las prescripciones orientarán las decisiones de la consultora detallando con precisión qué vecindarios específicos de distritos periféricos ofrecen el mejor retorno financiero con una exposición al riesgo controlada.
