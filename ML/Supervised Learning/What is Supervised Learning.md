# Machine Learning Notes

---

# 1️⃣ Supervised Learning

## What is Supervised Learning?
Supervised Learning means:
The model learns from data that already has answers (labels).

### Example (Car Dataset)

| Year | Mileage | Engine Size | Price |
|------|--------|-------------|-------|
| 2017 | 15944  | 1           | 12000 |
| 2018 | 9083   | 1           | 14000 |
| 2017 | 12456  | 1           | 13000 |

### Here:
- **Input (Features):** Year, Mileage, Engine Size  
- **Output (Label):** Price  

The model learns the relationship between inputs and output.

---

# 2️⃣ Types of Supervised Learning

Supervised Learning has two main types:

Supervised Learning
|

| |
Regression Classification


---

# 3️⃣ Regression

## What is Regression?
Regression means predicting a **number (continuous value)**.

### Examples:
- House price → 250000  
- Salary → 50000  
- Temperature → 30°C  

### Example:
Input:
- Year = 2017  
- Mileage = 14000  
- Engine Size = 1  

Output:
- Price = 12500  

✔ Output is a NUMBER → Regression

---

## Regression Algorithms:
- Linear Regression  
- Polynomial Regression  
- Ridge Regression  
- Lasso Regression  
- Decision Tree Regression  
- Random Forest Regression  
- Support Vector Regression  

---

# 4️⃣ Classification

## What is Classification?
Classification means predicting a **category (label)**.

### Examples:
- Spam / Not Spam  
- Sick / Healthy  
- Cheap / Expensive  

### Example:
Email → "Win money now"  
Output → Spam  

✔ Output is a CATEGORY → Classification

---

## Classification Algorithms:
- Logistic Regression  
- Decision Tree  
- Random Forest  
- Support Vector Machine  
- K-Nearest Neighbors  
- Naive Bayes  
- Neural Networks  

---

# 5️⃣ Regression vs Classification

| Feature | Regression | Classification |
|--------|-----------|----------------|
| Output | Number | Category |
| Example | Price = 12000 | Spam / Not Spam |
| Model | Linear Regression | Logistic Regression |

---

# 6️⃣ Supervised Learning Summary

- Regression → Predict numbers  
- Classification → Predict categories  

---

# 7️⃣ Unsupervised Learning

## What is Unsupervised Learning?
Data has NO labels.

### Example:
| Mileage | Engine |
|--------|--------|
| 15000  | 1      |
| 9000   | 1      |

No output column exists.

### Used for:
- Clustering
- Pattern finding

---

## Examples:
- Customer segmentation  
- Grouping similar cars  

---

# 8️⃣ Reinforcement Learning

## What is Reinforcement Learning?
Model learns by **trial and error**.

### Examples:
- Game AI  
- Robots  
- Self-driving cars  

### Idea:
- Reward for correct action  
- Penalty for wrong action  

---

# 9️⃣ Machine Learning Pipeline


Data Collection
↓
Data Cleaning
↓
Feature Engineering
↓
Train/Test Split
↓
Model Selection
↓
Model Training
↓
Model Evaluation
↓
Prediction


---

# 🔢 Label Encoding

## What is Label Encoding?
Label Encoding assigns a number to each category.

### Example:

| Color | Encoded |
|------|--------|
| Red   | 0      |
| Green | 1      |
| Blue  | 2      |

### Advantages:
- Simple
- Memory efficient
- Good for tree models

### Disadvantages:
- Creates fake order (0 < 1 < 2)
- Not good for linear models

---

# 🧩 One-Hot Encoding

## What is One-Hot Encoding?
Creates separate columns for each category.

### Example:

| Color | Red | Green | Blue |
|------|-----|-------|------|
| Red   | 1   | 0     | 0    |
| Green | 0   | 1     | 0    |
| Blue  | 0   | 0     | 1    |

### Advantages:
- No fake ordering
- Best for linear models & neural networks

### Disadvantages:
- More columns (high dimensionality)
- Not efficient for large categories

---

# ⚖️ Label Encoding vs One-Hot Encoding

| Feature | Label Encoding | One-Hot Encoding |
|--------|----------------|------------------|
| Output | Numbers | Binary columns |
| Order issue | Yes | No |
| Memory | Low | High |
| Best for | Tree models | Linear models / NN |
| Complexity | Simple | Medium |

---

# 🧠 Simple Trick to Remember

- Label Encoding → "Give Numbers"
- One-Hot Encoding → "Create Columns"

---

# ❓ Which is Better?

✔ There is NO single best method.

### Use:
- Label Encoding → Tree-based models (Decision Trees, Random Forest)
- One-Hot Encoding → Linear models, Neural Networks

---

# ✅ Final Summary

- Supervised Learning → Uses labeled data  
- Regression → Predict numbers  
- Classification → Predict categories  
- Unsupervised Learning → No labels  
- Reinforcement Learning → Trial & error  
- Encoding → Convert categories into numbers  

---
