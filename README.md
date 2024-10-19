# Analyze the Influence of Features Extracted from Audios on the Results of IELTS Speaking Test
This is a implementation of Analyze the Influence of Features Extracted from Audios on the Results of IELTS Speaking Test by me. It is accepted for presentation at the 2024 International Conference on Advanced Technologies for Communications (ATC) and soon will be published in the IEEE Xplore Digital Library

## Introduction
The demand for international English certifications like IELTS, TOEIC, and TOEFL has significantly increased in Vietnam's educational and employment sectors. While self-practice in reading and listening is common, developing speaking and writing skills requires supervision. Unfortunately, access to reputable preparation centers is limited, especially in rural areas, where high tuition fees can be prohibitive. Additionally, instructors struggle to correct speaking errors for multiple students, highlighting the need for an automated assessment system.

Our study aims to fill this research gap by enhancing English language learning for Vietnamese learners. We utilize data from a test preparation center in Ho Chi Minh City to extract meaningful features from audio recordings of speaking tests. Through statistical analysis, we examine how these features affect IELTS speaking scores. We also employ Machine Learning algorithms to predict scores based on the extracted features, yielding promising results. Our research provides valuable insights into speaking criteria assessment and identifies areas for improvement, enabling Vietnamese learners and teachers to adopt effective strategies for enhancing their scores.
## Data collection


| Attribute         | Meaning                                                                                                                                                     |
|-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Mean hesitation    | The average degree of hesitation in speech. It can have values ranging from 0.0 to 1.0. It is calculated by the time gap between the pronunciation of the preceding word and the following word (subtracting the start time of the following word from the end time of the preceding word). |
| Mean conf         | The average confidence level, which ranges from 0.0 to 1.0.                                                                                              |
| Grammar point     | The grammatical score of the speech is calculated using Grammarly’s algorithm.                                                                              |
| Unique word       | The percentage of unique words spoken in the speech. Reflects the speaker’s vocabulary.                                                                    |
| Rare word         | The percentage of words spoken that are rare or less common. Reflects the speaker’s proficiency in advanced vocabulary.                                     |
| Number of words    | The total number of words in the speech (including repeated words).                                                                                       |
| Score             | The IELTS speaking score, which is also the target variable.                                                                                               |



## Conclusion
This study presents the first data set collected on the characteristics of IELTS speaking practice audios and is also the first to analyze the influence of these characteristics on speaking test scores. Despite the considerable time and effort required for data collection, labeling, and feature extraction, we have achieved promising results. Our proposed model, capable of predicting IELTS speaking test scores based on extracted features, has the potential to reduce the cost of obtaining English proficiency certificates for Vietnamese individuals. Additionally, analyzing the effects of these features on IELTS test scores can help learners and teachers identify specific elements of speaking skills that need improvement.
