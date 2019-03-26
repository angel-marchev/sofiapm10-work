# Data Analysis (Module 2, p. 2/2)
## Feature Engineering

Based on the findings documented in section Preliminary Analysis we define the feature matrix that is used for the predictive model building.

We first make **feature selection** on the basis of the correlation analysis as well as taking into account results documented in the literature. In particular, the research of (Kurt, et al., 2008) uses weather indicators that are similar to those available from the Sofia Airport Weather Station. The authors suggest the following indicators as input in their model: weather condition, day and night temperature, humidity, pressure, wind speed and wind direction, day of the week. Therefore, minimum and maximum temperature, average humidity, and average pressure are initially selected. Instead of taking directly the observations on wind speed, we use them to construct an additional feature as explained in the next paragraph.

As explained in the previous section, **we consider that feature engineering plays crucial role in the construction of accurate predictive air pollution models**. The reviewed literature suggests that lagged values of  PM10
 concentration are strong predictors. Consequently, we refer to the partial ACF (PACF) presented at **Figure 13** in order to determine the number of relevant lags. The figure suggests that only the first lag impacts significantly the level of PM10 concentration therefore we include it in the feature matrix as lagP1. The lag effect is further considered with regard to the fact that **the city of Sofia is located in a hollow** , i.e. in _case of high concentration of_ PM10 _in the previous day as well as no or weak wind both during the previous and during the current day, we might expect high concentration of_ PM10 _for the current day_. This motivates introduction of two additional features:

CPt=sfcWindAVGt∗sfcWindAVGt−1

Rt=lagP1tCPt.

Following the preliminary analysis findings, we define the following dummy variables:

