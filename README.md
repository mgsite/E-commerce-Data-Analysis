# E-commerce Customer Behavior Analysis

## Overview

This project involves analyzing e-commerce customer behavior data to gain insights into customer demographics, purchasing patterns, and trends. The dataset includes information on customer age, gender, location, annual income, purchase history, browsing history, product reviews, and time on site. The analysis aims to enhance understanding of customer behavior and support strategic decision-making.

## Dataset

The dataset used for this analysis is the [E-commerce Customer Behavior Dataset](https://www.kaggle.com/datasets/samps74/e-commerce-customer-behavior-dataset). The columns in the dataset are:

- **Customer ID**: Unique identifier for each customer.
- **Age**: Age of the customer.
- **Gender**: Gender of the customer.
- **Location**: Location of the customer.
- **Annual Income**: Annual income of the customer.
- **Purchase History**: History of purchases made by the customer.
- **Browsing History**: History of browsing behavior.
- **Product Reviews**: Customer reviews for products.
- **Time on Site**: Time spent on the e-commerce site.

## Getting Started

### Prerequisites

Make sure you have the following libraries installed:

- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn
- jupyter

You can install the necessary libraries using pip:

```
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

# How to Run
### 1. Clone the Repository

git clone https://github.com/yourusername/e-commerce-customer-behavior-analysis.git
cd e-commerce-customer-behavior-analysis

### 2. Navigate to the Jupyter Notebook

Open the Jupyter Notebook:

jupyter notebook

Open the E-commerce_Analysis.ipynb notebook.

### 3. Load the Dataset

Ensure the dataset file E-commerce.csv is placed in the data directory. Adjust the file path in the notebook if necessary.

### 4. Run the Notebook

Execute each cell in the notebook to perform the data analysis.

# Analysis.

# 1. Data Exploration
In this step, we examine the basic properties of the dataset to understand its structure and contents. This includes:

- **Loading the Data**: We read the dataset into a DataFrame and inspected the first few rows to get an overview of the data.
- **Column Names and Data Types**: We checked the names of the columns and their respective data types to ensure they are as expected and to identify any necessary data type conversions.

```
# Load the dataset
df = pd.read_csv(r'C:\Users\María\Downloads\E-commerce.csv')

# Display the first few rows
df.head()

# Display column names and data types
df.info()
```

## Interpretation:
The dataset contains columns such as Customer ID, Age, Gender, Location, Annual Income, Purchase History, Browsing History, Product Reviews, and Time on Site. Data types were verified to ensure proper handling during analysis (e.g., numerical, categorical).

# Descriptive Statistics
Descriptive statistics provide a summary of the central tendencies, dispersion, and shape of the dataset's distribution. This includes:
-**Summary Statistics**: Mean, median, standard deviation, minimum, and maximum values for numerical columns.
-**Frequency Counts**: Counts for categorical variables like Gender and Location.

```
# Summary statistics for numerical columns
df.describe()

# Frequency counts for categorical columns
df['Gender'].value_counts()
df['Location'].value_counts()

```
## Interpretation:

Key statistics such as average age, income levels, and purchase history frequencies were calculated.
Categorical variables like Gender and Location were summarized to understand the distribution of different categories.


# 2. Exploratory Data Analysis (EDA)
## Distribution Analysis
This analysis focuses on the distribution of individual features to understand their spread and central tendencies. Key aspects include:

-**Age Distribution**: Analyzed how customer ages are distributed across the dataset.
-**Annual Income Distribution**: Examined the distribution of annual incomes.

```python

#Distribution of customer age
sns.histplot(df['Age'], kde=True)
plt.title('Age Distribution')
plt.xlabel('Age')
plt.ylabel('Frequency')
plt.show()

#Distribution of annual income
sns.histplot(df['Annual Income'], kde=True)
plt.title('Annual Income Distribution')
plt.xlabel('Annual Income')
plt.ylabel('Frequency')
plt.show()

```

### Interpretation:

-**Age Distribution**: Provided insights into the age range of customers, showing whether the customer base is young, middle-aged, or elderly.
-**Annual Income Distribution**: Illustrated income levels, helping to understand the economic profile of customers.

## Revenue by Location
This analysis assesses how revenue is distributed across different locations to identify regional performance:

-**Revenue Calculation**: Aggregated revenue data by location.
-**Visualization**: Used bar plots to compare revenue across locations.

```
#Calculate revenue by location
revenue_by_location = df.groupby('Location')['Annual Income'].sum().reset_index()

#Plot revenue by location
sns.barplot(x='Location', y='Annual Income', data=revenue_by_location)
plt.title('Revenue by Location')
plt.xlabel('Location')
plt.ylabel('Total Revenue')
plt.show()
```
### Interpretation:

- Identified which locations generate the most revenue.
- Provided insights into regional performance, guiding resource allocation and marketing strategies.

# 3. Customer Purchase Behavior
This analysis examines the patterns and trends in customer purchase behavior:

## Purchase Frequency: Analyzed how often customers make purchases.
Purchase Trends: Examined trends over time, if time-based data is available.
```
#Frequency of purchases
purchase_counts = df['Purchase History'].apply(lambda x: len(x.split(','))).value_counts()

#Plot purchase frequency
sns.histplot(purchase_counts, kde=True)
plt.title('Purchase Frequency Distribution')
plt.xlabel('Number of Purchases')
plt.ylabel('Frequency')
plt.show()
```
### Interpretation:

-**Purchase Frequency**: Provided insights into how frequently customers purchase, indicating the level of engagement.
-**Trends**: Identified patterns over time, helping to understand whether purchasing behavior is seasonal or consistent.




# 4. Results

### Customer Segmentation

Using K-Means clustering, we segmented the customers based on features such as Annual Income, Age, and Product Reviews. The clustering results help us identify distinct customer groups with similar characteristics.

![Customer Segmentation](images/customer_segmentation.png)

**Interpretation**:
- **Cluster 0**: Customers in this segment have lower annual incomes but higher product reviews. They might be frequent but lower-value customers.
- **Cluster 1**: This segment represents high-income customers with moderate product reviews, indicating potentially high-value customers.
- **Cluster 2**: Customers in this segment have a broad range of incomes and fewer product reviews. They could be less engaged or newer customers.
- **Cluster 3**: This group has high annual incomes and lower product reviews, suggesting customers who may be less engaged with product reviews despite high spending.

This segmentation allows us to tailor marketing strategies and product offerings based on customer profiles.

### Location Insights

We analyzed the average product reviews by location to understand how customer satisfaction varies across different regions.

![Average Product Reviews by Location](images/avg_product_reviews_by_location.png)

**Interpretation**:
- **Location A**: Shows the highest average product reviews, indicating a region with highly satisfied customers. Marketing efforts and product focus could be intensified here.
- **Location B**: Has moderate average reviews, suggesting that while customer satisfaction is decent, there may be room for improvement.
- **Location C**: Exhibits lower average reviews, which could signal issues with customer satisfaction or product quality in this area. Investigating further could help address these issues and improve customer experience.

By focusing on these insights, businesses can prioritize regions with higher customer satisfaction and address concerns in areas with lower reviews to enhance overall customer experience.

# Contributing
Contributions are welcome! If you have suggestions or improvements, please open an issue or submit a pull request.

# License
This project is licensed under the MIT License. See the LICENSE file for details.

## Contact
If you have any questions, please feel free to contact me at mgsite94@gmail.com
