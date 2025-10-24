### 1. **Categorical (Qualitative) Data**

These are labels or names used to identify categories. They don’t have numerical meaning.

-   **Nominal**: No inherent order.
    
    -   Examples:
        
        -   Sensor type: `Temperature`, `Humidity`, `Pressure`
            
        -   Protocol: `Wi-Fi`, `Bluetooth`, `Zigbee`
            
-   **Ordinal**: Categories with a logical order.
    
    -   Examples:
        
        -   Signal strength: `Low`, `Medium`, `High`
            
        -   Security level: `Basic`, `Advanced`, `Enterprise`
            

### 🔹 2. **Numerical (Quantitative) Data**

These are measurable values and can be used for mathematical operations.

-   **Discrete**: Countable values.
    
    -   Examples:
        
        -   Number of packets sent: `12`, `45`, `100`
            
        -   GPIO pins used: `3`, `7`, `10`
            
-   **Continuous**: Can take any value within a range.
    
    -   Examples:
        
        -   Temperature: `23.5°C`, `98.6°F`
            
        -   Voltage: `3.3V`, `5.0V`
            

### 🔹 3. **Time Series Data**

Data points indexed in time order—critical in embedded systems and sensor logs.

-   Examples:
    
    -   Sensor readings every second
        
    -   CPU usage over time
        
    -   IoT device heartbeat logs
        

### 🔹 4. **Textual Data**

Unstructured or semi-structured text—often used in NLP or log analysis.

-   Examples:
    
    -   Error messages: `"Sensor timeout"`
        
    -   User feedback: `"Device is slow to respond"`
        
    -   Firmware logs
        

### 🔹 5. **Binary Data**

Only two possible values—often used in classification or embedded flags.

-   Examples:
    
    -   `True`/`False`
        
    -   `Secure`/`Insecure`
        
    -   `On`/`Off`
        

### 🔹 6. **Mixed-Type Data**

Datasets that combine multiple types—common in real-world applications.

-   Example: A dataset for an IoT security system might include:
    
    -   Device ID (Nominal)
        
    -   Firmware version (Ordinal)
        
    -   Battery level (Continuous)
        
    -   Last ping time (Time Series)
        
    -   Status message (Textual)

 ## fillna()

 
`fillna()` is a powerful method in **Pandas** used to handle **missing data** (i.e., `NaN` values) in a DataFrame or Series. It lets you **fill in gaps** with specified values or strategies—essential for cleaning datasets before analysis or modeling.

### 🔧 Syntax
```
DataFrame.fillna(value=None, method=None, axis=None, inplace=False)
```

### 💡 Common Use Cases

#### 1. **Fill with a constant value**
```
df.fillna(0)
```

Replaces all `NaN` values with `0`.

#### 2. **Fill with column-specific values**
```
df.fillna({'temperature': 25, 'humidity': 50})
```

Fills missing values in each column with custom defaults.

#### 3. **Forward fill (propagate last valid value)**
```
df.fillna(method='ffill')
```

Useful for time series—fills gaps using the previous value.

#### 4. **Backward fill (use next valid value)**
```
df.fillna(method='bfill')
```

Fills missing values using the next available value.

#### 5. **In-place modification**
```
df.fillna(0, inplace=True)
```

Modifies the original DataFrame without creating a copy.

### 🧠 Why It Matters

For ML workflows, missing values can break models or skew results. `fillna()` helps you:

-   Maintain data integrity
    
-   Avoid dropping valuable rows
    
-   Prepare clean inputs for training   

## groupby()

`groupby()` in **Pandas** is one of the most powerful tools for data analysis—it lets you **split your data into groups**, apply operations to each group, and then **combine the results**. This is often referred to as the **Split–Apply–Combine** strategy.

### 🔧 Syntax
```
df.groupby('column_name')
```

You can also group by multiple columns:
```
df.groupby(['col1', 'col2'])
```

### 🧠 What You Can Do with `groupby()`

|    Operation    |           Example Use Case          |
|:---------------:|:-----------------------------------:|
| .sum()          | Total sales per product category    |
| .mean()         | Average temperature per sensor      |
| .count()        | Number of entries per device        |
| .max() / .min() | Highest/lowest reading per location |
| .agg()          | Apply multiple functions at once    |

### 🔍 Breakdown of `df.groupby('churn_label')[numeric_cols]`

-   `df`: Your DataFrame—likely containing customer or user data.
    
-   `.groupby('churn_label')`: Splits the data into groups based on the values in the `'churn_label'` column. For example:
    
    -   `churn_label = 0`: Customers who didn’t churn
        
    -   `churn_label = 1`: Customers who did churn
        
-   `[numeric_cols]`: Selects only the numeric columns from each group. This assumes `numeric_cols` is a list of column names like:
    
    ```
    numeric_cols = ['tenure', 'monthly_charges', 'total_charges']
    ```
    

### 🧠 What You Can Do Next

Once grouped, you can apply aggregation functions:
```
df.groupby('churn_label')[numeric_cols].mean()   # Average values per churn group
df.groupby('churn_label')[numeric_cols].sum()    # Total values per churn group
df.groupby('churn_label')[numeric_cols].count()  # Number of entries per group
```

### 📊 Example Output

If you run:

```
df.groupby('churn_label')[numeric_cols].mean()
```
You might get:

### 📊 Example

| churn_label | tenure | monthly_charges | total_charges |
|:-----------:|:------:|:---------------:|:-------------:|
| 0           | 32.5   | 65.4            | 2100.3        |
| 1           | 12.1   | 75.2            | 890.7         |

This tells you that churned customers tend to have shorter tenure and higher monthly charges—valuable insight for retention strategies.
