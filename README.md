#🏢 Insurance Customer Retention — Classification Project
Insurance Data Analysis


Prediction of whether an insurance customer will renew their policy, based on demographic, behavioral, product ownership, and financial variables.

📌 Project Overview
This project focuses on customer churn prediction in the insurance sector. Using a real-world-style dataset, the goal is to identify customers at risk of not renewing their policy — enabling proactive retention strategies.
Target Variable: PoliçeYenilemeDurumu (Policy Renewal Status)

1 → Retained (Evet)
0 → Churned (Negatif)


📂 Dataset
File: insuranceretention.csv
ColumnDescriptionPoliçeNumarasıUnique policy identifier (excluded from modeling)MüşteriCinsiyetiCustomer gender (Female / Male)_65YaşÜzeriWhether customer is over 65 (1/0)MedeniDurumMarital status (Married / Single)ÇocukVarmıWhether customer has children (Yes / No)PoliçeSüresiNumber of months insuredEvSigortasıVarlığıHome insurance ownershipAraçSigortasıVarlığıVehicle insurance status (Company / Competitor / None)SağlıkSigortasıVarlığıHealth insurance type (Standard / Comprehensive / None)TicariSigortaVarlığıCommercial insurance ownershipÇağrıMerkeziİletişimiCall center interaction frequencySonTedaviDetayıType of most recent medical treatmentAmeliyatGeçmişiSurgical history (Yes / No)AileHayatSigortasıVarlığıLife insurance type (None / Individual / Family)SözleşmeTürüContract type (Basic / Premium)BildirimTercihleriPreferred communication channelÖdemeYöntemiPayment methodAylıkÖdemeTutarıMonthly premium amountToplamÖdemeTutarıTotal premium paid over policy durationPoliçeYenilemeDurumuTarget variable — policy renewed or not

🔧 Project Structure
insurance_retention_SON.ipynb   # Main notebook
insuranceretention.csv          # Dataset
risksegmentlidosya.xlsx         # Output: customers with risk segments
ToplamUrunSayisi_0.xlsx         # Output: customers with 0 products
README.md

🧪 Workflow
1. Exploratory Data Analysis (EDA)

Distribution analysis of numerical and categorical variables
Retention rate breakdown by gender, marital status, payment method, and contract type
Cross-tabulations and KDE plots per retention status
Outlier detection using IQR method

2. Feature Engineering
New features created to improve model signal:
FeatureDescriptionToplamÜrünSayısıTotal number of insurance products ownedOrtalamaAylikOdemeTotal payment / policy durationUrunBasinaOdemeTotal payment / number of productsUrunYogunluguProducts per month of policy durationErkenDonemBinary flag: policy duration ≤ 12 monthsSüre_x_UrunInteraction term: duration × product countSureSegmentPolicy duration segmented into bandsRiskSkoruRule-based risk score (mobile use, products, duration)RiskSegmentiRisk label: Low / Medium / HighChurnOlasiligiPredicted churn probability from Logistic Regression
3. Model Training & Evaluation
Multiple classifiers were compared:
ModelMetric FocusLogistic RegressionBaseline, ROC-AUCRandom ForestRecall on churn classGradient BoostingF1 on churn classDecision TreeInterpretabilityKNNProximity-based comparison

class_weight='balanced' used to handle class imbalance
Stratified K-Fold cross-validation (5 folds)
Evaluation metrics: Recall (churn class), F1-score (churn class), ROC-AUC

4. Risk Segmentation
A business-readable risk score was created using rule-based logic, and further refined with model probabilities from Logistic Regression. Final output exported to Excel.

📦 Requirements
bashpip install pandas numpy matplotlib seaborn scikit-learn xgboost lightgbm catboost openpyxl

🚀 Getting Started
bashgit clone https://github.com/your-username/insurance-retention.git
cd insurance-retention
jupyter notebook insurance_retention_SON.ipynb

Make sure insuranceretention.csv is in the same directory as the notebook.


📊 Key Findings

Customers with automatic payment methods show higher retention rates
Multi-product ownership is positively correlated with retention
Customers in the early policy period (≤12 months) are at higher churn risk
Call center interaction frequency is a meaningful behavioral signal
Churned customers represent a significant share of total revenue paid


👩‍💻 Author
Ecem
Data Analyst | Miuul Data Analyst Bootcamp

📄 License
This project is for educational purposes.
