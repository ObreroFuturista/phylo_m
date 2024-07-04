#   Construccion de un árbol de Neighbour Joining en MEGA

El algoritmo de Neighbor-Joining (NJ), desarrollado por Saitou y Nei en 1987, se utiliza para generar 
un "árbol filogenético" único, que no necesariamente representa la historia evolutiva del grupo.

En el primer paso, se combinan las dos secuencias con la menor distancia genética (neighbors). 
Este par inicial se trata como una sola entidad y se busca la siguiente secuencia con la menor distancia genética 
respecto a este par. Este proceso se repite hasta que todas las secuencias se integran en el árbol (Saitou y Nei 1987). 

En el caso de secuencias de ADN, la distancia genética entre dos secuencias se calcula basándose en el número 
total de sustituciones de bases nitrogenadas, es decir, en la cantidad de bases nitrogenadas que difieren entre
las dos secuencias. Para seleccionar las secuencias con la menor distancia genética, que en la práctica implica
elegir las secuencias más similares, es necesario construir una matriz de distancias estándar entre todas las
posibles combinaciones de secuencias.

> [!NOTE]
> Es una aproximación para explorar los datos. Recordar que no incluye información sobre modelos de evolución molecular.  







