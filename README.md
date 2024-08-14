# walmart-weekly-sales-prediction-forecasting
**Problem Statement:**

A retail store that has multiple outlets across the country are facing issues in managing the inventory - to match the demand with respect to supply. You are a data scientist, who has to come up with useful insights using the data and make prediction models to forecast the sales for X number of months/years.

**Project Objective:**

The objective of this project is to build a model which predicts sales of the stores for the next 12 weeks. As in dataset, size and time related data are given as feature, so analyze if sales are impacted by time-based factors and space- based factor and the presence of holidays within a week can significantly elevate in-store sales.

**Data Description:**

The data contains historical sales data for 45 Walmart stores located in different regions.

Store — the store number

Date — the week

Weekly_Sales — sales for the given store in that week

Holiday_Flag — whether the week is a special holiday week

Temperature — average temperature in the region that week

Fuel_Price — cost of fuel in the region

CPI — the consumer price index

Unemployment — the unemployment rate

There are certain events and holidays which impact sales on each day.

For convenience, the four holidays fall within the following weeks in the dataset (not all holidays are in the data):

Super Bowl: 12-Feb-10, 11-Feb-11, 10-Feb-12, 8-Feb-13

Labor Day: 10-Sep-10, 9-Sep-11, 7-Sep-12, 6-Sep-13

Thanksgiving: 26-Nov-10, 25-Nov-11, 23-Nov-12, 29-Nov-13

Christmas: 31-Dec-10, 30-Dec-11, 28-Dec-12, 27-Dec-13

The walmart.csv contains 6435 rows and 8 columns.

**Data Pre-processing Steps and Inspiration:**

The Pre-processing of the data includes the following steps:

1. Data Cleaning: Cleaning the data by removing missing values, outliers and other inconsistencies.
2. Data Exploration: Exploring the data to gain insights and understanding the data.
3. Data Visualization: Visualizing the data for better understanding

**Handling Missing Values**

Walmart dataset consisting of 6435 rows and 8 columns, which has the target column Weekly_Sales. we could say the dataset is quite clean, where there are no missing values and duplicate values.

The Holiday_Flag column is containing discrete values (0 or 1)

**Outlier Detection**

