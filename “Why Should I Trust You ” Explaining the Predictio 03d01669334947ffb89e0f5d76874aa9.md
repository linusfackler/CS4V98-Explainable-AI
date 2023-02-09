# “Why Should I Trust You?”
Explaining the Predictions of Any Classifier (LIME)


# Why?

- If users won’t trust a model, they won’t use it
- trusting a prediction enough to take action based on it
    - vs.
- trusting a model to behave in reasonable ways if deployed

### Lime

→ “Local Interpretable Model-Agnostic Explanations”

- algorithm that can explain the predictions of any classifier
    - by approximating it locally with interpretable model

### SP-Lime

- method that selects a set of representative instances with explanations to address “trusting the model” problem

# Explanations

![Screenshot 2023-02-15 at 4.54.36 PM.png](%E2%80%9CWhy%20Should%20I%20Trust%20You%20%E2%80%9D%20Explaining%20the%20Predictio%2003d01669334947ffb89e0f5d76874aa9/Screenshot_2023-02-15_at_4.54.36_PM.png)

- explaining individual predictions: model predicts patient has flu → LIME highlights symptoms that led to prediction.
- sneeze, headache → flu
- no fatigue → no flu
- symptoms with relative weight to affect result

→ doctor can make decision whether to trust predictions (based on intelligible explanations)

- “explaining a prediction”
    
    → presenting textual or visual artifacts that provide qualitative understanding of relationship between instance’s components
    
- humans have prior knowledge about application domain
    - use it to accept/trust or reject a prediction
- providing explanations can increase acceptance of recommendations
- trust is required in every machine learning model

![Screenshot 2023-02-15 at 11.50.31 PM.png](%E2%80%9CWhy%20Should%20I%20Trust%20You%20%E2%80%9D%20Explaining%20the%20Predictio%2003d01669334947ffb89e0f5d76874aa9/Screenshot_2023-02-15_at_11.50.31_PM.png)

- here, right side with 94% accuracy is way worse
    - explanations make it possible to see
        - dataset has issues; “Posting” in training set is 99% atheism, even though doesn’t make sense

### Desired Characteristics for Explainers

- must be **************************interpretable**************************
    - provide qualitative understanding between input variables & response
    - must take into account user’s limitations
- ******************************local fidelity******************************
    - explanation must correspond to how the model behaves in the vicinity of the instance being predicted
    - does not imply global fidelity
- must be ****************************model-agnostic****************************
    - explainer should be able to explain any model
        - treat original model as black box
- provide **************************************global perspective**************************************
    - accuracy may not be suitable metric to evaluate model
        
        → we want to *****************explain the model*****************
        

# LIME

- GOAL: identify an interpretable model over ******************interpretable representation******************
- “agnostic”
    - therefore can be used for any machine learning model

### Interpretable Data Representation

- example: text classification
    - binary vector indicating presence/absence of word
- example: image classification
    - binary vector indicating presence/absence of contiguous patch of similar pixels

### Fidelity-Interpretability Trade-off

- We must
    - ******************************************************minimize unfaithfulness****************************************************** in **************************approximating************************** the ********************probability******************** in defined locality
    - have a **************************************************low measure of complexity************************************************** of the **********************explanation**********************

→ ensures both **interpretability** & **local fidelity**

### Sampling for Local Exploration

- minimize locality-aware loss without making assumptions about the probability
    - since we want explainer to be model-agnostic
- to learn local behavior of f (probability), we approximate unfaithfulness

### Sparse Linear Explanations

- text classification
    - ensures that explanation is interpretable
        - by letting interpretable representation be a bag of words
        - setting limit K on number of words
        - K can be as big as user can handle

![Screenshot 2023-02-16 at 1.13.03 AM.png](%E2%80%9CWhy%20Should%20I%20Trust%20You%20%E2%80%9D%20Explaining%20the%20Predictio%2003d01669334947ffb89e0f5d76874aa9/Screenshot_2023-02-16_at_1.13.03_AM.png)

- this produces explanation for individual prediction
    - complexity doesn’t depend on size of dataset, but on time to compute & # of samples N

### Deep networks for images

![Screenshot 2023-02-16 at 1.22.11 AM.png](%E2%80%9CWhy%20Should%20I%20Trust%20You%20%E2%80%9D%20Explaining%20the%20Predictio%2003d01669334947ffb89e0f5d76874aa9/Screenshot_2023-02-16_at_1.22.11_AM.png)

- b, c, d show superpixels explanations for top 3 predicted classes with rest greyed out
- model might predict wrong because it only uses a small part of the image which could be ambiguous

# Experiments

# Without LIME

![Screenshot 2023-02-01 at 2.22.43 PM.png](%E2%80%9CWhy%20Should%20I%20Trust%20You%20%E2%80%9D%20Explaining%20the%20Predictio%2003d01669334947ffb89e0f5d76874aa9/Screenshot_2023-02-01_at_2.22.43_PM.png)

- Here, assuming that blue dots are cases of no strokes, we predict now that everyone who falls into the blue area has no stroke.
    - this is very non-linear → no easy to explain relation in how we perform a prediction