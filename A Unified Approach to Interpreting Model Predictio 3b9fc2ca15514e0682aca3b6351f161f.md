# A Unified Approach to Interpreting Model Predictions



- While ML models have achieved high accuracy, complexity makes it difficult to interpret

→ SHAP (SHapley Additive exPlanations)

- interpreting model predictions in a unified way

# Existing methods for interpreting model predictions

### Global feature importance measures

- Global feature importance measures are used to determine the relative importance of different input features to a model's predictions across the entire input space.
- These measures can be used to identify the most important features for a given model, which can be useful for feature selection or identifying areas where more data collection or feature engineering may be needed.
- Some common methods for computing global feature importance measures include permutation feature importance and mean absolute Shapley values.

### Local feature importance measures

- Local feature importance measures are used to determine the relative importance of different input features to a model's prediction for a specific input or set of inputs.
- These measures can be used to understand why a particular prediction was made by a model, and can help identify which features are most important in making the prediction for that input.
- Some common methods for computing local feature importance measures include local Shapley values and LIME (Local Interpretable Model-agnostic Explanations).

### Example-based explanations

- Example-based explanations provide an explanation for a specific prediction made by a model for a specific input.
- These explanations are often visual and can help users understand how the model arrived at a particular prediction.
- Some common methods for generating example-based explanations include partial dependence plots, individual conditional expectation plots, and Anchors.

# SHAP framework

- based on concept of Shapley values
- model-agnostic
    - can be applied to any ML model

### Algorithm

- Shapley value
    - fair way of assigning credit to features based on their importance in making a prediction
- coalitional game
    - math framework used to compute Shapley values
    - each feature treated as player
    - goal is to attribute for making prediction to each player
- Shapley regression framework
    - modified version of coalitional game
    - can be used to compute Shapley values for machine learning models
    - each feature is assigned a weight based on its contribution to model’s output
- algorithm computes contribution of each feature to model’s output for the given input
- then combines contributions using Shapley values to obtain final SHAP values
- algorithm is computationally efficient & can be applied to any type of ML model (model-agnostic)

# Experiments

next