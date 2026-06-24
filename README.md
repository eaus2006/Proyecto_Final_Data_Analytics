# PROYECTO FINAL
# AD3005 - Introducción a Data Analytics y Big Data

### Universidad de Ingeniería y Tecnología (UTEC)
**Administración & Negocios Digitales | Ciclo 2026-1**

---

# Caso de Uso

## Caso 3: Turismo Digital y Precios de Alojamiento en Nueva York (NYC)

---

#  SafeInvest NYC Analytics

### Consultora Ficticia de Inversiones Inmobiliarias

---

#  Equipo de Trabajo

| Integrante | Rol |
|------------|-----|
| Matias Amaya | Data Support & QA Analyst |
| Manuel Aguirre | Data Support & Presentation Specialist |
| Giraldo Ruiz | Data Visualization Specialist |
| Eurymar Umbria | Lead Data Scientist & Project Manager |
| Luciana Pacheco | Business Strategist & Technical Writer |

--



## 2. DESCRIPCIÓN DEL PROBLEMA DE NEGOCIO



Los propietarios independientes y gestores de propiedades turísticas (anfitriones boutique) que operan en la plataforma Airbnb en la ciudad de Nueva York se enfrentan a un complejo dilema operativo y de posicionamiento comercial. Maximizar los ingresos requiere equilibrar de manera óptima la fijación de tarifas diarias (precios premium) con el mantenimiento de una alta tasa de ocupación (mínimos días de ociosidad anual). Mientras que las zonas con una altísima densidad turística (como Manhattan o Brooklyn) permiten validar tarifas por noche elevadas debido a su atractivo entorno, también se enfrentan a mercados hipercompetitivos y saturados de oferta, lo que puede elevar la volatilidad de la ocupación. Por otro lado, posicionar anuncios en distritos periféricos ofrece la ventaja de mercados menos saturados, pero expone a los gestores a una demanda turística más inestable y a variables de entorno externas, como los índices de criminalidad local, que impactan directamente en la reputación del anuncio y la confianza del huésped.



Actualmente, las decisiones de tarificación y posicionamiento estratégico se toman de forma aislada basándose en intuiciones empíricas o análisis parciales de la plataforma. La falta de un framework analítico centralizado que integre de manera limpia el rendimiento interno del alojamiento (Airbnb) con factores del entorno inmediato (seguridad ciudadana y tracción del vecindario) impide identificar con precisión el "Punto Dulce" (Sweet Spot) operativo: zonas geográficas y características clave del anuncio que garanticen un equilibrio perfecto entre tarifas premium, alta ocupación y entornos seguros para el turista.





---



## 3. OBJETIVOS DEL PROYECTO



### **OBJETIVO PRINCIPAL:**

Desarrollar un framework de analítica de datos mediante la integración de métricas de turismo digital y variables de entorno, con el fin de identificar las características y zonas geográficas óptimas en Nueva York que determinen un precio premium y una alta ocupación en Airbnb, orientando estratégicamente a propietarios y gestores en la optimización de sus ingresos y el posicionamiento seguro de sus alojamientos.



### **OBJETIVOS ESPECÍFICOS:**

* OE1: Evaluar la relación económica entre el valor patrimonial del suelo (entorno inmobiliario) por distrito y la tarifa diaria de los alojamientos en la plataforma Airbnb.

  * Hipótesis 1 (H1): ¿Existe una correlación lineal positiva y fuerte ($r > 0.70$) entre el precio promedio de venta de las propiedades inmobiliarias de la zona (SALE PRICE) y la tarifa por noche (price) de los alojamientos en Airbnb, demostrando que el costo del entorno determina el potencial de un precio premium?



* 0E2: Analizar el impacto de los niveles de seguridad ciudadana del entorno sobre las tarifas y la competitividad de los alojamientos turísticos.

  * Hipótesis 2 (H2): ¿Los distritos catalogados con niveles de riesgo por criminalidad altos (como Manhattan o Brooklyn, niveles 5 y 4) presentan una distribución de precios con techos económicos más altos y una mayor densidad de ofertas en comparación con distritos de riesgo bajo, demostrando que la alta tracción turística absorbe el factor de riesgo público?

 

