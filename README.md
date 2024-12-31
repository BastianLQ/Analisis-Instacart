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
Después de toda la investigación realizada podemos esbozar el siguiente perfil:
- __La clientela de Instacart consume productos naturales y catalogados como saludables, principalmente bananas, frutas en general, verduras y leche.__

<image src="https://github.com/BastianLQ/Analisis-Instacart/blob/main/Images/profile.png" alt="perfil">

Y el perfil puede ser dividido en 4 subgrupos:
- __Clientes frecuentes:__ Realizan más de un pedido a la semana con una cantidad considerable de artículos, y piden las mismas cosas una y otra vez, recurren a Instacart los lunes a la hora de desayuno.
- __Clientes casuales, pero fieles:__ Realizan en promedio una cantidad baja de pedidos, con una cantidad acotada de artículos, sin embargo piden las mismas cosas una y otra vez. Al igual que el grupo anterior, recuerren a instacart principalmente los lunes a la hora del desayuno.
- __Clientes casuales:__ Estos clientes prefieren realizar un pedido grande por mes, compran tanto productos "nuevos" como ya comprados anteriormente. Este grupo prefiere hacer compras los domingos a las 11:00 y a las 15:00.
- __Clientes ocasionales:__ Este grupo es el menos fiel, realiza pedidos ocasionalmente con pocos artículos. En un 92% de las veces compran productos por primera vez y los que deciden volver a comprar, lo hacen luego de 30 días.

### Recomendaciones
En base a la información recopilada y en pos de aumentar el beneficio neto y la fidelización de la clientela es que se realizan las siguientes recomendaciones:
- __Fomentar productos naturales:__ Ofrecer descuentos por volumen, envíos gratis y ofrecer cajas prearmadas personalizadas son ideas sólidas que potenciarán las ventas de estos productos. Compartir recetas inspiradas en los productos más vendidos podría resultar muy interesante también, el hecho de que varias marcas de comida reconocidas realicen esta práctica es un buen indicador de su efectividad.
- __Personalización por clúster de clientes:__
  - __Cluster 0:__ Incentivar la fidelidad y aumentar la cantidad de productos por pedido.
    - Ofrecer descuentos por agregar más ítems (compra 3, lleva 4).
    - Lanzar promociones exclusivas para los lunes por la mañana.
    - Implementar un programa de suscripción semanal para sus productos más frecuentes.
  - __Cluster 1:__ Incrementar el tamaño del pedido.
    - Ofrece combos para incrementar el número de productos en cada compra.
    - Promueve ofertas para compras superiores a un monto mínimo.
    - Resalta beneficios por compras recurrentes los lunes a las 10:00.
  - __Cluster 2:__ Aumentar la frecuencia de compra.
    - Envía recordatorios personalizados cerca de los 7 o 30 días tras su última compra.
    - Ofrece incentivos como descuentos por compras adicionales dentro del mismo mes.
    - Promociona paquetes premium de productos relacionados a sus preferencias.
  - __Cluster 3:__ Reactivar y fidelizar.
    - Enviar cupones de descuento exclusivos antes de los domingos.
    - Realizar campañas específicas para este segmento, destacando productos con precios competitivos.
    - Crear promociones de bienvenida para animarlos a realizar compras más frecuentes. 

## Ejecuta el proyecto [aquí](https://portfoliodabastianlopez.on.drv.tw/Portafolio/P3.html)
Para ver el diccionario de datos, el desarrollo completo en código, todos los gráficos y las conclusiones, haga click en el enlace de arriba.
