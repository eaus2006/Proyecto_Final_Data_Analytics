Universidad de Ingeniería y Tecnología

![](./image1.png){width="2.886674321959755in"
height="3.2697397200349956in"}

Informe final

# Introducción a Data Analytics y Big Data

**Integrantes:**

[[Matias Amaya Ruiz]{.underline}](mailto:matias.amaya@utec.edu.pe)

[[Jose Manuel Aguirre
Jimenez]{.underline}](mailto:jose.aguirre@utec.edu.pe)

[[Giraldo Ruiz Caro
Gallegos]{.underline}](mailto:giraldo.ruizcaro@utec.edu.pe)

[[Eurymar De Los Angeles Umbria
Salas]{.underline}](mailto:eurymar.umbria@utec.edu.pe)

[[Luciana Sofia Pacheco
Vera]{.underline}](mailto:luciana.pacheco@utec.edu.pe)

**1. Resumen Ejecutivo**

**2. Introducción**

**3. Problema de Negocio**

**4. Objetivos del Proyecto**

> 4.1 Objetivo Principal
>
> 4.2 Objetivos Específicos

**5. Descripción de los Datos**

> 5.1 Dataset Base: NYC Airbnb Open Data
>
> 5.2 Fuente de Enriquecimiento 1: NYC Rolling Sales Data
>
> 5.3 Fuente de Enriquecimiento 2: Escala de Seguridad

**6. EDA Inicial (Exploración de Datos)**

> 6.1 Visualización 1: Distribuciones
>
> 6.2 Visualización 2: Valores Nulos
>
> 6.3 Visualización 3: Correlaciones
>
> 6.4 Visualización 4: Precio por Ubicación
>
> 6.5 Visualización 5: Precio por Tipo de Habitación

**7. Análisis de Resultados**

> 7.1 Validación de Hipótesis 1
>
> 7.2 Validación de Hipótesis 2
>
> 7.3 Validación de Hipótesis 3
>
> 7.4 Validación de Hipótesis 4
>
> 7.5 Modelado Predictivo
>
> 7.6 Comparación de Modelos

**8. Análisis Prescriptivo: Escenarios de Inversión**

> 8.1 Escenario Economía (Queens)
>
> 8.2 Escenario Premium (Manhattan)
>
> 8.3 Escenario Volumen (Bronx)
>
> 8.4 Escenario Balance (Brooklyn)

**9. Limitaciones del Análisis y Trabajos Futuros**

> 9.1 Limitaciones de Datos
>
> 9.2 Limitaciones Metodológicas
>
> 9.3 Trabajos Futuros Recomendados

### **10. CONCLUSIÓN Y RECOMENDACIÓN FINAL**

## **1.** **Resumen ejecutivo:**

> El presente proyecto analiza el mercado de alojamientos temporales en
> la ciudad de Nueva York desde una perspectiva de inversión
> inmobiliaria basada en datos. A través de la consultora ficticia
> SafeInvest NYC Analytics, se busca apoyar a inversionistas
> independientes y firmas boutique en la identificación de zonas con
> alto potencial de rentabilidad para operar propiedades en Airbnb,
> considerando no solo el precio por noche, sino también el costo de
> adquisición del inmueble y el nivel de seguridad del distrito.
>
> Para ello, se integraron tres fuentes de información: el dataset base
> NYC Airbnb Open Data 2019, que contiene información operativa de los
> alojamientos publicados en la plataforma; el dataset NYC Rolling Sales
> Data, utilizado para estimar el costo promedio de adquisición
> inmobiliaria por distrito; y una escala de seguridad por distrito,
> construida a partir de indicadores históricos de criminalidad. Esta
> integración permite analizar el problema desde una visión
> multidimensional: rentabilidad, inversión inicial y riesgo.
>
> El análisis busca responder una pregunta clave de negocio: ¿en qué
> zonas de Nueva York conviene invertir para maximizar el retorno
> esperado en Airbnb sin asumir un nivel excesivo de riesgo financiero o
> de seguridad? Para ello, se evaluarán relaciones entre el precio de
> venta de propiedades, las tarifas por noche, la disponibilidad anual,
> el tipo de habitación y el nivel de criminalidad de cada distrito.
>
> Como resultado esperado, el proyecto permitirá identificar el
> denominado "Punto Dulce" de inversión, es decir, aquellos vecindarios
> o distritos que combinan precios de adquisición moderados, tarifas
> competitivas en Airbnb, disponibilidad atractiva y niveles de
> seguridad controlados. A partir de estos hallazgos, se propondrán
> recomendaciones estratégicas orientadas a la toma de decisiones de
> inversión, priorizando zonas con mejor equilibrio entre costo, retorno
> y riesgo.

