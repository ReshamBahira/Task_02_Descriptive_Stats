# 🔬 Research Findings: Comparative Analysis of Pure Python, Pandas, and Polars

This study evaluates three approaches to computing descriptive statistics—Pure Python, Pandas, and Polars—using the same dataset to assess differences in correctness, usability, performance, and data handling behavior.

---

## Consistency of Statistical Results

Achieving consistent numerical outputs across all three implementations required explicit alignment of statistical definitions and null handling strategies.

A key distinction was observed in the computation of standard deviation:
- Pure Python computes **population standard deviation (N)**
- Pandas and Polars default to **sample standard deviation (N−1)**

To ensure comparability, all implementations were standardized to use population-based calculations.

Handling of missing values also differed:
- **Pure Python**: explicit manual handling  
- **Pandas**: silently excludes nulls during aggregation  
- **Polars**: enforces strict null handling and often raises errors  

This demonstrates a trade-off between **convenience (Pandas)** and **transparency (Polars)**.

---

## Performance and Computational Efficiency

Significant performance differences were observed:

- **Pure Python**: several minutes (manual loops and grouping)
- **Pandas**: ~3–5 seconds
- **Polars**: ~1–2 seconds

Pure Python becomes impractical at scale, while Pandas and Polars leverage optimized internal implementations. Polars demonstrated the highest efficiency due to its Rust-based execution engine.

---

## Usability and Learning Curve

From a usability perspective:

- **Pandas** is the most accessible  
  - Intuitive API (`describe()`, `groupby()`, `value_counts()`)  
  - Strong documentation and community support  

- **Pure Python** provides foundational understanding  
  - Requires explicit logic for grouping, aggregation, and type inference  

- **Polars** introduces stricter typing and expression-based syntax  
  - Slightly higher learning curve  
  - Better suited for scalable and production workflows  

---

## Data Reliability and Validation

A key finding is that **no tool guarantees correctness**.

During analysis, discrepancies were observed in Polars outputs due to malformed input data (dictionary-like strings). Without cross-validation against Pure Python and Pandas, these issues could have gone unnoticed.

This highlights the importance of **validating outputs across multiple approaches**.

---

## Role of AI in Code Generation

AI tools were useful for generating initial code structure, but limitations were observed:

Common failure cases:
- Mixed-type columns  
- Encoding issues  
- Incorrect statistical assumptions (e.g., std deviation differences)  

AI-generated code should be treated as a **starting point**, not a final solution. All outputs must be verified, especially data cleaning and type handling logic.

---

## Data Cleaning and Type Inference

Unlike earlier datasets, this dataset stored numeric values directly. However, challenges remained in correctly identifying column types.

- Columns like `page_id` and `ad_id` appear numeric but are **categorical identifiers**
- An **80% numeric threshold** was used for classification
- Binary columns (0/1) were treated as numeric, where means represent **prevalence rates**

---

## Comparative Summary

| Dimension        | Pure Python | Pandas | Polars |
|-----------------|------------|--------|--------|
| Implementation Complexity | High | Medium | Medium |
| Ease of Use      | Moderate   | High   | Moderate |
| Type Handling    | Manual     | Implicit | Strict |
| Null Handling    | Manual     | Implicit | Explicit |
| Performance      | Low        | High   | Very High |
| Scalability      | Limited    | Moderate | High |

---

## Conclusion

Each approach offers distinct advantages:

- **Pure Python**: best for learning and understanding underlying mechanics  
- **Pandas**: best for everyday data analysis due to ease of use  
- **Polars**: best for performance and large-scale data processing  

Overall, the choice of tool depends on the balance between **ease of use, performance, and data reliability requirements**.
