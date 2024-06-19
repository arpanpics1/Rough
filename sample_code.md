Epic: Continuation on Exploration of Fetching Metadata from RDBMS Systems

Background
The ongoing exploration of fetching metadata from various RDBMS systems is crucial for enhancing the Data Catalog Management (DCM) system. This epic focuses on systematically capturing credentials, supporting the extraction of technical metadata from MS SQL Server, Oracle, and Teradata, incorporating error handling mechanisms, developing test automation, and preparing comprehensive documentation and training materials.

Objective
The primary objectives of this epic are to:
Implement a system for capturing credentials for any new RDBMS system.
Support the extraction of technical metadata from MS SQL Server, Oracle, and Teradata.
Incorporate robust error handling mechanisms.
Develop test automation to ensure the system's correctness and reliability.
Prepare detailed documentation and training materials for users and administrators.

User Tasks
User Task 1: Systematic Capturing of Credentials
I want to systematically capture credentials for any new RDBMS system from the UI, so that the system can securely and efficiently access and fetch metadata.

Acceptance Criteria:
A UI component is available for capturing and storing RDBMS credentials. For the time being, credentials can also be manually added to the DB table, untill UI Screen is developed.
Credentials are securely stored and managed.

User Task 2: Support Metadata Extraction
I want to support the extraction of technical metadata from MS SQL Server, Oracle, and Teradata, so that the DCM data model is enriched with comprehensive metadata from these systems.

Acceptance Criteria:
Technical metadata extraction is supported for MS SQL Server, Oracle, and Teradata.
Extracted metadata is accurately integrated into the DCM data model.
The system can handle metadata extraction for large datasets.

User Task 3: Incorporate Error Handling Mechanisms
As a Developer, I want to incorporate robust error handling mechanisms, so that the system can gracefully handle and report errors during metadata extraction.

Acceptance Criteria:
Error handling mechanisms are implemented for all supported RDBMS systems.
Errors are logged and reported in a user-friendly manner.
The system can recover from errors without significant downtime.

User Task 4: Develop Test Automation
I want to develop test automation to verify the correctness and reliability of the system, so that the system's functionality is thoroughly tested and validated.

Acceptance Criteria:
Automated test scripts are developed for all major functionalities.
The automation suite covers positive, negative, and edge cases.
Test results are documented, and issues are resolved promptly.

User Task 5: Prepare Documentation and Training Material
I want to prepare detailed documentation and training materials, so that users and administrators can understand and effectively use the system.

Acceptance Criteria:
Comprehensive documentation is created for all system features and processes.
Training materials are prepared to assist users and administrators.
Documentation and training materials are reviewed and approved by relevant stakeholders.