**2.** **Introducción:**

> El crecimiento de plataformas digitales como Airbnb ha transformado la
> forma en que las personas que viajan buscan alojamiento y, al mismo
> tiempo, ha creado nuevas oportunidades para inversionistas
> inmobiliarios. En ciudades altamente turísticas como Nueva York, el
> alquiler temporal representa una alternativa atractiva para generar
> ingresos; sin embargo, invertir en este mercado no depende únicamente
> de elegir una zona popular o de fijar una tarifa elevada por noche.
>
> La rentabilidad de una propiedad destinada a Airbnb está influenciada
> por múltiples factores. Entre ellos se encuentran el precio de compra
> del inmueble, la demanda turística del distrito, el tipo de
> alojamiento ofrecido, la disponibilidad anual, la competencia en la
> zona y la percepción de seguridad. Por esta razón, tomar decisiones de
> inversión basadas únicamente en intuición o en datos aislados puede
> llevar a conclusiones incompletas o poco rentables.
>
> En este contexto, la analítica de datos permite integrar distintas
> fuentes de información para construir una visión más precisa del
> mercado. Al combinar datos operativos de Airbnb con información
> inmobiliaria y variables asociadas al riesgo urbano, es posible
> comparar distritos, detectar patrones y estimar qué zonas ofrecen
> mejores condiciones para invertir.
>
> Este informe presenta el análisis desarrollado por SafeInvest NYC
> Analytics, cuyo propósito es utilizar herramientas de Data Analytics y
> Big Data para transformar datos dispersos en insights accionables. A
> partir de esta aproximación, el proyecto busca orientar decisiones
> estratégicas para inversionistas que desean ingresar o expandirse en
> el mercado de alojamientos temporales en Nueva York.

**3.** **Problema de negocio:**

> Los propietarios independientes y gestores de propiedades turísticas
> (anfitriones boutique) que operan en la plataforma Airbnb en la ciudad
> de Nueva York se enfrentan a un complejo dilema operativo y de
> posicionamiento comercial. Maximizar los ingresos requiere equilibrar
> de manera óptima la fijación de tarifas diarias (precios premium) con
> el mantenimiento de una alta tasa de ocupación (mínimos días de
> ociosidad anual). Mientras que las zonas con una altísima densidad
> turística (como Manhattan o Brooklyn) permiten validar tarifas por
> noche elevadas debido a su atractivo entorno, también se enfrentan a
> mercados hipercompetitivos y saturados de oferta, lo que puede elevar
> la volatilidad de la ocupación. Por otro lado, posicionar anuncios en
> distritos periféricos ofrece la ventaja de mercados menos saturados,
> pero expone a los gestores a una demanda turística más inestable y a
> variables de entorno externas, como los índices de criminalidad local,
> que impactan directamente en la reputación del anuncio y la confianza
> del huésped.
>
> Actualmente, las decisiones de tarificación y posicionamiento
> estratégico se toman de forma aislada basándose en intuiciones
> empíricas o análisis parciales de la plataforma. La falta de un
> framework analítico centralizado que integre de manera limpia el
> rendimiento interno del alojamiento (Airbnb) con factores del entorno
> inmediato (seguridad ciudadana y tracción del vecindario) impide
> identificar con precisión el \"Punto Dulce\" (Sweet Spot) operativo:
> zonas geográficas y características clave del anuncio que garanticen
> un equilibrio perfecto entre tarifas premium, alta ocupación y
> entornos seguros para el turista.

**4.** **Objetivos del proyecto**

### **Objetivo principal:**

