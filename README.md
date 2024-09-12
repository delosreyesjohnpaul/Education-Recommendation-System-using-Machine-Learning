
This repository contains a machine learning model built to predict and recommend potential career paths for students based on their academic performance, extracurricular activities, and personal attributes. It provides top career recommendations with associated probabilities using a trained classification model. The dataset includes features such as gender, absence days, weekly self-study hours, subject scores, and total/average scores.

### Key Components

1. **Data Preprocessing**: 
    - The dataset is scaled and encoded where necessary.
    - Categorical variables like gender, part-time job, and extracurricular activities are encoded for model input.

2. **Model**:
    - A trained classification model that predicts student career paths from 17 available classes (e.g., Lawyer, Teacher, Game Developer, etc.).
    - Model accuracy metrics such as confusion matrix and classification reports are included.
   
3. **Features Used**:
    - **Gender** (Male/Female)
    - **Part-time Job**
    - **Absence Days**
    - **Extracurricular Activities**
    - **Weekly Self-Study Hours**
    - **Subject Scores** (Math, Physics, Chemistry, Biology, History, etc.)
    - **Total Score** and **Average Score**

4. **Model Output**:
    - The model predicts the most likely career path for a student along with the top 5 career choices and their respective probabilities.

### Usage Instructions

1. **Prediction Function**:
   - `Recommendations`: Pass relevant student data to the `Recommendations` function to get the top 5 recommended careers along with probabilities.
   
2. **Model Loading**:
   - The trained model and scaler are stored in the `Models/` directory. To load them, use `pickle` as shown in the example.

3. **Sample Usage**:
   ```python
   final_recommendations = Recommendations(gender='female',
                                           part_time_job=False,
                                           absence_days=2,
                                           extracurricular_activities=False,
                                           weekly_self_study_hours=4,
                                           math_score=87,
                                           history_score=73,
                                           physics_score=98,
                                           chemistry_score=91,
                                           biology_score=79,
                                           english_score=60,
                                           geography_score=77,
                                           total_score=583,
                                           average_score=83.28)

   for class_name, probability in final_recommendations:
       print(f"{class_name} with probability {probability}")
   ```

4. **Saving and Loading the Model**:
   ```python
   # Saving the model
   pickle.dump(scaler, open("Models/scaler.pkl", 'wb'))
   pickle.dump(model, open("Models/model.pkl", 'wb'))
   
   # Loading the model
   scaler = pickle.load(open("Models/scaler.pkl", 'rb'))
   model = pickle.load(open("Models/model.pkl", 'rb'))
   ```

### Performance Metrics

- **Accuracy**: 83%
- **Macro Average F1-score**: 0.82
- **Confusion Matrix**: The matrix reveals how well the model performs across the 17 career classes.

### Dependencies

- Python 3.x
- scikit-learn 1.4.2
- NumPy
- pickle for model saving and loading

### Future Enhancements

- Adding more feature variables like socioeconomic background or school ranking.
- Training the model with a more diverse dataset to improve the prediction accuracy.

