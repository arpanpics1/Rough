Epic: Vault process integration and implementation for DQ4QD platform 

Background
DQ4QD platform currently manages various system credentials that are essential for its operations. To enhance security and ensure compliance with best practices, there is a need to implement credential vaulting for all system credentials, including BEM service IDs and Oracle system credentials for all environments. This epic involves making necessary code changes, informing the BEM team, and developing a strategic plan for vaulting credentials during the onboarding process.

Objective
The main objectives of this epic are to:
Vault BEM service IDs and notify the BEM team.
Vault Oracle system credentials for all environments.
Implement a strategic plan to vault any system credential during the onboarding process for new systems on the DQ4QD platform.

User Stories
User Story 1: Vault BEM Service ID
As a BEM AIF Owner, I want to vault the BEM service ID, so that the credential is securely stored and managed.

Acceptance Criteria:
The BEM service ID is securely vaulted.
Notifications are sent to the BEM team informing them of the vaulting process and any changes required on their end.
The DQ4QD platform is updated to use the vaulted BEM service ID.

User Story 2: Vault Oracle System Credentials
As a DQ4QD platform owner, I want to vault Oracle system credentials for all environments (Dev, UAT, Prod), so that they are securely stored and managed.

Acceptance Criteria:
Oracle system credentials for all environments are securely vaulted.
The DQ4QD platform is updated to use the vaulted Oracle system credentials.
The change is documented and communicated.

User Story 3: Strategic Plan for Vaulting New System Credentials
As a System user, I want a strategic plan for vaulting any new system credential during the onboarding process, so that credentials are securely stored from the beginning.

Acceptance Criteria:
Develop a strategic plan and process for vaulting new system credentials during onboarding.
The onboarding process is updated to include steps for credential vaulting.
Documentation is updated to reflect the new process.