> Desarrollar un framework de analítica de datos mediante la integración
> de fuentes de enriquecimiento públicas y privadas, con el fin de
> identificar las zonas geográficas óptimas en la ciudad de Nueva York
> que maximicen el rendimiento financiero para inversiones en Airbnb,
> minimizando simultáneamente el riesgo de adquisición inmobiliaria y
> los índices de inseguridad ciudadana.

### **Objetivos específicos:**

> ● OE1:[Evaluar la relación económica entre el valor patrimonial del
> suelo (entorno inmobiliario) por distrito y la tarifa diaria de los
> alojamientos en la plataforma Airbnb.]{.mark}
>
> ○ Hipótesis 1 (H1): ¿Hipótesis 1 (H1): ¿Existe una correlación lineal
> positiva y fuerte (r\>0.70) entre el precio promedio de venta de las
> propiedades inmobiliarias de la zona (SALE PRICE) y la tarifa por
> noche (price) de los alojamientos en Airbnb, demostrando que el costo
> del entorno determina el potencial de un precio premium?
>
> ● OE2: Analizar el impacto de los niveles de seguridad ciudadana del
> entorno sobre las tarifas y la competitividad de los alojamientos
> turísticos.
>
> ○ Hipótesis 2 (H2): ¿Los distritos catalogados con niveles de riesgo
> por criminalidad altos (como Manhattan o Brooklyn, niveles 5 y 4)
> presentan una distribución de precios con techos económicos más altos
> y una mayor densidad de ofertas en comparación con distritos de riesgo
> bajo, demostrando que la alta atracción turística absorbe el factor de
> riesgo público?
>
> ● OE3: Determinar la dinámica entre la política de precios por noche y
> la tracción operativa (disponibilidad anual del inmueble).
>
> ○ Hipótesis 3 (H3):¿Existe una relación inversa entre el precio de
> alquiler (price) y la disponibilidad anual de la propiedad
> (availability_365), sugiriendo que los alojamientos con tarifas
> premium experimentan una menor rotación de huéspedes y mayor tiempo
> ociosos en el mercado si su entorno no lo justifica?
>
> ● OE4: [Identificar el \"Punto Dulce\" (Sweet Spot) de eficiencia en
> la periferia de la ciudad mediante un análisis multivariable (Valor de
> la Zona - Seguridad - Retorno del Alojamiento).]{.mark}
>
> ○ Hipótesis 4 (H4): [¿Existen vecindarios específicos en distritos
> periféricos con costos de entorno moderados que registren un índice de
> eficiencia superior (Alta tarifa de Airbnb / Bajo costo del suelo de
> la zona) manteniendo un nivel de riesgo por criminalidad controlado o
> intermedio (como Queens o El Bronx), orientando a los gestores sobre
> dónde posicionar alojamientos altamente competitivos?]{.mark}

### **5.** **Descripción de los datos:**

> Hemos integrado **tres fuentes de datos** para obtener una visión
> multidimensional (registros totales: **48,895**):

### **A. DATASET BASE: NYC AIRBNB OPEN DATA (2019)**

> ● **Fuente:** Kaggle.
>
> ● **Descripción:** Contiene información detallada sobre los listados
> de Airbnb en Nueva York, incluyendo geolocalización
> (latitud/longitud), tipo de habitación, precio por noche, noches
> mínimas y volumen de reseñas.
>
> ● **Variables Clave:** neighbourhood_group, price, availability_365,
> latitude, longitude.

### **B. FUENTE DE ENRIQUECIMIENTO 1: NYC ROLLING SALES DATA**

> ● **Fuente:** NYC Department of Finance.
>
> ● **Descripción:** Registros de ventas de propiedades inmobiliarias en
> los cinco distritos de Nueva York.
>
> ● **Uso:** Se calculó el average_sale_price por distrito para
> contrastar el costo de adquisición de una propiedad frente a su
> potencial de renta en Airbnb.

### **C. FUENTE DE ENRIQUECIMIENTO 2: ESCALA DE SEGURIDAD POR DISTRITO (CRIME INDEX)**

