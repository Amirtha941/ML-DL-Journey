# describe()

The `describe()` function in **Pandas** is your go-to tool for getting a quick statistical summary of your dataset. It’s like a mini health checkup for your DataFrame—especially useful when you're exploring data or prepping it for machine learning.

### 🧪 What `describe()` Does

When you call `df.describe()` on a DataFrame:

-   It returns **descriptive statistics** for each column.
    
-   By default, it focuses on **numeric columns**, but you can include others too.
    

### 📊 Default Output Includes:

| Statistic |           Meaning          |
|:---------:|:--------------------------:|
| count     | Number of non-null entries |
| mean      | Average value              |
| std       | Standard deviation         |
| min       | Minimum value              |
| 25%       | 1st quartile (Q1)          |
| 50%       | Median (Q2)                |
| 75%       | 3rd quartile (Q3)          |
| max       | Maximum value              |


### 🧩 Syntax


```
df.describe(percentiles=None, include=None, exclude=None)
```

### 🔧 Useful Parameters

-   `percentiles`: Customize which percentiles to show (e.g., `[0.1, 0.9]`)
    
-   `include`: Include specific data types like `'object'`, `'all'`, or a list
    
-   `exclude`: Exclude specific data types

### 🧮 `numeric_cols = df.select_dtypes(include='number')`

-   **Purpose**: Filters the DataFrame `df` to include only columns with numeric data types (e.g., `int`, `float`).
    
-   **Why it matters**: Correlation calculations only make sense for numeric data. This step ensures you're not accidentally including strings or categorical data.
    

### 📐 `plt.figure(figsize=(8,5))`

-   **Purpose**: Initializes a new Matplotlib figure with a custom size—8 inches wide and 5 inches tall.
    
-   **Why it matters**: Controls the layout and readability of your heatmap, especially when dealing with many features.
    

### 🌡️ `sns.heatmap(numeric_cols.corr(), annot=True, cmap='coolwarm', fmt=".2f")`

This is the heart of our visualization. Let’s break it down:

|      Component      |                                       Function                                      |
|:-------------------:|:-----------------------------------------------------------------------------------:|
| numeric_cols.corr() | Computes the correlation matrix between numeric columns. Values range from -1 to 1. |
| annot=True          | Displays the actual correlation values inside each cell of the heatmap.             |
| cmap='coolwarm'     | Sets the color palette: blue for negative correlation, red for positive.            |
| fmt=".2f"           | Formats the annotation text to show 2 decimal places.                               |
| vmin / vmax         | Set color scale limits                                                              |


### 🏷️ `plt.title("Correlation between numeric features")`

-   **Purpose**: Adds a title to the plot.
    
-   **Why it matters**: Makes your visualization self-explanatory, especially when sharing or presenting.
    

### 🎯 `plt.show()`

-   **Purpose**: Renders the plot in your output window or notebook.
    
-   **Why it matters**: Without this, the plot might not display—especially in scripts or non-interactive environments.

  
# heatmap()
A **heatmap** is a powerful visual tool that uses color gradients to represent the magnitude of values in a matrix or dataset. Think of it as a thermal image for your data—hotter colors often mean higher values, cooler ones mean lower.

### 🔥 What Heatmaps Reveal

-   **Patterns**: Easily spot clusters, correlations, or anomalies.
    
-   **Density**: See where values concentrate.
    
-   **Comparisons**: Visually compare across rows and columns.
    

### 🧪 Common Use Cases

-   **Correlation matrices** in machine learning
    
-   **Sensor grids** in embedded systems
    
-   **Confusion matrices** in classification tasks
    
-   **UI click tracking** in web analytics

### 🧩 Key Parameters  

|  Parameter  |                   Purpose                   |
|:-----------:|:-------------------------------------------:|
| data        | 2D array or DataFrame                       |
| cmap        | Color palette (e.g., 'coolwarm', 'viridis') |
| annot       | Show values inside cells                    |
| linewidths  | Space between cells                         |
| vmin / vmax | Set color scale limits                      |

