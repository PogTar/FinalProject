About Dataset
This case requires to develop a customer segmentation to define marketing strategy. The
sample Dataset summarizes the usage behavior of about 9000 active credit card holders during the last 6 months. The file is at a customer level with 18 behavioral variables.

Following is the Data Dictionary for Credit Card dataset :-

CUST_ID : Identification of Credit Card holder (Categorical)<br>
BALANCE : Balance amount left in their account to make purchases (<br>
BALANCE_FREQUENCY : How frequently the Balance is updated, score between 0 and 1 (1 = frequently updated, 0 = not frequently updated)<br>
PURCHASES : Amount of purchases made from account <br>
ONEOFF_PURCHASES : Maximum purchase amount done in one-go <br>
INSTALLMENTS_PURCHASES : Amount of purchase done in installment <br>
CASH_ADVANCE : Cash in advance given by the user <br>
PURCHASES_FREQUENCY : How frequently the Purchases are being made, score between 0 and 1 (1 = frequently purchased, 0 = not frequently purchased) <br>
ONEOFFPURCHASESFREQUENCY : How frequently Purchases are happening in one-go (1 = frequently purchased, 0 = not frequently purchased) <br>
PURCHASESINSTALLMENTSFREQUENCY : How frequently purchases in installments are being done (1 = frequently done, 0 = not frequently done) <br>
CASHADVANCEFREQUENCY : How frequently the cash in advance being paid <br>
CASHADVANCETRX : Number of Transactions made with "Cash in Advanced" <br>
PURCHASES_TRX : Numbe of purchase transactions made <br>
CREDIT_LIMIT : Limit of Credit Card for user <br>
PAYMENTS : Amount of Payment done by user <br>
MINIMUM_PAYMENTS : Minimum amount of payments made by user <br>
PRCFULLPAYMENT : Percent of full payment paid by user <br>
TENURE : Tenure of credit card service for user <br>


First in code we import dataset then using frequency histogram and scatterplot we get some basic information about dataset.
As we have missing data in 2 variables(CREDIT_LIMIT,MINIMUM_PAYMENTS) so we use K-Nearest Neighbors to predict missing values.in sklearn there is appropriate Class KNNImputer,so we just use it.But there is one trick.We know that in algorithms which we use distances,we must standardize data,but such we have missing values and StandardScaler can't work correct in case of missing values then we initialyy did simple impuring then we standardize data and use K-Nearest Neigbors and then merge changes with dataframe.
To enshure that there are not missing values anymore we check it.

First histogram is shwoing frequency of Balance variable(feature)
Second is scatterplot which show some relationship(near to linear) between ONEOFF_PURCHASES and PURCHASES
Third is frequency histogram of variable BALANCE_FREQUENCY.
And last graph of part EDA is scatterplot showing relationship between

Next as our all variables are numeric so we can detect outliers and delete them for all variables.But As we delete every observation which contains outlier value of any of variables then few number of observations will rest.So we delete only those will contain outlier values of more than some percentages  of variables.<br>

After detecting outliers we plot correlation heatmap and we can see that there are high correlation between
columns PURCHASE_FREQUENCY and PURCHASES_INSTALLMENTS_FREQUENCY , less high correlation is between PURCHASES_TRX and PURCHASE_FREQUENCY.

Next step is making separate pipelines for preprocessing phase and one for training phase.