## Data Science em Produção
![This is an image](https://advancedinstitute.ai/wp-content/uploads/2019/04/regressao-1170x500.png)

### Project Motivation:

The Rossman company operates more than 3000 drugstores in 7 European countries. The CFO of the chain asked store managers for the prediction of your daily sales until six week in advance in order to allocate resources for store reform.
The sales are influenced by many factors, including promotion, competition, states and school and public holidays, seasonality and locality. 

###  Root cause of problem:

- The CFO needs to know how much each store will bring in profit to allocate in investment for renovation. 
 
###  Stakeholder

- CFO

### Solution Format:

- Daily salles for the next six week;
- Prediction problem; 
- Time series, Regression;
- Prediction accessed by cell phone.

### Solution Strategy: 

**Data Description:** Rename columns, Data dimensions, Data types, Replace NA.

**Feature Engineering**:  New features have been created through original features for validation business hypothesis: competition_time_month, competition_distance, competition_open_since_month, competition_open_since_year, promo2, promo2_since_week, promo2_since_year, promo_interval, competition_time_month.

**Data adjustment for application of the Machine Learning model:** Rescale, Encoding, Response Variable Transformation. Choices of the most relevant features for the model: Boruta algorithm.
 
**Machine Learning model applied**: Average Model, Linear Regression, Lasso, Random Forest Regressor, XGBoost Regressor.
 
**Machine Learning model used:** XGBoost Regressor.

### Data Insights
 
**1-** Stores with closer competitors should sell more. 

**2-** Stores with more assortment sell less.

**3-** Stores with longer competitions sell less.

**4-** Stores with longer active promotions sell less.

**5-** Open stores during the Christmas holiday sell less.

**6-** Stores with basic assortments show more sales. 

**7-** Stores sell more after the tenth day of each month.

**8-** The business day doesn’t have a positive correlation with sales amount. 

**9-** Sales volume is higher when the store is not on sale.

### Comparison of Machine Learning Model's Performance after cross validation 

![models_dsproducao](https://user-images.githubusercontent.com/77075354/199277525-0e2da3a3-9627-43f6-9900-421692beb47d.png)

### XGBoost Regressor after Fine Tuning 

![xg_boosty](https://user-images.githubusercontent.com/77075354/199278553-df8357a7-571b-48b5-923e-7b59f057a95b.png)

### Business Performance

![business_performance](https://user-images.githubusercontent.com/77075354/199278801-f0192861-cdbf-46bc-9c75-22cbe0e08133.png)

### Total Performance

![total_perfomance](https://user-images.githubusercontent.com/77075354/199278889-e562b8a2-4736-4ccd-8dc1-29c997f4e1b5.png)

### Production Deployment

Implantation with the goal to provide the model prediction for any user. The user can be: a person, smartphone, mobile app, site, Google sheets, excel sheets or any software connected on the internet which can execute an API solicitation. 
Posteriorly, both the API and the model will be loaded in on cloud server (Heroku) for the user to work with requests sent by the internet. For this was created a bot on Telegram, so that the requests of sales predictions can be done quickly and easily. The prediction can be accessed anytime and anywhere that has the internet just by entering the store number as input.





 