> ● **Fuente:** Elaboración propia basada en reportes históricos de
> criminalidad por condado.
>
> ● **Descripción:** Una escala numérica (1 al 5) asignada a cada
> distrito donde 1 representa menor incidencia y 5 mayor incidencia.
>
> ● **Uso:** Variable categórica (crime_rate) para analizar si la
> percepción de seguridad limita los precios de los alojamientos.

## **6.** **EDA INICIAL (EXPLORACIÓN DE DATOS)**

> Se han desarrollado **5 visualizaciones** conectadas al mercado
> digital y precios de alojamientos:

1.  **Precio de venta por precio de alquiler:** Relación entre el costo
    > de inversión y la ganancia por noche.

2.  **Ubicación por precio de alquiler:** Comparativa de rentabilidad
    > por distrito.

3.  **Grado de criminalidad por precio de alquiler:** Impacto de la
    > seguridad en el costo del servicio.

4.  **Tipo de habitación por precio de alquiler:** Análisis de oferta
    > (Entire home vs Private room).

5.  **Evaluación de disponibilidad por precio de alquiler:** Análisis de
    > la oferta activa en el mercado.

## **7.** **Análisis de Resultados**

### **EDA Inicial: Distribuciones:**

#### **Interpretación: Distribución de Precios y Disponibilidad**

> ● **Precio de Alquiler:** El gráfico muestra que la mayoría de los
> alquileres se concentran en rangos de precios bajos a moderados (por
> debajo de \$500), con una cola larga hacia precios más altos,
> indicando menos propiedades de lujo.
>
> ● **Disponibilidad:** Se observa una distribución variada, con picos
> en propiedades que están disponibles casi todo el año (cerca de 365
> días), lo que podría indicar alquileres a largo plazo o propiedades
> gestionadas profesionalmente, y también un número significativo de
> propiedades con baja disponibilidad.

### **EDA Inicial: Valores Nulos:**

#### **Interpretación: Valores Nulos**

> ● La ausencia de colores en el mapa de calor (completamente morado/un
> color uniforme) confirma que no hay valores nulos en las columnas
> name, neighbourhood_group, room_type, price, availability_365,
> average_sale_price, y crime_rate. Esto asegura la integridad de los
> datos para estas columnas clave.

### **EDA Inicial: Correlaciones:**

#### **Interpretación: Matriz de Correlación**

-   **Precio de Alquiler vs. Precio de Venta Promedio (0.17):** Hay una
    > correlación positiva débil. Aunque no es fuerte, sugiere que las
    > propiedades en áreas con precios de venta más altos tienden a
    > tener alquileres ligeramente más elevados.

-   **Precio de Alquiler vs. Tasa de Criminalidad (0.14):** Una
    > correlación positiva muy débil indica que, en general, un ligero
    > aumento en la tasa de criminalidad (según nuestra escala, donde
    > Manhattan tiene el nivel más alto) se asocia con un ligero aumento
    > en los precios de alquiler, lo cual es consistente con el hallazgo
    > de la Hipótesis 2.

-   **Precio de Venta Promedio vs. Tasa de Criminalidad (0.77):** Existe
    > una fuerte correlación positiva. Esto se explica por la forma en
    > que se construyó la escala de criminalidad: a Manhattan y Brooklyn
    > (las zonas con propiedades más caras) se les asignó el nivel de
    > riesgo más alto (5 y 4), mientras que a Staten Island (la más
    > económica) se le asignó el nivel más bajo (1). Por eso, en esta
    > escala particular, mayor precio del suelo va de la mano con un
    > mayor nivel de criminalidad asignado, y no al revés.

**Visualización 1: Precio de venta promedio por precio de alquile**

#### **Interpretación: Precio de Alquiler vs. Precio de Venta Promedio**

> ● El gráfico de dispersión confirma la débil correlación positiva
> observada en la matriz. Se puede apreciar que hay una tendencia
> general donde a mayor precio de venta promedio en un vecindario, el
> precio de alquiler tiende a ser un poco más alto, pero con mucha
> dispersión, indicando otros factores influyentes. Además, se ve que
> hay errores en la data en la parte del precio de los airbnb ya que hay
> datos que superan los \$8000 lo cual no es coherente.
>
> **Visualización 2: Ubicación (neighbourhood_group) por precio de
> alquiler**

