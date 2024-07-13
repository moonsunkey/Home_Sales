# Home_Sales

## Project Overview

The purpose of this project is to utilize Spark and PySpark SQL functions to analyze home sales data and compare the runtime with cached and partitioned data.

## Queries and Outputs

### 1. What is the average price for a four-bedroom house sold for each year?

```plaintext
+----+-------------+
|YEAR|AVERAGE_PRICE|
+----+-------------+
|2022|    296363.88|
|2021|    301819.44|
|2020|    298353.78|
|2019|     300263.7|
+----+-------------+
```

### 2. What is the average price of a home for each year the home was built, that has three bedrooms and three bathrooms?

```plaintext
+----+-------------+
|YEAR|AVERAGE_PRICE|
+----+-------------+
|2017|    292676.79|
|2016|    290555.07|
|2015|     288770.3|
|2014|    290852.27|
|2013|    295962.27|
|2012|    293683.19|
|2011|    291117.47|
|2010|    292859.62|
+----+-------------+
```
### 3. What is the average price of a home for each year the home was built, that has three bedrooms, three bathrooms, two floors, and is greater than or equal to 2,000 square feet? 

```plaintext
+----+-------------+
|YEAR|AVERAGE_PRICE|
+----+-------------+
|2017|    280317.58|
|2016|     293965.1|
|2015|    297609.97|
|2014|    298264.72|
|2013|    303676.79|
|2012|    307539.97|
|2011|    276553.81|
|2010|    285010.22|
+----+-------------+
```

### 4. What is the average price of a home per "view" rating having an average home price greater than or equal to $350,000? 

```plaintext
+----+-------------+
|view|AVERAGE_PRICE|
+----+-------------+
|  99|   1061201.42|
|  98|   1053739.33|
|  97|   1129040.15|
|  96|   1017815.92|
|  95|    1054325.6|
|  94|    1033536.2|
|  93|   1026006.06|
|  92|    970402.55|
|  91|   1137372.73|
|  90|   1062654.16|
|  89|   1107839.15|
|  88|   1031719.35|
|  87|    1072285.2|
|  86|   1070444.25|
|  85|   1056336.74|
|  84|   1117233.13|
|  83|   1033965.93|
|  82|    1063498.0|
|  81|   1053472.79|
|  80|    991767.38|
+----+-------------+
```

### Performance Analysis

Running the same query to answer the last question question above after caching the temporary table home_sales is about 0.00011658668518066406 seconds faster.

Then the data is partitioned by the "date_built" and a temporary table "homes_temp_view" is created based on the parquet data. Running the same query with the newly created table improves the time further by 0.00015974044799804688 seconds from running it with the cached data.
