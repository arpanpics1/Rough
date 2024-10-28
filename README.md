from pyspark.sql import SparkSession
from pyspark.sql.utils import AnalysisException

def create_spark_session():
    """Create a Spark session."""
    try:
        spark = SparkSession.builder \
            .appName("SQL Server Connection") \
            .config("spark.driver.extraClassPath", "path/to/sqljdbc4.jar") \
            .getOrCreate()
        print("Spark session created successfully.")
        return spark
    except Exception as e:
        print(f"Error creating Spark session: {e}")
        return None

def connect_to_sql_server(spark, jdbc_url, properties):
    """Connect to SQL Server and read data from a table."""
    try:
        df = spark.read.jdbc(url=jdbc_url, table="your_table_name", properties=properties)
        print("Data read successfully.")
        return df
    except AnalysisException as ae:
        print(f"Analysis error: {ae}")
    except Exception as e:
        print(f"Error connecting to SQL Server: {e}")
        return None

def main():
    # JDBC URL for SQL Server
    jdbc_url = "jdbc:sqlserver://<server_name>:<port>;databaseName=<database_name>"
    
    # Properties for the connection
    properties = {
        "user": "<username>",
        "password": "<password>",
        "driver": "com.microsoft.sqlserver.jdbc.SQLServerDriver"
    }

    # Create Spark session
    spark = create_spark_session()
    
    if spark:
        # Connect to SQL Server
        df = connect_to_sql_server(spark, jdbc_url, properties)
        
        if df is not None:
            # Show the DataFrame (for demonstration purposes)
            df.show()

if __name__ == "__main__":
    main()
