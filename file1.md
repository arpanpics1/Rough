### Epic: Integration of Data Catalog Management System (DCM) with Data Quality System (DQ4QD)

#### **Epic Title**: Seamless Metadata Integration Between DCM and DQ4QD Systems

#### **Epic Description**:  
This epic aims to integrate the Data Catalog Management (DCM) system, which harvests metadata from various systems, with the Data Quality system (DQ4QD) to streamline the process of capturing table and column metadata for quality assessments. The integration will allow the DQ4QD system to directly utilize the harvested metadata from DCM, eliminating the need for manual entry and enhancing the efficiency of the data quality processes. Two approaches are proposed: a pull-based metadata sync and a full system merger.

#### **Objectives**:
- Automate the flow of metadata between DCM and DQ4QD.
- Ensure seamless synchronization of table and column information for quality checks.
- Minimize the need for manual metadata entry by leveraging harvested data.
- Preserve data consistency and integrity, particularly when generating or updating metadata IDs.
- Enhance the user experience by making metadata readily available when adding new tables to the DQ4QD system.

#### **Approach 1: Pull Metadata from DCM on Demand (Pull-Based)**

1. **Story 1**: Metadata Sync Feature for DQ4QD
   - As a user, I want to pull the metadata of tables and columns from the DCM system directly into DQ4QD when I add a new table so that I can avoid manual entry.
   - **Acceptance Criteria**:
     - Metadata sync should be triggered upon adding a new table in DQ4QD.
     - Unique IDs should be generated for tables and columns in DQ4QD, separate from the DCM system.
     - Users should be notified of successful metadata import.

2. **Story 2**: Background Sync Process for Metadata Changes
   - As a user, I want the metadata in DQ4QD to be automatically updated when changes are made to the harvested metadata in DCM.
   - **Acceptance Criteria**:
     - Automatic updates should reflect changes made in DCM for tables and columns.
     - Conflict resolution rules should be defined when changes in metadata require user input.

#### **Approach 2: Full System Integration (Merging)**

3. **Story 3**: Metadata ID Unification
   - As a user, I want DQ4QD and DCM to share the same IDs for tables and columns so that metadata is consistent across both systems.
   - **Acceptance Criteria**:
     - Existing metadata IDs in both systems should be mapped and unified.
     - A migration script should update historical records in DQ4QD to reflect DCM IDs.
     - New tables and columns should have synchronized IDs across both systems.

4. **Story 4**: Historical Data Migration
   - As a developer, I need to migrate the historical metadata stored in DQ4QD to align with the DCM system so that all metadata IDs are consistent across both platforms.
   - **Acceptance Criteria**:
     - Historical metadata should be accurately migrated without data loss.
     - All references to old IDs should be updated across the entire system, including reports and dashboards.
     - Backward compatibility should be maintained for any system integrations dependent on the old ID format.

#### **Non-Functional Requirements**:
- Ensure that the integration does not introduce performance bottlenecks during metadata syncs.
- Maintain backward compatibility for systems relying on the current metadata structure in DQ4QD.
- Provide audit logs for metadata updates and sync operations.

#### **Dependencies**:
- Access to DCM’s API for metadata extraction.
- Collaboration between the teams managing DCM and DQ4QD to define a consistent ID scheme.
  
#### **Risks**:
- Changing metadata IDs in both systems could lead to inconsistencies if not carefully planned.
- Performance impacts during large metadata sync operations.

This epic will lay the foundation for an efficient metadata integration between the DCM and DQ4QD systems, providing flexibility for users to utilize harvested metadata directly or merge both systems for a unified experience.
