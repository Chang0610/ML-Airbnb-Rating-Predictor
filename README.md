# Machine Learing & Data Analytics---Analyzing Factors Affecting Airbnb Ratings in Oakland

## Introduction
### **Motivation**
The rise of the sharing economy, particularly platforms like Airbnb, has transformed the hospitality industry. With thousands of listings, understanding the key factors that influence guest satisfaction and high ratings is crucial for both hosts and guests. This project aims to:
- Identify key factors that impact Airbnb ratings.
- Provide insights for hosts to improve their listings.
- Enhance Airbnb's recommendation algorithms.

### **Dataset**
- **Airbnb Open Data**: [Airbnb Website](https://insideairbnb.com/get-the-data.html)
This study utilizes **Airbnb open data** for Oakland, which includes:
- **Listing Data**: 2,410 listings with structured details (e.g., price, number of bedrooms, amenities, and host information).
- **Review Data**: 123,088 guest reviews with sub-scores (accuracy, cleanliness, communication, etc.).

---

## **Data Processing**
- Selected relevant columns and removed those with excessive missing values.
- Standardized numerical formats (converted percentages, boolean values, and prices).
- **Performed Sentiment Analysis** on guest reviews to generate sentiment scores (-1 to 1).
- Merged **sentiment scores with structured listing data** to create a final dataset.
- Split data into **70% training and 30% testing** for robust model training.

---

## **Natural Language Processing (NLP)**
- **TF-IDF vectorization** was applied after text preprocessing (HTML removal, tokenization, and stopword elimination).  
### **Key Findings from NLP**
- **Positive impact words** (e.g., "private," "outdoor," "garden") correlate with higher ratings.
- **Negative impact words** (e.g., "deposit," "generic") correlate with lower ratings.

---

## **Predictive Models**
### **1. Linear Regression Model**
**Goal**: Identify the impact of structured features on review ratings.  
- **Key Predictors**: Host Response Rate, Communication Ratings, Bedrooms, Location Ratings, Price Sensitivity.
- **Performance**:
  - R² = **0.794**, Adjusted R² = **0.791**

### **2. Logistic Regression Model**
**Goal**: Classify listings into "high-rated" (≥4.89) and "low-rated" categories.  
- **Performance**:
  - Accuracy = **86.9%**, TPR = **89.4%**, FPR = **15.8%**
- **Findings**: Logistic regression works well for classification but has limitations in capturing non-linear relationships.

### **3. Decision Tree (CART) Model**
Trained on structured and NLP features to improve classification.  
**Best Performing Model: Decision Tree with Subscores**
- **Accuracy = 84.0%**, **TPR = 80.9%**, **FPR = 12.6%**

### **4. Random Forest & Boosting Models**
Ensemble learning further improved model performance.
- **Random Forest (DTC Subscores)**: **Accuracy = 86.4%**, ROC AUC = **0.948**
- **Gradient Boosting**: **Accuracy = 87.1%**, ROC AUC = **0.945**
- **Final Model**: Random Forest DTC Subscores
