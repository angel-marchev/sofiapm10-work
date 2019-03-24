
prof. Boryana Pelova, PhD, prof. Angel Marchev, PhD, ??? {#prof.-boryana-pelova-phd-prof.-angel-marchev-phd .ListParagraph}
========================================================

Faculty of Economics and Business Administration, Sofia University {#faculty-of-economics-and-business-administration-sofia-university .ListParagraph}
==================================================================

Abstract {#abstract .ListParagraph}
========

 {#section .ListParagraph}

General information
===================

#### Relevance {#relevance .ListParagraph}

This study is organized in cooperation with the Science meets Regions
event on Energy and Climate Change and Social Effects of Climate Change,
organized by Sofia municipality in March 2019. The premise here is that
the study would foster the debate on Sofia's air quality - one of the
biggest environmental issues of the city in later years. As the City of
Sofia goes through a phase of vast socio-economic improvement it
inevitably encounters the perils of this growth - disregarded
environmental effects. While Sofia Municipality has started to implement
prevention policies, in general there is lack of public consensus on the
issue, based on facts and rational arguments.

Taking on the biggest climate-related challenge of the City of Sofia is
not an easy undertaking. It requires multi-domain knowledge and
interdisciplinary research approach, while there are many aspects to be
studied. The current study focuses on one day prediction of air quality
by location which would give most useful application to the citizens,
but further research may be conducted on the polluting factors.

![](media/image1.png){width="6.014660979877515in"
height="2.932292213473316in"}

Fig. 1 Urban population exposure to concentrations above EU standards.

Source: European Environmental Agency: Bulgaria -- air pollution country
fact sheet 2017

#### Essence {#essence .ListParagraph}

In Sofia, the air pollution norms set by EU (50 µg/m^3^ daily average)
were exceeded on 70 days in the heating period from October 2017 to
March 2018, per citizens' initiative AirSofia.info. AirSofia measures
the air pollution in Sofia using citizen based network of sensors.

In particular, fine particles with diameter less than 10µm mixture of
solid particles and liquid droplets found in the air (PM10) are the most
dangerous and particularly interesting from research standpoint as the
prediction of PM10 is an important issue in control and reduction of
pollutants in the air.

![](media/image2.png){width="3.1829133858267715in"
height="2.2239588801399823in"}

Fig.2 Comparative visualization of fine particles with diameter less
than 10µm mixture of solid particles and liquid droplets found in the
air (PM10) Source: US EPA

#### Objectives {#objectives .ListParagraph}

The study aims to achieve results in predicting the PM10 high peaks of
concentration and forecast the pollution level. Still, to be as accurate
as possible and to have maximum coverage of the territory of Sofia, the
prediction of those peaks and concentration levels should be within a
24-hour period, using official and citizen network data.

The ultimate objective of this analysis is to deliver forecast for the
next 24 hours per station. The data for each station is a time series
sequence therefore at the end of the day we would employ time series
analysis.

Firstly there is bias correction of citizen science measurements,
checked against the "official" measurement stations. The official comply
with the EU directives on air quality monitoring can be used for
regulatory purposes, but are limited in number (only 5 in the whole
city). Citizen science stations have very good coverage of the city, but
may carry instrumental biases -- due to different measurement methods,
different interaction with meteorology, etc.

![](media/image3.png){width="4.1367814960629925in"
height="2.0989588801399823in"}

Fig. 3 AirSofia.Info citizen measurement network
([[http://airsofia.info]{.underline}](http://airsofia.info)).

Secondly a prediction model for next-day forecast of PM10 is built,
using additional factor from meteorological parameters (from a weather
forecast) and topography satellite data. When there are qualitative
prediction results, the data is mapped over geo-locations of Sofia.

#### Local context {#local-context .ListParagraph}

There are some local community factors to be understood about the study
which would shade a different light on the approach (and specifically
why is it done the way it is done). The research is as much data
oriented as it is public communication oriented. Of course this does not
reduce its rigorousness. The aim of the study is to utilize the
available data from the civic network stations in order to see and
present this as a viable (or not) alternative for measurement.

![](media/image4.png){width="6.270833333333333in"
height="2.7083333333333335in"}

Fig. 4 Locations of official measurement stations.

So in that regard this is a relatively small research oriented towards
the general public, and it address some of the hotly discussed topics in
the public circles:

1\) wide mistrust by the public to the official predictions (note: the
research team does not endorse this mistrust);

2\) popularity of the civic system of air quality sensors is based mostly
on the fact that the data is oriented locally (neighborhood by
neighborhood), and they give some local context and understanding to for
the citizens of Sofia.

3\) While no one disputes the vast technical superiority of the official
measurement stations over the civic network sensors, the popular opinion
is that the five official stations do not meet the needs of the citizens
for in-time and on-spot predictions.

![](media/image5.png){width="4.633804680664917in"
height="3.7031255468066493in"}

Fig. 5 Inversion and pollution as a result of topography of Sofia.

There have been some public concern regarding the sensors in the civic
network of stations -- all of them use the SDS011 optical sensor
(https://airbg.info/). Considering that the research team are not
experts in sensors, a background check has been made on the sensors. The
conclusion is that most of the critique towards them is at PM2.5 level,
while at PM10 level there are not too many objections to their
functioning (Assessment of Measurement Uncertainties for a SDS011
low-cost PM sensor from the Electronic Signal Processing Perspective,
Bernd Laquai, 4.10.2017,
https://www.researchgate.net/publication/320290219). There is
uncertainty of the measurements of these sensors under certain
conditions (temperature and moisture) so that the measurements start to
drift in one direction. Under such hypothesis a bias-correction
algorithm is a must along with all sorts of data cleansing as a standard
approach for big data research.

![](media/image6.png){width="5.536082677165354in"
height="2.8247419072615925in"}

https://luftdaten.info/en/home-en/

Regarding the fact that Copernicus CAMS is already providing PM10
forecasting at EU level, once again the scope of the data there and the
prolonged period for data access are not validated by the small size and
by the local orientation of the current study. This does not exclude
Copernicus CAM as future source of data, especially on the external
sources of air pollution.

#### Results {#results .ListParagraph}

1.  Bias correction model for the data of citizen science measurements
    of AirSofia.info, checked against the official measurement stations
    of EEA. This is a most useful result in itself, making the widely
    available data usable for research and information purposes.

2.  A prediction model for next-day forecast of PM10, using additional
    factors from meteorological parameters (from a weather forecast) and
    topography satellite data, mapped over geo-locations of Sofia.

3.  An open-source web representation of the research, including
    methodology, programming code in R for reproducibility, data
    transformation, numerical simulations, statistical modeling, data
    visualization, and interactive maps.

Methodology
===========

The problem of predicting the air pollution in urban areas has been of
central research interest in recent years. As suggested by (Kolehmainen,
et al., 2001) and later by (Russo, et al., 2015) forecasting air
pollution concentrations in urban locations emerges as a priority for
guaranteeing life and environmental quality. Consequently, numerous
papers are aimed to construct predictive models of daily air pollution
as measured by the concentrations of $\text{PM}_{10}$ and other air
pollutants such as $\text{SO}_{2}$, $\text{NO}_{2}$, $\text{CO}$, etc.
Nevertheless, the issue with $\text{PM}_{10}$ concentration is of
special importance as its yearly and 24-hour levels are subject to
restrictions defined by the new European Air Quality Directive[^1]. As
highlighted by (Siwek & Osowski, 2016) in order to comply with the short
term limits defined in the directive and diminish dangerous
concentration levels, actions should be planned at least one day in
advance.

This paper also contributes to the topic. **We develop a general
framework for analysis and prediction of air pollution in the city of
Sofia, Bulgaria, as measured by the level of the**
$\mathbf{\text{PM}}_{\mathbf{10}}$ air pollutant indicator. As a
starting point in our analysis we consider earlier findings documented
in the literature therefore the following text provides a brief review
of selected papers. We focus on utilized methodology so as to support
the process of defining proper predictive approach that is adopted in
our methodological framework.

Literature Review
-----------------

(Russo, et al., 2015) study daily $\text{PM}_{10}$ concentrations in the
metropolitan region of *Lisbon, Portugal* as measured by twelve
monitoring stations. The authors adapt neural networks approach. They
use as predictors **lagged values** (the lag is of one day) of daily
mean concentrations of various air pollutants as well as maximum
concentration of $\text{PM}_{10}$. Also, information on daily
circulation weather type at three boundary layers heights is considered
as well as other weather metrics such as temperature, wind direction and
intensity, humidity and radiance. (Catalano, et al., 2016) study hourly
mean concentration of $\text{NO}_{2}$ for *Marylebone road in the City
of London* based on past observations on the concentration of
$\text{NO}_{2}$ as well as traffic and weather conditions. The research
applies an **artificial neural network approach (ANN)** and the **ARIMAX
model**. Among others, the authors illustrate the benefits of the
**synergic use of both of the approaches** for improving the forecast
accuracy. (Feng, et al., 2015) study the level of air pollution in *two
areas located in northeast China* characterized by rapid increase of
urbanization as measured by the air pollutant $\text{PM}_{2.5}$. Their
methodology builds on ANN approach. In particular, the authors apply air
mass trajectory model to recognize distinct corridors for transport of
dirty and clean air to the studied stations, where **wind speed and
direction** are considered as parameters of the trajectory. Furthermore,
the original sequence of observations on $\text{PM}_{2.5}$ is decomposed
into series with lower variability via application of the **wavelet
transform**. The latter improves significantly the prediction accuracy.

(Cortina-Januchs, et al., 2015) build predictive model for the next
24-hours average air pollution concentration as measured by the level of
$\text{PM}_{10}$ and $\text{SO}_{2}$in *Salamanca, Mexico*. The latter
has been ranked as one of the most polluted cities in Mexico. The
database of features consists of **historic time series of
meteorological variables and concentrations of**
$\mathbf{\text{PM}}_{\mathbf{10}}$ for three measurement stations. The
proposed model is a combination of multilayer perception neural network
and clustering algorithm. Evaluation of performance is achieved on the
basis of **RMSE** (root mean squared error) and **MAE** (mean absolute
error) against simpler alternatives. (Kurt, et al., 2008) develop an
online air pollution forecasting system based on neural network
approach. The authors use **weather condition, day and night
temperature, humidity, pressure, and wind speed and direction**, as well
as **day of the week** as exogenous features. Documented results
evidence that quite accurate predictions are achieved even with a simple
neural network.

As suggested by the reviewed papers **meteorological variables** play an
important role in the process of predicting the concentration of air
pollutants in the air. Yet, their values are not available at the time
when the next day forecast is generated thus their predicted values are
used instead. (Huebnerova & Michalek, 2014) study the performance of
prediction models on the concentration of $\text{PM}_{10}$ when **the
predicted covariates are used instead of the observed ones** for Brno,
Czech Republic. They come to the finding that **there is no significant
effect** for the case under study and predicted meteorological variables
can be employed in the environmental management process. Last but not
least, the paper of (Siwek & Osowski, 2016) highlights the importance of
**feature engineering** in the process of building accurate air
prediction models.

Definition of Methodology Framework
-----------------------------------

We use the following summary of findings documented in the reviewed
literature as basis to define our methodology framework.

-   Lagged values of $\text{PM}_{10}$ concentration levels as well as
    meteorological indicators are used as common features in the process
    of building air pollution predictive models.

-   Authors such as (Siwek & Osowski, 2016), (Kurt, et al., 2008),
    (Feng, et al., 2015) suggest that feature engineering improves
    performance of these models.

-   Most of the authors adopt nonlinear models based on neural networks.

-   Combination of nonlinear modelling and ARIMAX is beneficial.

-   RMSE and MAE are used as common performance measure against simpler
    (naïve) forecasts.

We should note that the reviewed papers are focused solely on the
predictive modelling of air pollution measured at several official
stations. Therefore, **our core modelling process** is performed
**using** $\mathbf{\text{PM}}_{\mathbf{10}}$ **air pollution
measurements [at five official stations in Sofia]{.underline}**. At the
same time we **[integrate]{.underline}** this model to $\text{PM}_{10}$
air pollution measurements **for a wide coverage of observation points
spread over the entire city through utilization of citizens' science
stations data**. We consider the latter as an important contribution of
this research.

However, even widely available, citizens' science stations datasets
require bias correction so as to become usable for research and
information purposes. Therefore, the **first module (Module 1 at**
**Figure 1)** of our methodology performs citizens' science stations
data preprocessing and cleaning. We develop a robust procedure that
groups citizen science stations located in a close proximity into one
geo-unit. Measurements on $\text{PM}_{10}$ concentration within each
geo-unit are compared and if any differences behind a pre-specified
threshold are identified, cleaning is introduced. Furthermore, we
benchmark concentration levels at geo-units with those measured at the
official stations and bias correction is introduced where necessary.
***Module 1 automates fully the process of data preparation and data
cleaning. Its output is cleaned dataset by geo-units.***

The **second module** in our methodology framework **(Module 2 at**
**Figure 1)** performs the core prediction modelling. We use data on
$\text{PM}_{10}$ air pollution measurements at five official stations in
Sofia published by EEA and meteorological data as published by Sofia
Airport Weather Station. An important step in our analysis is the
process of feature engineering. Following the findings in the
literature, we adopt nonlinear approach. Yet, while the majority of
papers apply neural networks, we decide to model the observed
nonlinearities via the random forest approach. On one hand, our
preliminary data analysis indicates that tree-based methods are
particularly well-suited to dependencies observed in the analyzed
dataset. Thus, we derive prediction accuracy comparable to results
reported in similar studies, e.g. (Kurt, et al., 2008). At the same
time, unlike neural network, the random forest approach preserves
interpretability of results and enables analysis of variables
importance. ***The output of Module 2 is prediction model for next-day
PM~10~ concentration at the official stations***. It is based on
observed meteorological data. Yet, as suggested in (Huebnerova &
Michalek, 2014), predictions delivered using forecasted weather
indicators is not expected influence significantly the prediction
accuracy reported in Section 4 of this text.

The **third module** of our methodology **(Module 3 at** **Figure 1)**
integrates results of Module 1 and Module 2. It builds predictive models
by geo-units. The module applies ARIMAX modelling, where the matrix of
exogenous features $\mathbf{X}$ is defined as follows:

$$\mathbf{X} = \left\lbrack \begin{matrix}
\text{PM}_{1t} & \cdots & {PM5}_{1t} \\
\end{matrix}\text{\ \ \ \ \ }\begin{matrix}
F_{1t} & \cdots & F_{\text{Jt}} \\
\end{matrix}\text{\ \ \ \ } \right\rbrack.$$

$\left\{ \text{PM}_{\text{it}},\ t = 1,\ldots,T \right\}$ denotes the
$\text{PM}_{10}$ concentration measurement at official station
$i,\ where\ i = 1,\ldots,\ 5$ and
$\mathbf{F} = \left\{ F_{j,t},t = 1,\ldots,\ T;j = 1,\ldots,\ J \right\}$
is the features matrix generated by Module 2. Prior to fitting ARIMAX
parameters we apply LASSO[^2] so as to perform feature selection. We
should note that this approach incorporates ***additional corrective
modelling*** for the cleaned citizen network data through introduction
of $\left\{ \text{PM}_{\text{it}},\ t = 1,\ldots,T \right\}$ in the
ARIMAX model specification[^3], where $i$ is selected via the adopted
LASSO approach. ***The output of Module 3 is prediction model for
next-day PM~10~ concentration at geo-units***. Predictions could be
delivered by using the prediction output of Module 2.

Figure 1: Methodology framework.

Module 1
========

Module 2
========

This part of the text provides brief summary of our key findings on
Module 2 followed by a detailed exhibition of our empirical analysis. We
first present some of the most important data characteristics followed
by a description of the data preparation process. On the basis of the
performed preliminary analysis we chose random forest as our core
modelling approach. At the same time, the stage of preliminary analysis
supports **the process of feature engineering**. The latter is presented
in greater detail as it forms an **important contribution both to the
topic of Sofia air pollution modelling as well as to the general strand
in literature engaged with air pollution predictive models**. Next, we
present results of model estimation and highlight which variables are
the strongest predictors. Out-of-sample prediction accuracy is reported
at the end of the section.

Summary of key findings
-----------------------

Empirical Analysis
------------------

This part of the text provides detailed information on the performed
empirical analysis related to Module 2 of our research. The flowchart at
presents the core stages of our analysis.

Figure 2: Empirical analysis of Module 2: Workflow.

### Data Description (Understanding)

Table 1: Descriptive statistics of hourly
$\mathbf{\text{PM}}_{\mathbf{10}}$ concentration measurements at the
official stations in Sofia.

  **Station code**      **9421**              **9572**              **9616**              **9642**              **60881**
  --------------------- --------------------- --------------------- --------------------- --------------------- ---------------------
  Start date and time   2017-12-02 18:00:00   2017-12-02 18:00:00   2017-12-02 18:00:00   2017-12-02 18:00:00   2018-01-01 02:00:00
  End date and time     2018-09-14 23:00:00   2018-09-15 00:00:00   2018-09-15 00:00:00   2018-09-15 00:00:00   2018-09-14 20:00:00
  Number of obs.        6869                  6870                  6870                  6870                  6162
  Number of NAs         316                   185                   834                   254                   165
  Mean                  18.98                 34.07                 35.63                 33.49                 30.32
  Median                13.39                 23.10                 25.02                 24.07                 22.78
  Min                   0.09                  2.12                  4.03                  0.30                  5.45
  Max                   298.55                689.65                479.30                419.12                483.37
  1^st^ Quartile        9.08                  15.44                 17.88                 16.35                 16.41
  3^rd^ Quartile        20.11                 34.79                 36.97                 34.92                 31.68

This module is based on time series data of $\text{PM}_{10}$
concentration measurements at five official stations in Sofia as
published by the European Environment Agency. The raw data is hourly
sampled. Table 1 presents data summary statistics. As might be seen
hourly measurements are characterized by extreme maximum values and
asymmetric (left-skewed) frequency distributions. Also, one of the
stations[^4] is characterized by higher number of missing observations
amounting to approximately 12% of the entire sample. The latter findings
suggest that:

-   ![](media/image7.tiff){width="3.8152777777777778in"
    height="2.173611111111111in"}Data interpolation should be
    introduced. As might the seen from Figure 3, a long period is
    missing for station 9616. Therefore, we should apply conservative
    interpolation technique.

-   Averaging observations on daily basis would reduce noise and
    asymmetric distributional properties. Furthermore, the level of
    $\text{PM}_{10}$ concentration is subject to regulations on average
    24-hours basis.

The second source of data consists of meteorological information
published by Sofia Airport.

### Data Preparation

As explained in section 4.2.1 we would first interpolate missing values.
Linear interpolation is applied as more flexible opportunities such as
spline interpolation are not well-suited in case of long consequtive
periods of missing data. As a next step of our analysis hourly
$\text{PM}_{10}\ $measurements by stations are aggregated on daily basis
through averaging in time. The more important descriptive statistics of
the transformed dataset are summarized in

### Preliminary (Exploratory) Analysis

### Feature Engineering

### Predictive Modelling

### Validation (Out-of-Sample Accuracy)

Appendix M2
-----------

Module 3
========

Summary of key findings
-----------------------

TBD

Empirical Analysis
------------------

### Data description

Module 3 of this project involves the same datasets used in Module 1 and
Module 2.

-   Citizen science measurements of AirSofia.info

-   Official measurements of EEA

-   Satellite data on topography of Sofia

-   Weather data as published by Sofia Airport Weather Station

All those different types of data are important to our research as they
have a correlational impact i.e. windy weather might cause more
pollution to be dispersed while pleasant weather allows pollution to
build up.

### Data preparation

TBD

### Preliminary Analysis

TBD

### Feature Engineering

In order to define the best possible set of predictors for our model in
Module 3, we have used the so-called Lasso method. In statistics and
machine learning, Lasso (least absolute shrinkage and selection
operator; also Lasso or LASSO) is a regression analysis method that
performs both variable selection and regularization in order to enhance
the prediction accuracy and interpretability of the statistical model it
produces.

What LASSO does well is to provide a principled way to reduce the number
of features in a model. In contrast, automated feature selection based
on standard linear regression by stepwise selection or choosing features
with the lowest p-values has many drawbacks. Lasso involves a penalty
factor that determines how many features are retained. Using
cross-validation to choose the penalty factor helps assure that the
model will generalize well to future data samples.

### Predictive modelling

[ARIMA model]{.underline}

The predictive model used in Module 3 is one of the most popular models
for time series analysis and prediction -- ARIMA. An ARIMA model is a
class of statistical model for analyzing and forecasting time series
data. ARIMA is an acronym that stands for AutoRegressive Integrated
Moving Average. It is a generalization of the simpler AutoRegressive
Moving Average and adds the notion of integration. This acronym is
descriptive, capturing the key aspects of the model itself. Briefly,
they are:

-   **AR:** Autoregression. A model that uses the dependent relationship
    between an observation and some number of lagged observations.

-   **I:** Integrated. The use of differencing of raw observations (i.e.
    subtracting an observation from an observation at the previous time
    step) in order to make the time series stationary.

-   **MA:** Moving Average. A model that uses the dependency between an
    observation and residual errors from a moving average model applied
    to lagged observations.

Each of these components are explicitly specified in the model as a
parameter.

A standard notation is used of ARIMA(p,d,q) where the parameters are
substituted with integer values to quickly indicate the specific ARIMA
model being used. The parameters of the ARIMA model are defined as
follows:

-   **p:** The number of lag observations included in the model, also
    called the lag order.

-   **d:** The number of times that the raw observations are
    differenced, also called the degree of differencing.

-   **q:** The size of the moving average window, also called the order
    of moving average.

[auto.arima R function]{.underline}

Returns best ARIMA p,d,q order according to either AIC, AICc or BIC
value. The function conducts a search over possible model within the
order constraints provided.

### Validation

TBD

Conclusion
==========

Acknowledgement
===============

References
==========

Catalano, M. et al., 2016. Improving the prediction of air pollution
peak episodes generated by urban transport network. *Environmental
Science & Plicy,* Volume 60, pp. 69-83.Cortina-Januchs, M.,
Quintanilla-Dominguez, J., Vega-Corona, A. & Andina, D., 2015.
Development of a model for forecasting of PM10 concentrations in
Salamanca, Mexico. *Atmospheric Pollution Research,* Volume 6, pp.
626-34.Feng, X. et al., 2015. Artificial neural networks forecasting of
PM2.5 pollution using air mass trajectory based geographic model and
wavelet transformation. *Atmospheric Environment,* Volume 107, pp.
118-28.Huebnerova, Z. & Michalek, J., 2014. Analysis of daily average
PM10 predictions by generalized linear models in Brno, Czech Republic.
*Atmospheric Pollution Research,* Volume 5, pp. 471-76.Kolehmainen, M.,
Martikainen, H. & Ruuskanen, J., 2001. Neural networks and periodic
components used in air quality forecasting. *Atmospheric Environment,*
Volume 35, pp. 815-25.Kurt, A., Gulbagci, B., Karaca, F. & Alagha, O.,
2008. An online air pollution forecasting system using neural networks.
*Environment International,* Volume 34, pp. 592-98.Russo, A. et al.,
2015. Neural network forecast of daily pollution concentraion using
optimal meteorological data at synoptic and local scales. *Atmospheric
Pollution Research,* Volume 6, pp. 540-49.Siwek, K. & Osowski, S., 2016.
Data mining methods for prediction of air pollution. *Intrenational
Journal of Applied Mathematics and Computer Science,* 26(2), pp. 467-78.

[^1]: EC/2008/50.

[^2]: Least absolute shrinkage and selection operator.

[^3]: Technically speaking, if after cleaning data on $\text{PM}_{10}$
    concentrations by geo-units still some mismeasurements are left,
    they should be absorbed in the vector of residuals the estimated
    ARIMA equation.

[^4]: Station coded as 9642.
