## PROYECTO FINAL: AD3005 - INTRODUCCIÓN A DATA ANALYTICS Y BIG DATA
UNIVERSIDAD DE INGENIERÍA Y TECNOLOGÍA (UTEC)
Administración & Negocios Digitales | Ciclo 2026-1
CASO DE USO: CASO 3 - TURISMO DIGITAL Y PRECIOS DE ALOJAMIENTO EN NYC
1. PORTADA DEL EQUIPO
CONSULTORA FICTICIA: SafeInvest NYC Analytics (Consultora de Inversiones Inmobiliarias)

INTEGRANTES Y ROLES ACTUALIZADOS:
Matias Amaya -  Data Support & QA Analyst
Manuel Aguirre -  Data Support & Presentation SpecialisT
Giraldo Ruiz - Data Visualization Specialist
Eurymar Umbria -  Lead Data Scientist & Project Manager
Luciana Pacheco -  Business Strategist & Technical Write

Los propietarios independientes y gestores de propiedades turísticas (anfitriones boutique) que operan en la plataforma Airbnb en la ciudad de Nueva York se enfrentan a un complejo dilema operativo y de posicionamiento comercial. Maximizar los ingresos requiere equilibrar de manera óptima la fijación de tarifas diarias (precios premium) con el mantenimiento de una alta tasa de ocupación (mínimos días de ociosidad anual). Mientras que las zonas con una altísima densidad turística (como Manhattan o Brooklyn) permiten validar tarifas por noche elevadas debido a su atractivo entorno, también se enfrentan a mercados hipercompetitivos y saturados de oferta, lo que puede elevar la volatilidad de la ocupación. Por otro lado, posicionar anuncios en distritos periféricos ofrece la ventaja de mercados menos saturados, pero expone a los gestores a una demanda turística más inestable y a variables de entorno externas, como los índices de criminalidad local, que impactan directamente en la reputación del anuncio y la confianza del huésped.

Actualmente, las decisiones de tarificación y posicionamiento estratégico se toman de forma aislada basándose en intuiciones empíricas o análisis parciales de la plataforma. La falta de un framework analítico centralizado que integre de manera limpia el rendimiento interno del alojamiento (Airbnb) con factores del entorno inmediato (seguridad ciudadana y tracción del vecindario) impide identificar con precisión el "Punto Dulce" (Sweet Spot) operativo: zonas geográficas y características clave del anuncio que garanticen un equilibrio perfecto entre tarifas premium, alta ocupación y entornos seguros para el turista.

3. OBJETIVOS DEL PROYECTO
OBJETIVO PRINCIPAL:
Desarrollar un framework de analítica de datos mediante la integración de métricas de turismo digital y variables de entorno, con el fin de identificar las características y zonas geográficas óptimas en Nueva York que determinen un precio premium y una alta ocupación en Airbnb, orientando estratégicamente a propietarios y gestores en la optimización de sus ingresos y el posicionamiento seguro de sus alojamientos.

OBJETIVOS ESPECÍFICOS E HIPÓTESIS:
OE1: Evaluar la relación económica entre el valor patrimonial del suelo (entorno inmobiliario) por distrito y la tarifa diaria de los alojamientos en la plataforma Airbnb.

Hipótesis 1 (H1): ¿Existe una correlación lineal positiva y fuerte (r>0.70) entre el precio promedio de venta de las propiedades inmobiliarias de la zona (SALE PRICE) y la tarifa por noche (price) de los alojamientos en Airbnb, demostrando que el costo del entorno determina el potencial de un precio premium?

OE2: Analizar el impacto de los niveles de seguridad ciudadana del entorno sobre las tarifas y la competitividad de los alojamientos turísticos.

Hipótesis 2 (H2): ¿Los distritos catalogados con niveles de riesgo por criminalidad altos (como Manhattan o Brooklyn, niveles 5 y 4) presentan una distribución de precios con techos económicos más altos y una mayor densidad de ofertas en comparación con distritos de riesgo bajo, demostrando que la alta tracción turística absorbe el factor de riesgo público?

OE3: Determinar la dinámica entre la política de precios por noche y la tracción operativa (disponibilidad anual del inmueble).

Hipótesis 3 (H3): ¿Existe una relación inversa entre el precio de alquiler (price) y la disponibilidad anual de la propiedad (availability_365), sugiriendo que los alojamientos con tarifas premium experimentan una menor rotación de huéspedes y mayor tiempo ociosos en el mercado si su entorno no lo justifica?

OE4: Identificar el "Punto Dulce" (Sweet Spot) de eficiencia en la periferia de la ciudad mediante un análisis multivariable (Valor de la Zona - Seguridad - Retorno del Alojamiento).

Hipótesis 4 (H4): ¿Existen vecindarios específicos en distritos periféricos con costos de entorno moderados que registren un índice de eficiencia superior (Alta tarifa de Airbnb / Bajo costo del suelo de la zona) manteniendo un nivel de riesgo por criminalidad controlado o intermedio (como Queens o El Bronx), orientando a los gestores sobre dónde posicionar alojamientos altamente competitivos?

