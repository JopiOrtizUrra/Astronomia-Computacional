# Astronomia-Computacional
Trabajos de AST-305.
El objetivo del codigo es simular las estrellas que componen la via lactea, entregandonos informacion sobre la edad, estrellas en la main sequence y remanentes estelares, a partir de una masa dada para cada estrella con el metodo de monte carlo. Es relevante estudiar la composicion de la via lactea, para conocer la historia de evolucion y formacion de nuestra galaxia.

Initial mass function (IMF) es una funcion que describe la distribucion inicial de masas para una poblacion de estrellas. Se utilizo el modelo de IMF de Krouppa, el cual define que el numero de estrellas en un cierto rango de masa $(\xi(m))$ sigue la ley de potencia, dada por:

$$\xi(m) \propto m^{-\alpha}$$

con $m$ la masa y $\alpha$ un exponente que varia segun el rango de masa. Para mas detalles de la funcion leer la seccion 6.2 de Pavel Krouppa.

Star formation rate (SFR) señala cuantas estrellas se forman a lo largo de la vida de la galaxia. Se considera una formacion estelar constante, para lo cual se define que tiempo de vida de la via lactea ($t_{\text{MW}}$) es de 10 millones de años y que la edad actual de la estrella ($t_{\text{today}}$) viene dada por:

$$t_{\text{today}} = t_{\text{MW}} - t_{\text{birth}}$$

con $t_{\text{birth}}$ el año en que la estrella nacio.

Las estrellas que aun estan en su proceso de fusion de hidrogeno a helio se encuentran en la secuencia principal, mientras que aquellas que ya han agotado el hidrogeno en el nucleo son llamadas remanentes estelares. El tiempo que una estrella permanece en la MS ($t_{\text{MS}}$) esta determinado por su masa inicial como:

$$t_{\text{MS}} = \frac{10^{10}}{m^{-2.5}}$$

si la edad de la estrella es menor o igual al tiempo de la estrella en la MS, entonces la estrella siguen en la MS, por otro lado, si la edad es mayor al tiempo en la MS, entonces la estrella pasa a ser un remanente estelar. Cuando una estrella abandona la MS sigue distintos caminos segun su masa inicial, hasta llegar al tipo de remanete en que se convertira, ya sean white dawarf (WD), neutron star (NS) o black hole (BH). El tiempo que dura este camino es despreciable en comparacion al tiempo del remanente, es por ello que solo se consideran estrellas en la MS o remanentes en esta simulacion. Se utiliza la initial fraction to mass relation (IFMR) para ajustar el camino que traza la estrella desde la MS hasta ser remananente, donde cada tipo de remanente tiene su propia IFMR. Para mas detalles respecto a la IFMR de cada remanenete, revisar:

- para WD la seccion 8.4 de kalirai et al. (2008)
- para NS la seccion 5 de Rhaitel et al. (2018)
- para BH la seccion 4 de Rhaitel et al. (2018)
