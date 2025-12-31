# pandas-memory-optimization 🚀

## Why this project?
When datasets grow large, poor data type choices can silently kill performance.
This project focuses on **optimizing pandas DataFrame memory usage** without losing
any business meaning or analytical value.

The goal is simple:
➡️ Make the data **lighter, faster, and scalable** for real-world ML pipelines.

---

## Problem Statement
The original customer dataset uses default pandas data types:
- Categorical columns stored as `object`
- Numeric columns stored as 64-bit by default
- Ordinal features not explicitly modeled

At scale, these inefficiencies:
- Increase memory consumption
- Slow down model training
- Increase infrastructure costs

---
## 📂 Project Structure

```
pandas-memory-optimization/
│
├── data/
│   └── customer_train.csv 
│
├── notebooks/
│   └── dataframe_memory_optimization.ipynb
│
├── assets/
│   └── hr-image-small.png
│
└── README.md

```

---

## What I Did

### 🔧 Data Type Optimization
| Data Type | Optimization |
|---------|-------------|
| Binary categories | Converted to `bool` |
| Integer columns | Downcasted to `int32` |
| Float columns | Downcasted to `float16` |
| Nominal categories | Converted to `category` |
| Ordinal categories | Converted to **ordered categories** |

No numerical encoding for ordinal features — ordering is preserved **semantically**, not artificially.

---

### 📊 Ordinal Features Handled Correctly
- Experience level  
- Company size  
- Education level  
- University enrollment  
- Years since last job change  

These are modeled using `CategoricalDtype(ordered=True)` instead of integers.

---

## Business Logic Applied
Filtered the dataset to focus on recruiter-relevant candidates:
- **10+ years of experience**
- **Company size ≥ 1,000 employees**

This aligns the data with enterprise recruiter requirements.

---

## Results
✅ Significant reduction in DataFrame memory usage  
✅ No loss of information  
✅ Faster and more scalable preprocessing  

Memory comparison can be verified using:
```python
df.info(memory_usage="deep")
