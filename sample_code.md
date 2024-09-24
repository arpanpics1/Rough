from pyspark.sql import SparkSession

# Create a SparkSession with Hive support
spark = SparkSession.builder \
    .appName("Create External Hive Table") \
    .enableHiveSupport() \
    .getOrCreate()

# Specify the path where the external table data will be stored
external_table_path = "hdfs:///user/hive/warehouse/my_external_table"

# SQL query to create an external Hive table
create_table_query = f"""
CREATE EXTERNAL TABLE IF NOT EXISTS my_external_table (
    id INT,
    name STRING,
    age INT
)
ROW FORMAT DELIMITED
FIELDS TERMINATED BY ','
STORED AS TEXTFILE
LOCATION '{external_table_path}'
"""

# Execute the SQL query to create the external table
spark.sql(create_table_query)

# Stop the SparkSession
spark.stop()

