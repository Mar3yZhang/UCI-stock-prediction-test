# # :book:Report for the final-project ：

> + Course info ：I&C SCI_X426.85 (SUMMER 2022/REG 00267/SEC 1)
> + Project theme : Thinking about Purchasing Stock  Case Study
> + Group info :
>   + Group 2 : Qi Zhang && Xinmeng Liu

Notice: 

+ Please access to the ipynb file appendix to check the codes.

+ This PDF is only used to explain the operation.

  

## Task 0：Comprehend the features the csv file

 

| Feature        | Explanation                                            |
| -------------- | ------------------------------------------------------ |
| Date           | The recorded date                                      |
| Open           | The price of the stock when the market open            |
| High           | The highest price of the stock today                   |
| Low            | The lowest price of the stock today                    |
| Close          | The price of the stock when the market closed          |
| Adjusted close | The adjusted price of the stock when the market closed |
| Volume         | The number of transactions today                       |

*Notice: When it comes to the history stock analysis, adjusted close price is more useful.*



# Task 1: The choose of data set 

Our group has downloaded 4 stock records from the [Yahoo Finance](https://www.yahoo.com/author/yahoo-finance). ![records](README.assets/records.png)

And we choose to use the stock records of Apple corporation and Microsoft corporation because their amount of data is big enough.



# Task 2: Data Cleasing

1. Import the csv file through `pandas`

   > Notice: The 2020 data is not needed at all due to COVID-19 impacts.

2. Drop the null values of these data sets with null values

   Analysis: **No value is missing in these 2 data sets**

3.  Apply `PCA` analysis or `standarization` if necessary.

   Analysis: Unnecessary to do these operation at present.
   
4. Use the date of the stock record to replace the index. 

# Task 3: Analysis

## 1. Check the trend by close price

​	Here we draw the plots according to the daily stock close price of Apple and Microsoft between 2005-1-1 and 2025-8-1 excluding 2020.

​	We can see that `the close price of these 2 company is increasing in general. ` 

​	The price decrease at the end of 2021 but begin to ascend recently.

![1](README.assets/1-16601255150365.png)

![2](README.assets/2-16601255282457.png)

​	

## 2. Check the trend by MA of adjusted price

[Moving Average (MA)](https://www.investopedia.com/terms/m/movingaverage.asp):  

+ a moving average is a calculation used to analyze data points by creating a series of averages of different subsets of the full data set

+ By calculating the moving average, the impacts of random, short-term fluctuations on the price of a stock over a specified time frame are `mitigated`.

Here we use the SMA:
$$
SMA \ = \ \frac{A_1 +A_2+A_3+...+A_n}{n} \\\\
\ A=Average \ in \ period 
\\
n=Number \ of \ time \  periods
$$

According to the plots,we can see that :

1. The adj price of Apple and Microsoft `keep increasing in general` in this time period. 

2. `However, the price ascending of Microsoft seems smoother and the price of it is more stable than Apple`. 

+ > I guess it's because the profit of Apple mainly depends on the release of its new product. So the price of its stock can be up and down or you can say seasonal.
  >
  >  But Microsoft's profit mainly comes from the bonus of softwares. Although the software keeps updating, it can not suddenly attract a large amount of people to buy its product or abandon its product. That's why its stock seems more stable. 

![1](README.assets/1-16601265589119.png)

![](README.assets/2-166012657513311.png)

## 3. Calculate the Rate of Return by Adj Close
[Rate of Return (RoR)](https://www.investopedia.com/terms/r/rateofreturn.asp):

+ The rate of return is the net gain or loss of an investment over a specified time period, expressed as a percentage of the investment’s initial cost.

+ The dividends and effects of inflation are not taken into consideration in the simple rate of return calculation.

The formula to calculate the rate of return (RoR) is:
$$
Rate\ of \ return \ = \ \frac{Current \ value−Initial \ value} {Initial \ value}\times{100} \\\\
$$

We can see that Apple stock dropped almost 20% in 2008, ` and Microsoft's return ratio is more stable than Apple. ` 

![1](README.assets/Apple-RoR.png)

![2](README.assets/MS-RoR.png)

## 4. Check the correlation between stocks
​	The scatter matrix shows that the stock prices of Apple and Microsoft are approximately positively correlated. 

​	This is because they are both in technology industry and keep growing.
![1](README.assets/correlation.png)

## 5. Check the Expected Returns and Risk
   We take the mean of returns as their expected returns and the standard deviation of returns as their risk.

   We can see that Apple has more expected return and lower risk than Microsoft.

![1](README.assets/return_risk.png)



## Predict the trend of adjusted price

​	`Adjusted price` is useful in analyzing the price of history stock and the trend of it. To gain the profit from stocks, we should buy the stock when it has a low price and sell it out when the price of it is high. 

​	That is to say, if the future trend of a stock is  ascending, it's time to buy in and make some money!

​	So predict the trend of adjusted price helps us to decide which stock is profitable. 

Steps:

+ `Adjust the dataset`.  Adjusted price is set to be target while others are features.
+ `Data cleasing and split the data into train data set and test data set.`
+ Use the dataset to train different kinds of models and `find the best out of them`.
+ Use the best model to predict the future trend of this 2 company `relatively`.
+ Find out the better stock.

### Step 1: Feature Engineering

According to the heat map, some of the features are too related to be used in predict model. 

-> `As a result, we should develop 2 new features to feed the model.` 
$$
HL\_PCT \ = \ \frac{High−Low} {Close}\times{100} \\\\
$$

$$
PCT\_change \ = \ \frac{Close−Open} {Open} \times{100}\\\\
$$

### Step 2: Data Cleansing && Train_test_split

-> Set the adj price to be y and other features to be x.

-> X values varies so different that standrization is necessary.

-> Split the data

 

### Step 3: Choose the regression model and train them

 