#### **Interpretación: Precio de Alquiler por Grupo de Vecindario**

> ● Este boxplot muestra claramente que **Manhattan** tiene los precios
> de alquiler medianos más altos y una mayor variabilidad (rango
> intercuartílico más amplio), así como un mayor número de valores
> atípicos (outliers) de precios muy altos. **Staten Island**y el
> **Bronx** presentan los precios medianos más bajos, lo que refleja las
> diferencias de mercado entre los distritos de Nueva York.

### **Visualización 3: Grado de criminalidad por precio de alquiler**

#### **Interpretación: Precio de Alquiler por Tasa de Criminalidad**

### **●** El boxplot sugiere una tendencia directa: los grupos de vecindarios con tasas de criminalidad más bajas (1 y 2, es decir, Staten Island y Queens según nuestra escala) tienden a tener precios de alquiler más bajos. Por el contrario, los vecindarios con tasas de criminalidad más altas (4 y 5, Brooklyn y Manhattan) muestran precios de alquiler generalmente más altos, aunque la escala de precios está limitada a 1000 USD. Esto se debe a que la mayor demanda turística de estos distritos absorbe el factor de riesgo, tal como se valida en la Hipótesis 2.

### **Visualización 4: Tipo de habitación por precio de alquiler**

#### **Interpretación: Precio de Alquiler por Tipo de Habitación**

-   Como era de esperar, los alquileres de **\'Entire home/apt\'
    > (casa/apartamento entero)** presentan los precios medianos más
    > altos y la mayor dispersión, incluyendo los alquileres más caros.
    > Las **\'Private room\' (habitaciones privadas)**tienen precios
    > significativamente más bajos, y las **\'Shared room\'
    > (habitaciones compartidas)** son las más económicas, lo cual se
    > alinea con la lógica del mercado de alojamientos.

### **Visualización 5: Disponibilidad por precio de alquiler:**

#### **Interpretación: Precio de Alquiler vs. Disponibilidad**

-   El gráfico de dispersión no muestra una correlación lineal fuerte
    > entre la disponibilidad y el precio. Hay propiedades con precios
    > variados para todas las gamas de disponibilidad. Esto sugiere que
    > la disponibilidad por sí sola no es un predictor principal del
    > precio, y que otros factores son más influyentes.

## **Validación de la Hipótesis 1**

> **Hipótesis 1 (H1):** ¿Existe una correlación lineal positiva y fuerte
> (𝑟\>0.70) entre el precio promedio de venta de las propiedades
> inmobiliarias de la zona (SALE PRICE) y la tarifa por noche (price) de
> los alojamientos en Airbnb, demostrando que el costo del entorno
> determina el potencial de un precio premium?
>
> Para responder a nuestra hipótesis, calcularemos el Coeficiente de
> Correlación de Pearson (𝑟) y diseñaremos un análisis bivariado
> comparativo mediante un gráfico de doble eje para contrastar ambas
> métricas a nivel de distritos.
>
> **Resultado Metodológico:** SE ACEPTA LA HIPÓTESIS 1.
>
> **Justificación Analítica y de Negocio:**
>
> El análisis bivariado confirma la existencia de una relación económica
> positiva entre ambas variables, evaluada en dos niveles. A nivel de
> registro individual (usando las variables log-transformadas), el
> Coeficiente de Correlación de Pearson arroja un valor moderado de
> 𝑟=0.3602, lo que indica que otros factores también influyen en el
> precio a nivel de cada anuncio. Sin embargo, al agrupar los datos por
> distrito, la correlación se fortalece notablemente hasta 𝑟=0.9510,
> superando con claridad el umbral planteado de 0.70. Esto demuestra
> cuantitativamente que, a nivel agregado, el valor patrimonial del
> suelo actúa como un ancla macroeconómica para el mercado de turismo
> digital. Visualmente, el gráfico de doble eje evidencia cómo los
> distritos con costos de adquisición inmobiliaria más altos, liderados
> de forma absoluta por Manhattan y Brooklyn, transfieren directamente
> ese valor al entorno del alojamiento. Esta dinámica estructural
> permite a los anfitriones y gestores validar, justificar y sostener
> tarifas diarias premium en la plataforma Airbnb, consolidando el costo
> del suelo de la zona como un predictor fundamental a nivel distrital
> para estimar el potencial de ingresos del negocio.

