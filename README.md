# **Teledetección e Incendios Forestales**
 
Mediante la teledetección es posible monitorear incendios forestales, tanto su como su ubicación como los daños que ocasionan, para ello tenemos una gran cantidad de satélites al servicio de este propósito, uno de los más conocidos quizá es la constelación landsat junto con la constelación sentinel, este último concretamente es el que usamos en este pequeño caso de estudio en donde analizamos un incendio ocurrido en el Departamento de Puno -  Provincia de Lampa - Distrito de Lampa, un pequeño incendio que quemó alrededor de 126,3 hectáreas.
 
## 1. Detección del Incendio Forestal
 
Antes de realizar cualquier análisis con respecto de incendios forestales es necesario conocer la ubicación de los incendios, es decir, conocer donde ocurrió y cuándo ocurrió, esto con el fin de poder hacer la adquisición de las imágenes satelitales a ser utilizadas para el análisis.
 
Entonces, ¿cómo es que podemos conocer el "cuándo" y "dónde" de los incendios forestales?; para este fin, existen una considerable cantidad de plataformas que nos brindan esta información, alguna de ellas son las siguientes:
 
- [FIRMS](https://firms.modaps.eosdis.nasa.gov/).
- [GWIS](https://gwis.jrc.ec.europa.eu/).
- [QUEIMADAS](https://queimadas.dgi.inpe.br/queimadas/portal).
- [GEOSERFOR](https://geo.serfor.gob.pe/visor/).
 
A este fin la plataforma que brinda algunas herramientas bastante útiles es **FIRMS**, puesto que además de visualizar información de "focos de calor" (posibles incendios), nos brinda herramientas de consulta de datos históricos, así mismo nos brinda un sistema de alertas, que no es otra cosa que recibir información de focos de calor en una determinada área de interés a nuestros correos electrónicos a tiempo "casi real".
 
 ![](./img/firms.png) 
 
Para este caso en particular obtuvimos que el incendio ocurrió en el Distrito de Lampa del Departamento de Puno el día **12 de agosto del 2021 alrededor del mediodía** , es aquí donde toma sentido el término "tiempo casi real" puesto que la hora que brinda los datos de focos de calor no es la hora de ocurrencia de incendio, sino más bien, es la hora de adquisición de la información satelital ya sea **MODIS** o **VIIRS**.
 
---
 
## 2. Adquisición de las Imágenes 
 
Con la información del "cuando" y "donde", ya podemos realizar la búsqueda de la o las imágenes a ser usadas en el análisis, en este caso particular utilizamos imágenes Sentinel 2, concretamente 2 imágenes de la misma escena, esto con el fin de determinar tanto el área quemada como la severidad de la quema.
 
Las imágenes fueron descargadas por la plataforma [Copernicus Open Access Hub](https://scihub.copernicus.eu/) realizando el filtrado según la información del "cuando" y "donde" del incendio forestal.
 
 
 ![](./img/img.png) 
 
---
## 3. Procesamiento de las imágenes 
 
Todo el análisis se hizo utilizando [QGIS](https://qgis.org/es/site/), apoyandonos de un pluging bastante conocido que es el  [SCP](https://fromgistors.blogspot.com/p/semi-automatic-classification-plugin.html) que entre muchas de las funcionalidades que posee, tenemos el de poder hacer el pre procesamiento de las imágenes. Sumado a ello utilizamos un [modelo automatizado](https://github.com/hugoaluque/Modelo-QGIS_Incendios_Forestales) hecho en el ensamblador de modelos de QGIS, este modelo sirve para determinar area quemada y severidad de la quema utilizando como recurso las imégenes Satelitales  de antes y despues de un incendio.
 
 ![](./img/modelo.png) 
 
---
## 4. Resultados
 
Los resultados del análisis arrojaron que se quemaron **126,392** hectáreas aproximadamente, en su mayoría pajonales andinos, tipo de vegetación que es predominante en las zonas altiplánicas del Perú como es este caso.
concretamente el modelo usado nos da como resultado un archivo vectorial (.shp), el cual necesita recibir un pequeño arrego debido a que la metodología usada confunde algunos otros componentes de la superficie como área quemada (sombras, agua y nubes), también puede incluir el área quemada de otro incendio cercano.
 
 ![](./img/area_quemada.png) 
 
 
Por otro lado el modelo también calcula la severidad de la quema, obteniendo que en su mayoría el incendio causó una severidad baja, esto puede deberse a que el tipo de vegetación(pajonales andinos) suele propagarse y consumirse rápidamente además el fuego no consume la totalidad de la vegetación (partes de la vegetación próximas al suelo), pero, deja bastante rastro de ceniza.
 
![](./img/severidad.png) 
 
Finalmente en QGIS se generó un video y una animación en la herramienta de vista 3D, apoyándonos de un modelo digital de elevación descargado con el pluging [SRTM Downloader](https://plugins.qgis.org/plugins/SRTM-Downloader/).
 
  ![](./GIF-VIDEO/incendio.gif) 

