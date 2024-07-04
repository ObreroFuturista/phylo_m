#   Reconstruccion de un árbol de Neighbour Joining en MEGA

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

![image](https://github.com/ObreroFuturista/phylo_m/assets/32031932/1c0b7774-adfe-45cd-9d3b-6c28d396f5c5)

> [!NOTE]
> Es una aproximación para explorar los datos. Recordar que no incluye información sobre modelos de evolución molecular.

## Construcción de un árbol NJ en Mega


Descargar el [Archivo fasta](archivos/COI_sn_sh.fasta) que vamos a utilizar.


Es un archivo con secuencias del marcador COI de saltamontes romaleidos del estudio [Sequence-based species delineation and molecular phylogenetics of the
transitional Nearctic–Neotropical grasshopper genus Taeniopoda
(Orthoptera, Romaleidae)](archivos/Paper-SequencebasedspeciesdelineationTaeniopoda-May-2017Orthoptera.pdf) 
Está sin alinear, por lo que hay que alinearlo previamente.

Abrir MEGA y arrastar el archivo fasta hacía la aplicación.


Les aparecerá una ventana sobre si es un archivo para analizar y de alineamiento. 
![image](https://github.com/ObreroFuturista/phylo_m/assets/32031932/eae418da-3153-4ffc-9231-259efe57b811)
Seleccionan de alineamiento.  


El archivo aún tiene algunas secuencias que no están alineadas.
![image](https://github.com/ObreroFuturista/phylo_m/assets/32031932/584ae4b0-083a-4c68-af21-5042203c252e)
En el menu superior seleccionan la pestaña **Aligment** y le indican al programa que haga el alineamiento con MUSCLE o ClustalW


Ya tienen el alineamiento. 
![image](https://github.com/ObreroFuturista/phylo_m/assets/32031932/d5bc3148-4839-4c0f-b8b6-3c4e49e9b848)
Lo guardan en su computadora. 


El archivo alineado permanece en abierto en Mega, pero como archivo de datos. Cambiamos a la ventana del programa y arrastramos el archivo que recien guardamos. El boton de Phylogeny se selecciona Neighbour Joining
![image](https://github.com/ObreroFuturista/phylo_m/assets/32031932/b0ad1670-ca36-4afb-bae3-cc6b407f2578)


Pueden usar los valores por default. Si tarda mucho en la computadora pueden bajar en número de réplicas de bootstrab o aumentar los threads según los tengan disponibles.  
![image](https://github.com/ObreroFuturista/phylo_m/assets/32031932/2bc3684c-0021-42bf-87ea-bd42126f48c8)


En analisis correra 
![image](https://github.com/ObreroFuturista/phylo_m/assets/32031932/5f2a9552-c4e6-42a3-a80a-2302e4961b52)

Salvan el árbol incluyendo las longitudes de ramas y los valores de bootstrap. 
![image](https://github.com/ObreroFuturista/phylo_m/assets/32031932/483ffeaa-f326-43d2-aa40-8cbdbf4c6955)


Listo!
![image](https://github.com/ObreroFuturista/phylo_m/assets/32031932/c3e37b88-3192-463f-a94c-469f82f102bc)

Hay dos árboles. El de distancias y que nos interesa está en la pestaña **Original tree**. En la pestaña **Bootstrap consensus Tree** esta el árbol de 
las corridas para calcular los valores de bootstrap. Los valores en los nodos son los mismos que en el árbol de la primera pestaña. 

Pueden usar el programa [Figtree](http://tree.bio.ed.ac.uk/software/figtree/) para más opciones de visualización y edición del árbol. 
![image](https://github.com/ObreroFuturista/phylo_m/assets/32031932/1069566b-b034-426c-aae1-35df144c6f34)

