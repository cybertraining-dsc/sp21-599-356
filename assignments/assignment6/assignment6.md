# Forecasting Natural Gas Demand/Supply

Author: Baekeun Park

## Problem

South Korea relies on foreign imports for 92.8 percent of its energy resources as of the first half of 2020 [^1]. Among the energy resources, the Korea Gas Corporation imports Liquified Natural Gas(LNG) from around world and supplies it to power generation plants, gas-utility companies and city gas companies throughout the country [^2]. It produces and supplies Natural Gas(NG), in order to ensure stable gas supply for the nation. And it operates LNG storage tanks at LNG acquisition bases which can store LNG during the season when city gas demand is low and replenish LNG during winter when demand is higher than supply [^3]. 

The wholesale charges consist of raw material costs (LNG introduction and incidental costs) and gas supply costs through the main gas pipeline [^4]. It menas that wholesale charges include LNG production costs(NG to LNG), LNG transportation costs, LNG storage tanks operation and maintenance costs, and NG production costs(LNG to NG). Therefore, the forecasting NG demand/supply will not only help establish an optimized mid-to-long-term plan for the introduction of LNG, but also stable NG supply and economic effects.

## Dataset

There is a NG supply dataset[^5] from public data portal in South Korea. It includes four years of regional monthly NG supply. In addition, climate data[^6] for the same period can be obtained from the Korea Meteorological Administration. Similarly, data on the price of four types of oil[^7] and coal[^8] imported from the four countries are also available through corresponding agencies.

## Data Preprocessing

Python has a famous package, Pandas[^9], which can be used for the data preprocessing to deal with various type and shape of data. There may also be situations in which one-hot encoding[^10] is used, where some transformation can be performed to better train the network.

## Deep Learning Algorithm

Tensorflow[^11] is an end-to-end open source platform for machine learning and deep learning. It can be combined with Keras[^12] to develop the model. 

## Timeline

Week1: Find more related dataset, AI algorithms and works

Week2: Perform data preprocessing 

Week3: Design network model

Week4-Week5: Forecast NG demand/supply and Complite project

## References

[^1]: 2020 Monthly Energy Statistics, http://www.keei.re.kr/keei/download/MES2009.pdf, Sep. 2020

[^2]: Online Resource, https://www.kogas.or.kr:9450/eng/contents.do?key=1498

[^3]: Online Resource, https://www.kogas.or.kr:9450/portal/contents.do?key=2014

[^4]: Online Resource, https://www.kogas.or.kr:9450/portal/contents.do?key=2024

[^5]: Natural Gas Supply dataset, https://www.data.go.kr/data/15049904/fileData.do

[^6]: Regional Climate dataset, https://data.kma.go.kr/climate/RankState/selectRankStatisticsDivisionList.do?pgmNo=179

[^7]: Crude Oil Price dataset, https://www.petronet.co.kr/main2.jsp

[^8]: Bituminous Coal Price and Nations dataset, https://www.kigam.re.kr/menu.es?mid=a30102030203

[^9]: pandas, https://github.com/pandas-dev/pandas

[^10]: One-Hot Encoding, https://towardsdatascience.com/what-is-one-hot-encoding-and-how-to-use-pandas-get-dummies-function-922eb9bd4970

[^11]: Tensorflow, https://github.com/tensorflow/tensorflow

[^12]: Keras, https://github.com/keras-team/keras