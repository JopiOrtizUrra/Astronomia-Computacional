# Astronomia-Computacional
Trabajos de AST-305.
El objetivo del codigo es simular las estrellas que componen la via lactea, entregandonos informacion sobre la edad, estrellas en la main sequence y remanentes estelares, a partir de una masa dada para cada estrella con el metodo de monte carlo. Es relevante estudiar la composicion de la via lactea, para conocer la historia de evolucion y formacion de nuestra galaxia.

Initial mass function (IMF) es una funcion que describe la distribucion inicial de masas para una poblacion de estrellas. Se utilizo el modelo de IMF de Krouppa, el cual define que el numero de estrellas en un cierto rango de masa $(\xi(m))$ sigue la ley de potencia, dada por:

$$\xi(m) \propto m^{-\alpha}$$

con $m$ la masa y $\alpha$ un exponente que varia segun el rango de masa. Para mas detalles de la funcion leer la ecuacion 6 de la seccion 6.2 de Pavel Krouppa.

Star formation rate (SFR) señala cuantas estrellas se forman a lo largo de la vida de la galaxia. Se considera una formacion estelar constante, para lo cual se define que tiempo de vida de la via lactea ($t_{\text{MW}}$) es de 10 millones de años y que la edad actual de la estrella ($t_{\text{today}}$) viene dada por:

$$t_{\text{today}} = t_{\text{MW}} - t_{\text{birth}}$$

con $t_{birth}$ el año en que la estrella nacio.

Las estrellas que aun estan en su proceso de fusion de hidrogeno a helio se encuentran en la secuencia principal, mientras que aquellas que ya han agotado el hidrogeno en el nucleo son llamadas remanentes estelares. El tiempo que una estrella permanece en la MS ($t_{\text{MS}}$) esta determinado por su masa inicial como:

$$t_{MS} = \frac{10^{10}}{m^{-2.5}}$$

si la edad de la estrella es menor o igual al tiempo de la estrella en la MS, entonces la estrella siguen en la MS, por otro lado, si la edad es mayor al tiempo en la MS, entonces la estrella pasa a ser un remanente estelar. Los tipos de remanentes estelares, ya sean white dawarf (WD), neutron star (NS) o black hole (BH), estan definidos por initial fraction to mass relation (IFMR). 

