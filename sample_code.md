Epic: Enhancing Spark Streaming Jobs to Utilize Data Quality Rules from DQ4QD Platform
Background
The organization is currently running multiple Spark streaming jobs that process data from Kafka and write it to various sinks like Hive, RDBMS systems, and Elasticsearch. To ensure high data quality and consistency, there is a need to integrate these streaming jobs with the Data Quality for Quality Data (DQ4QD) platform. This integration will allow the Spark streaming jobs to apply predefined data quality rules during data processing and handle non-compliant records appropriately.

Objective
The primary objective of this epic is to enhance the existing Spark streaming jobs to:

Utilize data quality rules defined in the DQ4QD platform.
Sync non-compliant records to a designated Kafka topic, a separate Hive table, or Elasticsearch for further analysis and dashboard creation.
User Stories
User Story 1: Schema Onboarding and Rule Creation in DQ4QD
As a Data Engineer, I want to onboard schemas and create data quality rules in the DQ4QD platform, so that the streaming jobs can refer to these rules during execution.

Acceptance Criteria:

Schema definitions for all relevant data sources are onboarded into the DQ4QD platform.
Data quality rules are created and associated with the respective schemas in the DQ4QD platform.
The rules are tested and validated to ensure they cover all necessary data quality checks.
User Story 2: Enhancing Spark Streaming Jobs to Retrieve Data Quality Rules
As a Spark Developer, I want to modify the Spark streaming jobs to retrieve and apply data quality rules from the DQ4QD platform, so that the streaming data adheres to the defined quality standards.

Acceptance Criteria:

Spark streaming jobs are enhanced to connect to the DQ4QD platform and fetch the relevant data quality rules at runtime.
The streaming jobs apply these rules to the incoming data from Kafka.
Non-compliant records are identified and flagged for further processing.
User Story 3: Syncing Non-Compliant Records
As a Data Engineer, I want to configure the Spark streaming jobs to sync non-compliant records to a Kafka topic, a separate Hive table, or Elasticsearch, so that these records can be analyzed and monitored.

Acceptance Criteria:

Non-compliant records are routed to a designated Kafka topic for further processing.
Non-compliant records are saved to a separate Hive table for historical tracking and analysis.
Non-compliant records are indexed into Elasticsearch to create a dashboard for real-time monitoring.
User Story 4: Dashboard Creation for Non-Compliant Records
As a Data Analyst, I want to create a dashboard in Elasticsearch to monitor non-compliant records, so that I can gain insights into data quality issues and take corrective actions.

Acceptance Criteria:

A dashboard is created in Elasticsearch to visualize non-compliant records.
The dashboard provides filters and drill-down capabilities to analyze specific data quality issues.
Alerts are configured to notify stakeholders of significant data quality breaches.
