# machine-learning-challenge

## Random Forest Model

Ran this model a few different times with different estimator sets [200, 100, 50, 25, 15]. The training and testing scores decreased as the estimators were decreased but all test scores stayed above 99% and all test scores stayed above 89%. The scores and classification report displayed are for 200 estimators since the model seemed to perform better with more `n_estimators`.

### Preprocessing the Data

All columns used sans `koi_tce_plnt_num` since that was a planet number designator.
`koi_disposition` used as the y value in each of the models.
`x` values were scaled and `y` values were encoded as follows: `[0: 'CANIDATE', 1: 'CONDIRMED', 2: 'FALSE POSITIVE']`

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



## Model_2

