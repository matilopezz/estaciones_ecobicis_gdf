# 🚲 Análisis Geoespacial de Estaciones de Ecobici en CABA

Este proyecto es un análisis geoespacial exploratorio (EDA) que mapea la ubicación de las estaciones de Ecobici y las superpone sobre los límites de las comunas de la Ciudad Autónoma de Buenos Aires.

## 💾 Dataset

Se utilizaron dos fuentes de datos, del portal [BA Data](https://catalogo.datos.gba.gob.ar/dataset/):

* **Comunas (comunas.shp):** Un archivo Shapefile que contiene los polígonos (límites geográficos) de las comunas de CABA.
* **Estaciones Ecobici (nuevas-estaciones-bicicletas-publicas.csv):** Un archivo CSV con información de las estaciones, incluyendo sus coordenadas (`longitud` y `latitud`).

## 📈 Análisis y Visualizaciones Realizadas

El análisis principal se centró en la creación de una visualización geoespacial para entender la distribución de las estaciones.

### 1. Distribución de Estaciones de Ecobici por Comuna/Barrio

Se geolocalizaron todas las estaciones de Ecobici (convirtiendo sus coordenadas en puntos geométricos) y se proyectaron sobre el mapa de las comunas de CABA.

* **Visualización:** Se generó un mapa utilizando Matplotlib y Contextily que muestra:
    * **Capa 1 (Polígonos):** Los límites de las comunas (borde azul, sin relleno).
    * **Capa 2 (Puntos):** La ubicación de cada estación de Ecobici (marcador "x" de color verde).
    * **Capa Base:** Un mapa de fondo de OpenStreetMap para dar contexto geográfico.

## 🛠️ Herramientas Utilizadas

* **Lenguaje:** Python
* **Librerías:**
    * **Pandas:** Para la carga y manipulación inicial del archivo CSV de estaciones.
    * **GeoPandas:** Para la lectura del Shapefile, la creación del GeoDataFrame de estaciones (a partir de `longitud` y `latitud`) y la gestión de datos geoespaciales.
    * **Shapely:** (Usada por GeoPandas) para crear los objetos de geometría `Point`.
    * **Matplotlib:** Para la generación de la figura base (`fig, ax`) y la representación de las capas de datos (`.plot()`).
    * **Contextily:** Para añadir el mapa base (basemap) de OpenStreetMap y asegurar la correcta proyección (EPSG:3857).