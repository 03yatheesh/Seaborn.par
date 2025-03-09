# Seaborn Data Visualization Project

## Introduction
This project focuses on exploring and visualizing data using Seaborn, a Python library built on Matplotlib. The visualizations include scatter plots, line plots, histograms, KDE plots, heatmaps, and clustermaps, providing deep insights into different datasets.

## Datasets Used
The following datasets are used in this project:

- **Tips Dataset** – Contains information about total bills, tips, customer gender, smoking status, and dining time.
- **Gapminder Dataset** – Tracks life expectancy, GDP per capita, and population for different countries over time.
- **Titanic Dataset** – Includes passenger details like age, gender, survival status, and class.
- **Iris Dataset** – Consists of measurements of three iris flower species.

---

## Visualizations and Insights

### 1️⃣ Scatter Plots (Relational Analysis)
Scatter plots help visualize relationships between numerical variables.

#### Single Scatter Plot
```python
sns.scatterplot(x='total_bill', y='tip', data=tips)
```
*Shows the relationship between the total bill and the tip amount in a restaurant setting.*

#### Categorized Scatter Plot
```python
sns.scatterplot(x='total_bill', y='tip', data=tips, hue="sex", style='time', size='size')
```
*Categorizes scatter points by gender, dining time, and group size.*

#### Figure-Level Scatter Plot (relplot)
```python
sns.relplot(x='total_bill', y='tip', kind='scatter', data=tips, hue='sex', style='time', size='size')
```
*A higher-level function that can generate subplots automatically.*

---

### 2️⃣ Line Plots (Trends Over Time)
Line plots are ideal for showing trends in continuous data, such as life expectancy over time.

#### Line Plot for a Single Country
```python
sns.lineplot(x="year", y="lifeExp", data=gap[gap['country'] == 'India'])
```
*Displays how life expectancy in India has changed over time.*

#### Comparing Multiple Countries
```python
temp_df = gap[gap['country'].isin(['India', 'Pakistan', 'China'])]
sns.relplot(x="year", y="lifeExp", kind='line', data=temp_df, hue='country')
```
*Compares life expectancy trends across India, Pakistan, and China.*

---

### 3️⃣ Facet Grids (Row & Column Subplots)
Facet grids allow for comparison across multiple categories.

#### Subplots Based on Smoker & Gender
```python
sns.relplot(x="total_bill", y="tip", data=tips, col='smoker', row='sex')
```
*Creates subplots for male and female customers, further divided by smoking habits.*

#### Multi-Year Comparison Using Facet Grids
```python
sns.relplot(data=gap, x='lifeExp', y='gdpPercap', kind='scatter', col='year', col_wrap=4)
```
*Shows the relationship between life expectancy and GDP per capita across multiple years.*

---

### 4️⃣ Histograms (Distribution Analysis)
Histograms help visualize how data points are distributed.

#### Basic Histogram
```python
sns.histplot(tips['total_bill'])
```
*Displays the distribution of total bill amounts.*

#### Histogram with Custom Bins
```python
sns.displot(tips['total_bill'], kind='hist', bins=20)
```
*Uses 20 bins for more detailed visualization.*

#### Categorized Histogram
```python
sns.displot(data=tips, x='tip', kind='hist', hue='sex')
```
*Categorizes the histogram by customer gender.*

---

### 5️⃣ Kernel Density Estimation (KDE) Plots
KDE plots smooth out histograms to show probability distributions.

#### Basic KDE Plot
```python
sns.kdeplot(data=tips, x='total_bill')
```
*Shows the smooth distribution of total bill values.*

#### Filled KDE Plot with Categories
```python
sns.displot(data=tips, x='total_bill', kind='kde', hue='sex', fill=True)
```
*Fills the KDE plot for better visibility, differentiating male and female customers.*

---

### 6️⃣ Rug Plot (Individual Data Points on Axis)
Rug plots show where each data point lies.

```python
sns.kdeplot(data=tips, x='total_bill')
sns.rugplot(data=tips, x='total_bill')
```
*Adds a rug plot on top of the KDE plot, showing exact data points.*

---

### 7️⃣ Bivariate Analysis (Comparing Two Variables)

#### Bivariate Histogram
```python
sns.histplot(data=tips, x='total_bill', y='tip')
```
*Displays how tip amounts vary with total bill amounts using a color-coded 2D histogram.*

#### Bivariate KDE Plot
```python
sns.kdeplot(data=tips, x='total_bill', y='tip')
```
*Smooths out the 2D histogram using KDE.*

---

### 8️⃣ Heatmaps (Matrix Visualization)
Heatmaps help visualize data in a color-coded format.

#### Basic Heatmap
```python
temp_df = gap.pivot(index="country", columns='year', values='lifeExp')
plt.figure(figsize=(10,10))
sns.heatmap(temp_df)
```
*Displays life expectancy trends across different countries and years.*

#### Heatmap with Annotations
```python
sns.heatmap(temp_df, annot=True, linewidths=0.5, cmap='viridis')
```
*Adds numerical values inside the heatmap for better readability.*

---

### 9️⃣ Clustermaps (Hierarchical Clustering)
Clustermaps group similar data points together.

```python
iris = px.data.iris()
sns.clustermap(iris.iloc[:, [0, 1, 2, 3]])
```
*Clusters iris flower species based on petal and sepal sizes.*

---

## Conclusion
This project provides a comprehensive overview of Seaborn’s visualization capabilities, demonstrating how to:
- Analyze **relationships** between variables (scatter, relplot).
- Visualize **trends over time** (line plots).
- Study **data distributions** (histograms, KDE, rug plots).
- Perform **bivariate analysis** (2D histograms, KDE).
- Use **advanced visualizations** like heatmaps and clustermaps.

