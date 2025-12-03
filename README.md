# Hull Starter Notebook – Architecture Overview

This repository contains a structured collection of experimental models designed for the **Hull Tactical Market Prediction** task. The notebook includes multiple model variants (Model 1–7), each exploring different data pipelines, preprocessing strategies, and portfolio allocation logic within the constraints of the competition (investment bounds: `MIN_INVESTMENT = 0`, `MAX_INVESTMENT = 2`).

---

## **Project Architecture Overview**

The architecture of the notebook is built around a modular, multi-model experimentation framework. Each model follows a similar structure but implements its own feature engineering, data-handling logic, and prediction formulation.

### **1. Environment & Dependencies**

The notebook initializes the core scientific Python stack:

* `pandas` and `polars` for fast data manipulation
* `numpy` for numerical operations
* `pathlib` for file system management

This ensures a consistent baseline environment for all models.

---

### **2. Data Layer**

Each model reads the dataset from the **Hull Tactical Market Prediction** competition files.

Typical components:

* Path definitions using `Path('/kaggle/input/...')`
* Reading train/test files using **Pandas** or **Polars**
* Selecting essential columns such as `date_id` and `forward_returns`
* Optional merging of market features (E-features like `E1`, `E2`, ..., `E19`)

This layer abstracts dataset access and prepares structured input for modeling.

---

### **3. Feature Engineering Layer**

Although minimal in early models, later models add more variation, such as:

* Selecting subsets of features
* Handling missing values
* Generating statistical transformations
* Applying rolling or cross-sectional operations (depending on model)

Each model is intentionally kept simple to reduce overfitting and ensure computational efficiency.

---

### **4. Modeling Layer**

Instead of deep-learning models, the notebook focuses on **rule‑based** or **statistical** allocation strategies.

Each model:

* Defines investment boundaries (`MIN_INVESTMENT`, `MAX_INVESTMENT`)
* Computes a predicted allocation
* Often uses simple transformations of forward returns or engineered signals

This modular design allows rapid iteration.

---

### **5. Evaluation / Prediction Layer**

Each model generates predictions for submission:

* Predictions are shaped into the required format
* Prediction dictionaries or DataFrames are created
* Ensures the investment values fit within specified bounds

Some models include timing utilities (`%%time`) to measure runtime performance.

---

### **6. Multi‑Model Layout**

The notebook organizes models as **distinct sections**, each labeled with markdown headers:

```
## Model_1
## Model_2
## Model_3
...
## Model_7
```

Each block includes:

* Model-specific constants
* Data loading logic
* Feature preparation pipeline
* Prediction logic

This structure is efficient for comparison and experimentation.

---

## Folder / Code Structure Summary

*(As represented inside the notebook)*

```
- imports
- Model_1
- Model_2
- Model_3
- Model_4
- Model_5
- Model_6
- Model_7
```

Each model follows a pattern:

```
[Set investment bounds]
[Load data]
[Select / engineer features]
[Compute prediction]
[Store output]
```

---

## Overall Description (for GitHub README)

This notebook serves as a starter framework for building and testing multiple portfolio‑allocation models for the **Hull Tactical Market Prediction** challenge. It demonstrates:

* Efficient dataset loading using Pandas and Polars
* Multiple variations of simple rule‑based financial models
* A clear modular structure for comparing model ideas
* Consistent handling of prediction constraints required by the competition

The architecture supports experimentation, scalability, and a clear workflow for extending or replacing models.

---

## Usage

This notebook can be used to:

* Build financial prediction models
* Experiment with different data-processing pipelines
* Generate predictions for submission
* Extend into more complex ML models if desired

---

## License

You may add a license depending on your repository requirements.

---

If you'd like, I can:

* Convert this into a more formal technical documentation
* Expand each model's description individually
* Add diagrams (architecture flowchart)
* Add badges, contribution guidelines, or setup instructions
