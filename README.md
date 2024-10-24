# Deep Imbalanced Regression for Ventilator Pressure Prediction

**Abstract:** This project presents deep imbalanced regression approaches to simulate the pressure of a mechanical ventilator. In many real-world settings, imbalanced data impedes model performance of learning algorithms, like neural networks, mostly for rare cases. Ventilator pressure data, which was collected from a modified open-source ventilator exhibits imbalance distribution, where certain target values have significantly fewer observations. This paper exploits recent studies and provides a simulator based on a deep imbalance regression model to predict the airway pressure in the respiratory circuit during the inspiratory phase of a breath given a time series of control parameters and lung attributes. These approaches demonstrate the effectiveness of deep imbalance regression in tracking pressure waveforms compared to traditional deep learning models.

## Data Processing
Dataset: https://www.kaggle.com/c/ventilator-pressure-prediction

- **Feature Engineering**  
We started with 3 initial features [time_step, u_in, u_out] and 85 engineered features. All features except R and C were used as-is, while R and C were one-hot encoded for type information. Over 70 features were designed to improve model convergence and lower MAE scores. Statistical checks like multicollinearity and serial correlation were performed without significant findings.

- **Data Normalization**  
RobustScaler was used to shrink the dataset, speed up model training, and limit outlier effects. It removes the median and scales data based on the [20,80] quantile range, reducing variance. Centering and scaling are done independently for each feature, and the transform method stores the relevant statistics for future use.

## Results

Following (Liu et al.,2019), we divide the target space into three disjoint subsets:
many-shot region (bins with over 100 training samples), medium-shot region (bins
with 20100 training samples), and few-shot region (bins with under 20 training sam-
ples), and report results on these subsets, as well as overall performance.

| Shot  | MSE   | L1    | R2 Score |
|-----------|-------|-------|----------|
| Overall   | 0.608 | 0.431 | 0.991    |
| Many      | 0.209 | 0.277 | -0.000   |
| Median    | 1.399 | 0.752 | -0.003   |
| Low       | 3.756 | 1.315 | -1.264   |


<img width="360" alt="{ACA2011C-8DD2-4B0C-951A-0211BB7F691D}" src="https://github.com/user-attachments/assets/4a24d0f4-9666-41a5-ab8c-eea49b715aa7">



*for more details, please read ```manuscript.pdf``` file*


## References

[1] Author, Yuzhe Yang, Kaiwen Zha, Ying-Cong Chen, Hao Wang, Dina Katabi, Delving into
Deep Imbalanced Regression, 13 May 2021

[2] Author, Michael Steininger1, Konstantin Kobs1, Padraig Davidson1, Anna Krause1, Andreas
Hotho1, Density-based weighting for imbalanced regression, 2021

[3] Author, Abdelghani Belgaid, Deep Sequence Modeling for Pressure Controlled Mechanical
Ventilation, March 4, 2022.


