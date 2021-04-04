# Forecasting Natural Gas Demand/Supply

:o2: this is not proper markdown

Author: Baekeun Park

## Problem

South Korea relies on foreign imports for 92.8 percent of its energy resources as of the first half of 2020 [^1]. Among the energy resources, the Korea Gas Corporation imports Liquified Natural Gas(LNG) from around world and supplies it to power generation plants, gas-utility companies and city gas companies throughout the country [^2]. It produces and supplies Natural Gas(NG), in order to ensure stable gas supply for the nation. And it operates LNG storage tanks at LNG acquisition bases which can store LNG during the season when city gas demand is low and replenish LNG during winter when demand is higher than supply [^3]. 

The wholesale charges consist of raw material costs (LNG introduction and incidental costs) and gas supply costs [^4]. Therefore, the forecasting NG demand/supply will not only help establish an optimized mid-to-long-term plan for the introduction of LNG, but also stable NG supply and economic effects.

## Solution

There are many factors related to Gas demand/supply. Climate data such as temperature and humidity will be closely related. Also, data on other fossil fuels, such as oil and coal, which are used as power generation, can be used to forecast. 

Data preprocessing can be essential to make training data, because each data is from other area. Also, various AI algorithms such as deep learning, optimization and validation can be used in combination. 

## Open-Source Data

[Natural Gas Supply] https://www.data.go.kr/data/15049904/fileData.do

[Regional Climate] https://data.kma.go.kr/climate/RankState/selectRankStatisticsDivisionList.do?pgmNo=179

[Crude Oil Price] https://www.petronet.co.kr/main2.jsp

[Bituminous Coal Price and Nations] https://www.kigam.re.kr/menu.es?mid=a30102030203

## Data Preprocessing

[Pandas] (https://github.com/pandas-dev/pandas)

[One-Hot Encoding] (https://towardsdatascience.com/what-is-one-hot-encoding-and-how-to-use-pandas-get-dummies-function-922eb9bd4970)

## Deep-Learning Framework

[Tensorflow] (https://github.com/tensorflow/tensorflow)

[Keras] (https://github.com/keras-team/keras)

## References

[^1]: 2020 Monthly Energy Statistics, http://www.keei.re.kr/keei/download/MES2009.pdf, Sep. 2020

[^2]: Online Resource, https://www.kogas.or.kr:9450/eng/contents.do?key=1498

[^3]: Online Resource, https://www.kogas.or.kr:9450/portal/contents.do?key=2014

[^4]: Online Resource, https://www.kogas.or.kr:9450/portal/contents.do?key=2026