# Heat Sensitivity Index for Richmond, VA, 2024


## Introduction
The Heat Sensitivity Index (HSI) for 2024 is designed to assess the vulnerability of different census tracts to heat stress. This index incorporates a variety of socio-economic, health, and demographic variables to provide a comprehensive measure of heat sensitivity.

## Variables Used
The variables selected for creating the HSI are based on their relevance to heat sensitivity. These variables capture aspects of economic burden, social vulnerability, and health conditions that can exacerbate the effects of heat.

### 1. Economic Variables
- **df_acs2021_var1: 'Perc_pov'** - Percentage of people below 150% of the poverty level.
- **df_acs2021_var2: 'Perc_BurdRU'** - Percentage of severely burdened renter units (30% or more of income spent on rent).
- **df_acs2021_var3: 'Perc_BurdHousU'** - Percentage of severely burdened housing units (30% or more of income spent on housing).
- **df_acs2021_var4: 'Perc_NoVeh'** - Percentage of people with no vehicles.
- **df_acs2021_var10: 'Perc_Crowd'** - Percentage of housing units with more than 1 person per room.
- **df_acs2021_var13: 'HL_rating'** - Homelessness rating (1 to 5, with increasing homelessness).
- **df_acs2021_var23: 'En_Burden'** - Percentage of income spent on energy sources (electricity, gas, fuel) exceeding 6%.

### 2. Social-Cultural Variables
- **df_acs2021_var6: 'Perc_NoDis'** - Percentage of people with a disability.
- **df_acs2021_var7: 'Perc_Over65'** - Percentage of people over 65 years of age.
- **df_acs2021_var8: 'Perc_Under5'** - Percentage of people under 5 years of age.
- **df_acs2021_var9: 'Perc_NoEng'** - Percentage of people who speak English less than "very well".
- **df_acs2021_var11: 'Perc_UnS'** - Percentage of all races other than "white".

### 3. Health Variables
- **df_acs2021_var5: 'Perc_NoIns'** - Percentage of people with no insurance.
- **df_acs2021_var12: 'Perc_Preg12'** - Percentage of women who gave birth in the past 12 months.
- **df_acs2021_var14 to df_acs2021_var22: 'Data_Value'** - Crude prevalence rates for various health conditions (Asthma, Diabetes, High BP, Cancer, Obesity, Heart Disease, Stroke, Mental Health, COPD).

## Normalization
All selected variables were normalized using the Min-Max Scaler. This process is essential for ensuring that all variables contribute equally to the composite index, irrespective of their original scales.

**Normalization Formula:**
Xnorm = (X − Xmin) / (Xmax − Xmin)

where `X` is the original value, `Xmin` is the minimum value, and `Xmax` is the maximum value in the dataset.

*Reference: [Normalization vs Standardization - GeeksforGeeks](https://www.geeksforgeeks.org/normalization-vs-standardization/)*

## Creation of Sub-Indices
The normalized variables were grouped into three categories: Economic, Social-Cultural, and Health. For each census tract, the sub-index for each category was calculated by taking the mean of the normalized values of the variables within that category.

- **Economic Index**: Economic Index = mean(Perc_pov, Perc_BurdRU, Perc_BurdHousU, Perc_NoVeh, Perc_Crowd, HL_rating, En_Burden)
- **Social-Cultural Index**: Social-Cultural Index = mean(Perc_NoDis, Perc_Over65, Perc_Under5, Perc_NoEng, Perc_UnS)
- **Health Index**: Health Index = mean(Perc_NoIns, Perc_Preg12, Asthma, Diabetes, High BP, Cancer, Obesity, Heart, Stroke, MH, COPD)


## Final Heat Sensitivity Index
The final Heat Sensitivity Index for each census tract was obtained by averaging the normalized values of the three sub-indices. This approach ensures that each sub-index contributes equally to the final index.
Heat Sensitivity Index = mean(Economic Index, Social-Cultural Index, Health Index)


The final index was also normalized to ensure comparability across census tracts.

## Conclusion
The methodology for creating the Heat Sensitivity Index involves selecting relevant variables that capture economic, social-cultural, and health-related aspects of heat sensitivity. These variables were normalized, grouped into sub-indices, and then averaged to obtain a comprehensive measure of heat sensitivity for each census tract. This index can be used to identify vulnerable areas and guide resource allocation and policy interventions to mitigate the effects of heat stress.


![Social_Cultural_Index](https://github.com/user-attachments/assets/0a7a87f0-2dd8-4bba-8569-fb9b83d626f1)
![Heat_Sensitivity_Index](https://github.com/user-attachments/assets/f01c4224-b5b4-47da-bae4-fdc38540476b)
![Health_Index](https://github.com/user-attachments/assets/f59b72f8-b4ad-46ec-a2e3-872cc3b2b704)
![Economic_SVI](https://github.com/user-attachments/assets/a093c46d-4d6c-4100-86a3-ddc660581f1f)

