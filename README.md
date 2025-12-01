# Simulación Monte Carlo de la población estelar de la Vía Láctea
## Descripción
Este código es simula las estrellas que componen la vía lactea, entregandonos información sobre la edad, estrellas en la main sequence y remanentes estelares, a partir de una masa dada para cada estrella utilizando el método de monte carlo. Es relevante estudiar la composicion de la vía lactea, para conocer la historia de evolución y formación de nuestra galaxia.

Initial mass function (IMF) es una función que describe la distribución inicial de masas para una población de estrellas. Se utilizo el modelo de IMF de Krouppa, el cual define que el número de estrellas en un cierto rango de masa $(\xi(m))$ sigue la ley de potencia, dada por:

$$\xi(m) \propto m^{-\alpha}$$

con $m$ la masa y $\alpha$ un exponente que varia según el rango de masa. Para mas detalles de la función leer la seccion 6.2 de Pavel Krouppa.

Star formation rate (SFR) señala cuantas estrellas se forman a lo largo de la vida de la galaxia. Se considera una formación estelar constante, para lo cual se define que tiempo de vida de la Vía Láctea ( $t_{\text{MW}}$) es de 10 millones de años y que la edad actual de la estrella ($t_{\text{today}}$) viene dada por:

$$t_{\text{today}} = t_{\text{MW}} - t_{\text{birth}}$$

con $t_{\text{birth}}$ el año en que la estrella nació.

Las estrellas que aún estan en su proceso de fusión de hidrógeno a helio se encuentran en la secuencia principal, mientras que aquellas que ya han agotado el hidrógeno en el núcleo son llamadas remanentes estelares. El tiempo que una estrella permanece en la MS ($t_{\text{MS}}$) esta determinado por su masa inicial como:

$$t_{\text{MS}} = \frac{10^{10}}{m^{-2.5}}$$

si la edad de la estrella es menor o igual al tiempo de la estrella en la MS, entonces la estrella siguen en la MS, por otro lado, si la edad es mayor al tiempo en la MS, entonces la estrella pasa a ser un remanente estelar. Cuando una estrella abandona la MS sigue distintos caminos según su masa inicial, hasta llegar al tipo de remanete en que se convertirá, ya sean white dawarf (WD), neutron star (NS) o black hole (BH). El tiempo que dúra este camino es despreciable en comparación al tiempo del remanente, es por ello que solo se consideran estrellas en la MS o remanentes en esta simulación. Se utiliza la initial fraction to mass relation (IFMR) para ajustar el camino que traza la estrella desde la MS hasta ser remananente, donde cada tipo de remanente tiene su propia IFMR. Para mas detalles respecto a la IFMR de cada remanenete, revisar:

- para WD la seccion 8.4 de kalirai et al. (2008)
- para NS la seccion 5 de Rhaitel et al. (2018)
- para BH la seccion 4 de Rhaitel et al. (2018)

##  Requerimientos
Para ejecutar el código se requieren:

* \textbf{Python 3} (versión 3.x).
* \item \textbf{NumPy} para el manejo de arreglos y generación de variables aleatorias.
* \item \textbf{Matplotlib} para la generación de figuras y gráficos.
\end{itemize}
