# Monte Carlo Simulation of the Milky Way Stellar Population

## Description
This project simulates the stars that make up the Milky Way, providing information about stellar ages, main-sequence stars, and stellar remnants. Each star is assigned an initial mass drawn via Monte Carlo sampling. Understanding the stellar population helps us study the formation and evolutionary history of our galaxy.

To meet the objective of the simulation, it is important to understand some astronomical terms used throughout the process. The stars that make up the galaxy follow an **Initial Mass Function (IMF)**, that describes the mass distribution of stars at birth. This project uses the **Kroupa IMF**, which states that the number of stars in a given mass range ($\xi(m)$= dN\dm) follows a power law:

$$\xi(m) \propto m^{-\alpha}$$

where $(m)$ is the mass and $(\alpha)$ is a mass-dependent slope. For details related to $\alpha$ value at each mass range, see Section 6.2 of [Kroupa (2001)](https://ui.adsabs.harvard.edu/abs/2001MNRAS.322..231K/abstract). We used the functions for masses between 0.08 and 100 $M_\odot$. At the boundaries of these mass intervals, we noticed that the IMF appeared to be discontinuous. As a solution, we introduced proportionality constants ($k_i$) that, when applied to each segment of the piecewise function, produce a smooth and continuous Kroupa IMF. To obatain $k_i$ values, we used the next relation:

$$k_im^{-\alpha_i}=k_{i+1}m^{-\alpha_{i+1}}$$

Each star muss have a time of birt ($t_{\text{birth}}$). At this simulation we aasumed a constant **Star Formation Rate (SFR)**, that specifies how many stars form over the lifetime of the galaxy. The Milky Way’s lifetime is taken as $10^{10}$ years, and with this two parameters is possible to get the current age of a star.

Some stars that are still burning hydrogen in their cores lie on the **main sequence (MS)**. Once hydrogen is exhausted, they become **stellar remnants**. The MS lifetime is approximated as:

$$t_{\text{MS}} = \frac{10^{10}}{m^{-2.5}}$$

If the age of a star is less than or equal to its MS lifetime, it remains on the MS; otherwise, it becomes a remnant. Depending on their initial mass, stars evolve into **white dwarfs (WDs)**, **neutron stars (NSs)**, or **black holes (BHs)**. Post-MS evolution timescales are negligible compared to remnant lifetimes, so only MS stars and remnants are included in this model.

To see which can of remnant we have, we used the **Initial-to-Final Mass Relation (IFMR)**, that maps MS masses (initial mass) to remnant masses (final mass). Depending on the mass range (at the articles are called branches), functions for fitting the life of the stars changes. Each remnant type uses its own IFMR. See:

- **WD:** Section 8.4 of [Kalirai et al. (2008)](https://iopscience.iop.org/article/10.1086/527028)
- **NS:** Section 5 (equations 11–14) of [Raithel et al. (2018)](https://ui.adsabs.harvard.edu/abs/2018ApJ...856...35R/abstract)
- **BH:** Section 4 of [Raithel et al. (2018)](https://ui.adsabs.harvard.edu/abs/2018ApJ...856...35R/abstract)

We noticed that NS and BH coincide at the mass range $15 M_\odot \leq M_{\text{init}} < 18.5 M_\odot$. So at this range the final stellar fate may be either an NS or a BH. To handle this ambiguity, a probability of forming a BH is defined by Raithel et al. (2018), as $p_{\text{BH}} = 0.574$. Is important to mention that BH IFMR have a ejection parameter $(f_{\text{ej}})$ that represent the fraction of envelope to be ejected by the star. We utilized  $f_{\text{ej}}=0.9$. Both parameters,$p_{\text{BH}}$ and $f_{\text{ej}}$, are available for adjustments.

Till now, all the astronomical process requiered the initial mass of the stars. We used Monte Carlo method to obtain the initial mass that follow Krouppa IMF from a uniform random probability (u), that represent the value of dN/dm. If the probability of a star is under the Krouppa IMF, the stars will be part of the Milky Way. In case is equal or bigger, we ignore thoses stars.

## How to used the code
Before you start using the code, we recommend to read the flowchart in this repository. This will help you to understand the structure of the code, the sequence of the functiones and the defined paramters and thoses you can change to explore new reults.
### Requirements
To run the code, you need:

- Python 3  
- NumPy  
- Matplotlib  

Optional tools:

- Jupyter Notebook  
- VSCode, Spyder, or any Python-friendly IDE

### Limitations and Possible Extensions
This is a simplified stellar population model, with the following limitations:

- Constant SFR (no bursts or realistic star formation history).
- Single Kroupa IMF and no implications with matallicity.
- No detailed stellar evolution phases (e.g., red giants, supergiants).
- No binary systems, rotation, or additional physical effects.
- IFMRs are used only within their calibrated mass ranges; extrapolations may be unreliable.
- Recommended initial mass range: $0.08 M_\odot \leqM_{\text{init}}\leq 100 M_\odot$.

## Functions
The functions we used are described detallied into the code. If you one to know more information about a function used the command function_name.help().                                                                               

Despite its simplicity, this model provides a useful first approximation to the theoretical census of stars and remnants in a Milky Way–like galaxy and serves as a foundation for more advanced studies.


