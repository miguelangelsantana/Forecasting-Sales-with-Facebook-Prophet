# Sales Forecasting with Facebook Prophet
## Predicting Future Sales using Historical Data

**Author**: Miguel Santana

Thank you for reviewing this repository. The author's contact info, blog post, sources and social media profiles are listed below under **further information.**

The contents of this repository detail an analysis of product sales using regression and time series analysis. Our focus will be on leveraging Facebook Prophet's time series forecasting tools through additive regression. The analysis will provide insight into an unknown company's product sales for over 1000 stores with respect to features like store operations, holidays, promotions and customers.  

#### Project Framework | OSEMN

![!](/images/OSEMN.png)

**Data processing and analysis is completed using the OSEMN framework. The structure includes: Obtaining the data, Scrubbing (processing), Exploratory Data Analysis, Statistical Modeling and Interpretation of the Results.** 

#### The Data

The dataset was provided by Udemy. The Udemy citation is available below under **sources.** 

**Feature Key:**
* ID: Transaction ID
* Store: Store ID
* Sales: Sales per Day in Euros (Target)
* Customers: Customers per Day
* Open: Store Opened or Closed (Day)
* Promo: Running Promotion per Day 
* StateHoliday:
    * a: Public holiday
    * b: Easter
    * c: Christmas
    * 0: None
* SchoolHoliday: ID store affected by school closure

**Feature Key 2:**
* Store Type: a, b, c, d
* Assortment: basic(a), extra(b), extended(c)
* CompetitionDistance: distance to closest competitor in meters
* CompetitionOpenSince: date when competitor was open [Month/Year]
* Promo2: Continuing/Consecutive Promotion
* Promo2Since: date of promo 2 start
* PromoInterval: ID consecutive promo 2 intervals

## Scrubbing/Data Cleaning 

**Key Decisions**

* Fill null values
* Feature engineer using datetime
* Join data frames
* Extracting school and state holidays for Prophet model

## Feature Relationships | Sales Distribution
#### Monthly Sales Trends

![!](/images/salesXmonth.jpg)

#### Daily Sales Trends (Day of Month)

![!](/images/salesXdom.jpg)

#### Daily Sales Trends (Day of Week)

![!](/images/salesXdow.jpg)

## Identifying the Top 10 Performing Stores

![!](/images/top10Xsales.jpg)

#### Promotion 2 | Top Store Participation

![!](/images/promo2part.jpg)

Store 817 has the highest average sales. To our surprise, only 1 of the top 10 stores participates in promotion two. In addition, the top 10 stores are substantially closer to competitors when compared to the average distance of competition. 

# Statistical Modeling | Facebook Prophet | Store 817

**Forecast**

![!](/images/forecast.png)

**Seasonality Breakdown**

![!](/images/etsbreakdown.png)

### Evaluating Performance | Cross Validation

#### Plotting Residuals

**Plotting Root Mean Squared Error Against Horizon**

![!](/images/rmse.png)

**Plotting Mean Absolute Percent Error Against Horizon**

![!](/images/mape.png)

    The average MAPE is 7.8 percent.
    The average RMSE is 2025.914.

## Results, Limitations and Future Work

The model was able to predict sales for store 817 with an average percentage error of 7.8 percent. Our predictions show a decline in sales over the next 30 days but end short of the expected uptick in traffic that occurs over the holiday season (November and December). 

#### Limitations
The analysis is limited by the anonymity of the data. Per the source, the company is based in Europe and many external factors may influence sales including customer cultural preferences. Additionally, product knowledge is not available and features of the product itself may be influencing the analysis. 

#### Recommendations
While our analysis is limited, its worth noting that the top store is near competitors and is not participating in the second-extended promotion that is made available to approximately half of the stores in our dataset. With limited domain knowledge, a recommendation would include removing promotion two from bottom performing stores so they may focus on advertising traditional company wide promotions. In addition, the existence of competition with respect to the customer and product sold should be considered when opening new stores. 

#### Future Work
Future work should include additional store level data such as employees in store, online sales, product information and geographic information to consider additional external factors through feature engineering. 

### Further Information
Please review the narrative of our analysis in [our jupyter notebook](./jupyter_notebook.ipynb) or review our [presentation](./presentation.pdf)

For any additional questions, please reach out via email at santana2.miguel@gmail.com, on [LinkedIn](https://www.linkedin.com/in/miguel-angel-santana-ii-mba-51467276/) or on [Twitter.](https://twitter.com/msantana_ds)

A blog post on this analysis can be found on [Medium.](https://miguelangelsantana.medium.com/sales-forecasting-with-facebook-prophet-b0ff2fbee5de)

#### Sources

Notes and file sources can be found on Udemy. 

* Course Name: Data Science for Business by Ryan Ahmed

##### Repository Structure:

```

├── README.md               <- The top-level README for reviewers of this project.
├── jupyter_notebook.ipynb     <- narrative documentation of analysis in jupyter notebook
├── presentation.pdf        <- pdf version of project presentation

```

