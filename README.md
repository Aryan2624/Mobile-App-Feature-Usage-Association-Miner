# 📱 Mobile App Feature Usage Association Miner

A from-scratch Association Rule Mining project that analyzes real user-session behavior to discover which in-app actions are frequently associated and generate data-driven insights for UI redesign.

## 🎯 Objective

**Discover which in-app features/actions are used together to guide UI redesign.**

The project analyzes user behavior within sessions and identifies meaningful relationships between actions such as:

* View
* Cart
* Purchase

No frontend/UI is built. The project focuses on the **data processing and machine learning pipeline** that generates UI redesign recommendations.

## 📊 Dataset

**E-Commerce Behavior Data from Multi-Category Store**

Source: Kaggle — `mkechinov/ecommerce-behavior-data-from-multi-category-store`

The project uses real e-commerce behavioral data from **October 2019**.

### Dataset Columns

* `event_time`
* `event_type`
* `product_id`
* `category_id`
* `category_code`
* `brand`
* `price`
* `user_id`
* `user_session`

### Data Used

* Raw records loaded: **2,000,000**
* Records after preprocessing: **1,998,965**
* User-session transactions: **446,930**

The original dataset is not included in this repository because of its large size.

## 🧠 Algorithm

The project implements **Apriori Association Rule Mining from scratch**.

No pre-built machine learning algorithms such as `sklearn` or `mlxtend` are used.

The pipeline is:

```text
Kaggle Dataset
      ↓
Data Selection
      ↓
Data Cleaning
      ↓
Session-Based Transaction Creation
      ↓
Frequent Itemset Generation
      ↓
Support Calculation
      ↓
Association Rule Generation
      ↓
Confidence Calculation
      ↓
Lift Calculation
      ↓
Rule Evaluation
      ↓
UI Redesign Insights
```

## 📐 Evaluation Metrics

### Support

Measures how frequently an itemset occurs across all user sessions.

`Support(A,B) = Sessions containing A and B / Total Sessions`

### Confidence

Measures how frequently B occurs in sessions where A occurs.

`Confidence(A → B) = Support(A,B) / Support(A)`

### Lift

Measures the strength of an association compared with the normal occurrence of B.

`Lift(A → B) = Confidence(A → B) / Support(B)`

Interpretation:

* Lift > 1 → Positive association
* Lift = 1 → Independent
* Lift < 1 → Negative association

## 🏆 Main Result

The strongest meaningful association discovered was:

### 🛒 Cart → Purchase

| Metric          |     Result |
| --------------- | ---------: |
| Support         |  **2.27%** |
| Confidence      | **56.33%** |
| Lift            |   **8.79** |
| Test Confidence | **56.62%** |

Approximately **56.33% of sessions containing a cart action also contained a purchase action**.

The lift value of **8.79** indicates a strong positive association between Cart and Purchase relative to the baseline purchase frequency.

## 🧪 Evaluation

A manual train/test approach was used without `sklearn`.

The discovered `Cart → Purchase` relationship produced:

```text
Main Analysis Confidence : 56.33%
Test Confidence          : 56.62%
```

The close values indicate that the discovered relationship remains consistent on the held-out test sessions.

## 💡 UI Redesign Insights

Based on the discovered association:

* Keep the shopping cart clearly visible.
* Make checkout easily accessible from the cart.
* Reduce unnecessary steps between Cart and Purchase.
* Maintain a simple Cart → Checkout → Purchase flow.
* Prioritize this interaction path during UI redesign.

## 📈 Visualizations

The analysis includes visualizations for:

* User Action Distribution
* Frequent Itemset Support
* Association Rule Confidence
* Association Rule Lift
* Main Analysis vs Test Confidence

## 🛠️ Technologies

* Python
* NumPy
* Pandas
* Matplotlib
* Seaborn
* Google Colab
* Kaggle

## 🚫 ML Library Restrictions

The core association-mining pipeline was implemented without:

* Scikit-learn
* MLxtend
* TensorFlow
* PyTorch
* XGBoost
* LightGBM

Support, Confidence, Lift, transaction creation, rule generation, and evaluation were implemented manually.

## 📂 Project Structure

```text
Mobile-App-Feature-Usage-Association-Miner/
│
├── feature_usage_association.ipynb
├── results/
│   └── graphs/
├── README.md
└── requirements.txt
```

## 🚀 How to Run

1. Download the dataset from Kaggle.
2. Use the October 2019 CSV file.
3. Open `feature_usage_association.ipynb` in Google Colab or Jupyter Notebook.
4. Update the dataset path if necessary.
5. Run the notebook cells sequentially.
6. View the generated frequent itemsets, association rules, evaluation results, and visualizations.

## 🔮 Future Improvements

Future versions could include:

* Analysis across additional months.
* Category-specific associations.
* More detailed user behavior sequences.
* Additional association-rule pruning strategies.
* Larger-scale session analysis.
* More advanced UI redesign recommendations.

## 📌 Conclusion

This project demonstrates how association rule mining can be implemented from scratch and applied to real user behavioral data.

The strongest meaningful association was **Cart → Purchase**, with **56.33% confidence** and **8.79 lift**. Testing produced a similar **56.62% confidence**, indicating a stable relationship.

The results suggest that the Cart-to-Purchase interaction path should receive high priority when making data-driven UI redesign decisions.
