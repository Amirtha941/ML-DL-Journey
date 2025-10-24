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