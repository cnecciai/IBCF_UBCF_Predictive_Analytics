# Project #3 – Recommender Systems

## Authors: Kassandra Sellers, Clark Necciai  
**Group 46 – Predictive Analytics**  
**Date: June 25th, 2024**  

---

## 📌 Executive Summary
This project explores various **Recommender Systems**, including:
- **User-Based Collaborative Filtering (UBCF)**
- **Item-Based Collaborative Filtering (IBCF)**
- **Association Analysis Models**

We used the **Goodreads Dataset** to evaluate different models and found that the **IBCF model with Pearson correlation and the top 25 most similar items** performed best. Additionally, we identified three **association rules** describing frequently purchased book sets. Finally, we discuss the tradeoffs and applications of these models.

---

## 🛠 Problem Statement & Approach
Our tasks included:
1. **Exploratory Data Analysis (EDA)**: Discover insights about users, reviews, and books.
2. **Data Preprocessing**: Clean the dataset for modeling.
3. **Model Selection**: Compare UBCF and IBCF models.
4. **Association Rule Mining**: Identify frequently read book sets.

---

## 📊 Data Preprocessing
The Goodreads dataset consists of:
- **Books Dataset** (10,000 books)
- **Ratings Dataset** (981,756 ratings)

### 🔹 Cleaning Steps:
- Ignored missing values in `isbn`, `original_publication_year`, `original_title`, and `language_code`.
- Removed **36 duplicate books** and **2,278 duplicate ratings**.
- Eliminated **3,511 ratings** without a reference book.
- Filtered for users with at least **100 ratings**, reducing dataset size to **164,733 ratings**.

---

## 📈 Exploratory Data Analysis (EDA)
### 📚 Oldest Recorded Books
- Books before the common era (B.C.E.) included **The Epic of Gilgamesh**, **The Iliad**, and **The Odyssey**.
- **Plato** was the most published ancient author (5 books).

### ⭐ Rating Distribution Insights
- **Books rated 1 or 2** had fewer ratings, likely due to word-of-mouth.
- **Books rated 3, 4, or 5** had more reviews, indicating quality-driven engagement.

### 🏆 Highest Rated Authors & Books
- **Top-rated author**: *Bill Watterson (Calvin and Hobbes)* (Avg. rating: 4.71)
- **Top-rated book**: *The Complete Calvin and Hobbes* (Rating: 4.82)

---

## 🏗 Recommender Systems Modeling
**Utility Matrix:**
- **Users (Rows)**: 1,192
- **Books (Columns)**: 9,230
- **Sparsity**: **1.5%** of the matrix contains ratings.

### 🔹 Model Comparison
#### **UBCF vs. IBCF**
- **UBCF**: Similarity between users.
- **IBCF**: Similarity between items.
- Both models use **Pearson Correlation** or **Cosine Similarity**.

#### **Model Performance Metrics**
| Model Type | Parameter (nn/k) | Similarity Metric |
|------------|------------------|-------------------|
| UBCF | nn = 10 | Cosine Similarity |
| UBCF | nn = 10 | Pearson Correlation |
| UBCF | nn = 25 | Cosine Similarity |
| UBCF | nn = 25 | Pearson Correlation |
| IBCF | k = 10 | Cosine Similarity |
| IBCF | k = 10 | Pearson Correlation |
| IBCF | k = 25 | Cosine Similarity |
| **IBCF (Best)** | **k = 25** | **Pearson Correlation** |

📊 **Best Model Performance**: IBCF with **k=25, Pearson Correlation** had the highest **AUC** and best **Precision vs. Recall** tradeoff.

---

## 🔄 Predicted Book Recommendations
**UBCF Top 5 Predictions**:
1. *Winter’s Tale* (5.0)
2. *Green Rider* (5.0)
3. *Midnight Crossroad* (5.0)
4. *Birdman* (5.0)
5. *The Man With a Load of Mischief* (4.5)

**IBCF Top 5 Predictions**:
1. *A Short History of Nearly Everything* (4.55)
2. *The Drawing of the Three* (4.55)
3. *Blindness* (4.55)
4. *The Waste Lands* (4.55)
5. *Different Seasons* (4.55)

**Key Insight**: No overlap between UBCF and IBCF recommendations due to different similarity calculations.

---

## 🔍 Association Rule Mining
- Used **Apriori Algorithm** with:
  - **Support**: 0.046
  - **Confidence**: 1

**Top Association Rules:**
1. *A Crown of Swords* & *Winter's Heart* → *The Path of Daggers* (Lift: 17.27)
2. *Lord of Chaos* & *Winter's Heart* → *The Path of Daggers* (Lift: 17.27)
3. *Living Dead in Dallas* & *From Dead to Worse* → *Dead as a Doornail* (Lift: 17.02)

---

## 🏆 Discussion & Business Applications
### **UBCF & IBCF Models**
✅ Used for **personalized recommendations** in e-commerce and content platforms.  
⚠️ **Cold Start Problem**: New users or items lack sufficient data for recommendations.  

### **Association Rule Mining**
✅ Used for **retail product placement & cross-selling**.  
⚠️ Challenge: Determining optimal **support, confidence, and lift thresholds**.

### **Final Recommendation**
🔹 **IBCF (Item-Based Collaborative Filtering) is the best approach** due to its stability and effectiveness in making book recommendations.

---

## 🏁 Conclusion
1. **Preprocessed & explored** Goodreads dataset.
2. **Evaluated** multiple UBCF and IBCF models.
3. **Determined IBCF (k=25, Pearson) as the best** recommendation model.
4. **Generated association rules** for frequently read books.
5. **Discussed business applications & tradeoffs** of each model.

---

## 📂 Appendix
- **Figure #1**: Rating Distributions
- **Figure #2**: Top Average-Rated Authors
- **Figure #3**: Top Average-Rated Books
- **Figure #4**: Utility Matrix Sparsity
- **Figure #5**: Distribution of User Ratings
- **Figure #6**: ROC & Precision vs. Recall Graphs

---

## 📌 How to Run the Code
### 📥 Requirements
```bash
pip install numpy pandas scikit-learn matplotlib
```

### 🚀 Run the Analysis
```python
python recommender_system.py
```

---

## 📜 License
This project is licensed under the MIT License.

---

## 🔗 References
- [Goodreads Dataset](https://www.kaggle.com/datasets)
- [Scikit-Learn Documentation](https://scikit-learn.org/)
