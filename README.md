<div align="center">

# 🍕 Dominos - Predictive Purchase Order System

</div>

<div align="center">

[![](https://img.shields.io/badge/Python-FFD43B?style=for-the-badge&logo=python&logoColor=darkgreen)](https://www.python.org)
[![](https://img.shields.io/badge/scikit_learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/stable/)
[![](https://img.shields.io/badge/Numpy-777BB4?style=for-the-badge&logo=numpy&logoColor=white)](https://numpy.org)
[![](https://img.shields.io/badge/Pandas-2C2D72?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org)
[![](https://img.shields.io/badge/Plotly-239120?style=for-the-badge&logo=plotly&logoColor=white)](https://plotly.com)
[![](https://img.shields.io/badge/Machine%20Learning-FF6F00?style=for-the-badge&logo=google-cloud&logoColor=white)](https://www.google.com/)

</div>

<div align="center">
  
  <img src="https://github.com/user-attachments/assets/9bbc3acc-86f2-4e9e-9dbd-d5399264440e" width="800"/>
  
</div>

## 📈 Problem Statement

This project focuses on optimizing Domino's inventory management by building a predictive system that forecasts pizza sales and generates purchase orders for ingredients. By leveraging historical sales data, the goal is to develop a model that accurately predicts future sales, allowing Domino's to order the right amount of ingredients, minimizing waste, and preventing stockouts.

---

## 🎯 Objective:

- To Develop a predictive model to forecast pizza sales.
- To Create a purchase order system that calculates the required quantities of ingredients based on the sales forecast.
  
---

## 🔍 Dataset Overview

The project involves two datasets: **Pizza Sales** and **Pizza Ingredients**. 

- The **Pizza Sales Dataset** comprises 48,620 entries, each detailing an individual sale. This includes information such as `pizza_id` (a unique identifier for the sale), `order_id` (linking to a specific order), `pizza_name_id` (a unique identifier for each pizza), `quantity` (number of pizzas sold), `order_date` and `order_time` (when the sale occurred), `unit_price` and `total_price` (pricing details), as well as `pizza_size` and `pizza_category` (size and type of pizza). This dataset offers a thorough view of sales, covering pricing, timing, and pizza characteristics. 

- The **Pizza Ingredients Dataset** consists of 518 entries that describe the ingredients for various pizzas. It includes `pizza_name_id` (a unique identifier for each pizza), `pizza_name` (name of the pizza), `pizza_ingredients` (list of ingredients), and `Items_Qty_In_Grams` (the quantity of each ingredient used). This dataset provides detailed insights into the composition of each pizza and the amounts of ingredients required.

You can download the datasets from the following links:

[Download pizza_sales Dataset](https://docs.google.com/spreadsheets/d/1gB2O_G9G_ym41h-Wra3k4VDHHYVONh3jfkEBLzAOuUI/edit?usp=sharing)

[Download pizza_ingredients Dataset](https://docs.google.com/spreadsheets/d/13h0bdBCgcnf7kduth_5ci1pMytzXc02H57Ms30Xg5AA/edit?usp=drivesdk)

---

## 📊 Metrics

- [__Mean Absolute Percentage Error__](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.mean_absolute_percentage_error.html): Used to evaluate the accuracy of forecasting models. It measures the average absolute percentage error between the predicted values and the actual values. 

---

## 💡 Business Use Cases

- **Inventory Management**: Ensuring optimal stock levels to meet future demand without overstocking.
- **Cost Reduction**: Minimizing waste and reducing costs associated with expired or excess inventory.
- **Sales Forecasting**: Accurately predicting sales trends to inform business strategies and promotions.
- **Supply Chain Optimization**: Streamlining the ordering process to align with predicted sales and avoid disruptions.

---

## 🛠️ Approach

### I. Data Preprocessing 

**Data Cleaning** ensures the dataset's accuracy and consistency through:

- **Handling Missing Data**:
  - Detected missing values.
  - Replaced missing values using mean, median, mode, or placeholders.
  - Removed columns or rows with excessive missing data if necessary.

- **Removing Inconsistent Data**:
  - Checked for format consistency and valid ranges.
  - Fixed inconsistencies, such as standardizing text and correcting typos.

- **Handling Outliers**:
  - Identified outliers using statistical methods or visualizations.
  - Removed, transformed, or categorized outliers based on their impact.

### II. Exploratory Data Analysis (EDA)

**Exploratory Data Analysis (EDA)** discovers patterns, relationships, and anomalies in the data.

### i) Top-Selling Pizzas
- This visualization highlights the top 10 most popular pizzas based on total sales.
- It helps identify which pizzas are in highest demand among customers.
- The y-axis represents different pizza names, while the x-axis shows the quantity sold.

<div align="center">
  
![image](https://github.com/user-attachments/assets/3784b3a0-6a0e-4efb-9c7f-1de290136ae2)

</div>

#### ii) Distribution of Pizza Categories:
- This visualization displays the distribution of pizza orders across various categories (e.g., vegetarian, meat-lovers).
- It provides insights into customer preferences and trends by category.
- The y-axis represents different pizza categories, while the x-axis shows the number of orders for each category.
   
<div align="center">

![image](https://github.com/user-attachments/assets/795e0473-d3ec-40d0-8827-d7f60f029db6)

</div>

#### iii) Sales Trends Over Time:
- This visualization shows daily pizza sales over time by converting the order_date column into a datetime format.
- It helps identify trends, seasonality, and sales spikes throughout the observed period.
- The line plot illustrates the quantity of pizzas sold each day.

<div align="center">

![image](https://github.com/user-attachments/assets/673e6de1-c273-4176-87a0-96c472e5adae)

</div>

#### iv) Sales by Day of the Week
- This visualization aggregates total sales by day of the week to identify which days generate the most revenue.
- The data is grouped by day_of_week, summing the total_price for each day.
- The x-axis represents the days of the week (ordered from Monday to Sunday), while the y-axis shows the total sales for each day.
- The bar plot helps pinpoint trends in customer purchasing behavior throughout the week.

<div align="center">

![image](https://github.com/user-attachments/assets/f93f5b5d-9ba1-4714-9f46-32f79fd46754)

</div>

### III. Sales Prediction

Sales Prediction involves **Time Series Forecasting**, a technique used to predict future values based on historical data collected over time. The process includes the following steps:

#### i) Feature Engineering

Created new variables from the raw sales data to improve the model’s performance, such as:

- **Day of the Week**: Extracted the day of the week from the sales date to capture weekly variations.
- **Month**: Extracted the month from the sales date to account for monthly trends and seasonal patterns.
- **Holiday Effects**: Identified and included features for holidays or special events that can impact sales patterns.

#### ii) Model Selection

Model Selection involves choosing the most suitable forecasting model for our sales data:

- [__ARIMA (AutoRegressive Integrated Moving Average)__](https://www.statsmodels.org/stable/generated/statsmodels.tsa.arima.model.ARIMA.html): Captures trends and autocorrelations in non-seasonal data.
- [__SARIMA (Seasonal ARIMA)__](https://www.statsmodels.org/stable/generated/statsmodels.tsa.statespace.sarimax.SARIMAX.html): Extends ARIMA to handle seasonality.

#### iii) Model Training

Model Training involves fitting the chosen model to historical sales data:

- Split the data into training and test sets to evaluate model performance. 
- Trained the model on the training set by adjusting parameters to minimize prediction errors.
- Optimized model performance by tuning hyperparameters using techniques like cross-validation or grid search.

### iv) 📊 Model Evaluation

### Pizza Sales by Week

- This process begins by aggregating pizza sales on a weekly basis, converting the `order_date` to a datetime format for accurate grouping.
- The data is then split into training (80%) and testing (20%) sets to prepare for model evaluation.
- The Mean Absolute Percentage Error (MAPE) function is defined to assess model performance by comparing actual and predicted values.

#### ARIMA Model Tuning

- The ARIMA model is tuned using a grid search over specified values of p, d, and q parameters to find the optimal configuration.
- The model forecasts sales for the test set, and the best MAPE score and corresponding parameters are printed.
- The predicted values are formatted for display, allowing for easy comparison with actual sales.
- Finally, a line plot visualizes the actual vs. predicted weekly sales, helping to evaluate the ARIMA model's forecasting performance.

![image](https://github.com/user-attachments/assets/18f86ad0-f5a1-4fff-a851-27419f3b85c9)

#### Best SARIMA Model Training and Output

- The SARIMA model is trained with orders (1, 1, 1) for ARIMA and seasonal components.
- It forecasts sales for the test set, calculating the Mean Absolute Percentage Error (MAPE) for accuracy assessment.
- The best MAPE score is printed to evaluate model performance.
- Predictions are formatted for easy comparison with actual sales.
- A line plot visualizes actual vs. predicted weekly sales, aiding in performance evaluation.

![image](https://github.com/user-attachments/assets/73035ada-e18e-4d73-ad23-38345ae8be0b)

#### Prophet Model Forecasting
- The order_date column is converted to datetime format and renamed to 'ds' for dates and 'y' for target values.
- The Prophet model is fitted to the prepared data, with US country holidays included for enhanced accuracy.
- Future dates for the next 7 days are generated to predict sales.
- The forecast results are displayed using Prophet's built-in plotting functionality.

![image](https://github.com/user-attachments/assets/6bd8ea58-d141-4980-92ea-355b937b73ee)

![image](https://github.com/user-attachments/assets/d0b25630-b219-43f9-9c64-2009400e8244)

#### Regression Model
- Data Preparation: Converts order_date to datetime and aggregates weekly sales.
- Feature Engineering: Creates features: week of the year, day of the week, month, and year.
- Train-Test Split: Divides data into 80% training and 20% testing sets.
- Model Training: Trains a linear regression model on the training set.
- Model Evaluation: Calculates and prints MAPE for accuracy assessment.
- Visualization: Plots actual vs. predicted weekly sales for performance evaluation.

![image](https://github.com/user-attachments/assets/10c08dd4-72b1-4847-ba5a-52154b028d33)

#### LSTM Model for Weekly Sales
- Weekly sales data is aggregated and split into training (80%) and test sets, then normalized using MinMaxScaler.
- Sequences are created for LSTM input, and an LSTM model is trained to predict sales.
- The Mean Absolute Percentage Error (MAPE) is calculated to evaluate the model's accuracy.
- A plot compares actual vs. predicted weekly sales, assessing the LSTM model's performance.

![image](https://github.com/user-attachments/assets/bcbd5b62-4e5f-42c4-b010-6ec2a0d41537)

---

### 🧩 Model Comparison: MAPE Scores
Performance Overview: The table below summarizes the Mean Absolute Percentage Error (MAPE) scores of different forecasting models, highlighting their ranking and performance.

| Model      | MAPE   | Rank | Best/Worst |
|------------|--------|------|------------|
| SARIMA     | 0.1849 | 1    | Best       |
| ARIMA      | 0.1896 | 2    |            |
| Regression | 0.1911 | 3    |            |
| Prophet    | 0.1962 | 4    |            |
| LSTM       | 0.2404 | 5    | Worst      |

### Scores Visualization
- Generated bar charts to compare MAPE scores across different models for quick performance assessment.

![image](https://github.com/user-attachments/assets/941d9b80-1928-4a9a-a3f3-754412cd2a4a)

## Conclusion
The SARIMA model outperformed other models, providing the most accurate sales predictions, while LSTM yielded the least accurate results. This project lays the groundwork for improving inventory management through data-driven forecasting techniques.

### SARIMA Model Forecasting

This section demonstrates how to load the best-performing SARIMA model and use it to forecast future sales.

1. **Model Loading**: The SARIMA model, previously trained and saved as `best_sarima_model.pkl`, is loaded for use in forecasting.

2. **Forecasting**: The model predicts sales for the next 7 days (`n_forecast = 7`).

3. **Visualization**: A plot is generated to compare the training data with the forecasted sales, clearly illustrating expected future sales trends. The forecast is displayed in orange, while the training data is shown in blue.

![image](https://github.com/user-attachments/assets/c01708ef-253f-4e54-b447-5c77e2131604)

### Predicted Ingredient Quantities

This section calculates the total quantity of ingredients needed based on predicted pizza sales for the upcoming week.

- 1. Mapping Predicted Sales: The Ingredients_dataset maps predicted sales to corresponding ingredients from the next_week_pizza_sales_forecasts_arima.

- 2. Calculating Total Quantity: The total quantity for each ingredient is computed by multiplying the grams needed per item (Items_Qty_In_Grams) by the predicted quantity of pizzas sold.

- 3. Summarizing Totals: The summed total quantities for each ingredient are displayed as a dictionary, giving a clear overview of the ingredient requirements for the upcoming week.

- 4. Visualizing Quantities: A bar chart visualizes the top 10 predicted ingredients, illustrating the total quantity (in grams) needed for the next week.

- 5. Saving Results: The ingredient totals are saved to a CSV file, predicted_ingredient_totals.csv, for future reference and easy sharing.

<img width="721" alt="image" src="https://github.com/user-attachments/assets/1466b107-19ba-4bf8-9bbc-81182677558a">

![image](https://github.com/user-attachments/assets/a0e9ca84-4235-4eb9-b804-18733b654d96)

<img width="276" alt="image" src="https://github.com/user-attachments/assets/f1975c39-bf2e-42d9-9b90-15e006ae4deb">

---

## 🏆 Results

The project delivers highly accurate pizza sales forecasts, providing precise predictions for the upcoming week. These forecasts enable better planning and optimized inventory management. Based on the predicted sales, a comprehensive purchase order is generated, detailing the exact quantities of each ingredient required. This ensures that the necessary ingredients are stocked efficiently, minimizing waste and avoiding shortages. The result supports seamless operations by aligning supply with demand, improving both supply chain efficiency and overall business performance.

---

Clone the project:

```bash
git clone https://github.com/kadarmeeran465/dominos-predictive-purchase-order-system.git
```

Install dependencies:
```bash
pip install pandas, numpy, scikit-learn, statsmodels, fbprophet, seaborn, matplotlib
```
---
## 🔗 Links

[![LinkedIn](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/kadar-meeran465)
[![Gmail](https://img.shields.io/badge/gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:kadarmeeran465@gmail.com)
