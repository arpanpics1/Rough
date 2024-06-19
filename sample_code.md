Epic: Enhancing DQ4QD Platform to Display Job Status and Track Scheduler Activities
Background
The Data Quality for Quality Data (DQ4QD) platform currently executes data quality jobs (workflows or pipelines) using its internal scheduler and through Autosys jobs. However, the platform lacks an interface to display the status of these jobs. This makes it difficult to determine whether jobs are queued, started, running, finished, or have encountered errors (failed/aborted). Additionally, there is a need to track the execution of various scheduler activities (such as launcher, scheduler job, archival job, purge job, or onboarding jobs) for specific AIF (client).

Objective
The main objective of this epic is to enhance the DQ4QD platform by:

Implementing an interface to display the status of data quality jobs.
Tracking the execution of DQ4QD scheduler activities to ensure all tasks are triggered as expected.
User Stories

User Story 1: Display Job Status in DQ4QD Platform
As a Data Quality Analyst, I want to view the status of data quality jobs in the DQ4QD platform, so that I can monitor their progress and address any issues promptly.

Acceptance Criteria:
A user interface is created within the DQ4QD platform to display job statuses.
Job statuses include Queued, Started, Running, Finished, Error/Failed/Aborted.
The interface updates in real-time to reflect the current status of each job.
Users can filter and sort jobs based on their status, name, or execution time.

User Story 2: Track Scheduler Activities
As a System Administrator, I want to track whether the DQ4QD scheduler activities (launcher, scheduler job, archival job, purge job, onboarding jobs) were triggered for specific AIF (client), so that I can ensure all necessary tasks are executed correctly.

Acceptance Criteria:
A tracking system is implemented to log the execution of scheduler activities.
The system logs the start time, end time, and status (success/failure) of each scheduler activity.
Administrators can query the logs based on AIF (client) and job type.
Notifications are sent if any scheduler activity fails to trigger or encounters an error.

User Story 3: Integration with Autosys
As a Data Quality Engineer, I want the DQ4QD platform to integrate seamlessly with Autosys, so that job statuses and scheduler activities can be monitored and tracked uniformly.

Acceptance Criteria:
The DQ4QD platform fetches job statuses from Autosys. Whether jobs executed or there is a miss in job execution
The platform displays Autosys job statuses in the same interface as DQ4QD jobs.
