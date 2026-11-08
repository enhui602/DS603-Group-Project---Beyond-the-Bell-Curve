# DS603-Group-Project: Beyond-the-Bell-Curve
- Do daily gold and oil returns exhibit heavier tails than a Normal distribution and do extreme movements in gold and oil occur jointly more often than would be expected under independence?

# Master of Data Science in Economics (MDSE)
## Course: DS603-G1-Probability for Data Science

**Group Members:**
* Nehantha Sathesh (Student ID: 01551453)
* Toh En Hui (Student ID: 01551403)

**Repository Link:** [https://github.com/enhui602/DS603-Group-Project---Beyond-the-Bell-Curve](https://github.com/enhui602/DS603-Group-Project---Beyond-the-Bell-Curve)

---

## Beyond the Bell Curve: Extreme Movements in Gold and Oil Returns

### 1. Research Question
- Do daily gold and oil returns exhibit heavier tails than a Normal distribution
- Do extreme movements in gold and oil occur jointly more often than would be expected under independence?

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
* Summary statistics and the ten largest absolute returns for gold and Brent crude
* Empirical versus Normal tail probability table and tail-count figure
* Return histograms with Normal overlays, Q-Q plots and log-scale tail-probability plots
* Chebyshev bounds versus observed exceedance table
* Gold-crude return scatter plot and covariance matrix
* Yearly correlation table and chart with 95% confidence intervals, and rolling 252-day correlation chart
* Joint downside extreme tables (contingency table, observed versus independence benchmark) and joint downside days by year
* Robustness tables: either-direction extremes, threshold and sample-exclusion sensitivity, and 2019 versus 2020 comparison with its chart
* Final project presentation in `outputs/presentation/` (PDF)
  
### 5. Project Limitations
* **Days Are Not Independent:** Volatility clustering means extreme days bunch together in time, making Fisher’s $p$-value overly optimistic.
* **A Few Outlier Days Drive Crude Statistics:** Crude oil’s extreme kurtosis (27.3) relies heavily on a small handful of 2020 shock days, led by the massive −44% drop on 21 April 2020.
* **Unconditional Correlation Masks Dynamic Regime Shifts:** The full-sample correlation ($r = 0.17$) hides significant sub-period shifts, moving from −0.14 in 2019 (pre-crisis) to +0.10 in 2020 (crisis).
* **Association, Not Causation:** Fisher’s exact test confirms that extreme tail days co-occur statistically, but it does not establish that one market causes movement in the other or identify financial transmission mechanisms.



## Running the project

1. Create and activate a Python environment.
2. Install the required packages:

```
pip install -r requirements.txt
```

3. Obtain the licensed LSEG Datastream data (accessed through WRDS) separately and save the input file as `data/Crude_Gold_data.xlsx`. It must contain the Datastream mnemonics `GOLDBLN` (Gold Bullion LBM, US$/troy oz) and `OILBREN` (Brent crude, US$/barrel) for 4 Jan 2000 to 31 Dec 2025.
4. Open `notebooks/DS603_Group_Project.ipynb` and run all cells in order. The notebook uses paths relative to the repository root and also works when `notebooks/` is the working directory. For example:

```
jupyter notebook notebooks/DS603_Group_Project.ipynb
```

The notebook creates `data/`, `outputs/figures/` and `outputs/tables/` automatically if they are missing. In Google Colab, clone the repository and place the data file in `data/` before running.
5. The notebook creates all figures and statistical tables described below. The final presentation is supplied separately and is not generated by the notebook.

## Data availability

The Datastream/WRDS input is licensed and is therefore not included in a fresh clone. Once the required input file is obtained, running the notebook regenerates every figure and table in `outputs/`. The random seed is fixed (`RANDOM_SEED = 42`), so results are reproducible.