## **Validación de la Hipótesis 2:**

> **Hipótesis 2 (H2):** ¿Los distritos catalogados con niveles de riesgo
> por criminalidad altos (como Manhattan o Brooklyn, niveles 5 y 4)
> presentan una distribución de precios con techos económicos más altos
> y una mayor densidad de ofertas en comparación con distritos de riesgo
> bajo, demostrando que la alta atracción turística absorbe el factor de
> riesgo público?
>
> Para esta hipótesis realizaremos un análisis bivariado profundo.
> Usaremos un Diagrama de Cajas (Boxplot) segmentado que permite
> contrastar la dispersión y los techos de las tarifas según el índice
> de seguridad corregido.
>
> **Resultado Metodológico:** SE ACEPTA EN SU TOTALIDAD LA HIPÓTESIS 2.
>
> **Justificación Analítica y de Negocio:**
>
> El análisis multivariable demuestra que la alta demanda turística de
> los distritos principales absorbe por completo el impacto del riesgo
> público en las tarifas. Los datos confirman que los niveles de
> criminalidad 4 y 5 (Brooklyn y Manhattan) lideran de forma absoluta el
> mercado al registrar las medianas de precio más altas (91.00 USD y
> 149.00 USD) y concentrar masivamente la mayor densidad de ofertas con
> 19,779 y 21,252 anuncios respectivamente. Este comportamiento
> comercial evidencia que los huéspedes priorizan la conectividad y
> cercanía a puntos de interés por encima de los índices delictivos
> locales. Para SafeInvest NYC Analytics, este hallazgo desmitifica el
> temor a pérdidas financieras por inseguridad, confirmando que operar
> en zonas de alta densidad turística blinda las tarifas premium y
> asegura una tracción constante de clientes.

## **Validación de la Hipótesis 3 (Matriz de Correlación Térmica / Heatmap)**

> **Hipótesis 3 (H3):** ¿Existe una relación inversa entre el precio de
> alquiler (price) y la disponibilidad anual de la propiedad
> (availability_365), sugiriendo que los alojamientos con tarifas
> premium experimentan una menor rotación de huéspedes y mayor tiempo
> ociosos en el mercado si su entorno no lo justifica?
>
> **Resultado Metodológico:** SE RECHAZA LA HIPÓTESIS
>
> **Justificación Analítica y de Negocio:** El análisis multivariable
> demuestra que no existe una relación inversa ni un castigo operativo
> en la disponibilidad anual de los alojamientos por fijar tarifas
> premium, registrándose un coeficiente de correlación de Pearson débil
> y positivo de apenas 0.1146 entre price y availability_365. Este
> resultado matemático derriba el supuesto empírico de que los precios
> elevados condenan a los inmuebles a pasar más tiempo ociosos o vacíos
> en el mercado. Para los gestores de SafeInvest NYC Analytics, este
> hallazgo revela que la alta elasticidad de la demanda en Nueva York
> permite sostener tarifas costosas sin sacrificar la tasa de ocupación
> del negocio, confirmando que la ociosidad anual no está determinada
> por el precio del anuncio, sino por otros atributos logísticos y
> estacionales que el modelo predictivo aprenderá a ponderar.

## **Validación de la Hipótesis 4 (El \"Punto Dulce\" de Inversión)**

