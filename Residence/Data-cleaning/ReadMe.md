
### DataSet Description
The UR3 CobotOps dataset contains time-series sensor data collected from a UR3 collaborative robot during its normal operation cycles. It records key joint-level measurements such as current, speed, and temperature across six joints, along with tool usage metrics and system-level events like protective stops and grip loss. This dataset is ideal for analyzing robot behavior, detecting anomalies, and developing predictive maintenance models.

#### 1.Dataset Snapshot
- Rows: 7 404 (after cleaning)
- Columns: 24-
- Sequential/meta → Num, Timestamp, cycle, safety flags
- Joint sensors → Current_J0–J5, Speed_J0–J5, Temperature_T0/J1–J5
- Tool metric → Tool_current
- Time span: ≈ 250 robot cycles, ISO-8601 timestamps
#### 2. Key Insights from EDA
###### Currents
- J0 & J4 centred at 0 A (idle).
- J1/2/3/5 bimodal (≈ -2 A & 0 A) → two torque regimes.
- |I| > 3 A rare → flag as stress events.
###### Temperatures
- Warm-up bump (< 35 °C) then steady plateau (36–40 °C).
- J4/J5 hottest (~45 °C).
- is_warmup flag valuable for model segmentation.
###### Speeds
- ≈ 80 % rows near 0 rad/s (idle).
- Use is_moving = |speed| > 0.1.
###### Tool_current
- Mode ≈ 0.08 A, tail > 0.4 A indicates heavy load.
###### Safety flags
- Protective-stop & grip-lost almost zero → serve as anomaly labels.
#### 3. Data-Cleaning Pipeline (Major Steps)
###### Column trim & typing
- Stripped whitespace; parsed Timestamp to UTC; cast all joint sensors to float64.
###### Missing-value handling
- Forward-filled sensor gaps within the same cycle, then median-imputed leftovers.
- Filled safety flags with default 0/False; dropped rows with bad timestamps.
###### Duplicate & consistency checks
- Removed rows duplicated on (Timestamp, cycle).
- Ensured cycle numeric and monotonic per log.
###### Noise mitigation
- Clipped values outside ±3 IQR (per column); logged outlier flags.
- Logic flags: speed≠0 & current≈0, temperature < 20 °C or > 90 °C.
###### Exploratory plots
- Histograms for every sensor; joint-0 pairplot; time-series for key metrics.
- Correlation heat-map highlights strong links (current↔speed, current↔temp).
###### Challenge                                                                  |
- **NaNs scattered** across cycles           
- `Timestamp` strings with extra quotes      
- Hidden spaces in column names (`cycle `)   
- Pairplot errors from non-numeric artefacts 
- Long-tail outliers (currents/temps)   
