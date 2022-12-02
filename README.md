# Maven pizzas 2
## Archivos
- pizzas.py: script de python que hace una predicción de los ingredientes para 2016.
- order_details.csv: fichero que contiene información sobre la cantidad de pizzas ordenadas en un pedido y el identificador del pedido.
- orders.csv: fichero que contiene información sobre las fechas del pedido, al igual que el identificador del pedido.
- pizza_types.csv: fichero que contiene información sobre cada tipo de pizza, como una descripción y los ingredientes que la conforman.
- pizzas.csv: fichero que contiene información sobre el precio de cada pizza en relación a su tamaño.
- data_dictionary.csv: fichero que contiene información sobre los csv previamente descritos.
- data_info.xml: resumen de los datos proporcionados (número de NaN, Null, tipo de cada columna...).
- 2017_prediction.csv: fichero que contiene la predicción de ingredientes de cada semana para un año.
- requirements.txt: fichero de texto que contiene las librerías necesarias y sus versiones para la ejecución del script.

## Descripción del script
En este script se proporcinaban unos csv que no son para nada cómodos de usar, pues estaban plagados de casillas vacías, casillas con formato distinto al de la columna y fechas dadas de todas las maneras posibles. El procedimiento para tratar con ellos se divide en varias partes:
- Primero, ordenamos el csv en función del identificador del orden, ya que así podíamos trabajar con el csv ordenado cronológicamente.
- El número de NaN era tan grande que no podíamos trabajar descartando todas las filas que contuvieran al menos un NaN. Por ello, decidí rellenarlo con el dato de la fila anterior, es decir, usando method='ffill'.
- Por otro lado, existían números negativos en la cantidad, lo cual es incorrecto. Del mismo modo, teníamos cantidades dadas por el literal del número correspondiente, es decir, "One" en vez de 1. Por lo tanto, sustituimos el literal por su correspondiente valor numérico y las cantidades simplemente las pasábamos a positivo.
- La separación de las palabras de las pizzas era también diferente entre las distintas filas. Por lo que hubo que pasarlas todas al mismo formato y que estuvieran separadas por "_", así coincidía con el formato del resto de ficheros.
- Por último, para las fechas he utilizado una librería llamada "dateutils" que es capaz de transformar prácticamente cualquier formato de fecha al deseado. Simlemente tuve que hacer una distinción entre el formato que lo daba en la cantidad de segundos y el que tenía día, mes y año, o similar. Para ello, la función "timestamp" de la librería "time", transformaría dicho formato al deseado. 

En la elaboración del programa se ha seguido una estructura ETL. Para poder calcular la predicción de los ingredientes necesarios, hemos seguido el mismo procedimiento que para "Maven pizzas".

Posteriormente, dichos datos son exportados a un csv, llamado "2017_prediction.csv".
