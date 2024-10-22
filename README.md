# Analyze the Influence of Features Extracted from Audios on the Results of IELTS Speaking Test
This is a implementation of Analyze the Influence of Features Extracted from Audios on the Results of IELTS Speaking Test by me. It is accepted for presentation at the 2024 International Conference on Advanced Technologies for Communications (ATC) and soon will be published in the IEEE Xplore Digital Library

## Introduction
The demand for international English certifications like IELTS, TOEIC, and TOEFL has significantly increased in Vietnam's educational and employment sectors. While self-practice in reading and listening is common, developing speaking and writing skills requires supervision. Unfortunately, access to reputable preparation centers is limited, especially in rural areas, where high tuition fees can be prohibitive. Additionally, instructors struggle to correct speaking errors for multiple students, highlighting the need for an automated assessment system.

Our study aims to fill this research gap by enhancing English language learning for Vietnamese learners. We utilize data from a test preparation center in Ho Chi Minh City to extract meaningful features from audio recordings of speaking tests. Through statistical analysis, we examine how these features affect IELTS speaking scores. We also employ Machine Learning algorithms to predict scores based on the extracted features, yielding promising results. Our research provides valuable insights into speaking criteria assessment and identifies areas for improvement, enabling Vietnamese learners and teachers to adopt effective strategies for enhancing their scores.
## Data collection
<p align="center">
<img width="500" alt="{7FD73F31-E89D-4FF7-B271-470173C0EAE7}" src="https://github.com/user-attachments/assets/4e6a635d-3c2c-47c8-9eb5-97894a497c2d">
</p>


| Attribute         | Meaning                                                                                                                                                     |
|-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Mean hesitation    | The average degree of hesitation in speech. It can have values ranging from 0.0 to 1.0. It is calculated by the time gap between the pronunciation of the preceding word and the following word (subtracting the start time of the following word from the end time of the preceding word). |
| Mean conf         | The average confidence level, which ranges from 0.0 to 1.0.                                                                                              |
| Grammar point     | The grammatical score of the speech is calculated using Grammarly’s algorithm.                                                                              |
| Unique word       | The percentage of unique words spoken in the speech. Reflects the speaker’s vocabulary.                                                                    |
| Rare word         | The percentage of words spoken that are rare or less common. Reflects the speaker’s proficiency in advanced vocabulary.                                     |
| Number of words    | The total number of words in the speech (including repeated words).                                                                                       |
| Score             | The IELTS speaking score, which is also the target variable.                                                                                               |

## Data Analysis

Pearson Correlation Coeficients between featurea extracted and the target value
| Dependent Variable | r      | p-value      |
|--------------------|--------|--------------|
| Mean conf          | 0.136  | 8.581e-5     |
| Mean hesitation    | -0.017 | 0.61452      |
| Grammar point      | 0.187  | 6.197e-8     |
| Unique word        | 0.299  | 1.649e-18    |
| Rare word          | 0.256  | 7.635e-14    |
| Number of words    | 0.298  | 2.162e-18    |

The statistical data indicate that when considering the target
variable as a continuous variable, the extracted features are not
significant with the target variable except for the variable’s
Unique word and Number of words, which have correlation
coefficients ≈0.3 at a significance level <0.001.

One-way ANOVA Analysis between IELTS speaking score and feature values
| Dependent Variable | F       | p-value           |
|--------------------|---------|-------------------|
| Mean conf          | 11.499  | 5.630 × 10−14     |
| Mean hesitation    | 17.857  | 8.812 × 10−22     |
| Grammar point      | 4.548   | 5.409 × 10−05     |
| Unique word        | 13.602  | 1.060 × 10−16     |
| Rare word          | 11.565  | 4.621 × 10−14     |
| Number of word     | 15.198  | 9.332 × 10−19     |

<img width="400" alt="{65636A4B-6D95-4864-BB22-6195BE7E5FFE}" src="https://github.com/user-attachments/assets/a9e30ffc-6f52-4ea7-aa30-186e36695bd0">


