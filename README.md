🚀 Overview
Lost circulation is one of the most costly and challenging problems in drilling operations, occurring when drilling fluid escapes into formation fractures. This project combines domain expertise in drilling physics with advanced machine learning to create a predictive system that can:

Classify different types of lost circulation events

Predict fluid loss in real-time during drilling operations

Simulate drilling scenarios for proactive decision-making

Visualize risk factors and prediction confidence

📊 Problem Types Classified
🔄 Induced Fracture: ECD exceeds fracture pressure with high fluid loss (>50 bbl/hr)

🔴 Severe Natural Fracture: High fluid loss rates (20-50 bbl/hr)

🟡 Moderate Natural Fracture: Moderate fluid loss (5-20 bbl/hr)

🟢 No Loss: Normal operations (≤5 bbl/hr)

🛠️ Technical Approach
Physics-Guided Machine Learning
Instead of relying solely on data patterns, we incorporate drilling physics principles:

python
# Physics-based labeling rules
def generate_labels(df):
    conditions = [
        (df['ecd'] > df['fracture_pressure'] / (0.052 * df['depth'])) & (df['fluid_loss_rate'] > 50),
        (df['fluid_loss_rate'] > 20) & (df['fluid_loss_rate'] <= 50),
        (df['fluid_loss_rate'] > 5) & (df['fluid_loss_rate'] <= 20),
        (df['fluid_loss_rate'] <= 5)
    ]
    choices = ['Induced Fracture', 'Severe Natural Fracture', 'Moderate Natural Fracture', 'No Loss']
    return np.select(conditions, choices, default='Unknown')
Feature Engineering
Key drilling parameters used for prediction:

Depth and pressure profiles (pore pressure, fracture pressure)

Mud properties (weight, viscosity, yield point)

Hydraulics (flow rate, annular velocity, ECD)

Formation characteristics (permeability, fluid loss rates)

📈 Model Performance
Classification Results
Overall Accuracy: 99.80%

Precision/Recall by Class:

No Loss: 1.00 / 1.00

Moderate Natural Fracture: 1.00 / 1.00

Severe Natural Fracture: 0.98 / 1.00
