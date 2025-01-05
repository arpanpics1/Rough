Objective:
Enhance the existing Kafka consumer framework to securely manage consumer properties without storing credential information in the EEH database. Additionally, provide APIs to regulate the starting and stopping of consumers dynamically.

Acceptance Criteria 
1. Consumer Registration :  Register all Kafka consumers created via EEH Consumer framework with all required property details without storing credentials in the EEH database 
Ensure only non-sensitive property details (e.g., topic, group ID, configuration parameters) are stored in the EEH database.
2. Update and Refresh Consumer Properties : Update consumer properties and have the changes dynamically refreshed without downtime so that my consumer settings remain up-to-date.
Provide a mechanism to validate and save updated properties.
3. API for Consumer Control (Start/Stop): Create APIs to start and stop specific consumers dynamically so that EEH Admin can regulate all EEH Consumers.
Create endpoints for starting, stopping of consumers:
/consumer/start
/consumer/stop
4. API for Consumer Registration
As a developer, I want an API to register new consumers programmatically so that onboarding new consumers is streamlined.
Create an endpoint like /consumer/register to accept consumer details.
Validate the input properties and store non-sensitive information in the EEH database.





------------------------------------
------------------------------------

Objective:

Enhance the existing EEH Kafka consumer framework to improve functionality, scalability, and compatibility with modern systems while aligning with organizational requirements.

Acceptance Criteria 

1. Upgrade the Tier 1 Kafka clusters to the latest supported version and ensure seamless migration for all Tier 1 consumers to RHEL 9.
Perform a comprehensive assessment of current Tier 1 cluster configurations and compatibility with RHEL 9. Validate the framework’s functionality post-migration, ensuring no data loss or downtime.

2. Object Storage and Iceberg Table Format Support: Enhance the framework to support object storage solutions and enable integration with the Apache Iceberg table format for better schema evolution and performance.
Design and implement support for writing data to object storage systems (e.g., S3, Azure Blob Storage).
Integrate Iceberg format compatibility for Hive tables to support schema evolution and partition pruning.
Test data ingestion and query performance for object storage and Iceberg.
Develop and document a migration plan for existing consumers to adopt Iceberg format and object storage.


3. Promotion of Sample Consumer and Producer Applications to Production for future testing Tier 0 cluster issue


4. Integration with DQ4QD System and Complex Rule Support:Extend the framework to integrate with the DQ4QD system and support complex data quality rules for enhanced governance and monitoring.




------------------------------------
------------------------------------

Need to create EPIC on the below =, can you help me in expanding the details

Objective:
Develop a user-friendly, efficient, and secure dashboard that tracks vaulted IDs, secrets, and password rotation schedules. The system will notify users about upcoming and missed renewal deadlines to ensure compliance and security.

Acceptance Criteria:
1. Dashboard Overview : I want a comprehensive dashboard that displays all vaulted IDs, their associated secrets, and the status of their password rotations so that I can easily monitor and manage them.
Display vaulted IDs grouped by categories (e.g., application, system, or environment).
Provide a summary view showing total IDs, secrets, upcoming renewals, and overdue items.
2. Renewal Tracking: I want the dashboard to display the renewal dates for secrets and passwords so that I can plan timely actions.
Include columns like Vaulted ID, Secret Name, Last Rotation Date, Next Renewal Date, and Status (e.g., Pending, Completed, Overdue).
Color-coded indicators for urgency (e.g., green for on-track, yellow for upcoming, red for overdue).
3. Notification System :  I want to receive automated notifications when a renewal is due or overdue so that I never miss a critical update.
Notify users via email, in-app notifications.
Allow customizable notification thresholds (e.g., 7 days, 3 days, 1 day before the deadline).
Include escalation alerts for overdue renewals.
4. Renewal Process Integration : I want the dashboard to provide details of autosys jobs for renew passwords or secrets so that user can take immediate action.
5. Audit Logs : I want to see an audit trail of renewal actions taken, including timestamps and user details, so that I can ensure compliance.
Track and display all renewal activities and notifications sent.
Allow filtering and exporting logs for compliance audits.
6. Role-Based Access : I want to control who can view, edit, or manage the dashboard and renewal processes so that sensitive data is protected.

------------------------------------
------------------------------------
Need to create EPIC on the below , can you help me in expanding the details


Exploration on converting a hourly batch job to streaming alerting job

There are some existing hourly batch job those are use in fraud alerting, these jobs are having logic of aggregation and standard deviation, considering this and after further analysis these jobs need to be converted into Streaming jobs considering time windowing setup and job failure scenarios.



Objective:

Transform existing hourly batch fraud alerting jobs into real-time streaming alerting jobs to enhance timeliness and efficiency, leveraging aggregation and standard deviation logic with proper time windowing and robust failure handling mechanisms.

Acceptance Criteria:

1. Analysis of Existing Batch Jobs: Perform a comprehensive analysis of the current hourly batch jobs to understand their logic, dependencies, and data flow.
Review the code and configurations of existing batch jobs.
Document the aggregation and standard deviation logic currently implemented.
Identify data sources, sinks, and interdependencies with other systems.
Analyze job execution timelines, failure scenarios, and bottlenecks.

2. Design of Streaming Jobs: Create a blueprint for converting batch jobs into streaming jobs with time windowing and real-time alerting capabilities.
Design a streaming pipeline that incorporates aggregation and standard deviation logic.
Define appropriate time windows (sliding, tumbling, or session-based) for fraud detection.
Plan integration points with data sources and sinks (e.g., Kafka, databases, or object storage).
Develop strategies for managing late-arriving data and ensuring data consistency.

3. Implementation of Streaming Jobs: Develop and implement the streaming alerting jobs based on the proposed design.
Set up the streaming framework using Spark Streaming.
Implement aggregation and standard deviation calculations in the streaming pipeline.
Configure time windowing to align with fraud detection requirements.
Build fault-tolerance mechanisms to handle job failures and ensure reliability.
Develop and integrate alerting mechanisms (e.g., email, SMS, or dashboards).

4. Testing and Validation : Ensure the reliability and accuracy of the streaming jobs through comprehensive testing.
Conduct unit and integration testing for each component of the streaming pipeline.
Simulate real-world scenarios, including data delays, failures, and high-load conditions.
Validate the accuracy of fraud detection logic against historical batch job results.
Perform end-to-end testing with stakeholders to confirm functionality and performance.

