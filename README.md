from pyspark.sql import SparkSession

# Initialize Spark Session
spark = SparkSession.builder \
    .appName("PySpark SQL Server Example") \
    .config("spark.jars", "path_to_jdbc_driver/mssql-jdbc_auth-x.x.x.x64.dll") \
    .getOrCreate()

# Connection URL
url = "jdbc:sqlserver://YOUR_SERVER;databaseName=YOUR_DATABASE;integratedSecurity=true;"

# JDBC connection properties
connectionProperties = {
    "driver": "com.microsoft.sqlserver.jdbc.SQLServerDriver"
}

# Reading data from SQL Server into DataFrame
df = spark.read.jdbc(url=url, table="YourTable", properties=connectionProperties)

# Show DataFrame
df.show()

# Stop the Spark session
spark.stop()