* (OE3): Determinar la dinámica entre la política de precios por noche y la tracción operativa (disponibilidad anual del inmueble).

  * Hipótesis 3 (H3):¿Existe una relación inversa entre el precio de alquiler (price) y la disponibilidad anual de la propiedad (availability_365), sugiriendo que los alojamientos con tarifas premium experimentan una menor rotación de huéspedes y mayor tiempo ociosos en el mercado si su entorno no lo justifica?



* (OE4): Identificar el "Punto Dulce" (Sweet Spot) de eficiencia en la periferia de la ciudad mediante un análisis multivariable (Valor de la Zona - Seguridad - Retorno del Alojamiento).

  * Hipótesis 4 (H4): ¿Existen vecindarios específicos en distritos periféricos con costos de entorno moderados que registren un índice de eficiencia superior (Alta tarifa de Airbnb / Bajo costo del suelo de la zona) manteniendo un nivel de riesgo por criminalidad controlado o intermedio (como Queens o El Bronx), orientando a los gestores sobre dónde posicionar alojamientos altamente competitivos?



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

| **7 - 8** | **Analítica Diagnóstica:** Validación de las 4 hipótesis mediante análisis de datos bivariado y multivariable en Python. | Eurymar Umbria |

| **9 - 10** | **Construcción del Dashboard:** Diseño de visualizaciones interactivas y dinámicas enfocadas en la toma de decisiones. | Giraldo Ruiz, Manuel Aguirre |

| **11** | **Analítica Predictiva:** Implementación de modelos de aprendizaje supervisado (Machine Learning) para la estimación de tarifas. | Eurymar Umbria  |

| **12** | **Análisis Prescriptivo:** Simulación de escenarios de inversión y formulación de recomendaciones corporativas finales. | Eurymar Umbria, Mnuel y Matias |

| **13** | **Documentación Final y QA:** Consolidación del informe técnico en GitHub y control de calidad del código. | Matias Amaya y Manuel |

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

* **En el Código:** Se utilizarán las librerías `seaborn` y `matplotlib` en Python para generar gráficos de dispersión (`sns.scatterplot`) con líneas de tendencia que midan la correlación de Pearson entre el precio de Airbnb (`price`) y el costo de la propiedad (`average_sale_price`). Asimismo, se analizará estadísticamente el impacto del riesgo usando diagramas de cajas (`sns.boxplot`) segmentados por el nivel de criminalidad corregido (escala 1 al 5).



### 8.2. Implementación de la Solución Interactiva (Semanas 9-10)

* **Objetivo:** Construir el Dashboard interactivo para que los inversionistas de la consultora puedan explorar los datos dinámicamente y localizar visualmente el "Punto Dulce" de inversión.

* **Herramienta:** El despliegue se definirá mediante Power BI o Streamlit para asegurar que la visualización sea completamente dinámica, incorporando filtros por distrito (`neighbourhood_group`), rangos de presupuesto de capital y mapas interactivos basados en latitud y longitud.



### 8.3. Fase Predictiva con Machine Learning (Semana 11)

* **Objetivo:** Entrenar un algoritmo de aprendizaje supervisado (Regresión Lineal Múltiple / Árboles de Decisión) que permita predecir la tarifa óptima por noche de una nueva propiedad introducida al mercado basándose en variables predictoras clave.



### 8.4. Fase Prescriptiva y Conclusiones (Semana 12)

* **Objetivo:** Traducir las métricas estadísticas y las predicciones del modelo en recomendaciones estratégicas de negocio ("¿Qué pasaría si...?").

* **Impacto:** Las prescripciones orientarán las decisiones de la consultora detallando con precisión qué vecindarios específicos de distritos periféricos ofrecen el mejor retorno financiero con una exposición al riesgo controlada. TE PASO MI COLAB Q SE SUBIO TMB AL GITHUB Y DONDE YA ESTA TODO 

