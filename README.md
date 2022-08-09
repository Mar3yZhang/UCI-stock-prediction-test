# # :book:Report for the final-project ：Thinking about Purchasing Stock  Case Study

> + Course info ：I&C SCI_X426.85 (SUMMER 2022/REG 00267/SEC 1)
>
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

Our group has downloaded 4 stock records from the [Yahoo Finance](https://www.yahoo.com/author/yahoo-finance). ![records](images\records.png)

And we choose to use the stock records of Apple corporation and Microsoft corporation because their amount of data is big enough.



# Task 2: Data Cleasing

1. Import the csv file through `pandas`

   > Notice: The 2020 data is not needed at all due to COVID-19 impacts.

2. Drop the null values of these data sets with null values

   Analysis: **No value is missing in these 2 data sets**

3.  Apply `PCA` analysis or `standarization` if necessary.

   Analysis: **No value is missing in these 2 data sets**

# Task 3: Analysis

## The profit

​	Here we assume that the profit only depends on the difference between open price and close price. 
$$
Profit\ Today \ = \ Open \ price \ - \ Close \ price
$$
If the difference today is over 0, we think the stock today is profitable. Else it's not profitable.

+ And the high price, low price and adjusted price is not useful in this part of analysis.

