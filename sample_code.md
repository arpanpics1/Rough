Epic: Enhancing DQ4QD Platform for Object Storage Systems and file system support

Background
The Data Quality for Quality Data (DQ4QD) platform currently calculates data quality metrics from various systems. To expand its capabilities, the platform needs to be enhanced to add connectors for object storage systems like HCP and to perform data quality rules on objects stored there. Additionally, the platform should be able to handle data present in Hadoop HDFS file locations and files available at Hadoop system edge nodes.

Objective
The main objectives of this epic are to:
Integrate the DQ4QD platform with object storage systems (e.g., HCP) and Hadoop systems.
Enable data quality rules to be performed on data stored in these systems.
Enhance the onboarding process to include detailed configurations for file paths, credentials, and environments.

User Task
User Task 1: Object Storage System Integration
As a Data Quality Engineer, I want to add a connector for object storage systems like HCP to the DQ4QD platform, so that I can perform data quality checks on objects stored in these systems.

Acceptance Criteria:
A connector for HCP is implemented in the DQ4QD platform.
Data quality rules can be applied to objects stored in HCP.
The platform supports authentication and authorization mechanisms for accessing HCP.

User Task 2: Hadoop Integration
As a Data Quality Engineer, I want to add connectors for Hadoop HDFS and Hadoop edge nodes to the DQ4QD platform, so that I can perform data quality checks on data stored in these systems.

Acceptance Criteria:
Connectors for Hadoop HDFS and Hadoop edge nodes are implemented in the DQ4QD platform.
Data quality rules can be applied to files stored in HDFS and edge nodes.
The platform supports various file formats stored in Hadoop systems.

User Task 3: Enhanced Onboarding Process
As a System Administrator, I want an enhanced onboarding process for the DQ4QD platform, so that users can easily provide necessary details for configuring file paths, credentials, and environment-specific locations.

Acceptance Criteria:
The onboarding process includes fields for file path details (S3, HDFS, NAS/Edge node) and initial credentials for object storage.
Users can assign a name or alias to each file system or file path.
Users can specify the file format, delimiter, and schema.
Users can indicate whether the file location is static or dynamic (e.g., based on partitions).
Users can provide associated path locations for different environments (Dev, UAT, Prod).

User Task 4: New Data Quality Rules
As a Data Quality Analyst, I want to apply new types of data quality rules to the data, so that I can ensure comprehensive data quality checks.

Acceptance Criteria:
Implement a File Watcher rule that checks for file existence based on a pattern and specified intervals.
Implement a File Size rule to check if the file size is zero or matches a user-specified size.
Implement a rule to check the file schema against a predefined schema.
Implement a File Format Check rule to validate file formats such as CSV, JSON, Parquet, ORC, Avro, TXT, and Protobuf.
Ensure that existing rules (standard rules, table recon, lookup) are supported for the new data sources.
