# Reconstrucción de un árbol de inferencia bayesiana 

La inferencia bayesiana de árboles filogenéticos es un método estadístico que utiliza el teorema de Bayes para reconstruir 
las relaciones evolutivas entre especies o genes, integrando la incertidumbre de manera explícita. Este enfoque combina 
una probabilidad previa, que refleja el conocimiento inicial sobre los árboles y parámetros del modelo evolutivo, con
la verosimilitud, que es la probabilidad de los datos observados dados esos árboles y parámetros. Utilizando algoritmos
de Monte Carlo por cadena de Markov (MCMC), se muestrean posibles árboles para aproximar la distribución posterior. 
Esto resulta en una representación probabilística de las posibles relaciones evolutivas, proporcionando una evaluación 
más robusta de la incertidumbre en la filogenia inferida.

Actualiza la probabilidad de una hipótesis a medida que se dispone de más evidencia o información.

![image](https://github.com/ObreroFuturista/phylo_m/assets/32031932/ce8d3053-6d33-43a2-b30e-761427a17b61)

## Árbol de inferencia bayesiana con Mr Bayes

Primero debemos calcular el modelo de evolución molecular que mejor se ajuste a nuestros datos
Lo podemos hacer en Mega

Abrimos nuestro alineamiento nexus en Mega, y en la opción de Models seleccionamos Find Best DNA/Protein Models. 

![image](https://github.com/ObreroFuturista/phylo_m/assets/32031932/b81b277e-11fa-4c9a-9731-dfb8a61f35fd)

Obtenemos una lista con lo modelos más idóneos de mayor a menor según diferentes métricas. En general, entre menor  (Bayesian Information Criterion) se ajusta mejor. 

![image](https://github.com/ObreroFuturista/phylo_m/assets/32031932/7242d69e-7dc9-4b62-9bae-111627b2ca06)


Mr Bayes no implementa todos los modelos evaluados, solo [estos](archivos/mr_bayes.modelos.txt)

Vamos a utilizar el modelo de los implmentados por MrBayes con el valor mas alto de BIC (Bayesian information criterion), en este caso HKY+G

Al final del archivo Nexus agregamos este bloque. En este bloque indicamos la inicialización de MrBayes, establecemos una partición y con *lset* establecemos el modelo. Indicamos que 
el análisis correra por 10,000,000 de generaciones, con dos corridas y cuatro cadenas de Markov, y hacer un resumen de los parametros y árboles obtenidos. 

	begin mrbayes;
	outgroup 259CvaGUA;

	charset Subset1 = 1-626;
	partition PartitionFinder = 1:Subset1;
	set partition=PartitionFinder;

	lset applyto=(1) nst=2 rates=gamma;         
	mcmc ngen=1000000 temp=0.2 printfreq=1000 samplefreq=1000 nruns=2 nchains=4 savebrlens=yes burninfrac=0.25;

	sump;
	sumt contype=halfcompat;
	quit;
	end;

[Aquí pueden ver el alineamiento en nexus con los comandos.](archivos/COI_Ali_comandos.nexus)

Si descargan los executables de Windows deben tener un carpeta con estos archivos

Por cuestiones de conversión, en la linea donde que dice  *datatype=nucleotide;* cambiar a *datatype=dna;*

### Descargar MrBayes 

Descargar MrBayes desde este [sitio](https://nbisweden.github.io/MrBayes/download.html)

Tendrán una carpeta como esta. En la carpeta *bin* estan los .exe necesarios, pueden usar cualquiera
![image](https://github.com/user-attachments/assets/1ee0e417-578c-49ee-a134-00a7d119e966)

De manera similar a RAxML, abren MrBayes a con la línea de comandos, a través del símbolo del sistema. (Cambiarán las rutas en sus PCs)
![image](https://github.com/user-attachments/assets/61da8eb6-c8ae-417b-b6bb-0cee51cef02e)


Al ejecutar MrBayes aparece este texto
![image](https://github.com/user-attachments/assets/9844d0cb-11a7-4142-ab27-6233c2067655)


