# Analisis-Instacart
__Proyecto de análisis a la plataforma de delivery Instacart, análisis exploratiorio y visualización de datos__

<image src="https://github.com/BastianLQ/Analisis-Instacart/blob/main/Images/instacart.png" alt="Instacart">

_Fragmentos del notebook, para ver proyecto completo hacer click [aquí](https://portfoliodabastianlopez.on.drv.tw/Portafolio/P3.html)_

## Descripción del Proyecto
Este proyecto tiene como objetivo analizar datos de Instacart para extraer información valiosa sobre el comportamiento de los clientes. Utilizando [cinco datasets](https://drive.google.com/drive/folders/11ludpzThvf-xB6LfZW_xzCBK1Z91M_KA?usp=sharing) proporcionados por la plataforma, se llevó a cabo un proceso de limpieza, análisis y visualización de datos para identificar patrones y tendencias clave.
  
## Herramientas Utilizadas
- __Lenguaje de Programación:__ Python.
- __Entorno de Desarrollo:__ Jupyter Notebook.
- __Bibliotecas:__ Pandas, Matplotlib, Seaborn.

## Proceso del Proyecto
- __Descripción de los datos:__ Los datos fueron extraídos de [cinco datasets](https://drive.google.com/drive/folders/11ludpzThvf-xB6LfZW_xzCBK1Z91M_KA?usp=sharing) proporcionados por Instacart _(los datasets están en Drive porque superan el peso máximo permitido de GitHub)_, en esta fase, también, se les da una revisión superficial y se corrigen problemas de importación si es que llegasen a surgir.
- __Preprocesamiento de los datos:__ Se realizaron varias operaciones de limpieza, incluyendo manejo de valores nulos, normalización y formateo de datos.
- __Análisis exploratorio de datos (EDA):__ Esta fase se centró en analizar la integridad de los datos y rescatar insights valiosos. Utilizando pandas se exploraron los datos para obtener una comprensión inicial, intermedia y avanzada, y con matplotlib, se generaron visualizaciones para ilustrar los hallazgos clave del análisis.
- __Análisis de clústeres:__ Usando el algoritmo KMeans, se crean clústeres que son analizados en detalle.
- __Conclusiones:__ Se recopilan los principales hallazgos y se esbozan perfiles de clientes según los datos recopilados. Además se presentan insights accionables para personalizar la experiencia de usuario de la plataforma.

## Descubrimientos importantes
Comenzaremos listando los resultados en orden inverso al cual fueron descubiertos, comenzando por en análisis de clústeres para terminar con los descubrimientos generales:

### Creación de clústeres
Lo primero que se hizo para comenzar con el proceso de agrupación, fue determinar cuales serían las variables sobre las que trabajará el algoritmo. Para este caso se escogieron 4:
- Número de pedidos realizados.
- Total de productos comprados.
- Promedio de productos por pedido.
- Tasa de reordenación (métrica que indica la proporción de los productos que ya habían sido comprados anteriormente)
| Cluster | Tipo de cliente | Peaks semanales de compra | Porcentaje del total |
|---------|-----------------|---------------------------|----------------------|
| 0 | Clientes que realizan muchos pedidos de muchos artículos y tienden a repetir los productos | Lunes 10:00 | 38% |
| 1 | Clientes que realizan pocos pedidos de pocos artículos y repiten los productos | Lunes 10:00 | 32% |
| 2 | Clientes que realizan pocos pedidos de muchos artículos | Domingo 11:00 y 15:00 | 19% |
| 3 | Clientes que realizan pocos pedudis de pocos artículos y no repiten los productos | Domingos 15:00 | 11% |

## Ejecuta el proyecto [aquí](https://portfoliodabastianlopez.on.drv.tw/Portafolio/P3.html)
Para ver el diccionario de datos, el desarrollo completo en código, todos los gráficos y las conclusiones, haga click en el enlace de arriba.
