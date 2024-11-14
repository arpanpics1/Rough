from pyspark.sql import DataFrame
from pyspark.sql.functions import col, mean, stddev, expr

def detect_anomalies_on_stream(
    stream_df: DataFrame,
    anomaly_rules: dict,
    threshold_std_dev: float = 3.0,
    schema_validation: bool = True,
    log_anomalies: bool = True
) -> DataFrame:
    """
    Detects anomalies in a streaming DataFrame based on rule-based and statistical analysis.

    Parameters:
    - stream_df: The streaming DataFrame to analyze.
    - anomaly_rules: Dictionary containing SQL-based rules for anomaly detection.
    - threshold_std_dev: Number of standard deviations for statistical anomaly detection.
    - schema_validation: Whether to validate schema of each incoming record.
    - log_anomalies: If True, logs detected anomalies.

    Returns:
    - DataFrame with anomalies flagged or filtered.
    """
    
    # Apply rule-based anomaly detection
    rule_based_anomalies = stream_df
    for rule_name, rule_query in anomaly_rules.items():
        rule_based_anomalies = rule_based_anomalies.filter(expr(rule_query))
    
    # Statistical anomaly detection using mean and std dev
    stats = stream_df.agg(mean("value").alias("mean_val"), stddev("value").alias("std_dev"))
    mean_val, std_dev = stats.collect()[0]["mean_val"], stats.collect()[0]["std_dev"]
    statistical_anomalies = stream_df.filter(
        (col("value") > mean_val + threshold_std_dev * std_dev) |
        (col("value") < mean_val - threshold_std_dev * std_dev)
    )
    
    # Optional: Schema validation on incoming records
    if schema_validation:
        # Add schema validation logic here
        
    # Logging detected anomalies if enabled
    if log_anomalies:
        # Log anomalies with timestamp and rule information
    
    # Combine rule-based and statistical anomalies for output
    anomalies_df = rule_based_anomalies.union(statistical_anomalies)
    
    return anomalies_df
