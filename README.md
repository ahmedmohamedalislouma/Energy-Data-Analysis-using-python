# Energy Data Analysis

This repository contains a Python script for analyzing energy data, GDP data, and journal ranking data. The script utilizes the pandas library for data manipulation and analysis.

## Data Sources

The script uses the following data sources:

1. **Energy Indicators**: The energy data is loaded from the file `Energy Indicators.xls`, which is an Excel file containing indicators of energy supply and renewable electricity production from the United Nations for the year 2013.

2. **World Bank GDP Data**: The GDP data is loaded from the file `world_bank.csv`, which is a CSV file containing countries' GDP from 1960 to 2015.

3. **Scimago Journal and Country Rank Data**: The journal ranking data for Energy Engineering and Power Technology is loaded from the file `scimagojr-3.xlsx`, which is an Excel file ranking countries based on their journal contributions in the specified area.

## Analysis Steps

The script performs the following steps for data analysis:

### Step 0: Loading and Preprocessing Energy Data

- Loads the energy data from the `Energy Indicators.xls` file into a pandas DataFrame named **energy**.
- Removes unnecessary columns and changes column labels.
- Converts the 'Energy Supply' values to gigajoules.
- Handles missing data by replacing '...' with `np.NaN`.
- Renames certain countries according to the provided mapping.
- Removes numbers and parentheses from country names.

### Step 1: Loading and Preprocessing GDP Data

- Loads the GDP data from the `world_bank.csv` file into a pandas DataFrame named **GDP**.
- Skips the header rows.
- Renames certain countries according to the provided mapping.

### Step 2: Loading Scimago Journal Ranking Data

- Loads the Scimago Journal and Country Rank data for Energy Engineering and Power Technology from the `scimagojr-3.xlsx` file into a pandas DataFrame named **ScimEn**.

### Step 3: Joining the Datasets

- Joins the three datasets (GDP, energy, and ScimEn) into a new dataset named **Top_15_country**.
- Uses the intersection of country names for joining.
- Includes only the last 10 years (2006-2015) of GDP data.
- Includes only the top 15 countries based on Scimagojr Rank.
- Sets the index of the DataFrame to the name of the country and selects the specified columns.

### Step 4: Loss of Entries

- Calculates the number of entries lost during the join operation.

### Step 5: Average GDP over the Last 10 Years

- Calculates the average GDP over the last 10 years for each country.
- Excludes missing values from the calculation.
- Returns a Series named `avgGDP` with 15 countries and their average GDP sorted in descending order.

### Step 6: Mean Energy Supply per Capita

- Calculates the mean value of 'Energy Supply per Capita' across all countries.
- Returns a single number.

### Step 7: Maximum % Renewable

- Finds the country with the maximum '% Renewable' and its corresponding percentage.
- Returns a tuple with the name of the country and the percentage.

### Step 8: Ratio of Self-Citations to Total Citations

- Creates a new column named 'ratio' that represents the ratio of Self-Citations to Total Citations.
- Finds the country with the highest ratio.
- Returns a tuple with the name of the country and the ratio.

### Step 9: Categorizing Countries based on % Renewable

- Creates a new column named 'HighRenew' that categorizes countries as 1 if their '% Renewable' value is at or above the median, and 0 if it is
