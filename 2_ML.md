# Reconstrucción de un árbol con el método de Máxima Verosimilitud (Maximun Lakelihood)

El método ML estima la probabilidad de qué tan bien es explicada la matriz de caracteres por los árboles filogenéticos
(Topología y modelo de evolución molecular) (Felsenstein,  2004). Para un alineamiento D de secuencias de ADN de *n* especies,
el objetivo es identificar la filogenia, árbol o topología T que describa de manera más adecuada dicho alineamiento. 


Cálculo de la verosimilitud de cada árbol posible. La verosimilitud del árbol, que es una medida de cuán probable es que veamos
los datos que hemos observado, si este árbol fuera el correcto y la evolución siguiera el modelo que hemos seleccionado. 

![image](https://github.com/ObreroFuturista/phylo_m/assets/32031932/203619cb-cdd8-41cc-8378-f568e8709c72)

Se puede realizar en Mega. Aunque es preferible usar programas especializados como RAXML (Randomized Axelerated Maximum Likelihood)

## Inferencia de un árbol de Máxima Verosimilitud con valores de Bootstrap usando RAxML

RAxML (Randomized Axelerated Maximum Likelihood) (Stamatakis et al 2008) programa diseñado para realizar análisis filogenéticos 
mediante el método de máxima verosimilitud. Es capaz de manejar grandes conjuntos de datos y diversos modelos evolutivos de 
nucleótidos y aminoácidos. RAxML permite la paralelización para optimizar el rendimiento computacional.

![image](https://github.com/ObreroFuturista/phylo_m/assets/32031932/ef8bb55f-b204-44b4-8d59-4c7b23ae60da)

Descargar [RAxML](https://github.com/stamatak/standard-RAxML)
RAxML utiliza alineamientos en formato phyllip. Así que usamos la misma matriz que alineamos en Mega, pero pero en formato phyllip. 

Podemos convertir el archivo nexus a phyllip en la sigueinte [liga](https://sequenceconversion.bugaco.com/converter/biology/sequences/) 
![image](https://github.com/ObreroFuturista/phylo_m/assets/32031932/d08ae5e3-25aa-4fe9-b8e7-2172947ba120)

Con el archivo phyllip y los ejecutables de RAxML podemos correr una análisis completo (Búsqueda del mejor árbol y calcular los valiores de bootstrap)
con el siguiente comando. 

>raxmlHPC -f a -m GTRGAMMA -p 12345 -x 12345 -# 100 -s dna.phy -n T20


-f a: Búsqueda de árbol de arranque (bootstrap search) seguida de una búsqueda de la mejor máxima verosimilitud (ML) y un análisis del árbol de consenso. 

-m GTRGAMMA: Modelo de sustitución de nucleótidos a utilizar. Modelo GTR (General Time Reversible) con la corrección GAMMA para la heterogeneidad de tasas entre sitios.

-p 12345: Semilla para el generador de números aleatorios utilizado en la búsqueda de la máxima verosimilitud. Reproducibilidad de los resultados.

-x 12345: Semilla para el generador de números aleatorios utilizado en el análisis bootstrap. 

-# 100: Réplicas bootstrap.

-s dna.phy: Alineamiento en formato PHYLIP.

-n test: Proporciona un nombre (test) para el trabajo.
