# Flattener Trading Strategy

## Abstract

This project is completed during October 2017 as a milestone project for the fix income topics of my investment course. Fix income securities consists of sophisticated opreating mechanisms, which makes trading on such securities quite complicated. Often the strategies delivered in an academic setting are tremendously simplified. In this project, however, the only simplification we made is the usage of zero coupon bond. The specific instructions could be found in the  [Instructions](./Instructions.pdf) file in this repository.

## Acknowledgements

I would like to thank my fellow teammates, Yilan He, Su Bin Kwon, Nakul Thakare for their great contributions to making this project came to fruitrition.

## Background

Yield curve spread trades provide a wide variety of market participants the opportunity to generate returns and effectively hedge portfolios. In this project, We review the yield curve spread trade mechanics and execution of a flattener strategy using 2-year and 10-year zero coupon Treasury bonds. We have taken the daily U.S. Treasury yield data from Federal Reserve Board website for 2 year
and 10 year zero coupon bonds. This has the daily parameters needed to calculate the yield of any maturity bond by the Nelson-Siegel-Svensson yield curve model. The time period for analysis is from 30 December 1983 to 30 June 2017. 

## Strategy

We start with $1 million in initial capital and have 10% capital requirement in our trading positions. We setup a **DV01-neutral** yield curve spread trade by longing the 10-year Treasury bond (Back leg) and shorting 2-year Treasury bond (Front leg). This will essentially lead to flattening of the yield curve. We **rebalance our portfolio every week**. We **earn interest on the cash position** which is the value of the short position minus the value of the long position plus the amount of capital held against these positions. We **assume one-week Treasury yield as the interest rate**. 

We **close out our positions every week** and **invest the capital at the end of the week** (initial capital + portfolio revenue + interest) and rebalance our portfolio. We continue this process every week till June 30, 2017.

[![Flattener_Trading_Strategy_-_Report.jpg](https://s18.postimg.org/vd111p8p5/Flattener_Trading_Strategy_-_Report.jpg)](https://postimg.org/image/eci4t0vnp/)

## Main Hurdles and Their Solutions

In this project, we take passsage of time into account - that is, a 10 - year zero coupon bond will become 9-year-and-358-day bond every time we clear out our positions. 10 year yield are quite simple to obtain, as they are posted by the governments. The 9-year-and-358-day yield need to be obtained by the Nelson-Siegel-Svensson formula (shown below), the formula that is being used to estimate off-the-run bond yields by the Fed. 

[![Capture.png](https://s18.postimg.org/4y7lvhxsp/Capture.png)](https://postimg.org/image/vja4r205x/)

The parameters <a><img src="https://latex.codecogs.com/gif.latex?\inline&space;\beta" title="\beta" /></a> and <a><img src="https://latex.codecogs.com/gif.latex?\tau" title="\tau" /></a> could be obtained by from the [Federal Reserve Board Datasite](https://www.federalreserve.gov/pubs/feds/2006/200628/200628abs.html) together with the 10-year and 2-year yields. The specific execution of the trading strategy could be found in the [FlattenerTrade.R](./FlattenerTrade.R) file, and the report of this project could be found in the [Flattener Trading Strategy - Report](./Flattener_Trading_Strategy-Report.pdf) file

## Result Highlights

We ploted the decomposed total return by its different components -  the spread return, the time return, the convexity return. We found the residual return of taking the difference of total return and its decomposed return is very small - indicating that the authenticity of the return decomposition. The plot is shown below.

[![Flattener_Trading_Strategy_-_Report.jpg](https://s18.postimg.org/omkjsbyex/Flattener_Trading_Strategy_-_Report.jpg)](https://postimg.org/image/qedin8hrp/)
