## #1 — Creating, Reading, and Writing

### **Core Concepts**

- Pandas provides two fundamental objects:
    - **Series**: 1D labeled array
    - **DataFrame**: 2D labeled table
- DataFrames can be constructed manually or loaded from files.
- Pandas supports importing and exporting many formats: CSV, Excel, JSON, etc.
- Index labels provide structure to rows.

### **Key Points**
- Create DataFrames using:
    - dict of lists
    - list of dicts
    - 2D lists
- Read data from disk using `pd.read_csv(...)`.
- Write data with `.to_csv()`, `.to_excel()`, `.to_json()`.
- `index=False` avoids writing row numbers into saved files.

### **Example**
```python
import pandas as pd

df = pd.DataFrame({
    "Name": ["Bob", "Alice"],
    "Age": [25, 30]
})

df.to_csv("output.csv", index=False)
```
---
## #2 — Indexing, Selecting, and Assigning
### **Core Concepts**
- Accessing data: column selection, row selection, filtering.
- Two primary indexers:
    - `.loc` — label-based
    - `.iloc` — position-based
- New columns can be created and assigned.

### **Key Points**
- Column access:
    - Attribute: `df.column`
    - Indexer: `df["column"]`
- Boolean indexing filters rows.
- Avoid chained indexing; use `.loc`.
### **Example**

```python
cheap_italian = df.loc[
    (df["price"] < 20) & (df["country"] == "Italy")
]

df["price_per_point"] = df["price"] / df["points"]
```

---
## #3 — Summary Functions and Maps

### **Core Concepts**

- Summarizing data using built-ins like mean, min, max.
- Extracting unique values and frequencies.
- Transforming data with `map` and `apply`.

### **Key Points**
- `.describe()` gives high-level statistics.
- `.unique()` returns unique values.
- `.value_counts()` shows category frequencies.
- `map` = element-wise transformation (Series only).
- `apply` = flexible row/column transformations.

### **Example**
```python
df["review_length"] = df["description"].map(len)

df["is_expensive"] = df["price"].apply(lambda p: p > 50)
```

---

## #4 — Data Types and Missing Values
### **Core Concepts**
- Understanding pandas dtypes and converting between them.
- Handling missing values with detection, dropping, or filling.
- Missing values appear as `NaN` or `None`.

### **Key Points**
- Inspect types: `.dtype`, `.dtypes`
- Convert type: `astype()`
- Missing data operations:
    - Detect: `.isna()`, `.notna()`
    - Fill: `.fillna()`
    - Remove: `.dropna()`
- Missing values propagate through math unless handled.

### **Example**
```python
df["price"] = df["price"].astype("float64")

df["price"] = df["price"].fillna(df["price"].mean())
```

---

## #5 — Grouping and Sorting
### **Core Concepts**
- Grouping rows with similar values to compute aggregate statistics.
- Sorting results by column values.
- Multi-column grouping for hierarchical aggregation.

### **Key Points**
- `groupby()` splits the DataFrame by key(s).
- Aggregations: `.mean()`, `.max()`, `.count()`, `.min()`.
- Multiple aggregations via `.agg(["min", "max", "mean"])`.
- Sorting:
    - `sort_values("col")`
    - `ascending=False` for descending order.
### **Example**
```python
country_counts = df.groupby("country")["title"].count()

best = df.groupby(["country", "province"])["points"].max()
```
---

## #6 — Renaming and Combining Data
### **Core concepts**
- Modifying labels with `rename`.
- Combining multiple DataFrames using `concat`, `merge`, `join`.
- SQL-style merges support inner, outer, left, and right joins.

### **Key Points**
- Rename columns: `rename(columns={...})`
- Concatenate DataFrames vertically or horizontally with `concat`.
- Merge DataFrames on shared keys with `merge()`.
- Join DataFrames on their index using `.join()`.
### **Example**
```python
df = df.rename(columns={"points": "score"})

combined = df1.merge(df2, on="wine_id", how="inner")

stacked = pd.concat([df1, df2], axis=0)
```
