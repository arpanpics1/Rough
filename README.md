from pyspark.sql import SparkSession
from pyspark.sql.functions import col

# Initialize a SparkSession
spark = SparkSession.builder \
    .appName("Simple PySpark Example") \
    .getOrCreate()

# Create a DataFrame
data = [("James", "Smith", "USA", 34),
        ("Anna", "Rose", "", 41),
        ("Robert", "Williams", "USA", 62)]

columns = ["firstname", "lastname", "country", "age"]
df = spark.createDataFrame(data, columns)

# Show the DataFrame
df.show()

# Perform transformation: filter and add a new column
df_transformed = df.filter(col("country") == "USA") \
                   .withColumn("age_plus_ten", col("age") + 10)

# Show transformed DataFrame
df_transformed.show()

# Register the DataFrame as a SQL temporary view
df.createOrReplaceTempView("people")

# Perform a SQL query
result = spark.sql("SELECT firstname, age FROM people WHERE age > 35")

# Show the result of the SQL query
result.show()

# Stop the Spark session
spark.stop()