D1t={1,ifRHMAXt=100%0,else.

D2t={1,ifRsfcWindMINt=0km/h0,else.

D3t={1,ifPRCPAVGt=0mm0,else.

D=D1∗D2∗D3.

Finally, we introduce the day of the week and the month as predictors. The reader might find summary of features that are used in the next stage of the empirical analysis in **Table 5**.

![](/media/acf.png) 
Figure 13: Partial autocorrelation function of PM10 concentration. Each panel corresponds to one of the official stations.

Table 5: List of features used for prediction purposes.

| Variable name | Variable Label |
| --- | --- |
| TASMAX | Daily maximum temperature |
| TASMIN | Daily minimum temperature |
| RHAVG | Daily average relative humidity |
| PSLAVG | Daily average surface pressure |
| lagP1 |Previous day concentration of PM10 |
| CP | Cross-product of current and previous day wind speed |
| R |Ratio of the Previous day concentration of PM10 and the cross-product |
| D1 | Dummy variable reflecting the case of 100% maximum humidity |
| D2 | Dummy variable reflecting the case of 0 km/h minimum wind speed |
| D3 | Dummy variable reflecting the case of 0 mm average precipitation amount |
| D | D1\*D2\*D3 |
| day | Day of the week |
| month | Month of the year |

**Figure 14** presents the correlation matrix in absolute terms for the response and selected features variables for station 9421. Similar results for the rest of the stations are reported in the Appendix at the end of section 4.

 ![](/media/correlations.png)
Figure 14: Correlation matrix in absolute terms for the response and selected features variables for station 9421

##	Predictive Modelling

In this section we use the random forest approach so as to deliver nonlinear prediction model for each of the official stations. For this purpose we define Algorithm 1.  
1.	Split data on random basis into two subsets (train and test) of equal length.
2.	Fit random forest equation with 500 trees.
3.	Record equation and other control information.
4.	Perform 1 day ahead forecast over the test set.
5.	Calculate out-of-sample RMSE and MAE.
6.	Repeat steps 1 to 5 until 100 iterations are reached. Average results on variable importance, RMSE, MAE.
Algorithm 1: Algorithm for iterative application of the random forest approach to moderate sample size. 

![](/media/features importance.png)
Figure 15: Summary of feature importance expressed as percentage of the cumulative decrease in the optimized loss function. Station 9421.

It is worth noting that the algorithm assures robustness of results to the random sampling process. Thus we **deliver predictive equations and out-of-sample forecasts** for all of the official stations. Estimation results are similar therefore we report variable importance diagram for station 9421 at **Figure 15** , while results for rest of stations might be found in the Appendix at the end of Section 4. The following conclusions might be drawn:

> - The most important variable in predicting the air pollution in Sofia is the **Ratio** of the previous day concentration of PM10 and the cross-product of current and previous day wind speed.
> - **Previous day concentration of** PM10 and the cross-product of **current and previous day wind speed** are also essential predictors.
> - Season (month), temperature, humidity and pressure are **of secondary importance** in explaining the variation in the level of air pollution.
> - The latter findings suggest that other factors (such as road traffic intensity, etc.) that are absorbed to certain extent in the previous day concentration of PM10 might cause the huge impact captured by the synthetic variables R,CP,lagP1. Therefore, **enriching the feature space with additional information might be helpful in identifying the drivers behind their high values**.

## Validation (Out-of-Sample Accuracy)

**Table 6** and **Table 7** present out-of-sample RMSE and MAE on averaged over results for all the recorded iterations of Algorithm 1. **Predictive models delivered in section 4.2.5**. are denoted by **M3**.

| Table 6: Out-of-sample RMSE by stations.

|   | **M1** | **M2** | **M3** |
| --- | --- | --- | --- |
| **st9421** | 17.84 | 13.05 | 10.09 |
| --- | --- | --- | --- |
| **st9572** | 36.49 | 29.75 | 22.00 |
| --- | --- | --- | --- |
| **st9616** | 30.49 | 25.29 | 19.39 |
| --- | --- | --- | --- |
| **st9642** | 30.66 | 24.52 | 18.13 |
| --- | --- | --- | --- |
| **st60881** | 26.80 | 20.74 | 17.88 |
| --- | --- | --- | --- |

  | Table 7: Out-of-sample MAE by stations.

|   | **M1** | **M2** | **M3** |
| --- | --- | --- | --- |
| **st9421** | 60% | 42% | 34% |
| --- | --- | --- | --- |
| **st9572** | 66% | 50% | 43% |
| --- | --- | --- | --- |
| **st9616** | 60% | 38% | 36% |
| --- | --- | --- | --- |
| **st9642** | 59% | 40% | 35% |
| --- | --- | --- | --- |
| **st60881** | 47% | 39% | 33% |
| --- | --- | --- | --- |

Results are benchmarked against two naïve predictive models: {M1:PM10,T+1=1T∑t=1TPM10,t}
, {M2:PM10,T+1=PM10,T}.

As both of the tables suggest next-day forecasts generated by our predictive models **outperform considerably** the naïve forecast. Additionally, **achieved accuracy is comparable with that reported in similar studies** (see for example Table 3 at p. 596 of (Kurt, et al., 2008)). At the same time, our approach **preserves interpretability** of results and we consider this an important contribution of our research.



## Appendix Module 2

The following list of additional information is available at [this](https://drive.google.com/open?id=1kjY_12KpGAA5lQKoKYhKfY_ly3eSPr8L) link.

- Pairwise scatterplots for station 9572
- Pairwise scatterplots for station 9616
- Pairwise scatterplots for station 9642
- Pairwise scatterplots for station 60881
- Plot of the correlation matrix in absolute terms for station 9572
- Plot of the correlation matrix in absolute terms for station 9616
- Plot of the correlation matrix in absolute terms for station 9642
- Plot of the correlation matrix in absolute terms for station 60881
- Full correlation matrix (by all stations)
- Plot of the correlation matrix in absolute terms for the response and selected features variables for station 9572
- Plot of the correlation matrix in absolute terms for the response and selected features variables for station 9616
- Plot of the correlation matrix in absolute terms for the response and selected features variables for station 9642
- Plot of the correlation matrix in absolute terms for the response and selected features variables for station 60881
- Plot: Summary of feature importance expressed as percentage of the cumulative decrease in the optimized loss function. Station 9572
- Plot: Summary of feature importance expressed as percentage of the cumulative decrease in the optimized loss function. Station 9616
- Plot: Summary of feature importance expressed as percentage of the cumulative decrease in the optimized loss function. Station 9642
- Plot: Summary of feature importance expressed as percentage of the cumulative decrease in the optimized loss function. Station 60881


## Code
#### Set up environment
```R 
rm(list=ls())
gc()
```
Set the path of the folder with data
```R
setwd("/data")
``` 
Import data on EEU measurements for 2017 and 2018
```R
eeu=list.files(path="/data",pattern="BG*")
ddeu=lapply(eeu,read.csv,na.string=c("","NA"," "), stringsAsFactors = F, fileEncoding="UTF-16LE")
```
Name data sets by stations
```R
for (i in 1:length(eeu)){
  eeu[i]=gsub("BG_5_","st", eeu[i])
  eeu[i]=gsub("_timeseries.csv","", eeu[i])
  names(ddeu)[i]=eeu[i]
}
rm(eeu,i)
```
Select only the observations with averaging time == "hour"
```R 
for (i in 1:length(ddeu)){
  ddeu[[i]]=ddeu[[i]][ddeu[[i]]$AveragingTime=="hour",]
}

count = 0
i = 1
while(0 == 0){
  if (count == 1){
    i = i - 1
  }
  if(i > length(ddeu)){
    break
  }
  count = 0
  if(dim(ddeu[[i]])[1] == 0){
    ddeu[[i]] = NULL
    count = 1
  } 
  i = i + 1
}
rm(count,i)
```
Check variables' class of ddeu
```R 
sapply(lapply(ddeu,"[", ,"DatetimeEnd"),class)
sapply(lapply(ddeu,"[", ,"Concentration"),class)
```
Fix the class of the time variable
```R
if(!require(lubridate)){
  install.packages("lubridate")
  library(lubridate)
}
for (i in 1:length(ddeu)){
  ddeu[[i]]=ddeu[[i]][,c("DatetimeEnd","Concentration")]
  ddeu[[i]]$DatetimeEnd=ymd_hms(ddeu[[i]]$DatetimeEnd, tz="Europe/Athens")
  colnames(ddeu[[i]])=c("time","P1eu")
}

sapply(lapply(ddeu,"[", ,"time"),class)
``` 
Make a time vecor with hourly sampling rate
```R 
teu=list()
for (i in 1:length(ddeu)){
  teu[[i]]=as.data.frame(seq.POSIXt(from=min(ddeu[[i]]$time),to=max(ddeu[[i]]$time), by="hour"))
  colnames(teu[[i]])[1]="time"
}
```
Make a list of time series on official P10 concentration for every station
```R 
if(!require(dplyr)){
  install.packages("dplyr")
  library(dplyr)
}

if(!require(devtools)){
  install.packages("devtools")
  library(devtools)
}

for (i in 1:length(ddeu)){
  teu[[i]]=left_join(teu[[i]],ddeu[[i]],by="time")
}
names(teu)=names(ddeu)
```
Bind datasets 2017 and 2018 for each of the official points
```R 
teu$st9421=bind_rows(teu$st9421_2017,teu$st9421_2018)
teu$st9572=bind_rows(teu$st9572_2017,teu$st9572_2018)
teu$st9616=bind_rows(teu$st9616_2017,teu$st9616_2018)
teu$st9642=bind_rows(teu$st9642_2017,teu$st9642_2018)
teu$st60881=teu$st60881_2018

teu=teu[c("st9421", "st9572","st9616","st9642","st60881")]
for (i in 1:length(teu)){
  colnames(teu[[i]])[2]="P1"}
rm(i,ddeu)
```
Check for duplicates
```R 
sapply(teu,dim)[1,]
sum(duplicated(teu[[1]]$time)) #0
sum(duplicated(teu[[2]]$time)) #0
sum(duplicated(teu[[3]]$time)) #0
sum(duplicated(teu[[4]]$time)) #0
sum(duplicated(teu[[5]]$time)) #0
```
Interpolate missing values for P1eu
```R 
if(!require(imputeTS)){
  install.packages("imputeTS")
  library(imputeTS)
}
```
Check the numer of missing obs
```R 
sapply(sapply(teu,is.na),sum)
sapply(sapply(teu,is.na),sum)/sapply(teu,dim)[1,]
```
Apply linear interpolation
```R 
for (i in 1:length(teu)){
  teu[[i]][,2]=na.interpolation(teu[[i]][,2], option="linear")
}
rm(i)
``` 
#### Aggregate official measuremnets on daily basis
Extract date from the time variable
```R 
for (i in 1:length(teu)){
  teu[[i]]$date=date(teu[[i]]$time)
}
``` 
Aggregate data on daily basis
```R
aeu=list()
for (i in 1:length(teu)){
  aeu[[i]]=teu[[i]] %>%
    group_by(date) %>%
    summarise(P1=mean(P1))
}
names(aeu)=names(teu)
#rm(teu,i)

``` 
#### Import data on weather metrics
Import data on weather
```R
setwd("/")
ww=read.csv("lbsf_20120101-20180917_IP.csv",na.string=c("","NA"," ",-9999), stringsAsFactors = F)
``` 
Get a date vector
```R
ww$date=make_date(year=ww$year,month=ww$Month,day=ww$day)
ww=ww[,c(23,1:22)]
``` 
Check for poorly populated variables
```R 
colSums(is.na(ww))
ww$date[is.na(ww$VISIB)==T]
``` 
Entire period for PRCPMAX and PRCPMIN is missing
Last two months (Aug and Sep 2018) for VISIB are missing
Remove this variables from the sample
```R
ww=ww[,!names(ww) %in% c("PRCPMAX","PRCPMIN","VISIB","year","Month","day")]

``` 
#### Merge data on P10 and weather
```R 
for (i in 1:length(aeu)){
  aeu[[i]]=left_join(aeu[[i]],ww,by="date")
  aeu[[i]]$day=wday(aeu[[i]]$date,label=T)
}

``` 
Handle missing values
```R 
sapply(sapply(aeu,is.na),colSums)

for (i in 1:length(aeu)){
  aeu[[i]][,3:18]=sapply(aeu[[i]][,3:18],na.interpolation,option="linear")
}
rm(ww,i)
``` 
#### Look at the data first
Construct correlation matrix
```R 
cc=list()
for (i in 1:length(aeu)){
  cc[[i]]=cor(aeu[[i]][,2:18])
}
names(cc)=names(aeu)
```
Visualize correlation matrix
```R 
if(!require(plotly)){
  install.packages("plotly")
  library(plotly)
}
if(!require(RColorBrewer)){
  install.packages("RColorBrewer")
  library(RColorBrewer)
}
i=1 
```
Change i=1,2,3,4,5 so as to get plot for each station
```R 
plot_ly(x=rownames(cc[[i]])[1:nrow(cc[[i]])], y=colnames(cc[[i]])[nrow(cc[[i]]):1],z=abs(cc[[i]][nrow(cc[[i]]):1,1:nrow(cc[[i]])]),type="heatmap",colors=brewer.pal(8,"Reds"))

```
Stationarity tests
```R
if(!require(tseries)){
  install.packages("tseries")
  library(tseries)
}
aux=list()
for (i in 1:length(aeu)){
  a=adf.test(aeu[[i]]$P1)
  aux[[i]]=c(a$statistic,a$p.value)
  rm(a)
}
aux=as.data.frame(aux)
colnames(aux)=names(aeu)
rownames(aux)=c("ADF statistics", "p-value")

``` 
#### Feature engineering
```R 
eu=list()
for (i in 1:length(aeu)){
  eu[[i]]=aeu[[i]][,c("P1","TASMAX","TASMIN","RHAVG","PSLAVG","day")]
  eu[[i]]$lagP1=dplyr::lag(eu[[i]]$P1,1)
  eu[[i]]$month=month(aeu[[i]]$date)
  eu[[i]]$D1=ifelse(aeu[[i]]$RHMAX==100,1,0)
  eu[[i]]$D2=ifelse(aeu[[i]]$sfcWindMIN==0,1,0)
  eu[[i]]$D3=ifelse(aeu[[i]]$PRCPAVG==0,1,0)
  eu[[i]]$D=eu[[i]]$D1*eu[[i]]$D2*eu[[i]]$D3
  eu[[i]]$CP=aeu[[i]]$sfcWindAVG*(dplyr::lag(aeu[[i]]$sfcWindAVG,1))
  eu[[i]]$R=eu[[i]]$lagP1/eu[[i]]$CP
  eu[[i]]=eu[[i]][-1,]
}
names(eu)=names(aeu)
```
Construct correlation matrix
```R 
cc=list()
for (i in 1:length(eu)){
  cc[[i]]=cor(eu[[i]][,!names(eu[[i]]) %in% "day"])
}
names(cc)=names(eu)
``` 
Visualize correlation matrix
```R 
i=1 ``` ```R Change i=1,2,3,4,5 so as to get plot for each station
plot_ly(x=rownames(cc[[i]])[1:nrow(cc[[i]])], y=colnames(cc[[i]])[nrow(cc[[i]]):1],z=abs(cc[[i]][nrow(cc[[i]]):1,1:nrow(cc[[i]])]),type="heatmap",colors=brewer.pal(8,"Reds"))
``` 
#### Random forest
mean absolute percentage error
```R 
MAE=list() 
``` 
root mean squared error
```R 
RMSE=list()
``` 
feature importance
```R 
FI=list() 
for (i in 1:length(eu)){
  FI[[i]]=data.frame(matrix(NA,ncol=1,nrow=13))
  FI[[i]][,1]=as.character(names(eu[[i]])[-1])
  colnames(FI[[i]])="fname"
}
names(FI)=names(eu)

for (t in 1:100){
``` 
Split data into training and test set
```R 
set.seed(t)
  
  train=list()
  for (i in 1:length(eu)){
    train[[i]]=sample(nrow(eu[[i]]),round(nrow(eu[[i]])/2))
  }
```
Model estimation & feature importance
```R 
if(!require(randomForest)){
    install.packages("randomForest")
    library(randomForest)
  }
  eq=list()
  for (i in 1:length(eu)){
    eq[[i]]=randomForest(P1~.,data=eu[[i]][train[[i]],])
    a=data.frame(fname=as.character(rownames(eq[[i]]$importance)), imp=as.numeric(eq[[i]]$importance))
    colnames(a)[2]=paste("imp",t,sep="")
    FI[[i]]=left_join(FI[[i]],a,by="fname")
    rm(mae,rmse,a)
  }
```
Calculate out-of-sample accuracy
```R 
  mae=data.frame(matrix(NA,nrow=length(eu),ncol=3))
  rownames(mae)=names(eu)
  colnames(mae)=c("M1","M2","M3")
  rmse=data.frame(matrix(NA,nrow=length(eu),ncol=3))
  rownames(rmse)=names(eu)
  colnames(rmse)=c("M1","M2","M3")
  
  for (i in 1:length(eu)){
    f=predict(eq[[i]],newdata=eu[[i]][-train[[i]],])
    rmse[i,"M1"]=sqrt(mean((eu[[i]]$P1[-train[[i]]]-mean(eu[[i]]$P1[-train[[i]]]))^2))
    rmse[i,"M2"]=sqrt(mean((eu[[i]]$P1[-train[[i]]]-eu[[i]]$lagP1[-train[[i]]])^2))
    rmse[i,"M3"]=sqrt(mean((eu[[i]]$P1[-train[[i]]]-f)^2))
    mae[i,"M1"]=mean(abs((eu[[i]]$P1[-train[[i]]]-mean(eu[[i]]$P1[-train[[i]]]))/eu[[i]]$P1[-train[[i]]]))
    mae[i,"M2"]=mean(abs((eu[[i]]$P1[-train[[i]]]-eu[[i]]$lagP1[-train[[i]]])/eu[[i]]$P1[-train[[i]]]))
    mae[i,"M3"]=mean(abs((eu[[i]]$P1[-train[[i]]]-f)/eu[[i]]$P1[-train[[i]]]))
  }
  MAE[[t]]=mae
  RMSE[[t]]=rmse
}

rm(i,t)

MAE=as.data.frame(MAE)
RMSE=as.data.frame(RMSE)

mae=data.frame(matrix(NA,nrow=length(eu),ncol=3))
rownames(mae)=names(eu)
colnames(mae)=c("M1","M2","M3")
rmse=data.frame(matrix(NA,nrow=length(eu),ncol=3))
rownames(rmse)=names(eu)
colnames(rmse)=c("M1","M2","M3")
``` 
Devrie rmse and mae
```R 
for (i in 1:length(eu)){
  mae[i,"M1"]=mean(as.numeric(MAE[i,grep("^M1",names(MAE))]))
  mae[i,"M2"]=mean(as.numeric(MAE[i,grep("^M2",names(MAE))]))
  mae[i,"M3"]=mean(as.numeric(MAE[i,grep("^M3",names(MAE))]))
  rmse[i,"M1"]=mean(as.numeric(RMSE[i,grep("^M1",names(RMSE))]))
  rmse[i,"M2"]=mean(as.numeric(RMSE[i,grep("^M2",names(RMSE))]))
  rmse[i,"M3"]=mean(as.numeric(RMSE[i,grep("^M3",names(RMSE))]))
}
```
Derive importance
```R 
fi=list()
for (i in 1:length(FI)){
  fi[[i]]=data.frame(fname=FI[[i]]$fname)
  fi[[i]]$fimp=apply(FI[[i]][,2:101],1,mean)
  fi[[i]]$pfimp=fi[[i]]$fimp/sum(fi[[i]]$fimp)
  rownames(fi[[i]])=FI[[i]]$fname
}

i=5 
``` 
Change i=1,2,3,4,5 so as to get plot for each station
```R 
barplot(fi[[i]]$pfimp[order(fi[[i]]$pfimp,decreasing = T)], names.arg = fi[[i]]$fname[order(fi[[i]]$pfimp,decreasing = T)],col="light blue", ylab="Importance in %",las=2)
``` 
#### Get predition for P10 by stations
NB: This prediction assumes we have weather forecast 
Use the following code:
```R
f=list()
for (i in 1:length(eu)){
f[[i]]=predict(eq[[i]],newdata=[\#inseart here new data])
}
``` 
