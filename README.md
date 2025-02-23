
# Predicting H1N1 Vaccination Decisions Using Machine Learning: Insights from Demographic, Behavioral, and Attitudinal Factors

## Overview

The emergence of infectious diseases has been a significant public health concern worldwide. 

Vaccination plays a crucial role in controlling the spread of infectious diseases and mitigating their impact on society 

One such outbreak, the H1N1 influenza pandemic of 2009

In response to the 2009 H1N1 pandemic, governments and health organizations launched extensive vaccination campaigns

However, not all individuals chose to receive the vaccine.

Understanding the factors that influence vaccination behavior can help public health authorities design targeted campaigns

## Key Business Problem

1. What patterns or trends were observed in the demographic and behavioral characteristics of individuals who received the H1N1 vaccine versus those who did not?(Exploratory Data Analysis)

2. Is there a significant difference in H1N1 vaccine uptake between individuals with different levels of education (e.g., no high school, high school graduate, college degree, etc.)?(Hypothesis testing)

3. Which machine learning models is best for predicting the likelihood of an individual receiving the H1N1 vaccine, incorporating demographic and behavioral data?(Modeling)

4. What were the most important features (demographic, behavioral, and attitudinal) for predicting H1N1 vaccine uptake using machine learning models? (Feature Importance)

## Data Understanding
The dataset used in this study is sourced from the National 2009 H1N1 Flu Survey, conducted by the U.S. National Center for Health Statistics.

 It consists of responses from individuals across various demographic backgrounds and captures behavioral patterns, health conditions, and personal opinions regarding vaccination.
 
The dataset contains:
36 feature columns representing different attributes of survey respondents.
1 target variable (h1n1_vaccine) indicating whether an individual received the H1N1 vaccine (binary: 0 = No, 1 = Yes).

### Objective 1: Patterns and Trends

The plot clearly shows a significant imbalance in the number of individuals who received the H1N1 vaccine versus those who did not.

The non-vaccinated group (represented by 0) has a much larger count compared to the vaccinated group (represented by 1).

![image](https://github.com/user-attachments/assets/31976234-91a7-4e29-a621-8d5c7489be0c)

#### Further Insight

The stacked bar reveals that non-vaccinated individuals are more concentrated in younger age groups, while older age groups have a higher proportion of vaccinated individuals. 

This could indicate that age plays a crucial role in vaccine decision-making, with older individuals possibly perceiving a higher risk of H1N1 infection and thus opting for the vaccine.

![image](https://github.com/user-attachments/assets/d6b717ba-3e56-4d81-aca1-d7228372dd69)

#### Correlation Heatmap

Behavioral Variables Correlations: Several behavioral variables show moderate correlations with each other, such as:

Mask-wearing, Hand washing, and Avoiding large gatherings have a strong positive correlation with each other (e.g., behavioral face mask with behavioral_wash_hands at 0.34). 

This suggests that individuals who engage in one form of preventive behavior are likely to engage in others as well.

Social distancing behaviors (behavioral_large_gatherings and behavioral_outside_home) also show moderate correlations, suggesting that individuals who avoid large gatherings may also reduce contact outside their homes

### Objective 2: Hypothesis testing

H₀: There is no significant difference in the uptake of the H1N1 vaccine between individuals with different levels of education. 

H₁: There is a significant difference in the uptake of the H1N1 vaccine between individuals with different levels of education 

The p-value, which is probability of obtaining the observed results (or more extreme results) under the assumption that the null hypothesis is true, was 5.12e-22 (which is extremely small) is much less than the typical significance level of 0.05 hence rejecting the null hypothesis.

This implies that education level significantly affects vaccine uptake.
public health campaigns could benefit from being tailored to different education group

### Objective 3: Modeling

This section focused on finding the best model that would predict the likelihood of an individual receiving H1N1 vaccine. 

The Metric of focus, according to the competition require was ROC AUC, where a higher value indicates the model was the best.

Several models gave different ROC AUC values

We conclude that, based on the above table, XGboost hyper tuned was the best in predicting whether an individual will take the H1N1 vaccine since its  ROC AUC is the highest as shown below

![image](https://github.com/user-attachments/assets/6568376b-27c0-4796-815b-06b342126fbb)

### Objective 4: Feature Importance

The feature importance analysis from the XGBoost model highlights that age group (f16), opinion on getting sick from the vaccine, opinion on H1N1 vaccine risk (f14), and H1N1 concern (f0) are the most critical factors.

This suggests that age demographics and risk perception play a significant role in predicting vaccination decisions.

 Education (f17), race (f18), and sex (f19) also have substantial importance, indicating that demographic and societal factors strongly influence vaccination behavior.
 
In contrast, features such as household adults (f23), household children (f24), and behavioral antiviral medication use (f2) have minimal impact. 

This suggests that household composition and certain preventive behaviors are not strong predictors in this model.

![image](https://github.com/user-attachments/assets/fc0b300c-10ea-4a7e-a334-deb53270c0d2)

## Recommendations and Conclusion 

 
Age-Specific Outreach: Since age is the most significant predictor, vaccination campaigns should tailor messaging based on age group concerns and preferences.

Risk Perception Awareness: Misconceptions about the vaccine’s risk are highly influential. Public health campaigns should focus on correcting misinformation.

Targeted Education Programs: Given the importance of education and race, community engagement efforts should be adjusted for different educational backgrounds and cultural perspectives.

Doctor Involvement: Medical professionals should be leveraged to improve vaccine acceptance, as doctor recommendations (f9) and chronic medical conditions (f10) are among the influential factors.

Refinement of Public Health Strategies: More emphasis should be placed on factors with higher predictive power while deprioritizing less relevant features like household structure and certain behavioral aspects.

These insights can help improve vaccine uptake by focusing resources on the most impactful factors influencing decision-making.











