**Problem Statement:** Air pollution significantly impacts human health and the environment. The Air Quality Index (AQI) is a standardized method to measure and categorize air pollution levels. This problem requires analyzing air pollution data collected from various cities to compute AQI, categorize pollution severity using AQI buckets, and perform exploratory data analysis to derive meaningful insights.

The dataset contains air pollution metrics such as PM2.5, PM10, NO, NO2, NOx, NH3, CO, SO2, O3, Benzene, Toluene, and Xylene, recorded across different cities and dates.

**Tasks:**

1. **AQI Calculation:**

   - Compute AQI using PM2.5, PM10, SO2, NOx, NH3, CO, and O3.

   - Convert individual pollutant levels to sub-indices based on standard AQI breakpoints using the following formula:

     **Sub-Index Calculation Formula:**

     ```
     Sub-Index = [(High AQI - Low AQI) / (High Breakpoint - Low Breakpoint)] × (Pollutant Concentration - Low Breakpoint) + Low AQI
     ```

     Where:

     - **Sub-Index** = AQI contribution of a specific pollutant
     - **Pollutant Concentration** = Measured value of the pollutant
     - **High Breakpoint, Low Breakpoint** = AQI breakpoint values for the pollutant
     - **High AQI, Low AQI** = Corresponding AQI range values

   - The final AQI is determined as the **maximum** sub-index value, ensuring at least one value from PM2.5 or PM10 is available and at least three out of the seven pollutants contribute.

   - Categorize AQI into buckets based on the following table:

     | AQI Range | Category     |
     | --------- | ------------ |
     | 0 - 50    | Good         |
     | 51 - 100  | Satisfactory |
     | 101 - 200 | Moderate     |
     | 201 - 300 | Poor         |
     | 301 - 400 | Very Poor    |
     | 401+      | Severe       |

   - **Breakpoints for India AQI:**

     | Pollutant     | 0-50 | 51-100 | 101-200 | 201-300 | 301-400  | 401-500 |
     | ------------- | ---- | ------ | ------- | ------- | -------- | ------- |
     | PM2.5 (µg/m³) | 0-30 | 31-60  | 61-90   | 91-120  | 121-250  | 251+    |
     | PM10 (µg/m³)  | 0-50 | 51-100 | 101-250 | 251-350 | 351-430  | 431+    |
     | NO2 (µg/m³)   | 0-40 | 41-80  | 81-180  | 181-280 | 281-400  | 401+    |
     | SO2 (µg/m³)   | 0-40 | 41-80  | 81-380  | 381-800 | 801-1600 | 1601+   |
     | CO (mg/m³)    | 0-1  | 1.1-2  | 2.1-10  | 10.1-17 | 17.1-34  | 34.1+   |
     | O3 (µg/m³)    | 0-50 | 51-100 | 101-168 | 169-208 | 209-748  | 749+    |

2. **Example Calculation:**

   Given the following record:

   | City      | Date       | PM2.5 | NO2   | CO   | SO2   | O3    |
   | --------- | ---------- | ----- | ----- | ---- | ----- | ----- |
   | Ahmedabad | 2015-01-29 | 83.13 | 28.71 | 6.93 | 49.52 | 59.76 |

   - **PM2.5 (83.13 µg/m³) falls in the 61-90 range (101-200 AQI)**
     ```
     Sub-Index_PM2.5 = [(200 - 101) / (90 - 61)] * (83.13 - 61) + 101
                      ≈ 172.3
     ```
   - **NO2 (28.71 µg/m³) falls in the 0-40 range (0-50 AQI)**
     ```
     Sub-Index_NO2 = [(50 - 0) / (40 - 0)] * (28.71 - 0) + 0
                    ≈ 35.89
     ```
   - **CO (6.93 mg/m³) falls in the 2.1-10 range (101-200 AQI)**
     ```
     Sub-Index_CO = [(200 - 101) / (10 - 2.1)] * (6.93 - 2.1) + 101
                   ≈ 152.83
     ```
   - **SO2 (49.52 µg/m³) falls in the 41-80 range (51-100 AQI)**
     ```
     Sub-Index_SO2 = [(100 - 51) / (80 - 41)] * (49.52 - 41) + 51
                    ≈ 62.6
     ```
   - **O3 (59.76 µg/m³) falls in the 51-100 range (51-100 AQI)**
     ```
     Sub-Index_O3 = [(100 - 51) / (100 - 51)] * (59.76 - 51) + 51
                   ≈ 61.92
     ```
   - **Final AQI = max(172.3, 35.89, 152.83, 62.6, 61.92) = 172.3 (Moderate)**

3. **Data Cleaning and Preparation:**

   - Handle missing values in the dataset.
   - Convert date columns to proper datetime format for time-series analysis.
   - Identify outliers using statistical methods.

4. **Exploratory Data Analysis (EDA):**

   - Compute summary statistics.
   - Identify top polluted and cleanest cities.
   - Find seasonal trends and correlations.

5. **Implementation Using Pandas, NumPy:**

   - AQI calculations and analysis will be implemented using **Pandas** and **NumPy**.
   - Output will be written in **CSV files only**.
   - Use **Matplotlib/Seaborn** for data visualization.
   - Use **datetime** module for time-based analysis.

**Questions:**

- **Location-Based Analysis:**
  - Identify the top 5 most polluted cities based on PM2.5 levels.
  - Identify the top 5 cleanest cities based on PM2.5 levels.
- **Time-Based Analysis:**
  - Find the month with the highest average air pollution levels globally.
  - Identify seasonal trends in air pollution levels.
  - Find the hour of the day when air pollution is highest.

This problem provides an opportunity to understand air pollution trends and build data-driven solutions for pollution control.
