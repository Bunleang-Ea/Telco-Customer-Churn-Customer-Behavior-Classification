# Telco-Customer-Churn-Customer-Behavior-Classification
### Dataset: [Telco Customer Churn](https://www.kaggle.com/datasets/blastchar/telco-customer-churn).

### Dataset Overview:
Each row represents a customer, each column contains customer’s attributes described on the column Metadata.

### The data set includes information about:

- Customers who left within the last month – the column is called Churn
- Services that each customer has signed up for – phone, multiple lines, internet, online security, online backup, device protection, tech support, and streaming TV and movies
- Customer account information – how long they’ve been a customer, contract, payment method, paperless billing, monthly charges, and total charges
- Demographic info about customers – gender, age range, and if they have partners and dependents

### Goal:
- Classifying customer behavior to find solutions that can reduce customer churn

### Dataset Size
| Item | Value |
| :--- | :--- |
| Rows | 7043 |
| Columns | 21 |

# Analying Data
### Initial Exploration (Light EDA)
### Dataset Inspection

**Include:**
- missing values
- data types
- duplicates
- basic observations

**Discoveries**
- **Missing values**: Initially, 11 missing values were identified in the TotalCharges column. 
- **Data Types**: The TotalCharges column was incorrectly identified as 'object' type; all other columns had appropriate data types for their content.
- **Duplicates**: No duplicate rows were found in the dataset.
- **Basic Observations**: The dataset contains a mix of **numerical** (SeniorCitizen, tenure, MonthlyCharges) and **categorical** (gender, Partner, Dependents, PhoneService, etc.) features. Each row represents a unique customer.

### Data Cleaning
| Problem | Method | Justification |
| :--- | :--- | :--- |
| Missing numeric value | Replaced NaN in TotalCharges with 0 | These NaN’s corresponded to new customers with a tenure of 0, indicating they had not yet accumulated charges |
| Incorrect data type | Converted TotalCharges from 'object' to 'float64' | TotalCharges represents a numerical value, and an 'object' type prevents proper numerical analysis |
| Duplicates | No action required | A check for duplicate rows found 0 duplicates |

### Deeper Exploratory Data Analysis
- Examine the correlation between numerical variables to understand linear relationships. A heatmap is an excellent way to visualize this.
<img width="689" height="190" alt="image" src="https://github.com/user-attachments/assets/86647935-69f8-436b-82bf-fa88e41b4cc0" />

**+ Findings**:
- There is a very strong positive correlation (approximately 0.82) between tenure and TotalCharges. This makes intuitive sense, as customers who have been with the service longer (tenure) would naturally accumulate higher TotalCharges.
- There is also a moderate positive correlation between MonthlyCharges and TotalCharges. This also aligns with expectations, as higher monthly charges would contribute to higher total charges over time, though perhaps not as strongly as tenure alone.

### Data Visualization & Insights
**- Histogram**

<img width="859" height="547" alt="image" src="https://github.com/user-attachments/assets/fc48bcf4-0ba1-485a-84e8-331f80ff9801" />

- **Observation:** The monthly charges show a wide distribution. There's a noticeable peak at the lower end (around 20), suggesting a large segment of customers with lower cost services. Another group of customers is observed at higher charges (around 70-90), possibly indicating customers with more expensive services.

**- Correlation Heatmap**

<img width="904" height="836" alt="image" src="https://github.com/user-attachments/assets/72320721-9dcb-4160-b262-f10098ebec71" />

- **Observation:** The heatmap highlights a very strong positive correlation (approximately 0.82) between `tenure` and `TotalCharges`. There is also a moderate positive correlation between `MonthlyCharges` and `TotalCharges`.

**- Box Plot**

<img width="686" height="547" alt="image" src="https://github.com/user-attachments/assets/1a1ec1ad-6eda-483f-8fba-819315b67913" />

- **Observation:** The box plot can clearly shows the differences in churn between tenure and customer churn. The median tenure for customers who churned ("Yes") is much lower than those who did not churn ("No"). Furthermore, the entire "box" for the churned group is grouped at the lower end of the y-axis.

**- Bar Chart**

<img width="841" height="593" alt="image" src="https://github.com/user-attachments/assets/92ed0f33-cb80-4b94-a077-8e232c06b5eb" />

- **Observation:** The bar chart reveals a stark contrast in churn rates based on how customers pay their bills. Customers using "Electronic check" have a remarkably high churn rate of over 45%. In contrast, customers using automatic payment methods (Credit Card and Bank Transfer) have a much lower churn rate of around 15-16%.

### Outlier Analysis
- From our outlier investigation for numerical features like MonthlyCharges and TotalCharges was considered, no severe outliers were identified

# Insights
### Insight 1:

*   **Observation**: The bar chart clearly shows that customers using "Electronic check" have a higher churn rate compared to all other payment methods, reaching nearly 45%.

*   **Reasoning**: Unlike automatic methods like Credit Cards or Bank Transfers, Electronic Checks require manual monthly action. Where the customer must consciously decide to pay their bill every month, making it easier for them to cancel the service.

*   **Implication**: To reduce churn, the company should offer like a small monthly discount to encourage Electronic Check users to switch to automatic payment methods.

### Insight 2:

*   **Observation**: The boxplot shows that the median tenure for customers who churned ("Yes") is much lower than those who stayed. Most churned customers are concentrated at the very bottom of the tenure scale.

*   **Reasoning**: This indicates that the first few months are the most critical period for customer retention. If a customer is not satisfied early on, they leave before becoming "loyal" or long-term users.

*   **Implication**: The company can do follow-up calls or "new customer" guides, should be focused heavily on the first 6–12 months of the customer’s lifecycle to ensure they pass this high-risk period

### Insight 3:

*   **Observation**: The histogram of monthly charges shows two peaks: one big group at around 20 dollars and another wider group around 70 - 100 dollars. Which divides them in 2 groups price sensitive and service sensitive.

*   **Reasoning**: The data reveals that the company does not have a "typical" average customer. Instead, there are two separate segments: budget-conscious users with basic services and premium users with high-speed internet and add-on services.

*   **Implication**: They must try to do something to retain customers that are price sensitive and service sensitive.

---

