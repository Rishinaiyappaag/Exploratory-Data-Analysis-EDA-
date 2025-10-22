
# 📘 README — Task 2: Exploratory Data Analysis (EDA)
# 🎯 Objective

The goal of this task is to explore the Titanic dataset using statistical and visual techniques. Exploratory Data Analysis (EDA) helps understand the structure, relationships, and patterns in data before applying machine learning algorithms.

# 🧰 Tools & Libraries Used

Python

Pandas – for data handling and statistical summaries

Matplotlib – for static visualizations

Seaborn – for advanced statistical plots

Plotly – for interactive visualizations

# ⚙️ Steps & Explanation
1. Import Libraries

All essential Python libraries for data analysis and visualization are imported:

import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import plotly.express as px

2. Load Dataset

The Titanic dataset (Titanic-Dataset.csv) is loaded into a Pandas DataFrame:

data = pd.read_csv("Titanic-Dataset.csv")


The first few records, structure, and data types are displayed using:

data.info()
data.head()
data.describe(include='all')

3. Handle Missing Values

Missing data is identified and appropriately handled:

Numeric Columns: Filled with the median value.

Categorical Columns: Filled with the mode (most frequent value).

data[num_cols] = data[num_cols].fillna(data[num_cols].median())
data[cat_cols] = data[cat_cols].fillna(data[cat_cols].mode().iloc[0])


This ensures the dataset is clean and complete for analysis.

4. Summary Statistics

data.describe() provides key descriptive statistics such as mean, median, standard deviation, and percentiles, offering an initial understanding of data distribution and scale.

5. Distribution Analysis

Histograms are used to visualize numeric feature distributions:

data[num_cols].hist(bins=20, figsize=(12, 8), edgecolor='black')


This helps detect skewness, normality, and potential outliers.

6. Outlier Detection

Boxplots identify outliers and range of numeric variables:

sns.boxplot(x=data[col])


Features such as Fare and Age often show visible outliers in the Titanic dataset.

7. Relationship Analysis

A pairplot from Seaborn visualizes pairwise relationships between numeric features:

sns.pairplot(data[sample_cols])


This reveals feature interactions and possible clustering patterns.

8. Correlation Analysis

The correlation matrix measures linear relationships between features:

corr_matrix = data[num_cols].corr()
sns.heatmap(corr_matrix, annot=True, cmap='coolwarm')


Strong or weak correlations help identify redundant or influential variables.

9. Interactive Visualization (Plotly)

An interactive correlation matrix is created using Plotly:

px.imshow(corr_matrix, text_auto=True, color_continuous_scale='RdBu_r')


Users can hover over cells to view correlation values dynamically.

# 💡 Key Insights

‘Fare’ shows strong correlation with ‘Pclass’ (travel class).

‘Age’ distribution is slightly right-skewed.

Outliers exist in ‘Fare’ and ‘Age’ columns.

Data is now clean, making it ready for model training or feature engineering.

# 📊 Visual Outputs

Histograms – Distribution of numeric features.

Boxplots – Outlier detection per feature.

Pairplots – Relationships among numeric attributes.

Heatmaps – Correlation structure among features.

Plotly Chart – Interactive correlation exploration.
