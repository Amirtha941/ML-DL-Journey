## `sns.set(style="whitegrid")`

The line `sns.set(style="whitegrid")` is a configuration command from the **Seaborn** library in Python. It sets the overall aesthetic style for your plots.

### 🎨 What It Does

-   `style="whitegrid"` adds a **white background with gridlines**, which is especially useful for plots like **box plots**, **violin plots**, or **bar plots** where comparing values is easier with reference lines.
    
-   It improves readability and gives a clean, professional look to your visualizations.
    

### 🔧 Other Style Options in Seaborn

You can experiment with different styles depending on your data and presentation goals:

|    Style    |                       Description                      |
|:-----------:|:------------------------------------------------------:|
| "darkgrid"  | Dark background with gridlines                         |
| "whitegrid" | White background with gridlines (default for boxplots) |
| "dark"      | Dark background without gridlines                      |
| "white"     | White background without gridlines                     |
| "ticks"     | Minimalist style with ticks on axes                    |


## Box Plot


A **box plot** (also called a box-and-whisker plot) is a compact way to visualize the distribution of a dataset. It’s especially useful for spotting **skewness**, **spread**, and **outliers** at a glance.

### 📦 What a Box Plot Shows

It’s built from the **five-number summary**:

-   **Minimum**: The smallest value (excluding outliers)
    
-   **Q1 (First Quartile)**: 25th percentile
    
-   **Median (Q2)**: 50th percentile, the middle value
    
-   **Q3 (Third Quartile)**: 75th percentile
    
-   **Maximum**: The largest value (excluding outliers)
    

### 🧠 How to Interpret It

Here's how to read each part:

-   **The Box**: Represents the **interquartile range (IQR)** — the middle 50% of the data (from Q1 to Q3)
    
-   **The Line Inside the Box**: The **median** — tells you where the center of the data lies
    
-   **Whiskers**: Extend from the box to the **minimum and maximum** values (excluding outliers)
    
-   **Dots or Stars Outside the Whiskers**: These are **outliers** — values that fall outside 1.5 × IQR from the quartiles
    

### 🔍 Quick Insights You Can Get

-   If the **median is centered** in the box → data is symmetric
    
-   If the **median is closer to Q1 or Q3** → data is skewed
    
-   **Longer whiskers** → more spread in that direction
    
-   **Outliers** → potential anomalies or interesting data points
    

### 📊 Example Use Case

Say you're comparing test scores across three classes. A box plot for each class lets you instantly see:

-   Which class has the highest median score
    
-   Which class has the widest score range
    
-   Whether any class has outliers (e.g., a student who scored unusually low or high)