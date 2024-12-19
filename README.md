# Automobile-Sales-Analysis-During-Recession-Periods

Data Source: https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DV0101EN-SkillsNetwork/Data%20Files/historical_automobile_sales.csv

## Project Overview

This project involves analyzing historical automobile sales data to understand how economic recessions impact sales trends. The dataset includes various economic indicators and automobile-related features, allowing for comprehensive insights into sales trends during recession and non-recession periods. The primary goal is to identify patterns and relationships to support data-driven decision-making.

The project demonstrates expertise in data wrangling, exploratory data analysis, and visualization using Python libraries such as Pandas, Matplotlib, Seaborn, and others.

---

## Dataset Description

The dataset contains the following features:

| Variable                  | Description                                                                                   |
| ------------------------- | --------------------------------------------------------------------------------------------- |
| `Date`                    | The date of the observation                                                                   |
| `Year`                    | Year of the observation, extracted from `Date`                                                |
| `Month`                   | Month of the observation, extracted from `Date`                                               |
| `Recession`               | Binary variable indicating whether it was a recession period (1: recession, 0: non-recession) |
| `Automobile_Sales`        | The number of vehicles sold during the period                                                 |
| `GDP`                     | Per capita GDP value in USD                                                                   |
| `Unemployment_Rate`       | Monthly unemployment rate                                                                     |
| `Consumer_Confidence`     | Synthetic index representing consumer confidence                                              |
| `Seasonality_Weight`      | Weight representing the seasonality effect on automobile sales                                |
| `Price`                   | Average vehicle price during the period                                                       |
| `Advertising_Expenditure` | Advertising expenditure of the company                                                        |
| `Vehicle_Type`            | Type of vehicles sold (e.g., Superminicar, Smallfamilycar, Mediumfamilycar, Sports, etc.)     |
| `Competition`             | Measure of competition in the market                                                          |
| `City`                    | City-level data for analysis                                                                  |

---

## Project Steps

### 1. Data Wrangling

- **Preparing the dataset**: Extracted key features such as `Year` and `Month` from the `Date` column for analysis.
- **Filtering data**: Focused on recession periods to understand sales trends and identify patterns.

---

### 2. Exploratory Data Analysis (EDA)

#### TASK 1.1: Line Chart - Automobile Sales Over Time

Visualized how automobile sales fluctuated across different years, highlighting recession periods.

```python
sns.lineplot(data=df, x='Year', y='Automobile_Sales')
plt.title("Automobile Sales During Recession")
plt.xlabel("Year")
plt.ylabel("Automobile Sales")
plt.show()
```

---

#### TASK 1.2: Line Chart - Sales Trends by Vehicle Type

Compared sales trends across different vehicle types to observe variations during recession periods.

```python
sns.lineplot(data=df, x='Year', y='Automobile_Sales', hue='Vehicle_Type')
plt.title("Vehicle Type Sales Trends During Recession")
plt.xlabel("Year")
plt.ylabel("Automobile Sales")
plt.legend(title="Vehicle Type")
plt.show()
```

---

#### TASK 1.3: Bar Plot - Sales by Vehicle Type in Recession vs. Non-Recession Periods

Used a bar chart to compare sales trends across vehicle types during recession and non-recession periods.

```python
sns.barplot(data=df, x='Vehicle_Type', y='Automobile_Sales', hue='Recession')
plt.title("Vehicle Type Sales: Recession vs Non-Recession")
plt.xlabel("Vehicle Type")
plt.ylabel("Automobile Sales")
plt.legend(title="Recession")
plt.show()
```

---

#### TASK 1.4: Subplot - GDP During Recession and Non-Recession

Analyzed GDP variations over recession and non-recession periods using subplots.

```python
fig, ax = plt.subplots(1, 2, figsize=(12, 6))
recession_gdp = df[df['Recession'] == 1]
non_recession_gdp = df[df['Recession'] == 0]

sns.lineplot(data=recession_gdp, x='Year', y='GDP', ax=ax[0])
ax[0].set_title("GDP During Recession")

sns.lineplot(data=non_recession_gdp, x='Year', y='GDP', ax=ax[1])
ax[1].set_title("GDP During Non-Recession")

plt.show()
```

---

#### TASK 1.5: Bubble Plot - Seasonality Impact on Automobile Sales

Examined the impact of seasonality on sales during non-recession periods.

```python
sns.scatterplot(data=df[df['Recession'] == 0], x='Month', y='Automobile_Sales', size='Seasonality_Weight', legend=False)
plt.title("Seasonality Impact on Automobile Sales")
plt.xlabel("Month")
plt.ylabel("Automobile Sales")
plt.show()
```

---

#### TASK 1.6: Scatter Plot - Price vs. Sales Volume During Recession

Analyzed the relationship between average vehicle price and sales volume during recessions.

```python
sns.scatterplot(data=df[df['Recession'] == 1], x='Price', y='Automobile_Sales')
plt.title("Relationship Between Price and Sales During Recessions")
plt.xlabel("Average Vehicle Price")
plt.ylabel("Automobile Sales")
plt.show()
```

---

#### TASK 1.7: Pie Chart - Advertising Expenditure During Recession and Non-Recession Periods

Visualized advertising expenditure proportions during recession and non-recession periods.

```python
advertising_data = df.groupby('Recession')['Advertising_Expenditure'].sum()
advertising_data.plot(kind='pie', autopct='%1.1f%%')
plt.title("Ad Expenditure: Recession vs Non-Recession")
plt.ylabel("")
plt.show()
```

---

#### TASK 1.9: Line Plot - Effect of Unemployment Rate on Vehicle Type During Recession

Analyzed how the unemployment rate impacted sales for various vehicle types during recessions.

```python
sns.lineplot(data=df[df['Recession'] == 1], x='Unemployment_Rate', y='Automobile_Sales', hue='Vehicle_Type')
plt.title("Effect of Unemployment Rate on Vehicle Type and Sales")
plt.xlabel("Unemployment Rate")
plt.ylabel("Automobile Sales")
plt.legend(title="Vehicle Type")
plt.show()
```

---

## Results and Insights

- **Automobile Sales Fluctuation**: Significant drops in sales during recessions, with variations across vehicle types.
- **Impact of GDP and Consumer Confidence**: Recessions correlate with lower GDP and reduced consumer confidence, affecting sales.
- **Unemployment Rate**: Higher unemployment rates negatively impact automobile sales, with different effects on vehicle types.

---

## Tools and Libraries

- **Pandas**: Data manipulation and analysis.
- **Matplotlib/Seaborn**: Data visualization.
- **Jupyter Notebook**: Interactive coding environment.

---

## Repository Structure

```
automobile_sales_analysis/
├── data/
│   └── historical_automobile_sales.csv
├── notebooks/
│   └── automobile_sales_analysis.ipynb
├── README.md
└── results/
    ├── sales_trends.png
    ├── recession_vs_non_recession.png
    └── advertising_pie_chart.png
```

---

## Conclusion

This project provides valuable insights into how recessions impact automobile sales. By leveraging data analysis and visualization techniques, we identified key trends and relationships that can guide strategic decisions for businesses during economic downturns.

---

### Next Steps

- Investigate additional economic indicators to refine the analysis.
- Incorporate advanced predictive modeling techniques for future sales forecasting.

### Acknowledgments





