Epic: Enhancing DQ4QD Platform to Generate and Report File Size Distribution and Purge Statistics

Background
The Data Quality for Quality Data (DQ4QD) platform generates various files during the processing of mismatch records and health checks. To improve monitoring and management, there is a need to generate reports that provide insights into the number and size distribution of these files. Additionally, there is a requirement to report on the health check and mismatch/bad records tables' purge statistics.

Objective
The primary objective of this epic is to enhance the DQ4QD platform by:
Implementing functionality to generate reports on the number of files produced, categorized by file size.
Providing reports on the number of records within these files.
Creating purge reports for health check and mismatch/bad records tables.

User Tasks

User Task 1: File Size Distribution Report
As a Data Quality Analyst, I want to generate a report that categorizes the number of files by their size, so that I can monitor the volume and distribution of files produced by the DQ4QD platform.

Acceptance Criteria:
A report is generated that categorizes files into the following size buckets:
0 Bytes
0 KB - 10 KB
10 KB - 1 MB
1 MB - 10 MB
10 MB - 50 MB
50 MB - 128 MB
Greater than 128 MB

The report includes the number of files in each size bucket. and over all total no of records generated
The report can be executed on a daily, weekly, or monthly basis as required.


User Task 2: Health Check and Mismatch/Bad Records Purge Report
As a DQ4QD owner, I want to generate reports on the purging of health check and mismatch/bad records tables, so that I can track the efficiency and effectiveness of data purging processes.

Acceptance Criteria:
A report is generated showing the details of purged records from health check and mismatch/bad records tables.
The report includes the number of records purged, the time period of the purge.
The report can be scheduled to run on a specified frequency.
