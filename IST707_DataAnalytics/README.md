IST 707: Data Analytics

**Project:** Domestic Flight Delay Prediction
**Team:** Najah Bell, Matthew Hicks, Andrew Krick, Nomar Diaz
**Tools:** Python · scikit-learn · pandas · seaborn · K-Means · Random Forest



Project Overview

This project applied clustering and classification techniques to predict domestic flight departure and arrival delays using 2015 U.S. flight data from the Department of Transportation's Bureau of Transportation Statistics.



Dataset

•	**Source:** U.S. DOT Bureau of Transportation Statistics, 2015
•	**Raw observations:** 258,772 flights
•	**Working dataset (after removing cancelled, diverted, null-delay flights):** 252,733 observations
•	**Features:** 15 (from original 31), including airline, origin/destination airport, scheduled/actual times, delay duration by cause (air system, security, airline, late aircraft, weather)



Methods

Step 1 — Clustering (K-Means)
K-Means clustering was applied to determine the optimal number of delay categories. The **elbow method** identified 2 as the statistically optimal number of clusters. Three categories were implemented for analytical interpretability:
•	Early / On-Time
•	Delayed
•	Severely Delayed

The Davies-Bouldin index confirmed that three clusters showed slightly more overlap than two but no egregious mixing.

Step 2 — Classification (Random Forest)
Classification models were built and evaluated on both departure and arrival delay prediction.

| Task | Random Forest Accuracy |
|------|----------------------|
| Arrival Delay Prediction | ~80% |
| Departure Delay Prediction | ~62% |

All models performed substantially better on arrival delay prediction — arrival delays are more structurally predictable because they partially reflect the propagation of earlier delays along a flight's route.

Step 3 — Real-World Test Case
After fine-tuning, the model was applied to a hypothetical scenario:

Southwest Airlines flight, Chicago → Los Angeles, scheduled 2:00 PM, Wednesday December 25th, with a 10-minute departure delay.

**Model prediction: Delayed arrival.**



Files in This Folder

| File | Description |
|------|-------------|
| `IST707_Presentation.pptx` | Final project presentation slides |
| `flight_delay_analysis.ipynb` | Python notebook |



Reflection

The 18-percentage-point accuracy gap between arrival and departure delay prediction reveals a structural insight: departure delays depend on real-time external factors that are difficult to predict. In contrast, arrival delays inherit causal structure from earlier legs of a route. Understanding *why* a model performs the way it does, not just how accurately, is essential to responsible deployment.

