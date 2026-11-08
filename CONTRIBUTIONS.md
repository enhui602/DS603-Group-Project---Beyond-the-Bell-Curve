# Team Contributions Disclosure

**Course:** DS603-G1-Probability for Data Science
**Project:** Beyond the Bell Curve: Extreme Movements in Gold and Oil Returns  

---

## Team Members & Student IDs
* **Nehantha Sathesh** (Student ID: 01551453)
* **Toh En Hui** (Student ID: 01551403)

---

#### Nehantha Sathesh (01551453)
  * Generated Normal Q-Q plots, tail probability decay curves, log-return time series, and annual joint-downside distribution charts.
* Programmed the tail frequency evaluations ($|z| > 3$ SD days), theoretical Normal benchmark comparisons, and non-parametric Chebyshev inequality bounds.
* Implemented joint downside contingency matrices ($2 \times 2$ tables) and conducted statistical significance testing using **Fisher's Exact Test** to assess joint extreme occurrences.
* **Documentation & Review:**
  * Drafted technical methodology write-ups for statistical tests and probability bounds.
  * Cross-checked report interpretations against mathematical output models.

#### Toh En Hui (01551403)
  * Developed the primary data ingestion pipeline to process and clean 32,932 raw LSEG Datastream price rows (13,257 after deduplication), handling gap-spanning dates and constructing the 6,492 daily return series ($r_t = 100 \times \ln(P_t/P_{t-1})$).
  * Conducted sub-period regime shift analyses comparing pre-crisis (2019) vs. crisis (2020) volatility, daily standard deviations, and dynamic correlation shifts ($r = -0.14 \rightarrow +0.10$).
* **Documentation & Delivery:**
  * Lead author for the final project report structure, narrative interpretations, project limitations (volatility clustering, sample bias, and non-causality), and data ethics compliance guidelines.
---

## Joint Collaboration & Peer Review
* **Cross-Checking & Code Verification:** Both team members conducted peer code reviews, verifying that random seeds were fixed, relative file paths were maintained, and statistical outputs matched standard Python library baselines (`scipy.stats`, `pandas`).
* Designed and produced the final presentation slide deck (`DS603_GP_01551403_slides.pdf`).
* **Final Deliverable Assembly:** Jointly reviewed and finalized the `README.md`, `AI_USAGE.md`, report text, and final presentation slides before submission.
