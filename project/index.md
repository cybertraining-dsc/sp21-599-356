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

South Korea relies on foreign imports for 92.8 percent of its energy resources as of the first half of 2020 [^1]. Among the energy resources, the Korea Gas Corporation(KOGAS) imports Liquified Natural Gas(LNG) from around world and supplies it to power generation plants, gas-utility companies and city gas companies throughout the country [^2]. It produces and supplies Natural Gas(NG), in order to ensure stable gas supply for the nation. And it operates LNG storage tanks at LNG acquisition bases which can store LNG during the season when city gas demand is low and replenish LNG during winter when demand is higher than supply [^3]. 

The wholesale charges consist of raw material costs (LNG introduction and incidental costs) and gas supply costs [^4]. Therefore, the forecasting NG demand/supply will not only help establish an optimized mid-to-long-term plan for the introduction of LNG, but also stable NG supply and economic effects.



* <https://github.com/cybertraining-dsc/hid-example/blob/main/project/index.md>

Here comes a convincing introduction to the problem

## 2. Related Work

The related works are.

## 2. Report Format

The report is written in (hugo) markdown and not commonmark. As such some features are not visible in GitHub. You can 
set up hugo on your local computer if you want to see how it renders or commit and wait 10 minutes once your report is 
bound into cybertraining.

It is to be noted that markdown works best if you include an empty line before and after each context change. 
Thus the following is wrong:

```
# This is My Headline
This author does ignore proper markdown while not using empty lines between context changes
1. This is because this author ignors all best practices
```

Instead, this should be 

```
# This is My Headline

We do not ignore proper markdown while using empty lines between context changes

1. This is because we encourage best practices to cause issues.
```

## 2.1. GitHub Actions

When going to GitHub Actions you will see a report is autmatically generated with some help on improving your markdown. 
We will not review any document that does not pass this check.

## 2.2. PAst Copy from Word or other Editors is a Disaster!

We recommend that you sue a proper that is integrated with GitHub or you use the commandline tools. We may include 
comments into your document that you will have to fix, If you juys past copy you will 

1. Not learn how to use GitHub properly and we deduct points
2. Overwrite our coments that you than may miss and may result in point deductions as you have not addressed them.

## 2.3. Report or Project

You have two choices for the final project. 

1. Project, That is a final report that includes code.
2. Report, that is a final project without code.

YOu will be including the type of the project as a prefix to your title, as well as in the Type tag
at the beginning of your project.

## 3. Using Images

