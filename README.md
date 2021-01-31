# machine-learning-challenge

When comparing the different results of the models below, it was found that the [randomForest](https://github.com/meielerol/machine-learning-challenge/blob/main/model_randomForest.ipynb) model had the highest accuracy at 0.91, [model_1](https://github.com/meielerol/machine-learning-challenge/blob/main/model_1.ipynb) with 0.86, and [model_2](https://github.com/meielerol/machine-learning-challenge/blob/main/model_2.ipynb) following with 0.82.

The [model_2] predicted the most `CANIDATE` cases correctly, the [randomForest] model predicted the most `CONFIRMED` cases correctly, and all three models predicted 99% corectly for `FALSE POSITIVE` cases. The [randomForest] model caught the most `CANIDATE` positive cases correctly, the [model_2] caught the most `CONFIRMED` positive cases correctly, and all three models caught 100% of the `FALSE POSITIVE` positive cases correctly.

## Random Forest Model

Ran this model a few different times with different estimator sets [200, 100, 50, 25, 15]. The training and testing scores decreased as the estimators were decreased but all test scores stayed above 99% and all test scores stayed above 89%. The scores and classification report displayed are for 200 estimators since the model seemed to perform better with more `n_estimators`.

### Preprocessing the Data

All columns used sans `koi_tce_plnt_num` since that was a planet number designator.
`koi_disposition` used as the y value in each of the models.
`x` values were scaled and `y` values were encoded as follows: `[0: 'CANIDATE', 1: 'CONFIRMED', 2: 'FALSE POSITIVE']`

### Tuning the Model

The decision tree clasifier and random forest classifiers were used to model and discover the most & least important features of the data set.

Most imporant features with > 5%:
* 10.97% `koi_fpflag_co` - Centroid Offset Flag
* 9.79% `koi_fpflag_nt` - Not Transit-Like Flag
* 6.59% `koi_fpflag_ss` - Stellar Eclipse Flag
* 5.60% `koi_model_snr` - Transit Signal-to-Noise
* 5.36% `koi_prad` - Planetary Radius (Earth radii)

Least important features with < 1%:
* 0.84% `koi_srad_err2` - Negative Error: Stellar Radius (solar radii)
* 0.88% `koi_srad` - Stellar Radius (solar radii)
* 0.92% `koi_slogg_err1` - Positive Error: Stellar Surface Gravity (log10(cm s-2)
* 0.95% `koi_slogg` - Stellar Surface Gravity (log10(cm s-2)
* 0.96% `koi_steff` - Stellar Effective Temperature (Kelvin)
* 0.99% `koi_slogg_err2` - Negative Error: Stellar Effective Temperature (Kelvin)

### Scores and Classification Report

Training Data Score: 1.0

Testing Data Score: 0.9118993135011442

Grid Search Best Parameters: 

Grid Search Best Score: 0.8910912974188431

Classification Report: 
<p align="center"><img src="https://github.com/meielerol/machine-learning-challenge/blob/main/Images/classificationReport-model_randomForest-200.png" alt="Random Forest Classification Report"></p>

## Model_1

### Preprocessing the Data

All columns used sans `koi_tce_plnt_num` since that was a planet number designator.
`koi_disposition` used as the y value in each of the models.
`x` values were scaled and `y` values were encoded as follows: `[0: 'CANIDATE', 1: 'CONFIRMED', 2: 'FALSE POSITIVE']`

### Tuning the Model

This [model_1](https://github.com/meielerol/machine-learning-challenge/blob/main/model_1.ipynb) was run without removing any more additional columns than what was ran in the [randomForest](https://github.com/meielerol/machine-learning-challenge/blob/main/model_randomForest.ipynb) model so that a baseline could be created for comparing to [model_2](https://github.com/meielerol/machine-learning-challenge/blob/main/model_2.ipynb) when less features would be considered.

A `linear` support vector machine (SVM) classifier was used in creating [model_1] and a grid parameter of `{'C':[1,5,10], 'gamma':[0.001,0.001,0.01]}` was used.

### Scores and Classification Report

Training Data Score: 0.8371161548731643

Testing Data Score: 0.8564073226544623

Grid Search Best Parameters: {'C': 10, 'gamma': 0.001}

Grid Search Best Score: 0.8651509252723424

Classification Report: 
<p align="center"><img src="https://github.com/meielerol/machine-learning-challenge/blob/main/Images/classificationReport-model_1.png" alt="model_1 Classification Report"></p>

## Model_2

### Preprocessing the Data

Most columns used sans `koi_tce_plnt_num` since that was a planet number designator and columns `koi_srad`, `koi_srad_err1`, `koi_srad_err2`, `koi_slogg`, `koi_slogg_err1`, `koi_slogg_err2`, `koi_steff`, `koi_slogg_err1`,`koi_slogg_err2`.
`koi_disposition` used as the y value in each of the models.
`x` values were scaled and `y` values were encoded as follows: `[0: 'CANIDATE', 1: 'CONFIRMED', 2: 'FALSE POSITIVE']`

### Tuning the Model

This [model_2](https://github.com/meielerol/machine-learning-challenge/blob/main/model_2.ipynb) was run with removing the least significant features + their error values found by the [randomForest](https://github.com/meielerol/machine-learning-challenge/blob/main/model_randomForest.ipynb) model so that the results could be compared to [model_1](https://github.com/meielerol/machine-learning-challenge/blob/main/model_1.ipynb) and see which one performed better.

A `linear` support vector machine (SVM) classifier was used in creating [model_2] and a grid parameter of `{'C':[1,5,10], 'gamma':[0.001,0.001,0.01]}` was used.

### Scores and Classification Report

Training Data Score: 0.808697310699981

Testing Data Score: 0.8180778032036613

Grid Search Best Parameters: {'C': 10, 'gamma': 0.001}

Grid Search Best Score: 0.8580933131517476

Classification Report: 
<p align="center"><img src="https://github.com/meielerol/machine-learning-challenge/blob/main/Images/classificationReport-model_2.png" alt="model_2 Classification Report"></p>