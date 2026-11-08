# DS603-Group-Project: Beyond-the-Bell-Curve
- Do daily gold and oil returns exhibit heavier tails than a Normal distribution
- Do extreme movements in gold and oil occur jointly more often than would be expected under independence?

# Master of Data Science in Economics (MDSE)
## Course: DS603-G1-Probability for Data Science

**Group Members:**
* Nehantha Sathesh (Student ID: 01551453)
* Toh En Hui (Student ID: 01551403)

**Repository Link:** [https://github.com/enhui602/DS603-Group-Project---Beyond-the-Bell-Curve](https://github.com/enhui602/DS603-Group-Project---Beyond-the-Bell-Curve)

---

## Beyond the Bell Curve: Extreme Movements in Gold and Oil Returns

### 1. Research Question
Do daily gold and oil returns exhibit heavier tails than a Normal distribution, and do extreme movements in gold and oil occur jointly more often than would be expected under independence?

### 2. Dataset & Cleaning Notes
* **Data Source:** Daily price data extracted from the LSEG Datastream database (accessed via WRDS) covering the period from **4 January 2000 to 31 December 2025**.
  * **Gold Benchmark:** *Gold Bullion LBM $/t oz DELAY* (Mnemonic: `GOLDBLN`), representing the daily London gold benchmark in USD/troy oz.
  * **Oil Benchmark:** *Crude Oil BFO M1 Europe FOB $/BBI* (Mnemonic: `OILBREN`), representing the daily Brent crude benchmark in USD/barrel.
* **Data Ingestion & Cleaning:**
  * Raw dataset contained **32,932 price rows**, which was deduplicated to **13,257 rows** to align calendar dates across asset classes.
  * Computed daily log-return series across **6,492 observations** using the transformation: 
    $$r_t = 100 \times \ln\left(\frac{P_t}{P_{t-1}}\right)$$
  * Handled gap-spanning dates and non-trading alignment between commodities.

### 3. Methodology & Course Methods Applied
* **Parametric vs. Empirical Tail Analysis:** Evaluated empirical daily log-return distributions against fitted Gaussian benchmarks using standardized $z$-scores ($|z| > 3\sigma$).
* **Non-Parametric Probability Bounds:** Benchmarked observed tail exceedances against theoretical upper bounds derived from **Chebyshev’s Inequality** and **Cantelli’s Inequality** to assess maximum tail risk without assuming normality.
* **Co-movement & Joint Downside Modeling:** Measured covariance and dynamic correlation. Constructed $2 \times 2$ joint downside contingency tables using 5% tail thresholds and tested for statistical dependence using **Fisher's Exact Test** relative to theoretical independence benchmarks.
* **Regime Shift & Sub-Period Analysis (Robustness):** Compared extreme return behavior and correlation shifts between the pre-crisis period (**1 Jan 2019 – 31 Dec 2019**) and the COVID-19 disruption period (**1 Jan 2020 – 31 Dec 2020**).

### 4. Key Deliverables (Figures & Tables)
* **Summary Statistics Table:** Empirical moments including mean, standard deviation, negative skewness, and extreme excess kurtosis.
* **Normal Q-Q Plots & Log-Scale Tail Decay Curves:** Visualizing fat-tailed behavior and the systematic underestimation of extreme price shocks by Normal distributions.
* **Empirical vs. Chebyshev/Normal Exceedance Tables:** Comparing observed tail frequencies against theoretical model bounds.
* **Joint Downside & Scatter Distributions:** Scatter plots of daily return co-movements overlaid with joint 5% extreme threshold quadrants.

### 5. Project Limitations
* **Days Are Not Independent:** Volatility clustering means extreme days bunch together in time, making Fisher’s $p$-value overly optimistic.
* **A Few Outlier Days Drive Crude Statistics:** Crude oil’s extreme kurtosis (27.3) relies heavily on a small handful of 2020 shock days, led by the massive −44% drop on 21 April 2020.
* **Unconditional Correlation Masks Dynamic Regime Shifts:** The full-sample correlation ($r = 0.17$) hides significant sub-period shifts, moving from −0.14 in 2019 (pre-crisis) to +0.10 in 2020 (crisis).
* **Association, Not Causation:** Fisher’s exact test confirms that extreme tail days co-occur statistically, but it does not establish that one market causes movement in the other or identify financial transmission mechanisms.
