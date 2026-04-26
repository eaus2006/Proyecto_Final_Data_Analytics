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


Matias: Buscar data fuentes de enrequisimiento

Lu: Hipotesis y objetivos

Eurymar: Plan, descripcion del problema y datos

Giraldo y Manuel: 4. EDA Inicial: al menos 5 visualizaciones comentadas (distribuciones, valores nulos, primeras
correlaciones) Y LO DE IA
