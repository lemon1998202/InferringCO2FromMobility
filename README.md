# InferringCO2FromMobility
This is the repository for all analysis used in Wang et al "Inferring Carbon Emissions from Human Mobility Data".
## Computational environment

```
Python version 3.7.4 
JupyterNotebook Anaconda3
Platform: Intel(R) Core(TM) i7-10875H CPU @ 2.30GHz   2.30 GHz (64-bit)
Running under: Windows Feature Experience Pack1000.19053.1000.0
```
Python packages versions are specified as follows:

```
[1] conda                     4.12.0           py37h03978a9_0    conda-forge
[2] lightgbm                  3.0.0            pypi_0            pypi
[3] matplotlib                3.4.2            pypi_0            pypi
[4] networkx                  2.6.1            pypi_0            pypi
[5] numpy                     1.21.5           pypi_0            pypi
[6] pandas                    1.3.5            pypi_0            pypi
[7] scikit-learn              0.24.1           pypi_0            pypi
[8] scipy                     1.7.3            pypi_0            pypi
[9] seaborn                   0.12.1           pypi_0            pypi
[10] tqdm                     4.36.1           py_0              defaults
[11] xgboost                  1.6.2            pypi_0            pypi
```


## 1. CO<sub>2</sub> emissions data
This dataset is sourced from the Global Gridded Daily CO2 Emissions Dataset (GRACED), accessible at https://carbonmonitor-graced.com/. This dataset supports the work in Scientific Data 7, 392 (2020), Nature Communication 11, 5172 (2020), The Innovation, 2022, 3(1) and Scientific Data 10, 69 (2023). GRACED has been processed to derive daily CO2 emission within distinct regional boundaries. [这里不同国家的区域划分单位请确认]
* **China** - Daily CO<sub>2</sub> emission for various cities in China from January 1, 2020, to February 29, 2020.
* **Italy** - Daily CO<sub>2</sub> emission for various cities in Italy from January 1, 2020, to June 30, 2020.
* **Mexico** - Daily CO<sub>2</sub> emission for various cities in Mexico in the year 2020.
* **USA-County** - Daily CO<sub>2</sub> emission for various counties in the United States from January 1, 2020, to February 29, 2020.
* **USA-State** - Daily CO<sub>2</sub> emission for various states in the United States from January 1, 2020, to February 29, 2020.

## 2. Mobility data
Mobility data for China, Italy, Mexico, and the United States.
* **China** - The mobility data for various cities in China, along with the population and latitude-longitude data stored in `city_long_lan_pop.csv`.
* **Italy** - The weighted daily origin-destination matrices for Italy are available at https://data.humdata.org/dataset/covid-19-mobility-italy.
* **Mexico** - The daily intermunicipal travel networks of Mexico are available at https://osf.io/42xqz/.
* **the USA** - The multiscale dynamic human mobility flow dataset for the U.S. can be accessed at https://github.com/GeoDS/COVID19USFlows.

## 3. Correlation
Result: Correlation between Human Mobility and CO<sub>2</sub> Emissions - Code Execution and calculations.

* **`spatiotemporal correlations.ipynb`** - Code for Subplots Fig. 1a-c: calculate changes in intercity mobility and CO<sub>2</sub> emissions of multi-source, domestic aviation, and ground transportation.
* **`calculatie global features.ipynb`** - Calculate global features using `Mobility Data`.
* **`calculatie node features.ipynb`** - Calculate node features using `Mobility Data`.
* **`correlations between network features and CO2 emissions.ipynb`** - Code for Fig. 1e: calculate the correlation coefficient.
* **global** - Results of `calculatie global features.ipynb`, with the summary available in `global_features.csv`.
* **node** - Results of `calculatie node features.ipynb`, with the summary available in `node features.csv`.

## 4. Prediction
Utilizing different strategies to predict carbon emissions with network features, population data and latitude-longitude features.[这里的特征名称需要确认一下]
* **`LGBM-strategy1.ipynb`** and **`LGBM-strategy2.ipynb`** - The respective code for Strategy 1 and Strategy 2.
* **`res_lgbm_s1.csv`** and **`res_lgbm_s2.csv`** - The respective prediction result of `LGBM-strategy1.ipynb` and `LGBM-strategy2.ipynb`.
* **`plot the predicted result.ipynb`** - Code for Fig. 2: analyze the relations between the predicted CO2 emissions and observed CO<sub>2</sub> emissions for each strategy.

## 5. Evaluation
Evaluate the importance of features and perform robustness analysis.
* **`LGBM-strategy1-null model.ipynb`** and **`LGBM-strategy2-null model.ipynb`** - The different strategies for predicting CO<sub>2</sub> emissions with population and latitude-longitude features.
* **`res_lgbm_s1_null.csv`** and **`res_lgbm_s2_null.csv`** - The respective prediction result of `LGBM-strategy1-null.ipynb` and `LGBM-strategy2-null.ipynb`.
* **`ablation experiment.ipynb`** - Code for Fig. 3c: conduct ablation experiments.
* **`prediction with all historial data.ipynb`** - Code for Fig. 3d: predict CO<sub>2</sub> emissions with all history data.


## 6.extrapolation
In a consistent approach, we computed input data for predictive models for various countries by incorporating network features from their respective `mobility data`. The outcomes were then stored in the specified files. Subsequently, the data and predictive model were employed to generate the results in Fig. 4.
* **`input_Italy.csv`**
* **`input_Mexico.csv`**
* **`input_USA_county.csv`**
* **`input_USA_state.csv`**

## 7.city clusters
* **`city cluster- normal times.csv`** - The input data for `city cluster.ipynb`, includes total CO<sub>2</sub> emission data for cities, along with information about their respective urban clusters.
* **`city cluster.ipynb`** - Code for Fig. 5: analyze the characteristics of human mobility and CO<sub>2</sub> emissions in urban clusters.
