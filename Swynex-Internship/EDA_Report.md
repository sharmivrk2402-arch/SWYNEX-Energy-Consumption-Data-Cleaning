# Exploratory Data Analysis (EDA) — Energy Consumption Dataset

## 1. Objective
Explore the cleaned dataset from Task 1, calculate descriptive statistics, examine relationships and patterns, identify potential anomalies, and summarize useful insights.

## 2. Dataset overview
- Records: **1,000**
- Columns: **11 original columns plus the analysis-only `Hour` feature**
- Time coverage: **01 Jan 2022 00:00 to 11 Feb 2022 15:00**
- Missing values in the cleaned input: **0**
- Duplicate rows: **0**

The dataset contains timestamp, temperature, humidity, square footage, occupancy, HVAC usage, lighting usage, renewable energy, weekday, holiday status, and energy consumption.

## 3. Descriptive statistics
Energy consumption:
- Mean: **77.06**
- Median: **76.94**
- Standard deviation: **8.14**
- Minimum: **53.26**
- Maximum: **99.20**

### Numerical summary
|                   |   count |    mean |    std |     min |     25% |     50% |     75% |     max |
|:------------------|--------:|--------:|-------:|--------:|--------:|--------:|--------:|--------:|
| Temperature       |    1000 |   24.98 |   2.84 |   20.01 |   22.65 |   24.75 |   27.42 |   30    |
| Humidity          |    1000 |   45.4  |   8.52 |   30.02 |   38.3  |   45.97 |   52.42 |   59.97 |
| SquareFootage     |    1000 | 1500.05 | 288.42 | 1000.51 | 1247.11 | 1507.97 | 1740.34 | 1999.98 |
| Occupancy         |    1000 |    4.58 |   2.87 |    0    |    2    |    5    |    7    |    9    |
| RenewableEnergy   |    1000 |   15.13 |   8.75 |    0.01 |    7.63 |   15.07 |   22.88 |   29.97 |
| EnergyConsumption |    1000 |   77.06 |   8.14 |   53.26 |   71.54 |   76.94 |   82.92 |   99.2  |

## 4. Useful insights

### Insight 1 — Temperature has the strongest positive linear relationship with energy consumption
The Pearson correlation between temperature and energy consumption is **0.696**. This indicates a relatively strong positive linear association in this dataset: higher recorded temperatures tend to occur alongside higher energy consumption. Correlation does not prove that temperature causes the increase.

![Temperature vs energy](charts/02_temperature_vs_energy.png)

### Insight 2 — Average consumption is higher when HVAC is On
Average consumption is **79.42** when HVAC is On and **74.76** when it is Off. The difference is **4.66** (about **6.2%** relative to the Off average). This is an association, not proof that HVAC status alone explains the difference; temperature and occupancy may also differ between groups.

| HVACUsage   |   count |   mean |   median |
|:------------|--------:|-------:|---------:|
| Off         |     508 | 74.761 |   74.417 |
| On          |     492 | 79.425 |   78.732 |

![HVAC average](charts/03_hvac_average.png)

### Insight 3 — Higher occupancy group has the highest average consumption
After dividing records into four occupancy quantile groups, the highest-occupancy group averages **79.81**, compared with **75.11** in the lowest-occupancy group. The Pearson correlation between occupancy and consumption is **0.187**, which is a modest positive relationship overall.

| OccupancyBand     |   count |   mean |   median |
|:------------------|--------:|-------:|---------:|
| Lowest occupancy  |     287 | 75.109 |   75.602 |
| Lower-middle      |     294 | 77.021 |   76.647 |
| Upper-middle      |     208 | 76.995 |   76.573 |
| Highest occupancy |     211 | 79.813 |   80.46  |

![Occupancy groups](charts/05_occupancy_groups.png)

### Insight 4 — Saturday has the highest weekday average in this sample
The highest average by weekday is **Saturday (78.87)**, while the lowest is **Monday (76.06)**. These are descriptive differences in this sample; they should not be generalized without more data and context.

| DayOfWeek   |   count |   mean |   median |
|:------------|--------:|-------:|---------:|
| Monday      |     144 | 76.064 |   76.849 |
| Tuesday     |     144 | 77.385 |   77.399 |
| Wednesday   |     144 | 76.301 |   75.94  |
| Thursday    |     144 | 76.127 |   76.212 |
| Friday      |     136 | 77.804 |   77.031 |
| Saturday    |     144 | 78.869 |   78.535 |
| Sunday      |     144 | 76.881 |   76.019 |

![Weekday average](charts/04_weekday_average.png)

### Insight 5 — Hourly averages vary, but the spread is limited
The highest hourly mean occurs at **1:00 (79.27)** and the lowest at **9:00 (74.40)**. The difference is **4.87**. There is no clear monotonic rise or fall across the day from these averages.

![Hourly average](charts/07_hourly_average.png)

### Insight 6 — One low energy-consumption value is flagged by the IQR rule
Using the 1.5×IQR rule, the lower fence is **54.48** and the upper fence is **99.99**. **1** record(s) are flagged. This is a statistical flag, not automatically an error; inspect the original context before changing or removing it.
| Timestamp           |   EnergyConsumption |   Temperature |   Occupancy | HVACUsage   | LightingUsage   |
|:--------------------|--------------------:|--------------:|------------:|:------------|:----------------|
| 2022-01-03 21:00:00 |             53.2633 |       20.7357 |           4 | Off         | On              |

![Energy distribution](charts/01_energy_distribution.png)

## 5. Additional correlation observations
- Temperature vs energy consumption: **0.696**
- Occupancy vs energy consumption: **0.187**
- Humidity vs energy consumption: **-0.094**
- Renewable energy vs energy consumption: **0.081**
- Square footage vs energy consumption: **-0.001**

![Correlation matrix](charts/06_correlation_matrix.png)

## 6. Conclusion
In this dataset, temperature is the strongest numerical correlate of energy consumption. Higher average consumption is also observed when HVAC is On and in the highest occupancy group. Average consumption differs by weekday and hour, though these patterns are descriptive. One low consumption record is flagged by the IQR rule and should be reviewed rather than automatically removed.

## 7. Limitations
- The data covers only **42 calendar days** and should not be treated as a full-year picture.
- Correlations and group averages do not establish causation.
- The dataset does not provide units for all measurement columns in the supplied file; values are reported in the dataset's recorded units.
- The weekday column was corrected in Task 1 using the timestamp as the source of truth.

## 8. Tools
Python, Pandas, NumPy, Matplotlib, Jupyter Notebook.