The boxplots overlap significantly and do not
demonstrate classification between score levels. The result of
the F one-way ANOVA, with a low p value at high confidence (p value < 0.0001), indicates no significant difference
between the groups. However, when visualizing the groupings
between the dataset with IELTS speaking scores above 6.5
and the entire dataset in spider chart, we observe differences in the
values of the variables Grammar point, Unique word, Rare
word, Number of words, and Mean hesitation.

<p align="center">
<img width="600" alt="{9130AE12-87E5-4986-8B25-FC6E2982758A}" src="https://github.com/user-attachments/assets/b1baab54-29aa-4c3a-811b-d562363d9ad7">
</p>

## Model Prediction

| Metrics                        | MAE   | MSLE  | MAP    |
|---------------------------------|-------|-------|--------|
| Random Forest                   | 4.485 | 0.014 | 7.829  |
| Logistic Regression             | 4.606 | 0.013 | 8.150  |
| SVM                             | 5.515 | 0.013 | 7.840  |
| LightGBM                        | 5.447 | 0.014 | 9.277  |
| CatBoost                        | 5.442 | 0.014 | 9.269  |
| XGBoost                         | 4.769 | 0.011 | 8.220  |
| AdaBoost                        | 5.909 | 0.019 | 10.641 |
| SMOTE+Random Forest             | 4.879 | 0.016 | 9.002  |
| SMOTE+Logistic Regression        | 6.667 | 0.027 | 12.552 |
| SMOTE+SVM                       | 5.394 | 0.019 | 9.762  |
| SMOTE+LightGBM                  | 5.565 | 0.014 | 9.644  |
| SMOTE+CatBoost                  | 5.551 | 0.013 | 9.621  |
| SMOTE+XGBoost                   | 5.113 | 0.012 | 8.889  |
| SMOTE+AdaBoost                  | 5.939 | 0.022 | 11.289 |
| SMOTE+NearMiss+Random Forest     | 5.061 | 0.018 | 9.293  |
| SMOTE+NearMiss+Logistic Regression| 7.121 | 0.029 | 13.410 |
| SMOTE+NearMiss+SVM              | 5.818 | 0.022 | 10.571 |
| SMOTE+NearMiss+LightGBM         | 5.549 | 0.014 | 9.595  |
| SMOTE+NearMiss+CatBoost         | 5.537 | 0.013 | 9.574  |
| SMOTE+NearMiss+XGBoost          | 5.001 | 0.012 | 8.735  |
| SMOTE+NearMiss+AdaBoost         | 6.030 | 0.023 | 11.401 |

We observe that Machine Learning models can predict
IELTS speaking scores using data extracted from features.
The table of results highlights that the Random Forest model
achieved the best overall performance with the lowest MAE of
4.485 and the best MAP of 7.829, demonstrating reliable predictions. Additionally, the MAPE of 7.829 indicates that the model’s predictions deviate from the
true scores by an average range of 0.313 to 0.626, suggesting
a reliable performance. XGBoost stands out with the lowest
MSLE of 0.011, indicating its effectiveness in handling relative
errors. Moreover, the use of oversampling techniques like
SMOTE and NearMiss generally did not improve model performance and often resulted in higher error metrics, indicating
that these methods may not be suitable for the given dataset.

## Conclusion
This study presents the first data set collected on the characteristics of IELTS speaking practice audios and is also the first to analyze the influence of these characteristics on speaking test scores. Despite the considerable time and effort required for data collection, labeling, and feature extraction, we have achieved promising results. Our proposed model, capable of predicting IELTS speaking test scores based on extracted features, has the potential to reduce the cost of obtaining English proficiency certificates for Vietnamese individuals. Additionally, analyzing the effects of these features on IELTS test scores can help learners and teachers identify specific elements of speaking skills that need improvement.