4. DESCRIPCIÓN DE LOS DATOS
Se integraron tres fuentes de datos robustas para consolidar una base unificada de 48,895 registros:

A. Dataset Base (NYC Airbnb Open Data - 2019): Contiene variables críticas de geolocalización, precios base, noches mínimas y disponibilidad (neighbourhood_group, price, availability_365, latitude, longitude).

B. Enriquecimiento Inmobiliario (NYC Rolling Sales Data): Extraído del NYC Department of Finance, proporcionando la métrica aggregada average_sale_price para contrastar el valor de adquisición vs. renta.

C. Enriquecimiento de Seguridad (Crime Index por Distrito): Escala categórica ordinal y numérica (1 al 5) basada en históricos policiales de criminalidad por condado para mapear el riesgo real del entorno.

5. METODOLOGÍA RIGUROSA Y DESARROLLO TÉCNICO (ETAPAS EJECUTADAS)
A diferencia de la planificación inicial, el proyecto se consolidó en un flujo end-to-end automatizado en Python que abarcó desde la ingesta hasta la prescripción analítica:

5.1. Carga, Enriquecimiento y EDA Inicial
Descarga directa e integración desde repositorios controlados en GitHub.

Mapeo geográfico cross-dataset y análisis descriptivo de las distribuciones originales de las tarifas en USD.

5.2. Limpieza Avanzada e Ingeniería de Características (Antes/Después)
Tratamiento del Sesgo Inmobiliario: Se identificó que las tarifas de Airbnb en Nueva York siguen una distribución log-normal severa debido a la presencia de outliers extremos (propiedades de lujo) y relaciones no lineales con las características del entorno.

Justificación de la Transformación Matemática: Se aplicó la función matemática log1p() (log(x+1)) sobre la variable objetivo price.

Impacto Estadístico: Esta transformación estabilizó la varianza, mejoró drásticamente el comportamiento frente al test de normalidad de Shapiro-Wilk, robusteció los coeficientes de correlación y previno el sobreajuste (overfitting), garantizando modelos predictivos mucho más estables.

5.3. Validación de Hipótesis y Pruebas Paramétricas
Ejecución de tests paramétricos con estricta validación previa de supuestos de normalidad para responder matemáticamente a las preguntas H1, H2, H3 y H4 planteadas por el negocio.

5.4. Pipeline de Modelado Predictivo
Implementación de una arquitectura de evaluación cruzada (5-Fold Cross-Validation) para asegurar la capacidad de generalización de los algoritmos.

El pipeline procesa las variables de entorno (precios del suelo y tasas de criminalidad) y las del alojamiento de manera paralela.

5.5. Comparación de Modelos
Evaluación del rendimiento de múltiples algoritmos supervisados utilizando métricas de error robustas: R 
2
  (Coeficiente de Determinación), RMSE (Raíz del Error Cuadrático Medio), MAE (Error Absoluto Medio) y MAPE (Error Porcentual Absoluto Medio).

Toda interpretación final de las métricas de error fue re-convertida matemáticamente de la escala logarítmica a la escala original en dólares (USD) para una lectura de negocio real y transparente.

5.6. Análisis Prescriptivo y Simulación de Escenarios
Desarrollo de análisis de sensibilidad sobre las variables clave del entorno (ej. fluctuaciones del precio del suelo o incrementos marginales de criminalidad) para proyectar el impacto económico directo en la rentabilidad, permitiendo construir escenarios de simulación predictiva para la toma de decisiones estratégicas de inversión inmobiliaria.

6. APÉNDICE: BITÁCORA DE INTELIGENCIA ARTIFICIAL Y CONTROL DE CALIDAD
El desarrollo técnico liderado en Python se rigió bajo estrictos estándares de calidad. Se utilizaron asistentes de IA Generativa (ChatGPT/Gemini) bajo un esquema de ingeniería de prompts enfocado en optimizar el tratamiento de estructuras complejas de datos y acelerar la codificación limpia:

Estrategias de Ingesta: Diseño de funciones vectorizadas para acelerar la fusión (merge) libre de nulos entre el dataset base y las capas de enriquecimiento.

Optimización de Modelos: Ajuste hiperparamétrico guiado para optimizar la convergencia de las funciones de pérdida en los modelos con variables transformadas mediante log1p().

7. ## Distribución de Responsabilidades

| Integrante      | Responsabilidad Principal                                                                                                                                  |
| --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Eurymar Umbria  | Integración de datos, limpieza, EDA, validación de hipótesis, modelado predictivo, comparación de modelos, simulación de escenarios y coordinación general |
| Giraldo Ruiz    | Desarrollo del dashboard                                                                                                                                   |
| Luciana Pacheco | Informe final y presentación                                                                                                                               |
| Manuel Aguirre  | Apoyo en revisión de datos y presentación                                                                                                                  |
| Matias Amaya    | Apoyo en QA, revisión de resultados y presentación                                                                                                         |

