To generalize the code so the user can choose different algorithms (e.g., Fuzzy Matching, Regex Matching, or custom algorithms), we can create a modular framework where:

1. **Algorithms are implemented as independent Python functions**.
2. **Users can pass the desired algorithm as a parameter**.
3. **Dynamic UDF registration allows for flexibility**.

Here’s how you can achieve this:

---

### **Generalized Framework**

#### 1. **Define Matching Algorithms**
Create a set of functions implementing various matching algorithms.

```python
from pyspark.sql.functions import udf, col
from pyspark.sql.types import FloatType
from fuzzywuzzy import fuzz
import re

# Algorithm 1: Fuzzy Matching
def fuzzy_match(str1, str2):
    if str1 and str2:  # Check for non-null values
        return fuzz.ratio(str1, str2) / 100.0  # Convert to percentage (0 to 1 scale)
    return 0.0

# Algorithm 2: Regex Matching
def regex_match(pattern, text):
    if pattern and text:  # Check for non-null values
        return 1.0 if re.search(pattern, text) else 0.0
    return 0.0

# Algorithm 3: Custom Matching (Exact Match with Case Normalization)
def exact_match(str1, str2):
    if str1 and str2:  # Check for non-null values
        return 1.0 if str1.strip().lower() == str2.strip().lower() else 0.0
    return 0.0
```

#### 2. **Dynamic UDF Registration**
Create a mapping of algorithm names to their implementations.

```python
# Algorithm registry
ALGORITHM_REGISTRY = {
    "fuzzy": fuzzy_match,
    "regex": regex_match,
    "exact": exact_match
}

# Function to get UDF dynamically
def get_matching_udf(algorithm_name, *args):
    if algorithm_name not in ALGORITHM_REGISTRY:
        raise ValueError(f"Algorithm '{algorithm_name}' is not supported.")
    # Wrap the algorithm function as a UDF
    return udf(lambda x, y: ALGORITHM_REGISTRY[algorithm_name](x, y, *args), FloatType())
```

---

### **Generalized Recon Logic**

1. **Pass Algorithm and Threshold Dynamically**:
   - User specifies the algorithm (`fuzzy`, `regex`, `exact`) and the threshold for determining matches.

2. **Modified Recon Function**:
   Use the selected algorithm for recon.

```python
def perform_recon(table_a, table_b, common_field, match_field, algorithm_name, threshold, regex_pattern=None):
    # Join tables on the common field
    joined_df = table_a.join(table_b, on=common_field, how="inner")
    
    # Get UDF for the chosen algorithm
    match_udf = get_matching_udf(algorithm_name, regex_pattern) if algorithm_name == "regex" else get_matching_udf(algorithm_name)

    # Apply matching algorithm
    joined_df = joined_df.withColumn("similarity", match_udf(col(f"{match_field}_table_a"), col(f"{match_field}_table_b")))
    
    # Classify matches and non-matches based on the threshold
    matched_df = joined_df.filter(col("similarity") >= threshold)
    non_matched_df = joined_df.filter(col("similarity") < threshold)

    return matched_df, non_matched_df
```

---

### **Example Usage**

#### **1. Example Data**

**Table A**:
| id  | name       | city       |
| ----|------------|------------|
| 1   | Alice      | New York   |
| 2   | Bob        | Chicago    |
| 3   | Charlie    | San Francisco |

**Table B**:
| id  | name       | city        |
| ----|------------|-------------|
| 1   | Alicia     | New York    |
| 2   | Robert     | Chicago     |
| 4   | David      | Houston     |

#### **2. Call the Recon Function**

```python
# Initialize Spark session
spark = SparkSession.builder.appName("Generalized Recon").getOrCreate()

# Create DataFrames
columns_a = ["id", "name", "city"]
data_a = [(1, "Alice", "New York"), (2, "Bob", "Chicago"), (3, "Charlie", "San Francisco")]
table_a = spark.createDataFrame(data_a, columns_a)

columns_b = ["id", "name", "city"]
data_b = [(1, "Alicia", "New York"), (2, "Robert", "Chicago"), (4, "David", "Houston")]
table_b = spark.createDataFrame(data_b, columns_b)

# Perform recon using different algorithms
matched_fuzzy, non_matched_fuzzy = perform_recon(table_a, table_b, "id", "name", "fuzzy", 0.8)
matched_regex, non_matched_regex = perform_recon(table_a, table_b, "id", "name", "regex", 1.0, regex_pattern="Alic.*")
matched_exact, non_matched_exact = perform_recon(table_a, table_b, "id", "name", "exact", 1.0)

# Display results
print("Fuzzy Matching - Matched:")
matched_fuzzy.show()

print("Regex Matching - Matched:")
matched_regex.show()

print("Exact Matching - Matched:")
matched_exact.show()
```

---

### **How This Works**

1. **Dynamic Algorithm Selection**:
   - Users can select an algorithm from the `ALGORITHM_REGISTRY` by passing its name (`fuzzy`, `regex`, `exact`, etc.).

2. **Threshold-Based Classification**:
   - Records are classified as matched or non-matched based on a user-defined similarity threshold.

3. **Extensibility**:
   - New algorithms can be added to the `ALGORITHM_REGISTRY` easily.

4. **Custom Parameters**:
   - Algorithms requiring additional parameters (e.g., regex patterns) can be supported by adding them as function arguments.

---

### **Output Example**
**Fuzzy Matching**:
| id  | name       | similarity |
| ----|------------|------------|
| 1   | Alice      | 0.9        |

**Regex Matching**:
| id  | name       | similarity |
| ----|------------|------------|
| 1   | Alicia     | 1.0        |

**Exact Matching**:
| id  | name       | similarity |
| ----|------------|------------|
| -   | -          | -          |

This generalized approach allows users to configure the matching logic dynamically while keeping the system modular and extensible. Let me know if you need further refinements!