![image](https://github.com/user-attachments/assets/973d0dd6-9796-4774-a2b6-67d79bf51d70)

Outlier detection will be exclusively focused on numerical columns (integer data type) excluding 'holiday_flag' and 'date.' Target variables are also typically excluded from outlier analysis.

Analysis of correlation coefficients values indicates that outliers in both the 'Temperature' and 'Unemployment' columns may have a limited influence on weekly sales figures.

This suggests that the removal of outliers may not be necessary for the current investigation.

**Data Exploration and Data Visualization**
![image](https://github.com/user-attachments/assets/434adbf7-8310-4f45-96dd-189936d210c8)

**Holiday_flag**
![image](https://github.com/user-attachments/assets/020cb0a4-0bd1-481c-886e-5830d4047fd8)

![image](https://github.com/user-attachments/assets/a3712490-9f59-4593-b135-87ef7a6e3fbf)

An analysis of visual inspection of the plot between average sales and the holiday flag suggest a potential increase in sales during holiday weeks.

**Unemployment Column**
![image](https://github.com/user-attachments/assets/3f299185-4ea3-4dfe-8008-4701b8aa98f1)

The outliers in the Unemployment column are almost 500 rows. Apparently, the low unemployment rate occurred in 2012, while the high one occurred throughout the year.

![image](https://github.com/user-attachments/assets/28f0a6cd-480b-4efe-846e-a47e4b8e305c)

from 'Unemployment rate vs Store',

- it is visible that the store which has maximum average Unemployment rate is store number 12, 28, 38 and
- it is visible that the store which has minimum average Unemployment rate is store number 23,40

from ‘Average Weekly sales vs store'

- it is visible that the store which has maximum average weekly sales is store number 4,20 and
- it is visible that the store which has minimum average weekly sales is store number 5,33,36,38,44


![image](https://github.com/user-attachments/assets/afa35dbe-e7ba-438f-a784-4bb948562f45)

**_From Correlation this with Store_**

- store no. 38,44 has Strong negative correlation
- store no. 36 has Strong positive correlation

**Store 38:** -0.785290 (Strong negative correlation) - This store's weekly sales are negatively affected by the unemployment rate. As unemployment rate increases, weekly sales tend to decrease significantly. This store likely caters to a population that is more likely to be unemployed, or its products are considered non-essential during economic downturns.

**Store 45:** -0.0004041 (Very weak negative correlation) - There is almost no relationship between unemployment rate and weekly sales for this store. Changes in unemployment rate have little to no impact on sales. This store might sell essential goods or services that are not affected by economic fluctuations.

**Store 34:** 0.017010 (Weak positive correlation) - There is a slight positive relationship between unemployment rate and weekly sales for this store. As unemployment rate increases, weekly sales also tend to increase slightly. This could be due to several reasons, such as the store offering affordable products that people turn to during tough economic times, or it catering to a specific demographic that benefits from government unemployment assistance programs.

**Store 36:** 0.833734 (Strong positive correlation) - This store's weekly sales are positively affected by the unemployment rate. As unemployment rate increases, weekly sales tend to decrease significantly, suggesting other factors might be driving sales in this store.This store likely caters to a population that is less likely to be unemployed, or its products are seen as luxury items that people indulge in during economic downturns.

**In conclusion:**

Store 38 is most affected by the unemployment rate, with its weekly sales significantly decreasing as unemployment rises.

Store 44 shows an unusual positive correlation, where sales decrease with rising unemployment, suggesting other factors might be driving sales in this store.

**_from There plot we can see unemployment rate low, sales also low and correlation also low in store number.38_**

**Seasonal trend in weekly sales**

![image](https://github.com/user-attachments/assets/ad4b3fe5-6b4b-4824-bd6e-6efd4aee9f40)

1. We can see that in month of November and December weekly sales are going very high which means that maybe holidays that are in November and December are creating a huge impact on weekly sales
2. There is slight dip in sales in last December and start of January also
3. There is a seasonality in plot of weekly sales over the period of time which can be easily seen by plot
4. Average weekly sales are fluctuating around 4.5\*10^7

**Temperature column**

There are outliers in the Temperature column as many as 3 rows. Our assumption is that winter starts in early December and ends at the end of February 2011. So, these outliers can be considered reasonable. Therefore, we will leave this outlier.

**Temperature effects on the weekly sales**
![image](https://github.com/user-attachments/assets/62756dbf-4820-40f3-8299-28147bd9cc51)

1. Weekly sales have gone high after temperature 40 and are highest in range of 60-80
2. There is a seasonal trend in the temperature all over the dataset
3. Temperature is going high in June July of every year and becoming low in November, December

**CPI, Consumer Price index effect on the weekly sales**
![image](https://github.com/user-attachments/assets/59ee5ac9-59df-45cf-8ddd-82cab5a1ab67)

1. The Consumer Price Index (CPI) typically exhibits an upward trend year-over-year.
2. Analysis of correlation coefficients suggests that CPI may not have a significant impact on weekly sales.

**Fuel Price effect on weekly sales**
![image](https://github.com/user-attachments/assets/45a53185-fa45-4cdb-9b5a-f73e748c9698)

![image](https://github.com/user-attachments/assets/9bb7169c-ef7d-41c3-a137-79a98ab05202)

1. Analysis of the seasonality plot reveals the fuel price exhibits a noticeable increase in price after September 10th, 2010.
2. The 'Weekly Sales vs. Fuel Price' plot indicates an inverse relationship between these variables. When fuel prices greater then 3.922, weekly sales tend to be lower. Conversely, when fuel prices less than 3.922, weekly sales remain relatively stable.
3. Furthermore, the data indicates that the highest weekly sales occur when the fuel price is around 3.638, with a corresponding weekly sales value of approximately 38803767.47. and the lowest weekly sales occur when the fuel price is around 3.392, with a corresponding weekly sales value of approximately 279643.43.
4. The provided information, along with the established weak correlation between fuel prices and weekly sales, suggests that fluctuations in fuel prices may not have a significant impact on weekly sales figures.

_From graphs, it is seen that there are no significant patterns between CPI, temperature, unemployment rate, fuel price vs weekly sales. There is no data for CPI between 140-180 also._

**_Top performing stores according to the historical data._**

![image](https://github.com/user-attachments/assets/97dae698-65d1-4d6a-a704-b091ccec10a2)

- Weekly Sales was high for store number 20 its 301397792.46
- Weekly Sales was low for store number 33 its 37160221.96

**The worst performing store, and how significant is the difference between the highest and lowest performing stores.**

- Worst performing store: 33 with total sales of $37160221.96
- Best performing store: 20 with total sales of $301397792.46
- Percentage difference: 87.67%

**Choosing the Algorithm for the Project**

When it comes to machine learning, picking the right tool for the job is key. For tasks like sorting things into groups (classification) or predicting values (regression), supervised learning algorithms like Random Forests, Support Vector Machines, and k-Nearest Neighbours are common choices. Unsupervised learning tackles different challenges, like finding hidden structures in data (clustering) or reducing complexity (dimensionality reduction).

But what if you're looking to predict future trends? That's where time series analysis comes in. This is a specialized area of machine learning that deals with data points ordered in time, like stock prices or weather patterns. Here, algorithms like ARIMA, SARIMAX, Prophet, and LSTMs shine. They can learn from past patterns to make educated guesses about what might happen next.

**Feature Selection:**
![image](https://github.com/user-attachments/assets/38db88f4-7997-4987-9fc5-e8f6ab02668f)


Linear Regression ![image](https://github.com/user-attachments/assets/e863ce7e-0bfc-424b-bb0f-7bfa2ee4bbe5)


Decision Tree Regression ![image](https://github.com/user-attachments/assets/e07e6972-fd3c-4070-87f1-d767f93f6cfe)


Random Forest Regression ![image](https://github.com/user-attachments/assets/15dda3fb-3629-4037-a9d8-58540678b4b5)


KNN Regression ![image](https://github.com/user-attachments/assets/276f83ae-db76-4529-88dc-c34f2b9cf9b7)


XG Boost Regression ![image](https://github.com/user-attachments/assets/2887b5fb-eff5-4aed-b43c-2e1b500a7af5)


**ARIMA (Autoregressive Integrated Moving Average)**

ARIMA is a versatile model that can capture trends and short-term dependencies in data.

It works by considering two factors:

1. Autoregressive (AR): The influence of past values on the current value.
2. Moving Average (MA): The effect of past forecast errors on the current value.
3. ARIMA models are denoted by three parameters (p, d, q):
4. p: The number of past values it considers (AR terms).
5. d: The number of times the data needs to be differenced to make it stationary (remove trends).
6. q: The number of past forecast errors it considers (MA terms).

**SARIMA (Seasonal ARIMA)**

SARIMA is an extension of ARIMA that specifically addresses seasonality in data.

1. Seasonality refers to recurring patterns within a specific time period, like monthly sales figures or daily traffic patterns.
2. SARIMA incorporates additional parameters to account for these seasonal effects.
3. It's denoted by (p, d, q) x (P, D, Q, s) where:
4. (p, d, q) are the same ARIMA parameters.
5. (P, D, Q) are the seasonal parameters with similar meaning to (p, d, q) but applied to the seasonal lags.
6. s is the number of observations in each season (e.g., 12 for months).

**Choosing the right model:**

Use ARIMA if your data has no significant seasonal patterns.

Use SARIMA if your data exhibits seasonality and you want to improve your forecasts.

**_In essence:_**

ARIMA is for general time series forecasting.

SARIMA is for time series forecasting with seasonal patterns.

**Trend of Weekly sale for store no. 1**
![image](https://github.com/user-attachments/assets/69c34154-6869-4aa8-99b1-0bc454421fe4)


**Next Steps for all Stores**

- Forecast the sales for each store for the next 12 weeks.
- forecast the sales for all stores together create code with loop
- check trend seasonality and residues for all stores
- compare the 2012 data of all stores
- prove whether the data is stationary or not
- Split the data for training and Testing
- Determining Optimal ARIMA Hyperparameters (PDQ) for Multiple Stores Using AIC
- Model building – Arima for all stores
- Model building - Sarimax for all stores

**Forecast Weekly sales for Store No.**
![image](https://github.com/user-attachments/assets/1ded04f9-c6ba-47d4-9596-937a08dd060c)


**Prove Whether the Data Is Stationary or Not**

**p values are less than 0.05, data is stationary**

Stationary Series:

y1, y2, y3, y4, y5, y6, y7, y8, y9, y10, y11, y12, y13, y15, y16, y17, y18, y19, y20, y21, y22, y23, y24, y25, y26, y27, y28, y29, y31, y32, y33, y34, y35, y37, y39, y40, y41, y45

**_p values are more than 0.05, data is non stationary_**

Non-stationary Series:

y14, y30, y36, y38, y42, y43, y44

Observations of above all plots we can see this below mentions data not have predicated optimal forecasting results

**Non-stationary Series data: y14, y30, y36, y38, y42, y43, y44**

**some problems in this series data: y8, y23, y31, y35, y37, y40**

                  Rolling Mean Technique for Non-Stationary Data
![image](https://github.com/user-attachments/assets/ccfdcd11-282b-4672-9d75-3b41be551fe3)

![image](https://github.com/user-attachments/assets/11e5113e-44d5-44a8-9d6a-9e1e00c18540)

![image](https://github.com/user-attachments/assets/fdd21e01-a6ae-4864-b69e-0b8ea81d47b2)


               Sarimax Prediction weekly sales for Store No. 36
![image](https://github.com/user-attachments/assets/940ba86c-e405-4984-807d-632bd81b1361)




              Forecast Weekly sales for next 12 week for store no.36

![image](https://github.com/user-attachments/assets/a7bc8d22-bcca-45ef-a279-cdadd470c504)



**Motivation and Reasons for Choosing the Algorithm:**

While Linear Regression and KNN models didn't perform well for this dataset, Random Forest, Decision Tree, and XGBoost all showed promising results. Its ability to handle complex, non-linear relationships makes it perfect for Walmart's vast amount of data. Furthermore, XGBoost excels at large-scale tasks, meaning it can efficiently analyse Walmart's data to generate highly accurate predictions. Finally, XGBoost's ease of use ensures swift implementation. Leveraging historical trends, machine learning shines in sales forecasting for individual stores. The time series analysis indicates that the forecasting model effectively captures the underlying trends present in the historical data. While predictions exhibit some deviations, their general trajectory aligns with past patterns. The model's accuracy can be assessed using various metrics, ensuring its effectiveness.

Model Selection:

- SIRMAX allows for incorporating seasonal factors into ARIMA models. When fitting different SIRMAX models with varying seasonal parameters, AIC helps identify the model that best balances complexity (number of parameters) and goodness-of-fit.
- The model with the lowest AIC is generally preferred as it captures the data's underlying trends and seasonality effectively without introducing unnecessary complexity.
- Lower AIC: Indicates a better balance between capturing the data's patterns and keeping the model parsimonious (not overly complex).
- Note: While AIC is a valuable tool, it's not the only criterion for model selection. Other factors like interpretability of the model and forecast accuracy on hold-out data should also be considered.

**Assumptions**

While machine learning offers a powerful tool for sales forecasting, its efficacy in predicting sales for individual stores over a 12-week horizon hinges on the availability of comprehensive data. These algorithms rely on historical sales figures, customer demographics, store location, and potentially other relevant factors to identify patterns and trends. The absence of such data would render accurate sales forecasts for each store over a 12-week period unachievable.

**Model Evaluation and Techniques**

This project can benefit greatly from the incorporation of time series forecasting techniques, specifically SARIMAX models. SARIMAX models excel at analysing time-series data, uncovering trends, seasonality, and patterns that are crucial for accurate sales forecasting. By incorporating historical sales data alongside customer and store details, we can forecast sales for the next twelve weeks with improved accuracy. Time series forecasting has far-reaching applications, from predicting website traffic and customer demand to weather patterns and stock market fluctuations. As a cornerstone of machine learning, its growing adoption across industries highlights its significance. For aspiring data scientists, mastering time series forecasting equips them with a valuable skillset for tackling a multitude of real-world problems.  
<br/>**Model Evaluation:**  
Root Mean Squared Error (RMSE)

Akaike Information Criterion (AIC)  
Residual Analysis: Evaluating SARIMA Model Fit

**Inferences from the Same**

By analysing past sales data, Walmart can uncover hidden patterns and trends. This allows them to predict future sales for each store with surprising accuracy. It's like having a sixth sense for what customers will buy. But it doesn't stop there. Machine learning can also identify what makes sales tick. Weather, seasons, and even customer profiles - all these factors can be factored in to refine sales forecasts. The result? More accurate predictions, leading to smarter business decisions for Walmart.

**Future Possibilities of the Project**

Machine learning takes the steering wheel for sales forecasting at Walmart stores. Powerful algorithms, like regression and decision trees, analyse years of sales data. They factor in everything from past purchases to who your customers are. The result? Spooky-accurate sales predictions for each location. This isn't just about numbers. These insights empower smarter decisions on inventory, pricing, and how you reach your customers. It's like having a roadmap to growth, highlighting trends and opportunities waiting to be seized.

**Future Improvements:**

- enhance the forecasting model's accuracy, several refinements will be implemented.
- Data standardization techniques will be employed to ensure consistent patterns.
- Feature engineering and selection will be further optimized to identify the most impactful variables.
- Additionally, data encompassing a wider range of holidays, such as Easter, Halloween, and back-to-school periods, will be integrated to capture their influence on sales.
- Furthermore, the model's sensitivity to markdown events will be improved by incorporating departmental sales data.
- The possibility of developing specialized models for unique store types or departments will also be explored.
- Finally, market basket analysis may be conducted to identify high-demand items within specific departments, potentially informing future inventory management strategies.

**Conclusion:**

"The time series analysis indicates that the forecasting model effectively captures the underlying trends present in the historical data. While predictions exhibit some deviations, their general trajectory aligns with past patterns."

**References:**

**GitHub repository:** As outlined in a GitHub repository on EDA.

**Medium article:** As discussed in a Medium article about K-mean Clustering techniques.

**Kaggle Dataset:** As discussed in a Kaggle dataset on Online Retail.
