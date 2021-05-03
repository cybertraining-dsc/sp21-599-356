# Project: Forecasting Natural Gas Demand/Supply

[![Check Report](https://github.com/cybertraining-dsc/sp21-599-356/workflows/Check%20Report/badge.svg)](https://github.com/cybertraining-dsc/sp21-599-356/actions)
[![Status](https://github.com/cybertraining-dsc/sp21-599-356/workflows/Status/badge.svg)](https://github.com/cybertraining-dsc/sp21-599-356/actions)
Status: in progress, Type: Project

* :o2: Author missing
* :o2: Abstract should be defined by now
* :o2: Refernces shoudl be defined by now
* :o2: Introduction missing
* :o2: Refernces missing

Baekeun Park, [sp21-599-356](https://github.com/cybertraining-dsc/sp21-599-356/), [Edit](https://github.com/cybertraining-dsc/sp21-599-356/blob/main/project/index.md)

{{% pageinfo %}}

## Abstract

The forecasting of Natural Gas(NG) supply amount in South Korea is represented in this project. 

Dataset from various fields such as climate and prices of other energy resources are used as train datasets through data-preprocessing, and are trained using deep-learning methods, especially Multi-Layer Perceptron(MLP) with Long Short Term Memory(LSTM), using Tensorflow. The test datasets are monthly 

Contents

{{< table_of_contents >}}

{{% /pageinfo %}}

**Keywords:** Natural Gas, MLP with LSTM, Tensorflow, example. 

## 1. Introduction

South Korea relies on foreign imports for 92.8 percent of its energy resources as of the first half of 2020 [^1]. Among the energy resources, the Korea Gas Corporation(KOGAS) imports Liquified Natural Gas(LNG) from around world and supplies it to power generation plants, gas-utility companies and city gas companies throughout the country [^2]. It produces and supplies NG, in order to ensure stable gas supply for the nation. And it operates LNG storage tanks at LNG acquisition bases which can store LNG during the season when city gas demand is low and replenish LNG during winter when demand is higher than supply [^3]. 

The wholesale charges consist of raw material costs (LNG introduction and incidental costs) and gas supply costs [^4]. Therefore, the forecasting NG demand/supply will not only help establish an optimized mid-to-long-term plan for the introduction of LNG, but also stable NG supply and economic effects.

The factors which influence to NG demand include weather, economic conditions, and petroleum prices. The winter weather strongly influences NG demand and the hot summer weather can increase electric power demand for NG. In addition, some large-volume fuel consumers such as power plants and iron, steel, and paper mills can switch between NG, coal, and petroleum, depending on the cost of each fuel [^5].

Therefore, some indicators related to weather, economic conditions and price of other energy resources can be used for this project.

## 2. Related Work

Khotanzad and Elragal (1999) proposed a two-stage system with the first stage containing a combination of artificial neural network(ANN) for prediction of daily NG consumption [^6], and Khotanzad et al. (2000) combined eight different algorithms to improve the performance of forecasters [^7]. Mustafa Akpinar et al. (2016) used daily NG consumption data to forecast the NG demand by ABC-based ANN [^8]. Also, Athanasios Anagnostis et al. (2019) conducted daily NG demand prediction by a comparative analysis between ANN and LSTM [^9]. Unlike those methods, MLP with LSTM is applied for this project, and external factors affecting NG demand are changed and compared.

## 3. Datasets

As described above, weather datasets like temperature and precipitation, price datasets of other energy resources like crude oil and coal, and economic indicators like exchange rate are used in this project for forecasting NG demand.

There is an NG supply dataset [^10] from a public data portal in South Korea. It includes four years from 2016 to 2019 of regional monthly NG supply in the nine different cities of South Korea. In addition, climate data such as temperature and precipitation [^11] for the same period can be obtained from the Korea Meteorological Administration. Similarly, data on the price of four types of crude oil [^12] and various types of coal price datasets per month [^13] are also available through corresponding agencies. Finally, the Won-Dollar exchange rate dataset [^14] with the same period is used.

As mentioned above, each dataset has monthly information. It is regionally separated or combined according to the test scenario. For example, the NG supply dataset has nine different cities. One column of cities is split from the original dataset and merged with another regional dataset like temperature or precipitation. On the other hand, in the case of the test scenario, where a national dataset is needed, the summation value of all column data is created and used for it.

The dataset is applied differently for each scenario. In the scenario one, all dataset such as crude oil price, coal price, exchange rate, and regional temperature and precipitation are merged with regional dataset, especially seoul city. For the scenario two, all climate dataset are used with regional dataset. Only temperature dataset is utilized with regional dataset in the scenario three. In addition, in the scenario four, all cases are the same as in the scenario one, but the timesteps are changed to two months. Finally, national dataset is used for the scenario five. 

![Figure 1](https://raw.githubusercontent.com/cybertraining-dsc/sp21-599-356/main/project/images/each_factors.png)

**Figure 1:** External factors affecting natural gas

## 4. Methodology

## 4.1. Min-Max scaling

In this project, all datasets are rescaled between 0 and 1 by Min-Max scaling, one of the most common normalization methods. If there is a feature with anonymous data, The maximum value(max(x)) of data is converted to 1, and the minimum value(min(x)) of data is converted to 0. The other values between the maximum value and the minimum value get converted to x', between 0 and 1.

<img src="https://render.githubusercontent.com/render/math?math=%5CLarge%20%5Cfrac%7Bx-min(x)%7D%7Bmax(x)-min(x)%7D">

## 4.2. Training

For forecasting the NG supply amount from the time series dataset, MLP with LSTM network model is designed by using Tensorflow. The first and second LSTM layers have 100 units, and a total of 3 layers of MLP follow it. Each MLP layer has 100 neurons instead of the final layer, where its neuron is 1. In addition, dropout was designated to prevent overfitting of data, Adam is used as an optimizer, and Rectified Linear Unit(Relu) as an activation function.

![Figure 2](https://raw.githubusercontent.com/cybertraining-dsc/sp21-599-356/main/project/images/structure_of_network.png)

**Figure 2:** Structure of network model

## 4.3. Evaluation

To evaluate this network model, Mean Absolute Error(MAE) and Root Mean Squared Error(RMSE) are applied. The MAE measures the average magnitude of the errors and is presented by the formula as following, where n is the number of errors, <img src="https://render.githubusercontent.com/render/math?math=y_i"> is the <img src="https://render.githubusercontent.com/render/math?math=i%5E%7Bth%7D"> true value, and <img src="https://render.githubusercontent.com/render/math?math=%5Chat%7By_i%7D"> is the <img src="https://render.githubusercontent.com/render/math?math=i%5E%7Bth%7D"> predicted value.

<img src="https://render.githubusercontent.com/render/math?math=%5CLarge%20MAE%20%3D%20%5Cfrac%7B%5CSigma_%7Bi%3D1%7D%5En%7Cy_i-%5Chat%7By_i%7D%7C%7D%7Bn%7D">

Also, The RMSE is used for observing the differences between the real dataset and prediction values. The following is the formula of RMSE, and each value of this is same for MAE.

<img src="https://render.githubusercontent.com/render/math?math=%5CLarge%20RMSE%20%3D%20%5Csqrt%7B%5Cfrac%7B%5CSigma_%7Bi%3D1%7D%5En(y_i-%5Chat%7By_i%7D)%5E2%7D%7Bn%7D%7D">

## 4.4. Prediction

Since the datasets used for the training are normalized between 0 and 1, they get converted to a range of the ground truth values. From these rescaled datasets, it is possible to obtain the RMSE and compare the differences between a actual value and a predicted value.

## 5. Result

In all scenarios, main variables such as dropout, learning rate, and epochs are fixed under the same conditions and are 0.1, 0.0005, and 100 in order. In scenarios one, two, three, and five, the training set is applied as twelve months, and in scenario four, next month's prediction comes from the previous two months dataset. Each scenario shows individual results and is comprehensively compared at the end of this part. 

## 5.1 Scenario one(regional dataset)

The final MAE of train set is around 0.05 and the one of test set is around 0.19. The RMSE between real data and predicted data is around 227018. The predictive graph tends to deviate a lot at the beginning of epochs, but it shows quite a bit of agreement at the end of epochs.

![Figure 3](https://raw.githubusercontent.com/cybertraining-dsc/sp21-599-356/main/project/images/Error_For_SenarioOne.png)

**Figure 3:** Loss for scenario one

![Figure 4](https://raw.githubusercontent.com/cybertraining-dsc/sp21-599-356/main/project/images/Prediction_for_SenarioOne.png)

**Figure 4:** Prediction results for scenario one

## 5.2 Scenario two(regional climate dataset)

The final MAE of train set is around 0.10 and the one of test set is around 0.14. The RMSE between real data and predicted data is around 185205. Although the predictive graph still differ compared to real graph, it shows similar trends in shape.

![Figure 5](https://raw.githubusercontent.com/cybertraining-dsc/sp21-599-356/main/project/images/Error_For_SenarioTwo.png)

**Figure 5:** Loss for scenario two

![Figure 6](https://raw.githubusercontent.com/cybertraining-dsc/sp21-599-356/main/project/images/Prediction_for_SenarioTwo.png)

**Figure 6:** Prediction results for scenario two

## 5.3 Scenario three(regional temperature dataset)

The final MAE of train set is around 0.13 and the one of test set is around 0.14. The RMSE between real data and predicted data is around 207585. While the tendency to follow high and low seems similar, but changes in the middle seem to be misleading.

![Figure 7](https://raw.githubusercontent.com/cybertraining-dsc/sp21-599-356/main/project/images/Error_For_SenarioThree.png)

**Figure 7:** Loss for scenario three

![Figure 8](https://raw.githubusercontent.com/cybertraining-dsc/sp21-599-356/main/project/images/Prediction_for_SenarioThree.png)

**Figure 8:** Prediction results for scenario three

## 5.4 Scenario four(applying timesteps)

The final MAE of train set is around 0.06 and the one of test set is around 0.30. The RMSE between real data and predicted data is around 340843. Out of all scenarios, the predictive graph shows to have the most differences. However, in the last part, there is a somewhat similar tendency.

![Figure 9](https://raw.githubusercontent.com/cybertraining-dsc/sp21-599-356/main/project/images/Error_For_SenarioFour.png)

**Figure 9:** Loss for scenario four

![Figure 10](https://raw.githubusercontent.com/cybertraining-dsc/sp21-599-356/main/project/images/Prediction_for_SenarioFour.png)

**Figure 10:** Prediction results for scenario four

## 5.5 Scenario five(national dataset)

The final MAE of train set is around 0.03 and the one of test set is around 0.14. The RMSE between real data and predicted data is around 587340. the largest RMSE value is the result, but direct comparisons are not possible because the baseline volume is different from other scenarios. Although the predictive graph shows differences, it tends to be similar to the results in the scenario two. 

![Figure 11](https://raw.githubusercontent.com/cybertraining-dsc/sp21-599-356/main/project/images/Error_For_SenarioFive.png)

**Figure 11:** Loss for scenario five

![Figure 12](https://raw.githubusercontent.com/cybertraining-dsc/sp21-599-356/main/project/images/Prediction_for_SenarioFive.png)

**Figure 12:** Prediction results for scenario five

## 5.6 Overall results

Out of the five scenarios in total, the second and third have smaller RMSE, and the graphs also show relatively similar results. The first and fourth show differences in the beginning and similar trends in the last part. However, it is noteworthy that the gap at the beginning of them is very large, but it tends to shrink together at the point of decline and stretch together at the point of increase.

![Figure 13](https://raw.githubusercontent.com/cybertraining-dsc/sp21-599-356/main/project/images/compared_prediction.png)

**Figure 13:** Total prediction results

## 6. Benchmarks

For a benchmark, the Cloudmesh StopWatch and Benchmark [^15] are used to measure the performance of the program. The time spent on data load, data preprocessing, network model compile, training, and prediction was separately measured, and the overall time for execution of all scenarios is around 77 seconds. It can be seen that The training time for the fourth scenario is the longest and the one for the fifth scenario is the shortest.

![Figure 14](https://raw.githubusercontent.com/cybertraining-dsc/sp21-599-356/main/project/images/benchmark_all.PNG)

**Figure 14:** Benchmarks

## 7. Conclusion

Through this project, it can be seen that simplification of factors that have a significant impact shows better efficiency than combining various factors. Simply considering, the cold weather requires more heating, which increases the demand for NG. In addition, when there is a lot of precipitation, the weather is warm or hot, and in contrast, when it is cold, the precipitation is relatively cold. It can be seen that these seasonal elements show relatively high consistency when used as datasets, and that predictions are more effective when combined. However, the last part of the scenario used the dataset combined with various factors tends to match real data, and the results might vary if a dataset with a longer period of time is used and the ratio of training set is adjusted.

In this project, forecasting NG demand and supply is carried out using external factors. As mentioned earlier, South Korea relies on imports for most of its energy resources. Market conditions may also be volatile depending on the government's energy policy direction. Therefore, efficient energy demand forecasts will have to be constantly supplemented and developed. In addition, it is believed that advanced forms of NG-related research should be conducted using various data and more professional analysis.

## 8. Acknowledgments

The author would like to thank Dr. Gregor von Laszewski for his invaluable feedback on this paper, and Dr. Geoffrey Fox for sharing his expertise in Deep Learning and AI applications throughout this course.

## 9. References

[^1]: 2020 Monthly Energy Statistics, [Online resource]
      <http://www.keei.re.kr/keei/download/MES2009.pdf>, Sep. 2020

[^2]: KOGAS profile, [Online resource]
      <https://www.kogas.or.kr:9450/eng/contents.do?key=1498>

[^3]: LNG production phase, [Online resource]
      <https://www.kogas.or.kr:9450/portal/contents.do?key=2014>

[^4]: NG wholesale charges, [Online resource] 
      <https://www.kogas.or.kr:9450/portal/contents.do?key=2026>

[^5]: Natural gas explained, [Online resource], 
      <https://www.eia.gov/energyexplained/natural-gas/factors-affecting-natural-gas-prices.php>, Aug, 2020

[^6]: A. Khotanzad and H. Elragal, "Natural gas load forecasting with combination of adaptive neural networks," IJCNN'99. International Joint Conference on Neural Networks. Proceedings (Cat. No.99CH36339), 1999, pp. 4069-4072 vol.6, doi: 10.1109/IJCNN.1999.830812.

[^7]: A. Khotanzad, H. Elragal and T. . -L. Lu, "Combination of artificial neural-network forecasters for prediction of natural gas consumption," in IEEE Transactions on Neural Networks, vol. 11, no. 2, pp. 464-473, March 2000, doi: 10.1109/72.839015.

[^8]: M. Akpinar, M. F. Adak and N. Yumusak, "Forecasting natural gas consumption with hybrid neural networks — Artificial bee colony," 2016 2nd International Conference on Intelligent Energy and Power Systems (IEPS), 2016, pp. 1-6, doi: 10.1109/IEPS.2016.7521852.

[^9]: A. Anagnostis, E. Papageorgiou, V. Dafopoulos and D. Bochtis, "Applying Long Short-Term Memory Networks for natural gas demand prediction," 2019 10th International Conference on Information, Intelligence, Systems and Applications (IISA), 2019, pp. 1-7, doi: 10.1109/IISA.2019.8900746.

[^10]: NG supply dataset, [Online resource], 
      <https://www.data.go.kr/data/15049904/fileData.do>, Apr, 2020

[^11]: Regional climate dataset, [Online resource]
      <https://data.kma.go.kr/climate/RankState/selectRankStatisticsDivisionList.do?pgmNo=179>

[^12]: Crude oil orice dataset, [Online resource]
      <https://www.petronet.co.kr/main2.jsp>

[^13]: Bituminous coal price dataset, [Online resource]
      <https://www.kores.net/komis/price/mineralprice/ironoreenergy/pricetrend/baseMetals.do?mc_seq=3030003&mnrl_pc_mc_seq=506>

[^14]: Won-Dollar exchange rate dateset, [Online resource]
      <http://ecos.bok.or.kr/flex/EasySearch.jsp?langGubun=K&topCode=022Y013>

[^15]: Gregor von Laszewski, Cloudmesh StopWatch and Benchmark from the Cloudmesh Common Library, [GitHub] 
      <https://github.com/cloudmesh/cloudmesh-common>