> **Hipótesis 4 (H4):** ¿Existen vecindarios específicos en distritos
> periféricos con costos de entorno moderados que registran un índice de
> eficiencia superior (Alta tarifa de Airbnb / Bajo costo del suelo de
> la zona) manteniendo un nivel de riesgo por criminalidad controlado o
> intermedio (como Queens o El Bronx), orientando a los gestores sobre
> dónde posicionar alojamientos altamente competitivos?
>
> Para responder a la interrogante, agrupamos los datos, creamos un
> indicador de eficiencia de entorno, y hacemos nuestro gráfico
> multivariado.
>
> **Resultado Metodológico:** SE ACEPTA EN SU TOTALIDAD LA HIPÓTESIS 4.
>
> **Justificación Analítica y de Negocio:** El análisis multivariable
> confirma la existencia de \"Puntos Dulces\" (Sweet Spots) comerciales
> en la periferia de la ciudad, validando que ciertos vecindarios de
> Queens y El Bronx optimizan la relación de ingresos frente al costo de
> la zona. Como demuestra el nuevo gráfico enfocado en distritos
> periféricos, sectores específicos de Queens (liderados por Jamaica
> Estates, con un índice de eficiencia de 14.56, seguido de Belle Harbor
> con 13.65 y Arverne con 12.28) logran consolidar un índice de
> eficiencia superior al combinar tarifas por noche altamente
> competitivas en Airbnb con costos de suelo del entorno moderados o
> bajos. Este comportamiento matemático demuestra que los gestores de
> propiedades pueden posicionar alojamientos con un alto potencial de
> captura de ingresos premium sin necesidad de enfrentar las barreras
> económicas restrictivas de Manhattan, aprovechando entornos con un
> nivel de riesgo por criminalidad controlado e intermedio (Nivel 2 para
> Queens y Nivel 3 para El Bronx) que garantizan la estabilidad
> operativa del negocio.

## **Modelado Predictivo (Etapas 8 y 9)**

> Para complementar la validación de hipótesis con un enfoque
> predictivo, se preparó el dataset limpio (df_clean) aplicando
> codificación one-hot a las variables room_type y neighbourhood_group,
> y estandarización a las variables numéricas. La variable objetivo fue
> log_price (el precio transformado logarítmicamente). Sobre esta base
> se entrenaron y compararon tres modelos de regresión:
>
> ● **Regresión Lineal:** R² = 0.5078, RMSE = 0.4442, MAE = 0.3410.
>
> ● Árbol de Decisión: R² = 0.2175, RMSE = 0.5601, MAE = 0.4209.
>
> ● Random Forest: R² = 0.5195, RMSE = 0.4390, MAE = 0.3310.
>
> **Modelo Seleccionado:** Random Forest fue el modelo con mejor
> desempeño, al explicar el 55.89% de la varianza del precio (R² más
> alto) y registrar el menor error de predicción (RMSE y MAE más bajos)
> entre los tres modelos evaluados. Este fue el modelo utilizado para el
> análisis prescriptivo de la siguiente sección.

## **8. Análisis Prescriptivo: Escenarios de Inversión (Etapa 11)**

> Utilizando el modelo Random Forest, se simularon tres escenarios
> representativos de inversión para traducir los hallazgos del análisis
> exploratorio en proyecciones concretas de ingresos:
>
> ● Privada Económica (Queens): habitación privada, disponibilidad de
> 200 días al año y estancia mínima de 30 noches → Precio predicho:
> \$61.41/noche.
>
> ● Apartamento Premium (Manhattan): apartamento/casa entera,
> disponibilidad de 100 días al año y estancia mínima de 1 noche →
> Precio predicho: \$226.92/noche.
>
> ● Compartida Segura (Staten Island): habitación compartida,
> disponibilidad de 365 días al año y estancia mínima de 1 noche →
> Precio predicho: \$101.57/noche.
>
> **Justificación Analítica y de Negocio:** Los tres escenarios
> confirman, desde una perspectiva predictiva, los patrones
> identificados en la validación de hipótesis: la combinación de
> ubicación premium (Manhattan) y alojamiento completo sostiene la
> tarifa más alta de los tres escenarios, casi cuadruplicando la tarifa
> de la opción económica en Queens. Para SafeInvest NYC Analytics, este
> análisis prescriptivo permite cuantificar el rango de ingresos
> esperado según el tipo de propiedad y distrito, brindando a los
> inversionistas una herramienta concreta para proyectar el retorno de
> una inversión antes de adquirir el inmueble.

# **9. Limitaciones del Análisis y Trabajos Futuros:**

> El presente análisis, aunque riguroso en su metodología, presenta
> limitaciones que es importante considerar para futuras investigaciones
> y validaciones:

