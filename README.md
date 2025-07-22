# insurance
insurance-project
Insurance Claim Prediction
This project uses a dataset of insurance policyholders to predict whether an individual will file an insurance claim based on demographic and health-related features.

📁 Dataset Description
The dataset contains the following columns:

Column	Description
age	Age of the policyholder
sex	Gender of the policyholder (0 = Female, 1 = Male)
bmi	Body Mass Index
children	Number of children/dependents
smoker	Smoking status (1 = Smoker, 0 = Non-smoker)
region	Geographic region (0–3 categorical)
charges	Medical insurance charges
insuranceclaim	Target variable (1 = Claim made, 0 = No claim)
🎯 Objective
Predict the likelihood that a person will file an insurance claim using features like age, BMI, smoking status, etc.

🧪 Models Used
Logistic Regression
Random Forest
Gradient Boosting
(Optional) Neural Network
⚙️ Setup
Clone the repo
Install dependencies:
pip install -r requirements.txt
python main.py
