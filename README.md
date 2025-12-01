# Monte Carlo Simulation of the Milky Way Stellar Population

## Description
This project simulates the stars that make up the Milky Way, providing information about stellar ages, main-sequence stars, and stellar remnants. Each star is assigned an initial mass drawn via Monte Carlo sampling. Understanding the stellar population helps us study the formation and evolutionary history of our galaxy.

To meet the objective of the simulation, it is important to understand some astronomical terms used throughout the process. The stars that make up the galaxy follow an **Initial Mass Function (IMF)**, that describes the mass distribution of stars at birth. This project uses the **Kroupa IMF**, which states that the number of stars in a given mass range ($\xi(m))$) follows a power law:

$$\xi(m) \propto m^{-\alpha}$$

where $(m)$ is the mass and $(\alpha)$ is a mass-dependent slope. For details related to $\alpha$ value at each mass range, see Section 6.2 of [Kroupa (2001) – The Initial Mass Function of Stars](https://ui.adsabs.harvard.edu/abs/2001MNRAS.322..231K/abstract).


The **Star Formation Rate (SFR)** specifies how many stars form over the lifetime of the galaxy. A constant SFR is assumed. The Milky Way’s lifetime is taken as \(t_{\text{MW}} = 10^{10}\) years, and the current age of a star is:

\[
t_{\text{today}} = t_{\text{MW}} - t_{\text{birth}}
\]

Stars that are still burning hydrogen in their cores lie on the **main sequence (MS)**. Once hydrogen is exhausted, they become **stellar remnants**. The MS lifetime is approximated as:

\[
t_{\text{MS}} = \frac{10^{10}}{m^{-2.5}}
\]

If the age of a star is less than or equal to its MS lifetime, it remains on the MS; otherwise, it becomes a remnant. Depending on their initial mass, stars evolve into **white dwarfs (WDs)**, **neutron stars (NSs)**, or **black holes (BHs)**.  
Post-MS evolution timescales are negligible compared to remnant lifetimes, so only MS stars and remnants are included in this model.

The **Initial-to-Final Mass Relation (IFMR)** maps MS masses to remnant masses. Each remnant type uses its own IFMR. See:

- **WD:** Section 8.4 of Kalirai et al. (2008)  
- **NS:** Section 5 (equations 11–14) of Raithel et al. (2018)  
- **BH:** Section 4 of Raithel et al. (2018)

---

## Mixed NS/BH Mass Range
In the intermediate mass range:

\[
15 \le M_{\text{init}} < 18.5 \, M_\odot
\]

the final stellar fate may be either an NS or a BH.  
To handle this ambiguity, a probability of forming a BH is defined:

\[
p_{\text{BH}} = 0.574
\]

consistent with Raithel et al. (2018).  
You may adjust both \(p_{\text{BH}}\) and the ejection parameter \(f_{\text{ej}}\) to explore different physical scenarios.

---

## Requirements
To run the code, you need:

- Python 3  
- NumPy  
- Matplotlib  

Optional tools:

- Jupyter Notebook  
- VSCode, Spyder, or any Python-friendly IDE

---

## Limitations and Possible Extensions
This is a simplified stellar population model, with the following limitations:

- Constant SFR (no bursts or realistic star formation history).
- Single Kroupa IMF and fixed metallicity (no \(Z\)-dependence).
- No detailed stellar evolution phases (e.g., red giants, supergiants).
- No binary systems, rotation, or additional physical effects.
- IFMRs are used only within their calibrated mass ranges; extrapolations may be unreliable.
- Recommended initial mass range:

\[
0.08\,M_\odot \lesssim M_{\text{init}} \lesssim 100\,M_\odot
\]

Despite its simplicity, this model provides a useful first approximation to the theoretical census of stars and remnants in a Milky Way–like galaxy and serves as a foundation for more advanced studies.


