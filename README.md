# Student Performance Prediction Using Supervised Unsupervised Learning, Reainforcedment Learning 

This project applies both **supervised** and **unsupervised** machine learning algorithms...

## Table of Contents
- [Project Overview](#project-overview)
- [Algorithms Used](#algorithms-used)
- [Data](#data)
- [Usage](#usage)
- [Results](#results)
- [Future Enhancements](#future-enhancements)

## Project Overview
The goal of this project is to leverage machine learning techniques...

## Algorithms Used
### Supervised Learning
- **Logistic Regression**: A baseline classification algorithm...

### Unsupervised Learning
- **K-Means Clustering**: Used to segment students...

## Results
- **Logistic Regression**: Achieved 83.93% accuracy...

### License
None

---
# 1. Introduction
In the field of education, predicting student performance has become increasingly critical in improving learning outcomes, early intervention, and resource allocation. Educational institutions rely on various strategies to identify students at risk of underperformance, but traditional methods often fall short in effectively analyzing the diverse and complex factors that influence student success. As the availability of educational data grows, machine learning (ML) offers a promising approach to enhancing predictive accuracy by analyzing student data more comprehensively.

The primary objective of this study is to explore and compare the effectiveness of various machine learning algorithms in predicting student performance by analyzing academic history, behavioral data, and socio-economic factors. This research aims to build predictive models that assist educators in identifying students who may be at risk of academic struggles.

In this study, we employ supervised, unsupervised, and reinforcement learning algorithms, applying two algorithms from each learning approach. The study delves into the theoretical foundations of the selected algorithms, focusing on their strengths, limitations, and suitability for educational data analysis. Additionally, we outline the data preprocessing steps and feature engineering techniques utilized to ensure high-quality inputs for the models.

Through rigorous evaluation and comparison, this report provides insights into the performance of the different algorithms for predicting student outcomes. We assess the models using critical performance metrics such as accuracy, precision, recall, and F1-score to determine which algorithm is better suited for the task of student performance prediction.

Ultimately, the findings of this study aim to contribute valuable knowledge to the ongoing research on improving student performance prediction through machine learning, with potential applications in enhancing learning experiences, optimizing teaching methods, and supporting data-driven decision-making in education.

---

# 2. Dataset
## 2.1. Exploration & Selection
To predict student performance, we looked at different educational datasets to find one with a wide range of useful information about students, including their personal details, academic background, and behavior. These factors are important for creating a good prediction model. After reviewing several options, we chose the Open University Learning Analytics Dataset (OULAD)[1] for our study. OULAD is a great fit because it has detailed data on student activities, course structures, and assessments, making it ideal for our predictive modeling.

We selected OULAD for these reasons:
1. **Detailed Student Information:** The dataset includes more than 32,000 student records, offering information like gender, region, education level, and disability status. It also tracks how students interact with the Virtual Learning Environment (VLE), providing important insights into their engagement with the course materials.
2. **Course and Assessment Data:** OULAD provides detailed information on courses (modules), assessments, and student registration, allowing us to analyze how students perform across different assessments and course presentations, such as the B (February) and J (October) presentations.
3. **Tracking VLE Engagement:** One of the main strengths of OULAD is that it tracks student interactions with the VLE. This helps us understand their level of engagement with learning resources, which is crucial for predicting success.
4. **Time-Based Data:** The dataset includes time-related details like registration dates, submission deadlines, and the frequency of VLE usage. This time-based information is very useful for both supervised and unsupervised learning models, as it adds an important time factor to the analysis.
5. **Easy to Use:** OULAD is well-structured and clearly explained, making it simple to use in educational research and machine learning. This helps speed up the process of building and testing predictive models.

## 2.2. Preparation
Every data-driven project needs to start with proper preparation of the dataset to ensure it is clean, organized, and ready for analysis. In this project, we aim to predict student performance using machine learning methods, utilizing the Open University Learning Analytics Dataset (OULAD). To make sure the dataset is reliable for analysis, we followed a clear data preparation process. OULAD contains valuable information about student interactions, demographics, and academic performance, making it a great choice for machine learning tasks. Below is an overview of the steps we took to prepare the data:

1. **Loading the Data:** After downloading the dataset, we loaded it into a Jupyter Notebook environment for exploratory data analysis (EDA) and cleaning. OULAD comes in several CSV files, including:
   - assessments
   - courses
   - studentAssessment
   - studentInfo
   - studentRegistration
   - studentVle
   - vle

   These were imported using the pandas library in Python. We examined each file to check its structure and ensure the data was consistent.

2. **Merging Datasets:** We merged the `studentInfo.csv` and `studentRegistration.csv` datasets to combine demographic information with registration details. This step provided a more holistic view of each student's academic journey by incorporating both demographic data and registration statuses. After the merge, we dropped the `date_unregistration` column, as it was no longer relevant for the analysis.

3. **Interaction Data Processing:** We grouped data by module, presentation, and student, calculating the average and total number of clicks each student made. We also counted the number of days a student interacted with the course and the number of unique materials they accessed.

4. **Merging and Analyzing Course Interaction Percentages:** We counted the number of unique learning materials available for each module and calculated the percentage of materials each student accessed, providing insights into their engagement.

5. **Tracking and Merging Assessment Types:** We counted and categorized the assessments (CMA, Exam, TMA) in each module and presentation, merging this information with student data to understand assessment completion.

6. **Handling Missing Data:** We removed any rows with missing values and used one-hot encoding for categorical variables, converting columns like `code_module`, `code_presentation`, and `region` into numeric form.

7. **Exporting Processed Data:** We exported the processed dataset into a CSV file for further analysis and modeling.

8. **Visualizing Feature Correlations:** Using a heatmap, we visualized correlations between features like `clicks`, `days_logged`, and `final_result`, providing insights into feature relationships.

9. **Outlier Detection and Removal:** We used boxplots to detect outliers in numeric features and removed unrealistic data points to ensure data accuracy.

---

# 3. Methodology
### Supervised Learning Algorithms
#### Logistic Regression
- **Why Use Logistic Regression?**
  - It's simple, easy to understand, and effective for predicting binary outcomes like pass or fail.
- **Model Training:** The dataset was split into training (80%) and testing (20%) sets. The data was scaled, and L2 regularization was applied to avoid overfitting.

#### Random Forest
- **Why Use Random Forest?**
  - Random Forest is great for complex data, combining multiple decision trees to improve accuracy and handle many features.
- **Model Training:** Multiple decision trees were built, and their results were combined for final predictions.
  
### Unsupervised Learning Algorithms
#### K-Means Clustering
- **Why Use K-Means?**
  - Great for identifying patterns or groupings in data. It can cluster students based on their engagement levels, helping identify low-, medium-, and high-engagement clusters.

#### DBSCAN
- **Why Use DBSCAN?**
  - DBSCAN can identify outliers, such as students with minimal engagement or erratic behavior, which can be useful for early intervention.

### Reinforcement Learning
- **How It Works:**
  - An agent interacts with an environment, taking actions, receiving rewards or penalties, and learning to make better decisions over time to maximize rewards.
  
---

# 4. Results
The results of the models were analyzed using metrics such as accuracy, precision, recall, and F1-score.

- **Logistic Regression:** Accuracy: 83.93%, Precision: 0.85, Recall: 0.84, F1-Score: 0.84.
- **Random Forest:** Accuracy: 85.41%, Precision: 0.86, Recall: 0.85, F1-Score: 0.85.
- **K-Means Clustering:** Identified 3 distinct clusters based on engagement patterns.
- **DBSCAN:** Detected clusters and outliers, helping identify students at risk of failure.

---

# 5. Model Evaluation
- **Logistic Regression:** Provided a solid baseline with good accuracy but struggled with borderline students.
- **Random Forest:** Outperformed Logistic Regression and highlighted key features such as `mean_sum_click` and `days_logged`.
- **K-Means Clustering:** Helped group students based on engagement levels.
- **DBSCAN:** Identified outliers, who may need special attention to avoid failure.

---

# 6. Conclusion
This analysis used both supervised and unsupervised machine learning techniques to predict student performance based on their engagement with the course. Random Forest provided the best overall performance, while K-Means and DBSCAN helped in segmenting students and identifying outliers. Practical applications include offering extra support to low-engagement students and using the insights to tailor teaching strategies.

Reinforcement learning algorithms also demonstrated potential for improving decision-making by optimizing actions based on rewards and penalties received from students' learning behaviors. This method could further enhance student performance prediction through adaptive learning interventions.

