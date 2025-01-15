# What Drives the Price of a Car?

## Business understanding:
The business problem revolves around predicting the price of used vehicles based on various attributes such as their age, mileage (odometer readings), engine size (cylinders), manufacturer, condition, and other relevant features.

### Notebook path: 
https://github.com/shikhakala/Practical_Application_2/blob/main/Shikha_Practical_Application2.ipynb

## Key insights and findings:
https://github.com/shikhakala/Practical_Application_2/blob/main/Shikha_Practical_application%202.docx

### Key Business Insights

1.	Factors Influencing Car Prices:
  * Year: Newer cars (post-2015) have significantly higher prices. Each additional year increases the price by ~$968.
  * Mileage (Odometer): Cars with lower mileage (<50,000 miles) command higher prices. Each additional mile decreases the price by ~$0.05.
  * Cylinders: Cars with higher cylinders (4, 6, and 8) are valued more. Each additional cylinder increases the price by ~$3,127.
2.	Visual Findings:
  * Paint Color: Vehicles in black and white colors have higher prices, while green and purple are less desirable.
  * Condition: Vehicles in "new" and "good" condition dominate the higher price range.
  * Fuel Type: Diesel and electric vehicles are the most expensive, while gas and hybrids are more affordable.
  * Drive Type: 4WD and RWD vehicles command premium prices due to their utility and performance associations.
  * Car Size: Full-size vehicles are premium, while compact and mid-size vehicles cater to budget-conscious buyers.
  * Car Type: Trucks, SUVs, and pickups dominate the high price ranges. Sedans and mini-vans are more affordable.
3.	State-Specific Insights:
  * Higher Prices: States like West Virginia, Alaska, and Wyoming have higher average prices.
  * Lower Prices: States like Iowa, Virginia, and Michigan feature lower-priced vehicles.

## Summary of Key Business Actions
1.	Segment Inventory:
* Stock premium vehicles (e.g., electric, luxury, full-size) for high-demand regions and demographics.
* Prioritize affordable vehicles (e.g., compact, gas-powered) for budget-focused buyers.
2.	Location-Based Strategy:
* Focus high-end inventory in regions like West Virginia, Alaska, and Wyoming.
* Promote affordable cars in Iowa, Wisconsin, and Connecticut.
3.	Market Differentiation:
* Highlight features like low mileage, popular colors (white, black), and high-demand fuel types (diesel, electric).
* Use targeted promotions for vehicles with manual transmissions or less popular colors.
4.	Focus on Vehicle Condition:
* Emphasize "new" and "good" condition vehicles to maximize margins.
* Leverage lower-condition vehicles for bargain hunters and niche markets.
5.	Leverage Trends:
* Market SUVs, pickups, and full-size vehicles to customers in rural or high-demand markets.
* Use luxury and niche vehicles (e.g., coupes, convertibles) to cater to specific buyer preferences.

## Model Comparison for Price Prediction
1.	Using Only Numerical Features
Features: year, odometer, cylinders

|Model	            |RMSE	    |R² Score	|Cross-Validation R²|
|-------------------|---------|---------|-------------------|
|Linear Regression	|8313.18	|0.53	    |-                  |
|Ridge Regression	  |8313.18	|0.53	    |0.52               |
|Lasso Regression	  |8313.18	|0.53	    |0.52               | 

Insights:
* Numerical features alone explain 53% of the variance in car prices, but the error (RMSE: 8313) is relatively high. Models perform equally.
2.	Adding Categorical Features
Features: Numerical + condition, transmission, fuel, title_status

|Model	            |RMSE	    |R² Score	|Cross-Validation R²|
|-------------------|---------|---------|-------------------|
|Linear Regression	|7332.7	  |0.62	    |-                  |
|Ridge Regression	  |7310.5	  |0.63	    |0.59               |
|Lasso Regression	  |7560	    |0.60	    |0.59               |

Insights:
* Adding categorical features improves the R² Score to 0.63 and reduces the RMSE to 7310. Ridge regression performs slightly better than Lasso.
3.	Full Feature Set with Ordinal Encoding
  
|Model	            |RMSE	    |R² Score	|
|-------------------|---------|---------|
|Linear Regression	|7560.03	|0.64|
|Ridge Regression	|7560.03	|0.64|
|Lasso Regression	|7560.03	|0.64|

Features: All numerical and categorical features (manufacturer, model, state)



Insights:
* The inclusion of additional categorical features slightly improves performance but does not drastically change results.



4.	Polynomial Features (Degree = 2)
Features: All numerical and categorical features with polynomial expansion

|Model	            |RMSE	    |R² Score	|Cross-Validation R²|
|-------------------|---------|---------|-------------------|
|Linear Regression	|6450.57	|0.72	|-|
|Ridge Regression	|6448.94	|0.72	|0.70|
|Lasso Regression	|6446.48	|0.72	|0.70|

Insights:
* Polynomial features significantly improve model performance. The R² score reaches 0.72, and the RMSE reduces to ~6446. Lasso regression slightly outperforms Ridge and Linear Regression.
5.	Cross-Validation with Optimal Alpha

|Model	            |RMSE	    |R² Score	|Best Alpha|
|-------------------|---------|---------|-------------------|
|Ridge Regression	|6461.58	|0.71	|100|
|Lasso Regression	|6461	|0.71	|0.46|

Insights:
* Fine-tuning hyperparameters using cross-validation provides optimal results. Ridge and Lasso regressions both achieve an R² of 0.71 with similar RMSE values (~6461).

Summary of Model Performance

|Model	            |Best R²	    |Lowest RMSE	|Best Configuration|
|-------------------|---------|---------|-------------------|
|Linear Regression	|0.72	|6450.57	|Polynomial Features (Degree = 2)|
|Ridge Regression	|0.72	|6448.94	|Polynomial + Alpha Tuning (100)|
|Lasso Regression	|0.72	|6446.48	|Polynomial + Alpha Tuning (0.46)|






 

