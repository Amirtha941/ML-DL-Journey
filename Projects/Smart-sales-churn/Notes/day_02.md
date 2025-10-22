
## 🧩 **Step 5 → Identify Target Column**

### 🔹 `if target_col not in df.columns:`

Checks whether your chosen column name (like `"churn_label"`) actually exists in your dataset.

### 🔹 `df.columns`

Gives a list of all column names in your DataFrame.  
Useful to confirm spelling and case.

### 🔹 `print([col for col in df.columns if 'churn' in col.lower()])`

Searches all columns that contain the word “churn” (case-insensitive).  
Helps you find potential target columns when you’re unsure of the name.

----------

## 📊 **Step 6 → Target Distribution**

### 🔹 `df[target_col].value_counts()`

Counts how many “Yes” and “No” (or 1 and 0) values are in your target column.  
Helps you check **class balance** — important for model training.

👉 Example output:

`No  5174  Yes  1869` 

### 🔹 `sns.countplot(x=target_col, data=df)`

Creates a bar chart showing how many customers churned vs didn’t churn.  
(Here `sns` = Seaborn, a plotting library.)

### 🔹 `plt.title('Churn Distribution')`

Adds a title to the plot.

### 🔹 `plt.show()`

Displays the chart output.

----------

## 🧹 **Step 7 → Data Type Check & Missing Values**

### 🔹 `df.isna().sum()`

Checks for **missing (NaN)** values in each column.  
The `.sum()` part counts how many NaNs are present per column.

👉 Example:

`totalcharges  11 senior_citizen 0` 



`isna()` is a **Pandas function** used to **detect missing values** in a DataFrame or Series. It returns a Boolean mask where:

-   `True` means the value is missing (like `NaN`, `None`, or `NaT`)
    
-   `False` means the value is present
    

### 🔍 Example

python

```
import pandas as pd
import numpy as np

df = pd.DataFrame({
    'Name': ['Alice', 'Bob', None],
    'Age': [25, np.nan, 30]
})

print(df.isna())

```

**Output:**

Code

```
    Name    Age
0  False  False
1  False   True
2   True  False

```

### 🧠 Use Cases

-   **Check for missing data**: `df.isna().sum()` gives count of missing values per column
    
-   **Filter missing rows**: `df[df['Age'].isna()]` returns rows where Age is missing
    
-   **Clean data**: Combine with `fillna()` or `dropna()` to handle missing entries
    

### 🔁 Related Functions

| Function |        Description        |
|:--------:|:-------------------------:|
| isna()   | Detect missing values     |
| notna()  | Detect non-missing values |
| dropna() | Remove missing values     |
| fillna() | Replace missing values    |

### 🔹 `df.dtypes`

Shows the **data type** of each column (like `int64`, `float64`, or `object`).  
This helps you find columns that should be numbers but are stored as text.

### 🔹 `pd.to_numeric(df['totalcharges'], errors='coerce')`

Converts a text column into numbers.  
If something can’t be converted (like a blank or text), it becomes `NaN` instead of crashing.  
`errors='coerce'` means “quietly turn bad data into NaN”.

### 🔹 `df['totalcharges'].isna().sum()`

Counts how many NaN values were created during that conversion.

----------

## 🧠 **Step 8 → Initial Observations**

### 🔹 `df.shape`

Tells how many rows and columns your dataset has, as a tuple `(rows, columns)`.

### 🔹 `print("- Dataset Shape:", df.shape)`

Displays the dataset size clearly, e.g. `(- Dataset Shape: (7043, 33))`.

### 🔹 The print statements in this step

Summarize what you have done — it’s not analysis, but a quick checkpoint.  
It’s a way of confirming:

-   You loaded the data correctly
    
-   Target is identified
    
-   Missing values are known
    
-   Columns are cleaned


## 💡 **Summary Table for Notes**

|               Function              |         Meaning / Use         |           Example Output           |
|:-----------------------------------:|:-----------------------------:|:----------------------------------:|
| df.columns                          | Lists all column names        | ['customerid', 'churn_label', ...] |
| df[target_col].value_counts()       | Counts how many Yes/No        | No: 5174, Yes: 1869                |
| sns.countplot()                     | Bar chart for target variable | Churn distribution plot            |
| df.isna().sum()                     | Count missing values          | totalcharges: 11                   |
| df.dtypes                           | Show data types               | float64, object, int64...          |
| pd.to_numeric(..., errors='coerce') | Convert column to numbers     | Converts text → NaN                |
| df.shape                            | Shows (rows, columns)         | (7043, 33)                         |
