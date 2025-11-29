# Astronomia-Computacional
Trabajos de AST-305.
El objetivo del codigo es simular las estrellas que componen la via lactea, entregandonos informacion sobre la edad, estrellas en la main sequence y remanentes estelares, a partir de una masa dada para cada estrella con el metodo de monte carlo. Es relevante estudiar la composicion de la via lactea, para conocer la historia de evolucion y formacion de nuestra galaxia.

Initial mass function (IMF) es una funcion que describe la distribucion inicial de masas para una poblacion de estrellas. Se utilizo el modelo de IMF de Krouppa, el cual define que el numero de estrellas en un cierto rango de masa $(\xi(m))$ sigue la ley de potencia, dada por:

$$\xi(m)\propto m^{-\alpha}$$

con $m$ la masa y $\alpha$ un exponente que varia segun el rango de masa. Para mas detalles de la funcion leer la ecuacion 6 de la seccion 6.2 de Pavel Krouppa.

Star formation rate (SFR) señala cuantas estrellas se forman a lo largo de la vida de la galaxia. Se considera una formacion estelar constante, para lo cual se define que tiempo de vida de la via lactea ($t_{MW}$) es de 10 millones de años y que la edad actual de la estrella ($\t_{today}$) viene dada por:

$$t_{today} = t_{MW} - t_{birth}$$

con $t_{birth}$ el año en que la estrella nacio.