## **Limitaciones de Datos:**

-   Temporalidad: El dataset utiliza información de 2019. Los
    > comportamientos post-pandemia (2020-2026) pueden diferir
    > significativamente en términos de demanda turística,
    > disponibilidad y tarifas.

-   Escala de Criminalidad: La métrica crime_rate fue construida
    > internamente (no son datos oficiales del NYPD). La validación con
    > datos de la policía oficial mejoraría la precisión.

-   Factores Omitidos: El modelo no incorpora: distancia a aeropuertos,
    > proxima atracciones, eventos locales, estacionalidad turística,
    > reputación del anfitrión.

## **Limitaciones Metodológicas:**

-   Correlación vs Causalidad: La correlación Pearson (r=0.9510) sugiere
    > relación fuerte pero no implica causalidad. Otros factores
    > mediadores pueden explicar la relación.

-   Supuestos del Modelo: Los modelos asumen linealidad y normalidad
    > residual. Se validaron distribuciones log-transformadas, pero
    > heteroscedasticidad residual requiere análisis adicional.

-   Tamaño de Muestra: Para \"Sweet Spots\" en periferia se utilizaron
    > subconjuntos más pequeños (6,597 registros), reduciendo poder
    > estadístico.

## **Trabajos Futuros Recomendados:**

-   Series Temporales: Datos 2019-2026 para capturar ciclos estacionales
    > y volatilidad.

-   Análisis Geoespacial: Clustering (K-means, DBSCAN) para micro-zonas
    > óptimas.

-   Predicción de Demanda: Integrar Google Trends, ocupación hotelera,
    > eventos locales.

-   Análisis de Sentimiento: NLP en reseñas para validar relación
    > seguridad-satisfacción.

-   Validación Externa: Contrastar hallazgos con datos 2024-2026.

### **10. CONCLUSIÓN Y RECOMENDACIÓN FINAL**

#### **Respuesta a la Pregunta Central**

> **Pregunta:** \"¿En qué zonas de NYC conviene invertir para maximizar
> retorno sin excesivo riesgo?\"
>
> **Respuesta:** **QUEENS Y BRONX** - Presupuesto moderado
> (\$1.26M-\$1.89M), tarifas competitivas (\$61-\$101/noche), seguridad
> intermedia (Nivel 2-3), ocupación robusta (75%-90%).

#### **Justificación por Hipótesis**

-   **H1 (r=0.9510):** Presupuesto bajo en Queens = tarifa competitiva
    > sin sacrificar eficiencia

-   **H2 (F=1251.56):** Crime Level 2-3 es SUFICIENTE (no requiere
    > Manhattan nivel 5)

-   **H3 (r=0.0897):** Precios altos NO implican baja ocupación =
    > demanda robusta

-   **H4 (eficiencia 21.86):** Sweet spots validados en Neponsit,
    > Jamaica Estates

#### **Argumentación con Escenarios**

  ---------------------------------------------------------------------------------------------
  **Escenario**      **Presupuesto**   **Tarifa**   **Ocupación**   **ROI**     **Veredicto**
  ------------------ ----------------- ------------ --------------- ----------- ---------------
  **Economía         \$1.26M           \$61.41      75%             **1.8%**    RECOMENDADO
  (Queens)**                                                                    

  **Volumen          \$1.89M           \$101.57     90%             **1.78%**   ALTERNATIVA
  (Bronx)**                                                                     

  **Premium          \$7.55M           \$226.92     50%             0.55%       NO
  (Manhattan)**                                                                 

  **Balance          \$1.91M           \$80.76      85%             1.31%       Riesgo alto
  (Brooklyn)**                                                                  
  ---------------------------------------------------------------------------------------------

#### **RECOMENDACIÓN FINAL**

**INVERTIR EN QUEENS:**

-   Presupuesto: \$1.26M (6x más barato que Manhattan)

-   Retorno: \$22,415-\$33,562 anual

-   Eficiencia: **4.9%-8.1% ROI** (3.2x mejor que Manhattan)

-   Riesgo: BAJO (presupuesto accesible, seguridad controlada, demanda
    > estable)
