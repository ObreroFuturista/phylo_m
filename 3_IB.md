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


La cuestión es que Mr Bayes no implementa todos los modelos evaluados, solo [estos](archivos/mr_bayes.modelos.txt)


Al final del archivo Nexus agregamos este bloque 


begin mrbayes;
outgroup 259CvaGUA;

	charset Subset1 = 1-626;

	partition PartitionFinder = 1:Subset1;
	set partition=PartitionFinder;

	lset applyto=(1) nst=6 rates=invgamma;

mcmc ngen=1000000 temp=0.2 printfreq=1000 samplefreq=1000 nruns=2 nchains=4 savebrlens=yes burninfrac=0.25;
sump;
sumt contype=halfcompat;
quit;
end;
