# Task_02_Descriptive_Stats
# 📊 Descriptive Statistics Analysis — Milestone A

## 📌 Project Overview

This project implements descriptive statistical analysis on real-world datasets using three different approaches:

1. **Pure Python (Standard Library Only)**
2. **Pandas**
3. **Polars**

The objective is to understand how data analysis works at different abstraction levels — from manual implementation to high-performance libraries — while producing consistent results across all approaches.

The analysis includes:
- Dataset-level statistics
- Column-level statistics
- Grouped analysis
- Data type inference and handling
- Performance and behavior comparison

---

## ⚙️ How to Run the Scripts

### 🔹 Requirements
- Python 3.x
- Google Colab or local environment

---

### 🔹 Script 1: Pure Python

**File:** `pure_python_analysis.py`

**Run:**
```bash
python pure_python_analysis.py
```

**Description:**
- Uses only standard libraries (`csv`, `math`, `collections`)
- Manually computes:
  - Mean, median, standard deviation
  - Mode, frequency counts
  - Grouped analysis using dictionaries

---

### 🔹 Script 2: Pandas

**File:** `pandas_analysis.py`

**Install:**
```bash
pip install pandas
```

**Run:**
```bash
python pandas_analysis.py
```

**Description:**
- Uses Pandas DataFrame operations
- Handles malformed CSV using fallback parsing
- Uses built-in methods:
  - `describe()`
  - `groupby()`
  - `value_counts()`

---

### 🔹 Script 3: Polars

**File:** `polars_analysis.py`

**Install:**
```bash
pip install polars
```

**Run:**
```bash
python polars_analysis.py
```

**Description:**
- Uses Polars for high-performance data processing
- Handles malformed CSV using Python `csv` pre-processing
- Implements strict type handling and fast grouped analysis

---

## 📊 Summary of Findings

### 🔹 Dataset Insights

- The dataset contains a large number of records with minimal missing values, indicating high data quality.
- A small number of entities (e.g., `page_id`) dominate the dataset, showing a skewed distribution.
- Most numeric variables (e.g., `spend`, `impressions`) show:
  - Low median values
  - High mean values
  - → indicating outliers and skewness

### 🔹 Behavioral Insights

- Campaign behavior varies significantly across groups:
  - Some groups focus on high-volume output
  - Others focus on targeted engagement (high CTA usage)
- Binary indicator columns (0/1) reveal prevalence patterns:
  - Mean values can be interpreted as percentage occurrence

### 🔹 Data Characteristics

- Certain columns appear numeric (e.g., `page_id`, `ad_id`) but are actually categorical identifiers
- Proper type inference is critical to avoid incorrect aggregation
- Grouped analysis highlights differences in strategy across entities

---

## ⚖️ Comparison of Approaches

| Dimension | Pure Python | Pandas | Polars |
|---|---|---|---|
| Code Complexity | High | Medium | Medium |
| Ease of Use | Moderate | High | Moderate |
| Type Handling | Manual | Implicit | Strict |
| Null Handling | Manual | Silent | Explicit |
| Performance | Slow | Fast | Fastest |
| Scalability | Low | Medium | High |

---

### 🔹 Key Observations

**✅ Pure Python**
- Best for understanding internal mechanics
- Requires explicit handling of:
  - Missing values
  - Type inference
  - Grouping logic
- Not scalable for large datasets

**✅ Pandas**
- Most user-friendly
- Ideal for day-to-day analysis
- Provides high-level abstraction
- May silently ignore issues (e.g., nulls)

**✅ Polars**
- Fastest and most efficient
- Strict type system improves reliability
- Less forgiving with malformed data
- Better suited for large-scale processing

---

## ⚠️ Data Handling Challenges

- The dataset contained malformed dictionary-like fields
- Differences in parsing behavior:
  - Pandas: flexible, skips errors
  - Polars: strict, requires preprocessing
- Solution:
  - Used Python `csv` module to safely load data before processing in Polars

---

## 🧠 Key Learnings

- High-level tools (Pandas, Polars) abstract complex operations, but understanding fundamentals (via Pure Python) is critical
- Data validation is essential — tools do not guarantee correctness
- Performance differences become significant even at moderate dataset sizes
- Choosing the right tool depends on:
  - Dataset size
  - Required performance
  - Level of control needed

---

## 📄 Reflection

For a deeper comparison of:
- Standard deviation differences
- Null handling behavior
- Learning recommendations
- AI usage

👉 See: [REFLECTION.md](./REFLECTION.md)

---

## 🚀 Conclusion

This project demonstrates that:

- **Pure Python** builds foundational understanding
- **Pandas** enables efficient and intuitive analysis
- **Polars** provides high-performance, scalable processing

Each tool serves a different purpose, and effective data analysis requires understanding their strengths, limitations, and appropriate use cases.
