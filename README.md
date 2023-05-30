# Data-Mining-Project2

## Introduction

In this repository, I will upload my works and our teams' result in different tags.

Shortly saying we have done project with theme : How can we predict 2 week later's stock?

## Theme

We have explored on Korea's company which belong so KOSPI 200 determined at 2023 May 13. Our goal was to predict whether stock price(closed price) will increase or decrease when Financial Statements is announced. We set target variable by following :

Listed Company must announce their Financial Statements every quarter. When Financial Statement is announced, we are interested if stock price will increase/decrease after 2 weaks. For example if some company announced their Financial Statement at May 1, we are interested in stock price at May 15. Our target variable is 1(increase) if stock price increased in this moment, is 0(decrease) if stock price decreased in this moment.

Target = 1 if (Stock price at May 1) < (Stock price at May 15)

Target = 0 if (Stock price at May 1) > (Stock price at May 15)

## DataSet

We used not only Financial Statements but also Quarter's Economical Statements, Quarter's Market Statements, News number during the time period. Following is data source

- Financial Statement : 
- Quarter's Economical Statements : 
- Quarter's Market Statements : 
- News data : 
- Daily Stock data : 

We joined these data as following :

- Bind daily stock data(at the day company announced financial statement and after 2 weeks) and Financial Statement by company's name.
- Bind Quarter's Economical Statements and Quarter's Market Statements with Financial Statement data by the quarter.
- Bind News data with Financial Statement data by company's name

We then manipulated our target variable as described. Also we added one hot encoding of company's industry belonged to. There are 11 kinds : Construction, Consumer discretionary goods, Financial, Industry goods, Consumer goods, Energy(Chemical), Information Technology, Heavy industry, Steel material, Communication service, Health care.

We obtained 3329 observations with 56 variables. Organized with 1 target variable, 44 variables from above datasets, 11 variables from one hot encoding of company type. We divided 2996 and 333 observations and allocated into train, test set.

### Variables (Independent variables)

- Financial : BPS, EPS, NPGR, EPU, PBR, PER, ROE(%), 부채비율(%), 영업이익률(%), 유보율(%), 총부채회전율, 총자본회전율, 총자산회전율
- Economical, Market Statements : GDP, 최종 소비지출, 경제 심리지수, KOSPI index, 산업 생산지수, 소비자심리지수, 수출출하지수, 실업률, 소비자물가지수, 생산자물가지수, 수입물가지수, 금융기관 유동성, 국채금리, 총 주식거래량, 수출물량지수, 수입물량지수, 경상수지, 자본수지, 시장평균 미국달러, Financial stress index, 은행실제 총 예금, 증권 고객 예탁금, 투신 채권형, 은행 금전신탁, CMA 취급증권사수, 퇴직연금적립금 합계, 거래소 순 매수금액, 코스닥 순매수금액, 시가총액
- News : News number

## Modeling

We have tried following Models : 

- Logistic Regression based Methods : Logistic Regression, Logistic Regression with second interaction, Logistic Regression with second interaction only on continuous variables, Logistic Regression with Ridge, Logistic Regression with Lasso
- Discrimental Methods : LDA, Naive Bayes
- Ensemble Methods : Bagging, RandomForest, xGBoost, adaBoost
- Support Vector Machine : Radial kernel, Polynomial kernel, Linear kernel, Sigmoid kernel
- Non parametrical method : KNN


## Modeling Result

We compared accuracy based on 10 fold Cross Validation via Accuracy. We tuned parameter by 10 fold Cross Validation and compared Models.

<img width="701" alt="Accuracy barplot" src="https://github.com/DongHyun-Park-1021/Data-Mining-Project2/assets/54579806/f4ad3b7f-7d63-405a-9392-af327b284196">

We differed seed number and generated different 10 fold. We drew error bar plot of CV accuracy for each seed number. x mark is above graph's CV accuracy which is when seed 1.

<img width="729" alt="Accuracy Different CV" src="https://github.com/DongHyun-Park-1021/Data-Mining-Project2/assets/54579806/dbff9253-52bf-414e-b9d8-c8c685293a10">

## Model Performance and Inference

Applying best model (Random forest with 5 parameter selection on each branch, using 1500 trees) performs on test set as below. This is confusion matrix.


