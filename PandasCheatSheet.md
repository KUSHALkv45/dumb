Absolutely. Think of this as a **Pandas field manual** you keep in your backpack before walking into a data-analyst interview 🧭🐼
Clean, compact, and battle-tested.

---

# 🐼 Pandas Cheat Sheet (Interview-Focused)

---

## 1️⃣ Creating & Inspecting Data

```python
import pandas as pd
```

### Create DataFrame

```python
df = pd.DataFrame({
    "A": [1, 2, 3],
    "B": [4, 5, 6]
})
```

### Quick look

```python
df.head()
df.tail()
df.sample(5)

df.shape
df.columns
df.dtypes
df.info()
df.describe()
```

---

## 2️⃣ Selecting Data (VERY IMPORTANT)

### Columns

```python
df["A"]
df[["A", "B"]]
```

### Rows

```python
df.iloc[0]          # by index
df.iloc[0:5]

df.loc[0]           # by label
df.loc[df["A"] > 2]
```

### Conditional filtering

```python
df[(df["A"] > 1) & (df["B"] < 6)]
df[df["A"].isin([1, 3])]
```

---

## 3️⃣ Handling Missing Values

```python
df.isna()
df.isna().sum()
df.isna().mean() * 100
```

### Drop

```python
df.dropna()
df.dropna(axis=1)
```

### Fill

```python
df.fillna(0)
df["A"].fillna(df["A"].mean())
df.ffill()
df.bfill()
```

---

## 4️⃣ Data Type Conversion

```python
df["A"] = df["A"].astype(int)
df["date"] = pd.to_datetime(df["date"], errors="coerce")
df["num"] = pd.to_numeric(df["num"], errors="coerce")
```

### Datetime features

```python
df["year"] = df["date"].dt.year
df["month"] = df["date"].dt.month
df["day"] = df["date"].dt.day
df["hour"] = df["date"].dt.hour
```

---

## 5️⃣ Sorting & Ranking

```python
df.sort_values("A")
df.sort_values(["A", "B"], ascending=[True, False])
```

```python
df["rank"] = df["A"].rank(method="dense")
```

---

## 6️⃣ GroupBy (MOST ASKED)

### Basic

```python
df.groupby("category")["sales"].sum()
```

### Multiple aggregations

```python
df.groupby("category").agg(
    total_sales=("sales", "sum"),
    avg_sales=("sales", "mean"),
    cnt=("sales", "count")
).reset_index()
```

### Get row with max per group

```python
df.loc[df.groupby("category")["sales"].idxmax()]
```

---

## 7️⃣ Value Counts & Percentages

```python
df["status"].value_counts()
df["status"].value_counts(normalize=True) * 100
```

---

## 8️⃣ Duplicates

```python
df.duplicated()
df.drop_duplicates()
df.drop_duplicates(subset=["user_id"], keep="last")
```

---

## 9️⃣ Apply, Map, Vectorization

### Apply (row/column-wise)

```python
df["A"].apply(lambda x: x * 2)
```

### Map (dictionary mapping)

```python
df["grade"] = df["score"].map({
    "A": "Excellent",
    "B": "Good"
})
```

⚠️ Prefer **vectorized operations** over `apply`.

---

## 🔟 Binning & Categorization

```python
pd.cut(df["age"], bins=[0,18,35,60,100])
```

```python
pd.qcut(df["income"], q=4)
```

---

## 1️⃣1️⃣ Merging & Joining

```python
pd.merge(df1, df2, on="id", how="inner")
pd.merge(df1, df2, on="id", how="left")
```

```python
df1.join(df2.set_index("id"), on="id")
```

---

## 1️⃣2️⃣ String Operations

```python
df["name"].str.lower()
df["name"].str.upper()
df["email"].str.contains("@gmail")
df["text"].str.replace("old", "new")
df["text"].str.split("_")
```

---

## 1️⃣3️⃣ Outlier Detection (IQR)

```python
Q1 = df["x"].quantile(0.25)
Q3 = df["x"].quantile(0.75)
IQR = Q3 - Q1

df[(df["x"] < Q1 - 1.5*IQR) | (df["x"] > Q3 + 1.5*IQR)]
```

---

## 1️⃣4️⃣ Reshaping Data

### Pivot

```python
df.pivot(index="date", columns="category", values="sales")
```

### Pivot Table

```python
pd.pivot_table(
    df,
    index="date",
    columns="category",
    values="sales",
    aggfunc="sum"
)
```

---

## 1️⃣5️⃣ Performance Tips (Interview Gold)

* Prefer vectorized ops over loops
* Use `.loc[]` to avoid `SettingWithCopyWarning`
* Avoid chained indexing
* Use `category` dtype for low-cardinality strings

```python
df["type"] = df["type"].astype("category")
```

---

## 🎯 If You Remember ONLY These

If interview pressure hits, **lock these in**:

* `groupby + agg`
* `value_counts(normalize=True)`
* `idxmax()`
* `pd.to_datetime`
* `merge`
* `isna().mean()`

---

If you want next:

* 🧠 **SQL → Pandas mapping cheat sheet**
* 🔥 **Top 15 Pandas interview traps**
* 📊 **EDA cheat sheet**
* 📝 **Mock interview with timer**

Just tell me what you want next.
