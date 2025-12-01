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
- para NS la seccion 5, ecuaciones 11, 12, 13, 14 de Rhaitel et al. (2018)
- para BH la seccion 4 de Rhaitel et al. (2018)
## Zona mixta NS/BH
En el rango intermedio $$15 \le M_{\mathrm{init}} < 18.5~M_\odot$$ el destino puede ser NS o BH.  
Para tratar esta ambigüedad se define una probabilidad de formar un BH
    
        $$p_{\text{BH}} = 0.574$$
    consistente con las fracciones reportadas por Raithel et al. (2018).
    Puede modificar tanto $p_{\mathrm{BH}}$ como el parámetro de eyección $f_{\mathrm{ej}}$ para explorar los diferentes escenarios físicos.
##  Requerimientos
Para ejecutar el código se requieren:

* Python 3 (versión 3.x)
* NumPy para el manejo de arreglos y generación de variables aleatorias.
* Matplotlib

Opcionalmente se puede trabajar en Jupyter Notebook, o en algún editor como VSCode, Spyder o similar.

## Limitaciones y posibles extensiones
Este modelo es intencionalmente simplificado, por lo que algunas de sus principales limitaciones son:
* Se asume SFR constante, sin incluir episodios de formación estelar intensa ni una historia de formación más realista.
* Se supone una única IMF de Kroupa y una única metalicidad, sin explorar la dependencia con $Z$.
* No se modela la evolución detallada, no se incluyen fases de gigante roja, supergigante, etc. sólo se distingue entre estrellas en MS y remanentes.
* No se incluyen sistemas binarios, rotación ni otros efectos que pueden modificar el destino estelar.
* Las IFMRs se aplican en los rangos de masa donde fueron calibradas, por ello para masas fuera de estos rangos la extrapolación no es fiable.
* El rango recomendado de masas iniciales es
    
        $$0.08~M_\odot \lesssim M_{\mathrm{init}} \lesssim 100~M_\odot$$
    coherente con la IMF implementada en el código.

A pesar de estas simplificaciones, el modelo entrega una primera aproximación útil al censo teórico de estrellas y remanentes en una galaxia tipo Vía Láctea y sirve como base para extensiones a estudios más complejos.
