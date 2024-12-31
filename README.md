# Analisis-Instacart
__Proyecto de análisis a la plataforma de delivery Instacart, análisis exploratiorio y visualización de datos__

<image src="https://github.com/BastianLQ/Analisis-Instacart/blob/main/Images/instacart.png" alt="Instacart">

_Para ver desarrollo en código hacer click [aquí](https://portfoliodabastianlopez.on.drv.tw/Portafolio/P3.html)_

## Descripción del Proyecto
Este proyecto tiene como objetivo analizar datos de Instacart para extraer información valiosa sobre el comportamiento de los clientes. Utilizando [cinco datasets](https://drive.google.com/drive/folders/11ludpzThvf-xB6LfZW_xzCBK1Z91M_KA?usp=sharing) proporcionados por la plataforma, se llevó a cabo un proceso de limpieza, análisis y visualización de datos para identificar patrones y tendencias clave.
  
## Herramientas Utilizadas
- __Lenguaje de Programación:__ Python.
- __Entorno de Desarrollo:__ Jupyter Notebook.
- __Bibliotecas:__ Pandas, Matplotlib, Seaborn, Scikit-learn.

## Proceso del Proyecto
- __Descripción de los datos:__ Los datos fueron extraídos de [cinco datasets](https://drive.google.com/drive/folders/11ludpzThvf-xB6LfZW_xzCBK1Z91M_KA?usp=sharing) proporcionados por Instacart _(los datasets están en Drive porque superan el peso máximo permitido de GitHub)_, en esta fase, también, se les da una revisión superficial y se corrigen problemas de importación si es que llegasen a surgir.
- __Preprocesamiento de los datos:__ Se realizaron varias operaciones de limpieza, incluyendo manejo de valores nulos, normalización y formateo de datos.
- __Análisis exploratorio de datos (EDA):__ Esta fase se centró en analizar la integridad de los datos y rescatar insights valiosos. Utilizando pandas se exploraron los datos para obtener una comprensión inicial, intermedia y avanzada, y con matplotlib, se generaron visualizaciones para ilustrar los hallazgos clave del análisis.
- __Análisis de clústeres:__ Usando el algoritmo KMeans, se crean clústeres que son analizados en detalle.
- __Conclusiones:__ Se recopilan los principales hallazgos y se esbozan perfiles de clientes según los datos recopilados. Además se presentan insights accionables para personalizar la experiencia de usuario de la plataforma.

## Descubrimientos importantes
Comenzaremos listando los resultados en orden inverso al cual fueron descubiertos, comenzando por en análisis de clústeres para terminar con los descubrimientos generales:

### Creación de clústeres
Lo primero que se hizo para comenzar con el proceso de agrupación, fue determinar cuales serían las variables sobre las que trabajará el algoritmo. Para este caso se escogieron las siguientes:
- Número de pedidos realizados.
- Total de productos comprados.
- Promedio de productos por pedido.
- Tasa de reordenación (métrica que indica la proporción de los productos que ya habían sido comprados anteriormente).

Lo que viene después es determinar el número de clústeres (grupos) que serán creados por el algoritmo, para ello, usamos el conocido "método del codo" (explicación en el notebook), con el que determinamos que __el número óptimo de clústeres es 4__.

<image src="https://github.com/BastianLQ/Analisis-Instacart/blob/main/Images/output_165_0.png" alt="Plot">

Ahora, se visualizarán las diferentes distribuciones horarias y diarias (dia de la semana) en que los clientes de los diferentes clústeres hacen sus pedidos (tener en cuenta que el día 0 corresponde al domingo).

<image src="https://github.com/BastianLQ/Analisis-Instacart/blob/main/Images/output_177_0.png" alt="Plot">
<image src="https://github.com/BastianLQ/Analisis-Instacart/blob/main/Images/output_178_0.png" alt="Plot">
<image src="https://github.com/BastianLQ/Analisis-Instacart/blob/main/Images/output_179_0.png" alt="Plot">
<image src="https://github.com/BastianLQ/Analisis-Instacart/blob/main/Images/output_180_0.png" alt="Plot">

Se contrastarán, también, mediante histogramas, los días que tardan los clientes de cada clúster en volver a hacer un pedido.

<image src="https://github.com/BastianLQ/Analisis-Instacart/blob/main/Images/output_192_0.png" alt="Plot">
<image src="https://github.com/BastianLQ/Analisis-Instacart/blob/main/Images/output_193_0.png" alt="Plot">
<image src="https://github.com/BastianLQ/Analisis-Instacart/blob/main/Images/output_194_0.png" alt="Plot">
<image src="https://github.com/BastianLQ/Analisis-Instacart/blob/main/Images/output_195_0.png" alt="Plot">

Por último, construiremos gráficos de dispersión para analizar la relación entre variables y la división de los clústeres.

<image src="https://github.com/BastianLQ/Analisis-Instacart/blob/main/Images/output_169_0.png" alt="Plot">
<image src="https://github.com/BastianLQ/Analisis-Instacart/blob/main/Images/output_171_0.png" alt="Plot">

En base al análisis de clústeres realizado, podemos resumir los hallazgos más importantes en la siguiente tabla:
  
| Cluster | Cantidad de productos por pedido | Reordenación | Días para volver a hacer un pedido | Peaks semanales de compra | Porcentaje del total |
|---------|----------------------------------|--------------|------------------------------------|---------------------------|----------------------|
| 0 | 12.5 | 71.2% | Menor o igual a 7 días | Lunes 10:00 | 38% |
| 1 | 6.6 | 70.8% | Mayoritariamente 7 días, grupo secundario de 30 días | Lunes 10:00 | 32% |
| 2 | 19.7 | 48.8%  | Mayoritariamente 30 días, grupo secundario de 7 días | Domingo 11:00 y 15:00 | 19% |
| 3 | 7.6 | 17.7% | 30 días | Domingos 15:00 | 11% |

Observando la tabla podemos concluir adicionalmente que:
- __Mientras más bajan los días para volver a hacer un pedido, más baja la tasa de reordenación.__
- __Los clústeres con la mayor tasa de reordenación (0 y 1) tienen su peak de compras el lunes a las 10:00 (hora de desayuno).__
- __La cantidad de productos por pedido no tiene relación con la tasa de reordenación, como se podría suponer.__

### Hallazgos generales
Hay descubrimientos que trascienden a los clústeres y cuentan para todos los clientes, tienen relación con los productos favoritos, los cuales se calcularon de las siguientes maneras:
- Productos más vendidos.
- Productos más re-ordenados.
- Productos más veces puestos primero en el carrito.

Estos son los resultados:

<image src="https://github.com/BastianLQ/Analisis-Instacart/blob/main/Images/output_131_0.png" alt="Plot">
<image src="https://github.com/BastianLQ/Analisis-Instacart/blob/main/Images/output_141_0.png" alt="Plot">
<image src="https://github.com/BastianLQ/Analisis-Instacart/blob/main/Images/output_153_0.png" alt="Plot">

Observando estos gráficos podemos concluir que:
- __Los clientes de Instacart prefieren productos naturales y catalogados como saludables, principalmente bananas, y también frutas, verduras y leche.__

### Perfil de cliente

## Ejecuta el proyecto [aquí](https://portfoliodabastianlopez.on.drv.tw/Portafolio/P3.html)
Para ver el diccionario de datos, el desarrollo completo en código, todos los gráficos y las conclusiones, haga click en el enlace de arriba.