![Figure 1](https://github.com/cybertraining-dsc/fa20-523-314/raw/main/project/images/chart.png)

**Figure 1:** Images can be included in the report, but if they are copied you must cite them [^1].

## 4. Using itemized lists only where needed

Remember this is not a powerpoint presentation, but a report so we recommend

1. Use itemized or enumeration lists sparingly
2. When using bulleted lists use * and not - 

## 3. Datasets

There is a NG supply dataset[^5] from public data portal in South Korea. It includes four years of regional monthly NG supply in South Korea (from 2016 to 2019, nine different cities). In addition, climate data[^6] for the same period can be obtained from the Korea Meteorological Administration. In the case of metropolitan cities such as Busan, the climate data for the city are used, while for areas larger than cities(e.g. Gyeonggi), the data for areas with supply stations are used. Similarly, data on the price of four types of oil[^7] and various types of coal price dataset per month[^8] are also available through corresponding agencies. Finally, the Won-Dollar exchange rate dataset with same period is used.

Datasets can be huge and GitHub has limited space. Only very small datasets should be stored in GitHub.
However, if the data is publicly available you program must contain a download function instead that you customize. 
Write it using pythons `request`. You will get point deductions if you check-in data sets that are large and do not use
the download function.

## 4. Method

## 4.1. Min-Max scaling

In this project, all datasets are rescaled between 0 and 1 by Min-Max scaling which is one of the most common normalization methods. If there is a feature with unspecified data, The maximum value(max(x)) of data is converted to 1, and the minimum value(min(x)) of data is converted to 0. The other values between the maximum value and the minimum value get converted to x' which can be between 0 and 1.

<img src="https://render.githubusercontent.com/render/math?math=x'%20%3D%20%5Cfrac%7Bx-min(x)%7D%7Bmax(x)-min(x)%7D">

## 4.2. Training

For forcasting the NG supply amount from time series dataset, MLP with LSTM network model is designed by using tensorflow. The first and second layer of LSTM has 100 units, and total 3 layers of MLP follow it. Each MLP layers has 100 neurons instead of the final layer where its neuron is 1. In addition, dropout was designated to prevent overfitting of data, Adam is used as an optimizer, and Rectified Linear Unit(Relu) as an activation function.

## 4.3. Evaluation

To evaluate this network model, Mean Absolute Error(MAE) and Root Mean Squared Error(RMSE) are applied. The MAE measures the average magnitude of the errors and is presented by the formula as following, where n is the number of errors, <img src="https://render.githubusercontent.com/render/math?math=y_i"> is the <img src="https://render.githubusercontent.com/render/math?math=i%5E%7Bth%7D"> true value, and <img src="https://render.githubusercontent.com/render/math?math=%5Chat%7By_i%7D"> is the <img src="https://render.githubusercontent.com/render/math?math=i%5E%7Bth%7D"> predicted value.

<img src="https://render.githubusercontent.com/render/math?math=MAE%20%3D%20%5Cfrac%7B%5CSigma_%7Bi%3D1%7D%5En%7Cy_i-%5Chat%7By_i%7D%7C%7D%7Bn%7D">

Also, The RMSE is used for observing the differences between real dataset and prediction values. The following is formula of RMSE and each values of this are same to them of MAE.

<img src="https://render.githubusercontent.com/render/math?math=RMSE%20%3D%20%5Csqrt%7B%5Cfrac%7B%5CSigma_%7Bi%3D1%7D%5En(y_i-%5Chat%7By_i%7D)%5E2%7D%7Bn%7D%7D">

## 4.4. Prediction



## 5. Result

## 6. Benchmark

Your project must include a benchmark. The easiest is to use cloudmesh-common [^2]
 
## 7. Conclusion

A convincing but not fake conclusion should summarize what the conclusion of the project is.

## 8. Acknowledgments

Please add acknowledgments to all that contributed or helped on this project.

## 9. References

Your report must include at least 6 references. Please use customary academic citation and not just URLs. As we will at 
one point automatically change the references from superscript to square brackets it is best to introduce a space before 
the first square bracket.

[^1]: 2020 Monthly Energy Statistics, [Online resource]
      <http://www.keei.re.kr/keei/download/MES2009.pdf>, Sep. 2020

[^2]: KOGAS profile, [Online resource]
      <https://www.kogas.or.kr:9450/eng/contents.do?key=1498>

[^3]: LNG production phase, [Online resource]
      <https://www.kogas.or.kr:9450/portal/contents.do?key=2014>

[^4]: NG wholesale charges, [Online resource] 
      <https://www.kogas.or.kr:9450/portal/contents.do?key=2026>

[^5]: NG supply dataset, [Online resource], 
      <https://www.data.go.kr/data/15049904/fileData.do>, Apr, 2020

[^6]: Regional climate dataset, [Online resource]
      <https://data.kma.go.kr/climate/RankState/selectRankStatisticsDivisionList.do?pgmNo=179>

[^7]: Crude oil orice dataset, [Online resource]
      <https://www.petronet.co.kr/main2.jsp>

[^8]: Bituminous coal price dataset, [Online resource]
      <https://www.kores.net/komis/price/mineralprice/ironoreenergy/pricetrend/baseMetals.do?mc_seq=3030003&mnrl_pc_mc_seq=506>

[^9] Won-Dollar exchange rate dateset, [Online resource]
      <http://ecos.bok.or.kr/flex/EasySearch.jsp?langGubun=K&topCode=022Y013>

[^1]: Use of energy explained - Energy use in homes, [Online resource] 
      <https://www.eia.gov/energyexplained/use-of-energy/electricity-use-in-homes.php>


[^2]: Gregor von Laszewski, Cloudmesh StopWatch and Benchmark from the Cloudmesh Common Library, [GitHub] 
      <https://github.com/cloudmesh/cloudmesh-common>

