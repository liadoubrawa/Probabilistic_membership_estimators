# Probabilistic membership estimators

Here, you can find the first version of the adaptive membership estimator (AME) and fixed aperture estimator(FAE) algorithms (Doubrawa et al. 2023). We ran the estimator using the mock catalogue from simulated sky lightcone by Araya-Araya et al.(2021); Werner et al. (2022), made to emulate the S-PLUS1 survey first data release (Mendes de Oliveira et al. 2019). 

We present the algorithms and example runs.

# About AME
In the following, we present the main steps:

(i) Remove obvious non-members by cutting out all galaxies outside a radius of 2.5 Mpc in the plane-of-the-sky, and 𝑧𝑐𝑙𝑢𝑠𝑡𝑒𝑟 ± 0.05.

(ii) Calculate the galaxy density profile. A characteristic radius (𝑅𝑐), will be defined as a break or “knee” in this profile.

(iii) Draw a photo-z PDF-based random redshift value for each galaxy within 𝑅𝑐.

(iv) Calculate the sample velocity dispersion with the drawn redshifts, after a 3𝜎 clipping process.

(v) Run HDBSCAN using the remaining galaxies. Input parameters are galaxy positions and RFAE (𝑅 < 𝑅𝑐), as the minimum cluster size parameter. 

(vi) Repeat N times the steps 3–5. The final probability is 𝑃𝑚𝑒𝑚 = 𝑁𝑚𝑒𝑚/𝑁.


# About FAE
In the following, we present the main steps:

(i) Select galaxies within a radius of 500 kpc, and redshift interval, 𝑧𝑐𝑙𝑢𝑠𝑡𝑒𝑟 ± 0.05.

(ii) Integrate the selected galaxies photo-z PDF within the redshift interval (Prob).

(iii) Calculate the richness (Ri) as the sum of Prob

(iv) Remove field contribution within the cluster area (Rfield)

(v) Final richness, RFAE = Ri - Rfield


# Output

- For the galaxy catalg file, the code returns the membership probability for each galaxy within Rc and the cluster identification number.
- For the cluster catalog, we provide subproduct examples that can be derived from the galaxies' probabilities, such as richness, optical luminosity and total stellar.

# Reference

For more information about the code see Doubrawa et al. (2023). You can also send me an email if you prefer (lia.doubrawa@usp.br).
