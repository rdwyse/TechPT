TechPT Data Management Documentation
2024.09.17

# Table of Contents

Here's an updated **Table of Contents** reflecting the sections of the **TechPT Data Management Documentation** you provided, including the detailed steps, actions, and processes documented for the project:

# Table of Contents

1. [Introduction to the Data Management Documentation](#introduction-to-the-data-management-documentation)
2. [Data Cleanup Process Documentation](#data-cleanup-process-documentation)
    - [Date: 2024.09.13](#date-20240913)
        - [Following Solution C Procedures](#following-solution-c-procedures)
        - [Backing Up the Original Data](#backing-up-the-original-data)
        - [Configuring Excel Worksheet](#configuring-excel-worksheet)
        - [Sorting and Filtering, and Removing Testing Data](#sorting-and-filtering-and-removing-testing-data)
    - [Date: 2024.09.15](#date-20240915)
        - [Transfer SelfMonitoring6 to ConfMonitoring6](#transfer-selfmonitoring6-to-confmonitoring6)
        - [Cleaning Confederate Guide End of Session Entries](#cleaning-confederate-guide-end-of-session-entries)
        - [Additional test data removal](#additional-test-data-removal)
    - [Date: 2024.09.16](#date-20240916)
        - [Set CaregiverID to Case Assignment](#set-caregiverid-to-case-assignment)
        - [Cleaning CaregiverID during simulated child session](#cleaning-caregiverid-during-simulated-child-session)
        - [Adjusting Records for Caregiver Entry Due to Guide Reset](#adjusting-records-for-caregiver-entry-due-to-guide-reset)
            - [EDIT 1](#edit-1)
            - [EDIT 2](#edit-2)
        - [Investigate Confederate note indicating caregiver guide issue](#investigate-confederate-note-indicating-caregiver-guide-issue)
        - [Adjusting Records for Confederate Compliance Based on Trial Notes](#adjusting-records-for-confederate-compliance-based-on-trial-notes)
        - [Adjusting Confederate Interaction Based on Trial Notes](#adjusting-confederate-interaction-based-on-trial-notes)
        - [Correcting CaregiverID for Confederate Guide Based on Research Notes](#correcting-caregiverid-for-confederate-guide-based-on-research-notes)
        - [Review of Confederate Guide Entry - No Action Required](#review-of-confederate-guide-entry---no-action-required)
        - [Correcting Study Phase and CaregiverID Based on Research and Session Notes](#correcting-study-phase-and-caregiverid-based-on-research-and-session-notes)
        - [Mastery Criteria Review Based on 8029hmvgjh Note](#mastery-criteria-review-based-on-8029hmvgjh-note)
        - [Missing TrialDirection Recordings During Training Sessions](#missing-trialdirection-recordings-during-training-sessions)
3. [Table Naming Convention](#table-naming-convention)
    - [Components Breakdown](#components-breakdown)
    - [Example Table Names](#example-table-names)
        1. [All Actual Child Trials for Case 1 (Caregiver as Respondent)](#all-actual-child-trials-for-case-1-caregiver-as-respondent)
        2. [Simulated Child Trials for Training Phase 2 (T2) for Case 1 (Confederate as Respondent)](#simulated-child-trials-for-training-phase-2-t2-for-case-1-confederate-as-respondent)
        3. [All Trials for Baseline Phase (BL) Across All Respondents](#all-trials-for-baseline-phase-bl-across-all-respondents)
        4. [All Actual Child Trials for All Cases in Training Phases](#all-actual-child-trials-for-all-cases-in-training-phases)
        5. [All Simulated Child Trials for Reversal to Baseline Phase (RTB) (IOA as Respondent)](#all-simulated-child-trials-for-reversal-to-baseline-phase-rtb-ioa-as-respondent)
    - [Broader Aggregated Examples](#broader-aggregated-examples)
        1. [All Actual Child Trials for All Cases Across All Phases](#all-actual-child-trials-for-all-cases-across-all-phases)
        2. [All Records for Case 1 Across All Phases and Respondents](#all-records-for-case-1-across-all-phases-and-respondents)
4. [Data Preparation](#data-preparation)
    - [Workflow Summary](#workflow-summary)
    - [Data Preparation in Excel for Confederate Monitoring Analysis](#data-preparation-in-excel-for-confederate-monitoring-analysis)
        - [Introduction](#introduction)
        - [Loading the Master Table](#loading-the-master-table)
        - [Using Power Query for Data Filtering and Transformation](#using-power-query-for-data-filtering-and-transformation)
        - [Processing Simulated Child (SC) Sessions](#processing-simulated-child-sc-sessions)
        - [Processing Actual Child (AC) Sessions](#processing-actual-child-ac-sessions)
        - [Combining SC and AC Data](#combining-sc-and-ac-data)
        - [Conclusion](#conclusion)
5. [Prism Design Considerations](#prism-design-considerations)
    - [Table Format: XY Data in GraphPad Prism](#table-format-xy-data-in-graphpad-prism)
        1. [Entering Multiple Sets of Data That Don’t Share X Values](#entering-multiple-sets-of-data-that-dont-share-x-values)
        2. [Example Table Structure for a Single Participant](#example-table-structure-for-a-single-participant)
6. [Documentation for Data Transfer and Plotting in GraphPad Prism](#documentation-for-data-transfer-and-plotting-in-graphpad-prism)
    1. [Steps for Manual Data Transfer and Plotting in GraphPad Prism](#steps-for-manual-data-transfer-and-plotting-in-graphpad-prism)
        - [Merging Data Tables](#merging-data-tables)
        - [Creating Data Tables for Additional Series](#creating-data-tables-for-additional-series)
        - [Verifying Data Alignment](#verifying-data-alignment)
7. [Steps for Python Script to Automate Data Transfer to Prism](#steps-for-python-script-to-automate-data-transfer-to-prism)
    - [Introduction](#introduction)
    - [Processing Session Data](#processing-session-data)
    - [Main Loop: Generating Columns for Each Session](#main-loop-generating-columns-for-each-session)
    - [Output Formatting](#output-formatting)


# Introduction to the Data Management Documentation

The data management documentation for the "TechPT" project serves as a comprehensive guide detailing the organization, extraction, processing, and validation of all data collected during the study. This study examines the functional relationship between caregiver participation in a technology-assisted training program and the effectiveness of direction delivery to children. To ensure the accuracy and integrity of the collected data, meticulous records have been maintained throughout each phase of the research, from initial data capture to final analysis. 

This documentation outlines the methods used for data handling, focusing on the following key areas:
1. Data Extraction and Filtering: Specific techniques and procedures used to extract relevant data subsets from the master table, based on unique identifiers such as caregiver IDs, session types, or phases of the study. This ensures that only the necessary data is extracted for analysis while maintaining the integrity of the original dataset.
2. Table Structures and Comparison Methods: An explanation of how the raw data is organized into structured tables for different analyses, including comparisons between self-monitoring and confederate monitoring, session duration calculations, and compliance rates.
3. Formula and Script Documentation: A detailed breakdown of the formulas and scripts (both in Excel and Python) used to process the data, calculate session durations, and generate compliance scores.
4. Validation and Integrity Checks: Steps taken to verify the completeness and accuracy of the data, ensuring any anomalies are identified and corrected.
5. Preparation for GraphPad Prism: Final preparation of the datasets for statistical analysis and visualization, including specific formatting techniques required for smooth import into GraphPad Prism.

This documentation ensures that the data processes are transparent, replicable, and accurate, supporting the study's findings and contributing to the scientific rigor of the project.

# Data Cleanup Process Documentation

## Date: 2024.09.13

### Following Solution C Procedures
- Action: Followed Solution C procedures for manual extraction of the JSON data and converting it to a structured format.
  - See Solution C documentation for details within the qualtics guide (https://github.com/rdwyse/TechPT/blob/main/2023-247%20TechPT%20-%20Qualtrics%20Documentation.md#solution-c-data-extraction-procedure).

### Backing Up the Original Data
- Action: Saved a copy of the original raw data table as a separate document (`TechPT - 2024.09.13 - RAW Qualtrics Data transformed to CSV - Original Unedited.CSV`).
  
- Reason: To preserve the original data in its unaltered form for reference or reprocessing if necessary.

### Configuring Excel Worksheet
- Action: Duplicated the `TechPT - 2024.09.13 - RAW Qualtrics Data transformed to CSV - Original Unedited.CSV` into a new Excel worksheet.
  - New Worksheet Name: `TechPT - Master Table`.
  
- Reason: The `Master Table` will serve as the primary working copy for all data cleaning operations. The original cleaned data is preserved for comparison.

### Sorting and Filtering, and Removing Testing Data
- Action: 
  - Sorted the `CGID` (Caregiver ID) column in ascending order to easily identify test records.
  - Deleted the rows containing recorded activity from testing, identified by testing CGID.
    - Rows Removed: 791 - 871.
  
- Reason: 
  - These rows were identified as test data and should not be included in the final analysis.



## Date: 2024.09.15

### Transfer SelfMonitoring6 to ConfMonitoring6
- Action: 
  - Custom sorted by **Respondent** to isolate `0_CONF` entries, then sorted by **Date** to isolate the beginning of data collection where the error occurred.
  - **Range T407:T612** (SelfMonitoring6) was cut and pasted into **Range AD407:AD612** (ConfMonitoring6).
  - Subsequent rows already had the confederate response correctly documented in **ConfMonitoring6**.

- Reason: 
  - The confederate's monitoring data was mistakenly recorded under **SelfMonitoring6** instead of **ConfMonitoring6** due to a programming error.
  - No data duplication or overwriting occurred because the confederate guide only used the SelfMonitoring indices to maintain the `AggregateData` structure.
  - The error was identified during sessions on **2024-08-08** and resolved before the next day’s sessions by updating the header script (see **EventRecorder** function documentation).

- Observation on Redundancy:
  - **ConfResponse** and **ConfMonitoring6** fields are redundant:
    - **ConfResponse** is coded as `0 = Comply`, `1 = NoComply`.
    - **ConfMonitoring6** is coded as `0 = NoComply`, `1 = Comply`.

---

### Cleaning Confederate Guide End of Session Entries

- Action:
  - Sorted the **EventNote** column in ascending order to identify instances of `4.0_End_of_Session`.
  - Located **Rows 744 - 789** where `4.0_End_of_Session` was present.
  - Deleted the cell contents for **Range X744:X789** (ConfResponse) and **Range AD744:AD789** (ConfMonitoring6).

- Reason:
  - Due to a design flaw in the confederate guide, **ConfResponse** and **ConfMonitoring6** values were not cleared when a session was ended prematurely (i.e., before a trial was executed).
  - The confederate response values were pre-loaded before trials but weren’t properly nulled upon early session termination. This led to incorrect data being carried over.

- Outcome:
  - By deleting the pre-loaded data in **ConfResponse** and **ConfMonitoring6**, the dataset now accurately reflects the absence of trials during sessions that were ended before execution.


### Additional test data removal

- Action: 
  - Sorted the **EventNote** column in ascending order to identify instances of `4.0_End_of_Session`.
  - Deleted the row containing recorded activity from testing, .
    - Row Removed: 790.

- Reason:
  - identified by IOAVideo Name `Test498_1_BL_1.MOV`

  -Action:
  - Sorted the **Respondent** column in ascending order, then DateTimeStamp in ascending order.
  - Deleted the row containing recorded activity from testing, .
    - **Row Removed:** 789.

- Reason:
  - identified by IOAVideo Name `Test498_1_BL_1.MOV`

  ## Date: 2024.09.16

  ### Set CaregiverID to Case Assignment

- Action:
  - Utilized Excel Find and replace function to replace all `CGID` values with the corresponding `CaseAssignment` values.

- Reason:
  - The `CGID` values were used for randomization and identification during the study, but are now removed to mitigate risk of CaregiverID being linked back to private health information.

  ### Cleaning CaregiverID during simulated child session

- Action:
  - Sorted the **DateTimeStamp** column in ascending order.
  - Replaced CaregiverID for both caregiver and confederate entries during identified session
    - **CaregiverID** was misrecorded as `Case2` and replaced with `Case3`.
    - Replaced 28 entries E591:E618 with `Case3`.
    - Updated Session Note with `**Addressed 2024.09.16**` to indicate the correction.

- Reason:
  - instanceiD `rfolltfbkr` note indicating "wrong caregiverid during simulated child"
  - Verified timestamps and sessions completed during the day to ensure correct replacement.

### Adjusting Records for Caregiver Entry Due to Guide Reset

**EDIT 1:**

- Action:
  - Custom sorted **Respondent** in ascending order, then sorted the **DateTimeStamp** column in ascending order.
  - Deleted the row containing instanceID `z82e5xapom`, which represented the survey start for the caregiver.
  - Updated the `TotalSessionTrials` and `SessionBlockCount` for the session following the guide reset:
    - Added 1 to `TotalSessionTrials` and 0.5 to `SessionBlockCount` for **Range J288:K294** (7 entries).
    - Updated the caregiver end-of-session instanceID `vbbxofr3i5` to match the standard format by replicating the previous trial count values.
  - Updated the confederate trial note with **Addressed 2024.09.16** to indicate the correction.

- Reason:
  - InstanceID `9tqvddipvs`: The confederate trial note indicated, "Participant accidentally advanced the trial without self-monitoring?" This was the first note recorded after the caregiver guide reset.
  - InstanceID `vmfqt8wmtu`: The previous entry was a caregiver trial, which occurred directly before the first opportunity to make a note.
  - InstanceID `z82e5xapom`: This was a `0_SurveyStart` for the caregiver.
  - The guide reset also reset the `TotalSessionTrials` and `SessionBlockCount`.
  - Only one trial had occurred prior to the reset, so 1 was added to `TotalSessionTrials` and 0.5 to `SessionBlockCount` following the guide reset.

**EDIT 2:**

- Action:
  - Custom sorted **Respondent** in ascending order, then sorted the **DateTimeStamp** column in ascending order.
  - Deleted the row containing instanceID `gog0nhhfcf`, which represented the survey start for the caregiver.
  - Updated the `TotalSessionTrials` and `SessionBlockCount` for the session following the guide reset:
    - Added 4 to `TotalSessionTrials` and 2 to `SessionBlockCount` for **Range J170:K183** (14 entries).
    - Updated the caregiver end-of-session instanceID `vbbxofr3i5` to match the standard format by replicating the previous trial count values.
  - Updated the confederate trial note with **Addressed 2024.09.16** to indicate the correction.

- Reason:
  - InstanceID `2ihhrtz5xp`: The confederate trial note indicated, "Had to restart caregiver guide." This was the first note recorded after the caregiver guide was reset.
  - InstanceID `o37jreo054`: The previous entry was a caregiver trial, which occurred directly before the first opportunity to make a note.
  - InstanceID `gog0nhhfcf`: This was a `0_SurveyStart` for the caregiver.
  - The guide reset also reset the `TotalSessionTrials` and `SessionBlockCount` for the caregiver
  - Four trials had occurred prior to the reset, so 4 was added to `TotalSessionTrials` and 2 to `SessionBlockCount` following the guide reset.
    -Upon review of the timestamps, it was identified that the caregiver guide did not record `totalsessionTrial` 4. 

- Observation:
  - There is now a missing piece of caregivermonitoring data for this trial.


### Investigate Confederate note indicating caregiver guide issue

- Action:
  - updated confederate trial note with **Addressed 2024.09.16** to indicate the investigation.

- Observation:
  - Confederate guide note InstanceID `0kaipj5v5x` indicated, "Caregiver guide was interupted and reset"
  - No erranious was found within the data set. 
  

### Adjusting Records for Confederate Compliance Based on Trial Notes

- Action:
  - Sorted by **ConfTrialNote** in ascending order to identify instances where trial notes indicated an error in confederate compliance.
  - Updated **ConfMonitoring6** to reflect the correct compliance status as indicated in the trial notes for the following instanceIDs:
    - `g1p4exdh69`
    - `ylwmempocs`
    - `fezz3o4qcl`
    - `sv1ln9v67n`
  - Updated the confederate trial note with **Addressed 2024.09.16** to indicate the correction.

- Reason:
  - The trial notes for these instances indicated errors in confederate compliance that were not accurately reflected in **ConfMonitoring6**.
  - Adjustments were made to ensure that **ConfMonitoring6** accurately represents the confederate's behavior as described in the notes.

### Adjusting Confederate Interaction Based on Trial Notes

- Action:
  - Identified instanceID `v6pz5ir50l`, where the trial note stated, "No interaction last trial."
  - Located the previous confederate trial response, instanceID `sr093zo0zh`.
  - Updated **ConfederateInteraction** for `sr093zo0zh` from `1` to `0` to accurately reflect the lack of interaction in the last trial as noted.
  - Updated the confederate trial note with **Addressed 2024.09.16** to indicate the correction.

- Reason:
  - The trial note indicated that no interaction occurred during the previous confederate trial, but **ConfederateInteraction** was marked as `1`.
  - This adjustment ensures that **ConfederateInteraction** accurately represents the trial behavior based on the note.

### Correcting CaregiverID for Confederate Guide Based on Research Notes

- Action:
    - Reviewed external research notes on an alternative platform for **Case2**, which indicated, "I used the wrong CaregiverID during the first few," with a session of the same date.
  - Sorted the data in ascending order by **Date** and identified the corresponding timestamps for the session mentioned in the research note.
    - **Start of session:** instanceID `yd6f1txm6f` (Row 59).
    - **End of session:** instanceID `heh1nahvk3` (Row 137).
  - The discrepancy began with the first trial of the confederate guide and persisted until the second actual child trial (requiring opening and closing the confederate guide).
    - Identified the confederate guide resolution of discrepancy at **Row 95** (instanceID `budjp46u8w`).
  - Updated the **CaregiverID** in **Cells E60:E94** (18 entries) to reflect **Case2**.

- Reason:
  - Based on the research notes, the wrong **CaregiverID** was used during the first few trials, requiring updates to the confederate guide entries.
  - Verification of the timestamps and session notes confirmed the correct entries for the **CaregiverID** correction.

- Observation:
  - No further complications are expected as a result of this correction.

### Review of Confederate Guide Entry - No Action Required

- Action:
  - Marked the trial note with **Addressed 2024.09.16** to indicate that the review was completed.

- Review:
  - Identified instanceID `vws0jd4py3`, where the trial note stated, "Sent wrong guide."
  - Only two confederate guide records prior to note within session, both marked as `0_Survey_start` approximately 12 minutes apart.
  - No other anomalies were identified during the session, and no relevant entries were found in research notes notes.

- Reason:
  - Although the trial note mentioned sending the wrong guide, no discrepancies or issues were found in the logs or research notes. As a result, no changes were made.

### Correcting Study Phase and CaregiverID Based on Research and Session Notes

- Action:
  - Identified instanceID `ihaltfgu1j`, where the session note stated: "Had the phase set to baseline in my guide, should be T2, check caregiver too. I assumed Mastery."
  - Reviewed research notes, which indicated: "Used the wrong CGID for XXX [Case 3] at 9 AM, used XXX [Case2]."
  - Identified session start at instanceID `aayf1gemmr` and session stop at instanceID `hfvedav993`.
  - Updated **StudyPhase** from `0_BL` to `2_t2` for **Cells G430:G464** (17 entries).
  - Updated **CaregiverID** from `Case2` to `Case3` for **Cells E430:E465** (36 entries).
  - Marked the trial note with **Addressed 2024.09.16** to indicate the review was completed.

- Reason:
  - The session was incorrectly recorded with **StudyPhase** set to baseline (`0_BL`) when it should have been set to `2_t2`.
  - Additionally, the wrong **CaregiverID** was used for the session, necessitating the update to **Case3**.

- Observation:
  - This correction will need to be noted in the methods section and graphically represented.
  - Mastery criteria were actually met a few trial blocks before the session was concluded.
  - The directions delivered by the caregiver would have been different if the correct phase was set. Although, there is overlap in the directions delivered by both caregivers.

### Mastery Criteria Review Based on 8029hmvgjh Note
- Action:  
  - Updated the trial note for instanceID `8029hmvgjh` with **Addressed 2024.09.16** to indicate that the note had been reviewed and documented

- Reason:  
  - Reviewed the confederate guide note for instanceID `8029hmvgjh`, which stated: "Not sure if Mastery criteria included all items or just this phase." 
  - The confederate note raised concerns about whether the correct mastery items were being used for the session's phase. Upon review of mastery criteria within , the criteria had been incorrectly tailored for each phase.
   - Checked the mastery criteria applied during this session and identified to ensure that only the relevant items for the current phase (T1, T2, or T3) were being evaluated.
  - Verified that the mastery criteria for each phase had been correctly updated based on previous changes (see **Mastery Criteria Update** section of Qualtrics documentation). 
  
- Outcome:  
  - Confederate Guide logic was updated upon the identification of this error.
  - This will require discussion within the manuscript and graphical representation.
  - Marked the note as resolved in the session data, and no additional discrepancies were found.

### Missing TrialDirection Recordings During Training Sessions

- Observation:  
  - The `TrialDirection` field in the caregiver guide was only recorded during Baseline and Actual Child sessions. No `TrialDirection` data was recorded during training sessions.

- Suspected Cause:  
  - It is likely that a variable for recording `TrialDirection` was missed within the qualtrics question specific javascript api window within caregiver training.

- Erroneous Recordings:  
  - In some cases, `TrialDirection` was erroneously recorded during caregiver `4.0_End_of_Session` events, these do not reflect actual training session data as it is a pre-cached entry for the following trial.
  
- Validation of Caregiver Guide Function:  
  - Despite the absence of `TrialDirection` recordings during training sessions, caregiver-delivered directions were observed and functioned correctly, indicating that the `CaregiverDirection` pool and function were working properly throughout the study.

- Action:  
  - Documented this oversight for future reference without attempting to correct javascript for future studies.


# Data Preparation

## Workflow Summary 

This workflow combines the strengths of **Excel** and **Power Query** for data management and **GraphPad Prism** for visualization. The goal is to efficiently organize data and produce high-quality graphs without performing complex statistical analysis.

### 1. **Data Preparation in Excel**:
   - **Data Import**: The master table is loaded into Excel and processed using **Power Query**.
   - **Power Query for Filtering and Transformation**: Power Query is used to filter and transform the dataset (e.g., extracting data for specific cases, respondents, or sessions). Filters are applied to select relevant columns and rows, such as extracting all **Actual Child (AC)** trials for **Case 1** with **Confederate (CONF)** as the respondent.
   - **Automated Updates**: The query results are loaded back into Excel. Any changes made to the master table are reflected in the query results when refreshed.
   - **Excel Functions for Real-Time Calculations**: Supplemental calculations such as averages, compliance rates, or specific lookups are handled within Excel using functions like `FILTER`, `XLOOKUP`, and `AVERAGE`.

### 2. **Exporting Data to GraphPad Prism**:
   - Once the data is cleaned and organized in Excel, it is exported as a **CSV file** for use in GraphPad Prism.
   - This file will contain the relevant variables for generating  visualizations.
   
### 3. **Visualization in GraphPad Prism**:
   - **Data Import**: The cleaned CSV file is imported into GraphPad Prism.
   - **Graph Creation**: Prism is used to create publication-quality graphs, focusing on visual comparisons such as **SelfMonitoring vs. ConfMonitoring** or phase-by-phase analyses.
   - **No Complex Statistics**: Since complex statistical analysis is not needed, Prism is used mainly for its graphing capabilities.

### Key Points:
- **Excel** is used for **data management** and **real-time calculations**.
- **Power Query** allows for dynamic filtering and automated updates from the master table.
- **GraphPad Prism** is used solely for generating high-quality visualizations, without conducting complex statistical tests.
- **Exporting** data from Excel to Prism as a **CSV** ensures smooth transitions between data preparation and visualization.


## Naming Convention:

```plaintext
<SessionType>_<StudyPhase>_<CaregiverID>_<Respondent>_<Additional Details>_<Version>
```

### Components Breakdown:
1. **SessionType**: 
   - **AC**: Actual Child trials.
   - **SC**: Simulated Child trials.
   
2. **StudyPhase**:
   - **BL**: Baseline.
   - **T1**, **T2**, **T3**: Training Phases 1 to 3.
   - **RTB**: Reversal to Baseline.

3. **CaregiverID or GroupDescription**: 
   - Either a specific case ID (e.g., **Case1**, **Case2**) or a group descriptor (e.g., **AllCases**, **BaselineGroup**).

4. **Respondent**:
   - **CARE**: Caregiver.
   - **CONF**: Confederate.
   - **IOA**: Interobserver Agreement.

5. **Additional Details**: 
   - Any additional descriptors for the dataset, such as **TrialType**, **ChildTrials**, **Monitoring**, etc., to differentiate between datasets if needed.
   
6. **Version**: 
   - **V1**, **V2**, etc., for different versions of the table.

### Example Table Names:

1. **All Actual Child Trials for Case 1 (Caregiver as Respondent)**:
   - `AC_T1_Case1_CARE_ChildTrials_V1`: All actual child trials for **Case 1**, in **T1**, with **Caregiver (CARE)** as the respondent, version 1.

2. **Simulated Child Trials for Training Phase 2 (T2) for Case 1 (Confederate as Respondent)**:
   - `SC_T2_Case1_CONF_ChildTrials_V1`: Simulated child trials for **Case 1**, in **T2**, with **Confederate (CONF)** as the respondent, version 1.

3. **All Trials for Baseline Phase (BL) for Case 1 (Interobserver Agreement as Respondent)**:
   - `AC_BL_Case1_IOA_AllTrials_V1`: All trials during the **Baseline phase (BL)** for **Case 1**, with **IOA** as the respondent, version 1.

4. **Actual Child Trials for All Cases in Training Phases**:
   - `AC_T1_AllCases_AllRespondents_ChildTrials_V1`: Aggregated table of **all actual child trials** for all cases, during **T1**, across all respondents, version 1.

5. **Simulated Child Trials for Reversal to Baseline Phase (RTB) for IOA Respondent**:
   - `SC_RTB_Case1_IOA_ChildTrials_V1`: Simulated child trials during the **Reversal to Baseline (RTB)** phase for **Case 1**, with **IOA** as the respondent, version 1.

### Broader Aggregated Examples:
1. **All Actual Child Trials for All Cases Across All Phases**:
   - `AC_ALL_AllCases_AllRespondents_ChildTrials_V1`: All actual child trials for all cases, across all phases and respondents, version 1.

2. **All Records for Case 1 Across All Phases and Respondents**:
   - `AC_ALL_Case1_AllRespondents_AllTrials_V1`: Aggregated table of all records for **Case 1**, across all phases and respondents, version 1.

 

## Data Preparation in Excel for Confederate Monitoring Analysis

### 1. **Introduction**
   - This sections outlines the steps to clean, filter, and organize  Monitoring data for analysis and visualization in GraphPad Prism. 
   - The goal is to process data from both Simulated Child (SC) and Actual Child (AC) sessions, calculating trial block scores, averages, and counts for each session.

### 2. **Loading the Master Table**
   - **Step 1**: Import the master table into Excel from a CSV file.
     - Navigate to the **Data** tab in Excel.
     - Select **Get Data** → **From File** → **From CSV** and choose the master table.
   - **Step 2**: Format the imported data as a table in Excel.
     - Select the table and choose **Format as Table** to enable easier filtering and querying.

### 3. **Using Power Query for Data Filtering and Transformation**
   - **Step 1**: Load the master table into Power Query.
     - Go to the **Data** tab in Excel and click **Get Data** → **From Table/Range** to open the table in Power Query.
   - **Step 2**: Define key parameters in Power Query: ALL_ALL_Case1_CONF_TrialBlockScoring_v1
     - Parameters for filtering the data dynamically are set at the start of the script. These include `CaregiverID`, `Respondent`, `SessionType`, and `EventNote`.
   
   ```go
   let
       CaregiverID = "Case1",  // Parameter: Case1, Case2, Case3
       Respondent = "1_CONF",  // Parameter: 1_CONF, 2_IOA, CARE
       EventNote_Prefix = "3.0_Conf",  // Match the first 8 characters of EventNote
       SessionType_SC = "1_SC",  // Simulated Child session type
       SessionType_AC = "0_AC"   // Actual Child session type
   ```

   ### 4. **Processing Simulated Child (SC) Sessions**

   #### **Filtering and Sorting SC Sessions**
   - **Step 1**: Filter for SC sessions based on the parameters.
     - The script filters rows that match the selected `CaregiverID`, `Respondent`, `EventNote_Prefix`, and **Simulated Child** sessions.

     ```go
     #"Filtered Rows_SC" = Table.SelectRows(#"Changed Type", each 
         ([CaregiverID] = CaregiverID) and 
         ([Respondent] = Respondent) and
         (Text.Start([EventNote], 8) = EventNote_Prefix) and
         ([SessionType] = SessionType_SC)
     )
     ```
   - **Step 2**: Sort SC sessions chronologically by `DateTimeStamp`.
     ```go
     #"Sorted Rows_SC" = Table.Sort(#"Filtered Rows_SC", {{"DateTimeStamp", Order.Ascending}})
     ```

   #### **Creating Trial Blocks for SC Sessions**
   - **Step 3**: Add an index column to uniquely identify each trial.
     ```go
     #"Added Index_SC" = Table.AddIndexColumn(#"Sorted Rows_SC", "Index", 1, 1, Int64.Type)
     ```
   - **Step 4**: Create `TrialBlockGroup` by grouping trials into pairs.
     - Each pair of trials is treated as a block, and trial block scores will be computed for each pair.
     ```go
     #"Added TrialBlockGroup_SC" = Table.AddColumn(#"Added Index_SC", "TrialBlockGroup", each Number.IntegerDivide([Index] - 1, 2) + 1)
     ```

   #### **Computing Trial Block Scores for SC**
   - **Step 5**: Calculate the trial block scores for SC sessions based on Confederate Monitoring variables (**ConfMonitoring1-6a_3**).
     - For each trial block, a score of `1` is assigned if both trials have a value of `1` for a given variable, otherwise, the score is `0`.

     ```go
     #"Added Custom_SC" = Table.AddColumn(#"GroupedTBRows_SC", "TrialBlockScore_SC", each
         let
             TrialRows = [ComputedTrialBlockSubTable],
             Trial1 = if Table.RowCount(TrialRows) > 0 then TrialRows{0} else null,
             Trial2 = if Table.RowCount(TrialRows) > 1 then TrialRows{1} else null,
             // Extract fields from Trial2
             SessionNumber = if Trial2 <> null then Trial2[SessionCount] else null,
             StudyPhase = if Trial2 <> null then Trial2[StudyPhase] else null,
             TB_ConfMonitoring1 = if (Trial1[ConfMonitoring1] = 1 and Trial2[ConfMonitoring1] = 1) then 1 else 0,
             TB_ConfMonitoring2 = if (Trial1[ConfMonitoring2] = 1 and Trial2[ConfMonitoring2] = 1) then 1 else 0,
             // Continue for all other ConfMonitoring variables
         in
         [
             SessionNumber = SessionNumber,
             StudyPhase = StudyPhase,
             TB_ConfMonitoring1 = TB_ConfMonitoring1,
             TB_ConfMonitoring2 = TB_ConfMonitoring2
             // Include other ConfMonitoring variables
         ]
     )
     ```

   #### **Calculating Averages and Counts for SC**
   - **Step 6**: Compute averages and counts for Confederate Monitoring variables across all trial blocks.
     - **T1** includes variables 1, 2, and 6a_1-6a_3.
     - **T2** includes variables 3, 4, and 5.

     ```go
     #"Added SC_T1_Count" = Table.AddColumn(#"Expanded TrialBlockScore_SC", "SC_T1_Count", each 
         [TB_ConfMonitoring1] + [TB_ConfMonitoring2] + [TB_ConfMonitoring6a_1] + [TB_ConfMonitoring6a_2] + [TB_ConfMonitoring6a_3]
     ),
     #"Added SC_T1_Average" = Table.AddColumn(#"Added SC_T1_Count", "SC_T1_Average", each 
         [SC_T1_Count] / 5
     ),
     #"Added SC_T2_Average" = Table.AddColumn(#"Added SC_T1_Average", "SC_T2_Average", each 
         [SC_T2_Count] / 3
     ),
     ```

### 5. **Processing Actual Child (AC) Sessions**

#### **Filtering and Processing AC Sessions**
   - **Step 1**: Filter for AC sessions based on the selected parameters.
     ```go
     #"Filtered Rows_AC" = Table.SelectRows(#"Changed Type", each 
         ([CaregiverID] = CaregiverID) and
         ([Respondent] = Respondent) and
         (Text.Start([EventNote], 8) = EventNote_Prefix) and
         ([SessionType] = SessionType_AC)
     )
     ```
   - **Step 2**: Adjust the columns for AC trials, ensuring they align with SC structure.
     ```go
     #"Selected Columns_AC" = Table.SelectColumns(#"Filtered Rows_AC", {"DateTimeStamp", "CaregiverID", "SessionCount", "StudyPhase", 
         "ConfMonitoring1", "ConfMonitoring2", "ConfMonitoring3", "ConfMonitoring4", "ConfMonitoring5", 
         "ConfMonitoring6a_1", "ConfMonitoring6a_2", "ConfMonitoring6a_3"}),
     #"Renamed Columns_AC" = Table.RenameColumns(#"Selected Columns_AC", {{"SessionCount", "SessionNumber"}})
     ```

#### **Calculating Averages and Counts for AC**
   - **Step 3**: Compute averages and counts for Confederate Monitoring variables for the AC trials, similar to the SC calculations.
     ```go
     #"Added AC_T1_Count" = Table.AddColumn(#"Added TrialBlockGroup_AC", "AC_T1_Count", each 
         [ConfMonitoring1] + [ConfMonitoring2] + [ConfMonitoring6a_1] + [ConfMonitoring6a_2] + [ConfMonitoring6a_3]
     ),
     #"Added AC_T1_Average" = Table.AddColumn(#"Added AC_T1_Count", "AC_T1_Average", each 
         [AC_T1_Count] / 5
     ),
     #"Added AC_AllConfMonitoring_Average" = Table.AddColumn(#"Added AC_T1_Average", "AC_AllConfMonitoring_Average", each 
         [AC_AllConfMonitoring_Count] / 8
     )
     ```

### 6. **Combining SC and AC Data**

   - **Step 1**: Ensure the SC and AC tables have the same columns and structure.
     - If a column is missing in either table, it's added with `null` values.
     ```go
     #"Adjusted SC Table" = Table.SelectColumns(#"Added SC_AllConfMonitoring_Average", AllColumns, MissingField.UseNull),
     #"Adjusted AC Table" = Table.SelectColumns(#"Added AC_AllConfMonitoring_Average", AllColumns, MissingField.UseNull)
     ```

   - **Step 2**: Combine the SC and AC tables into a single dataset.
     ```go
     #"Combined AC_SC Results" = Table.Combine({#"Adjusted SC Table",

### `ALL_ALL_Case1_CONF_TrialBlockScoring_v1` Power Query Code:



```go
let
    // Define parameters (Case1, Case2, Case3)
    CaregiverID = "Case1",  // Select the relevant participant ID
    Respondent = "1_CONF",  // Parameter: 1_CONF, 2_IOA, CARE (Confederate, IOA, Caregiver)

    EventNote_Prefix = "3.0_Conf",  // Match the first 8 characters of EventNote
    SessionType_SC = "1_SC",   // Set session type for Simulated Child
    SessionType_AC = "0_AC",   // Set session type for Actual Child

    // Load the data from Excel table
    Source = Excel.CurrentWorkbook(){[Name="Table2"]}[Content],

    // Ensure consistent data types
    #"Changed Type" = Table.TransformColumnTypes(Source, {
        {"InstanceID", type text}, {"EventNote", type text}, {"DateTimeStamp", type datetimezone}, 
        {"ResponseIDx", type text}, {"CaregiverID", type text}, {"Respondent", type text}, 
        {"StudyPhase", type text}, {"SessionType", type text}, {"SessionCount", Int64.Type}, 
        {"ConfMonitoring1", Int64.Type}, {"ConfMonitoring2", Int64.Type}, {"ConfMonitoring3", Int64.Type}, 
        {"ConfMonitoring4", Int64.Type}, {"ConfMonitoring5", Int64.Type}, {"ConfMonitoring6a_1", Int64.Type}, 
        {"ConfMonitoring6a_2", Int64.Type}, {"ConfMonitoring6a_3", Int64.Type}
    }),

    // 1. Handle SC Trials

    // Filter for SC sessions
    #"Filtered Rows_SC" = Table.SelectRows(#"Changed Type", each 
        ([CaregiverID] = CaregiverID) and 
        ([Respondent] = Respondent) and
        (Text.Start([EventNote], 8) = EventNote_Prefix) and  // Match the first 8 characters of EventNote
        ([SessionType] = SessionType_SC)
    ),

    // Sort the table by DateTimeStamp to ensure the rows are in chronological order
    #"Sorted Rows_SC" = Table.Sort(#"Filtered Rows_SC", {{"DateTimeStamp", Order.Ascending}}),

    // Add an index column starting from 1
    #"Added Index_SC" = Table.AddIndexColumn(#"Sorted Rows_SC", "Index", 1, 1, Int64.Type),

    // Create TrialBlockGroup column by dividing the Index by 2 and adding 1 (pairs of two trials per group)
    #"Added TrialBlockGroup_SC" = Table.AddColumn(#"Added Index_SC", "TrialBlockGroup", each Number.IntegerDivide([Index] - 1, 2) + 1),

    // Group by TrialBlockGroup (which uniquely identifies each block of two trials)
    #"GroupedTBRows_SC" = Table.Group(#"Added TrialBlockGroup_SC", {"TrialBlockGroup"}, {
        {"ComputedTrialBlockSubTable", each _, type table}
    }),

    // Compute the trial block scores for SC ConfMonitoring variables and extract additional fields from Trial 2
    #"Added Custom_SC" = Table.AddColumn(#"GroupedTBRows_SC", "TrialBlockScore_SC", each
        let 
            TrialRows = [ComputedTrialBlockSubTable],  // set to the sub-table of trials within each trial block
            Trial1 = if Table.RowCount(TrialRows) > 0 then TrialRows{0} else null, // First trial in the block
            Trial2 = if Table.RowCount(TrialRows) > 1 then TrialRows{1} else null, // Second trial in the block
            
            // Extract additional fields from Trial2 (if it exists)
            SessionNumber = if Trial2 <> null then Trial2[SessionCount] else null,
            StudyPhase = if Trial2 <> null then Trial2[StudyPhase] else null,
            CaregiverID = if Trial2 <> null then Trial2[CaregiverID] else null,
            DateTimeStamp = if Trial2 <> null then Trial2[DateTimeStamp] else null,

            // Compute scores for ConfMonitoring
            TB_ConfMonitoring1 = if (Trial1[ConfMonitoring1] = 1 and Trial2[ConfMonitoring1] = 1) then 1 else 0,
            TB_ConfMonitoring2 = if (Trial1[ConfMonitoring2] = 1 and Trial2[ConfMonitoring2] = 1) then 1 else 0,
            TB_ConfMonitoring3 = if (Trial1[ConfMonitoring3] = 1 and Trial2[ConfMonitoring3] = 1) then 1 else 0,
            TB_ConfMonitoring4 = if (Trial1[ConfMonitoring4] = 1 and Trial2[ConfMonitoring4] = 1) then 1 else 0,
            TB_ConfMonitoring5 = if (Trial1[ConfMonitoring5] = 1 and Trial2[ConfMonitoring5] = 1) then 1 else 0,
            TB_ConfMonitoring6a_1 = if (Trial1[ConfMonitoring6a_1] = 1 and Trial2[ConfMonitoring6a_1] = 1) then 1 else 0,
            TB_ConfMonitoring6a_2 = if (Trial1[ConfMonitoring6a_2] = 1 and Trial2[ConfMonitoring6a_2] = 1) then 1 else 0,
            TB_ConfMonitoring6a_3 = if (Trial1[ConfMonitoring6a_3] = 1 and Trial2[ConfMonitoring6a_3] = 1) then 1 else 0
        in
        [
            SessionNumber = SessionNumber,
            StudyPhase = StudyPhase,
            CaregiverID = CaregiverID,
            DateTimeStamp = DateTimeStamp,
            // Removed TrialBlockGroup to avoid duplicate column
            TB_ConfMonitoring1 = TB_ConfMonitoring1,
            TB_ConfMonitoring2 = TB_ConfMonitoring2,
            TB_ConfMonitoring3 = TB_ConfMonitoring3,
            TB_ConfMonitoring4 = TB_ConfMonitoring4,
            TB_ConfMonitoring5 = TB_ConfMonitoring5,
            TB_ConfMonitoring6a_1 = TB_ConfMonitoring6a_1,
            TB_ConfMonitoring6a_2 = TB_ConfMonitoring6a_2,
            TB_ConfMonitoring6a_3 = TB_ConfMonitoring6a_3
        ]
    ),

    // Expand the TrialBlockScore record into separate columns for SC
    #"Expanded TrialBlockScore_SC" = Table.ExpandRecordColumn(#"Added Custom_SC", "TrialBlockScore_SC", 
    {"SessionNumber", "StudyPhase", "CaregiverID", "DateTimeStamp", 
    "TB_ConfMonitoring1", "TB_ConfMonitoring2", "TB_ConfMonitoring3", "TB_ConfMonitoring4", 
    "TB_ConfMonitoring5", "TB_ConfMonitoring6a_1", "TB_ConfMonitoring6a_2", "TB_ConfMonitoring6a_3"}),

    // Add custom SC calculations for counts and averages
    #"Added SC_T1_Count" = Table.AddColumn(#"Expanded TrialBlockScore_SC", "SC_T1_Count", each 
        [TB_ConfMonitoring1] + [TB_ConfMonitoring2] + [TB_ConfMonitoring6a_1] + [TB_ConfMonitoring6a_2] + [TB_ConfMonitoring6a_3]
    ),
    #"Added SC_T2_Count" = Table.AddColumn(#"Added SC_T1_Count", "SC_T2_Count", each 
        [TB_ConfMonitoring3] + [TB_ConfMonitoring4] + [TB_ConfMonitoring5]
    ),
    #"Added SC_AllConfMonitoring_Count" = Table.AddColumn(#"Added SC_T2_Count", "SC_AllConfMonitoring_Count", each 
        [SC_T1_Count] + [SC_T2_Count]
    ),
    #"Added SC_T1_Average" = Table.AddColumn(#"Added SC_AllConfMonitoring_Count", "SC_T1_Average", each 
        [SC_T1_Count] / 5
    ),
    #"Added SC_T2_Average" = Table.AddColumn(#"Added SC_T1_Average", "SC_T2_Average", each 
        [SC_T2_Count] / 3
    ),
    #"Added SC_AllConfMonitoring_Average" = Table.AddColumn(#"Added SC_T2_Average", "SC_AllConfMonitoring_Average", each 
        [SC_AllConfMonitoring_Count] / 8
    ),

    // 2. Handle AC Trials

    // Filter for AC sessions
    #"Filtered Rows_AC" = Table.SelectRows(#"Changed Type", each 
        ([CaregiverID] = CaregiverID) and 
        ([Respondent] = Respondent) and
        (Text.Start([EventNote], 8) = EventNote_Prefix) and  // Match the first 8 characters of EventNote
        ([SessionType] = SessionType_AC)
    ),

    // Select necessary columns and rename SessionCount to SessionNumber
    #"Selected Columns_AC" = Table.SelectColumns(#"Filtered Rows_AC", {"DateTimeStamp", "CaregiverID", "SessionCount", "StudyPhase", 
        "ConfMonitoring1", "ConfMonitoring2", "ConfMonitoring3", "ConfMonitoring4", "ConfMonitoring5", 
        "ConfMonitoring6a_1", "ConfMonitoring6a_2", "ConfMonitoring6a_3"}),
    #"Renamed Columns_AC" = Table.RenameColumns(#"Selected Columns_AC", {{"SessionCount", "SessionNumber"}}),

    // Add TrialBlockGroup column, set to null (or any appropriate value)
    #"Added TrialBlockGroup_AC" = Table.AddColumn(#"Renamed Columns_AC", "TrialBlockGroup", each null),

    // Add custom AC calculations for counts and averages
    #"Added AC_T1_Count" = Table.AddColumn(#"Added TrialBlockGroup_AC", "AC_T1_Count", each 
        [ConfMonitoring1] + [ConfMonitoring2] + [ConfMonitoring6a_1] + [ConfMonitoring6a_2] + [ConfMonitoring6a_3]
    ),
    #"Added AC_T2_Count" = Table.AddColumn(#"Added AC_T1_Count", "AC_T2_Count", each 
        [ConfMonitoring3] + [ConfMonitoring4] + [ConfMonitoring5]
    ),
    #"Added AC_AllConfMonitoring_Count" = Table.AddColumn(#"Added AC_T2_Count", "AC_AllConfMonitoring_Count", each 
        [AC_T1_Count] + [AC_T2_Count]
    ),
    #"Added AC_T1_Average" = Table.AddColumn(#"Added AC_AllConfMonitoring_Count", "AC_T1_Average", each 
        [AC_T1_Count] / 5
    ),
    #"Added AC_T2_Average" = Table.AddColumn(#"Added AC_T1_Average", "AC_T2_Average", each 
        [AC_T2_Count] / 3
    ),
    #"Added AC_AllConfMonitoring_Average" = Table.AddColumn(#"Added AC_T2_Average", "AC_AllConfMonitoring_Average", each 
        [AC_AllConfMonitoring_Count] / 8
    ),

    // 3. Define the list of all required columns
    AllColumns = {
        "DateTimeStamp", "CaregiverID", "SessionNumber", "TrialBlockGroup", "StudyPhase",
        "TB_ConfMonitoring1", "TB_ConfMonitoring2", "TB_ConfMonitoring3", "TB_ConfMonitoring4",
        "TB_ConfMonitoring5", "TB_ConfMonitoring6a_1", "TB_ConfMonitoring6a_2", "TB_ConfMonitoring6a_3",
        "SC_T1_Average", "SC_T2_Average", "SC_AllConfMonitoring_Average", "SC_T1_Count", "SC_T2_Count", "SC_AllConfMonitoring_Count",
        "AC_T1_Average", "AC_T2_Average", "AC_AllConfMonitoring_Average", "AC_T1_Count", "AC_T2_Count", "AC_AllConfMonitoring_Count"
    },

    // 4. Adjust SC table to have all required columns
    #"Adjusted SC Table" = Table.SelectColumns(#"Added SC_AllConfMonitoring_Average", AllColumns, MissingField.UseNull),

    // 5. Adjust AC table to have all required columns
    #"Adjusted AC Table" = Table.SelectColumns(#"Added AC_AllConfMonitoring_Average", AllColumns, MissingField.UseNull),

    // 6. Combine the adjusted SC and AC tables
    #"Combined AC_SC Results" = Table.Combine({#"Adjusted SC Table", #"Adjusted AC Table"}),

    // 7. Reorder the columns as needed
    #"Reordered Columns" = Table.ReorderColumns(#"Combined AC_SC Results", AllColumns),
    #"Sorted Rows" = Table.Sort(#"Reordered Columns",{{"DateTimeStamp", Order.Ascending}})
in
    #"Sorted Rows"
```

### Conclusion:
This script provides a clean, processed dataset that groups trials into blocks, computes monitoring scores, and calculates averages. It ensures that each trial block is scored based on the performance of both trials in the block and includes additional relevant metadata for further analysis.

## **Prism Design Considerations**

This section outlines the design considerations for setting up data for GraphPad Prism using trial blocks as the X-axis for individual participants. The goal is to visualize different phases of a study, such as baseline, training, and return to baseline, for a single participant, while allowing flexibility in the structure for trials that do not share the same X values across phases. Information is summarized from Prism Manual.

### **Table Format: XY Data in GraphPad Prism**

In GraphPad Prism, an **XY data table** is structured so that each point is defined by an **X** and **Y** value. The table can accommodate different phases or data series, even if they do not share the same X values. This format is ideal for analyzing time-based data or trial blocks across different phases for a participant.

#### **Key Characteristics of an XY Table:**
- **X Column**: Represents the independent variable (in this case, trial blocks).
- **Y Columns**: Represent the dependent variable (EDC performance). You can have multiple Y columns for each phase of the study.
- **Staggered Data**: If trials within a phase do not start at the same X value, you can stagger the data entry by leaving rows blank and starting the data at the correct X point for each phase.


#### **Entering Multiple Sets of Data That Don’t Share X Values**

 Each XY data table in Prism has a single X column for up to 104 sets of Y values (i.e., phases or variables). If different phases or data series do not share the same X values (e.g., if trial blocks begin at different points within the study), you can handle this by **staggering the data entry**. This means leaving blank rows where needed and only entering values where the X value corresponds to the start of that phase.

#### **Best Practice for Staggering Data**:
1. **Start Entering Data at the Correct X Value**: You don’t need to start entering data in the first row. If one phase begins at a later trial block, simply start that phase’s data in a later row, leaving previous X values blank.
2. **Separate Phases into Different Y Columns**: For each phase (e.g., Baseline, Training 1, Training 2), use separate Y columns to keep the data organized.


## **Example Table Structure for a Single Participant**

For a participant, the data can be structured as follows:

| X (Trial Block) | Baseline (Y1) | Training 1 (Y2) | Training 2 (Y3) | Maintenance (Y4) |
|-----------------|---------------|-----------------|-----------------|------------------|
| 1               | 85            |                 |                 |                  |
| 2               | 87            |                 |                 |                  |
| 3               | 89            |                 |                 |                  |
| 4               |               | 70              |                 |                  |
| 5               |               | 72              |                 |                  |
| 6               |               | 75              |                 |                  |
| 7               |               |                 | 80              |                  |
| 8               |               |                 | 83              |                  |
| 9               |               |                 | 85              |                  |
| 10              |               |                 |                 | 88               |
| 11              |               |                 |                 | 90               |

#### **Explanation**:
- **X (Trial Block)**: Represents the trial block number.
- **Baseline (Y1)**: This participant's data during the baseline phase.
- **Training 1 (Y2)**: Data for the first training phase, which starts later than the baseline.
- **Training 2 (Y3)**: Data for the second training phase, starting even later.
- **Maintenance (Y4)**: Data for the maintenance phase, which begins after the training phases.


#### **Considerations for Graphing in Prism**:
- **Error Bars**: If you have replicate values for each trial block, Prism allows you to add error bars by using subcolumns. For each replicate, you can enter the corresponding Y value in the subcolumns.
- **Annotations**: Use Prism’s annotation feature to mark key points, such as the transition from one phase to another or significant changes in performance.
- **Handling Missing Data**: Blank cells will be automatically ignored by Prism, and no lines will be drawn through them, allowing for clear representation of the different start points of phases.



### Documentation for Data Transfer and Plotting in GraphPad Prism

#### **Steps for Manual Data Transfer and Plotting in GraphPad Prism**:

##### 1. **Y-Axis Group Labels in Prism**:
   - Each Y-axis group within **Prism** was named according to the study phase and session type.
   - **Example Y-axis group labels**:
     - `BL_AC` (Group A)
     - `BL_SC` (Group B)
     - `T1_SC` (Group F)
     - `T2_SC_1` (Group H)
     - `RTB_AC` (Group N)

##### 2. **Merging Data Tables**:
   - The **AC_ALL_Case1_CONF_X_V1** table (15 entries) was merged into the **ALL_ALL_Case1_CONF_TrialBlockScoring_v1** table (41 entries).
   - This resulted in a combined dataset with **56 entries**. The `TrialBlockGroup` column was updated as follows:
     - **X.5**: Assigned to baseline entries.
     - **X.25, X.5, X.75**: Assigned to the remaining AC sets (entries from the merged table).

   This merged dataset was then transferred to GraphPad Prism for further visualization.

##### 3. **Transferring Data Series to Prism**:

1. **Starting with `AllConfMonitoring_Average` Values**:
   - The first step was to copy the **`AllConfMonitoring_Average`** values from the combined dataset in Excel and paste them into Prism.
   - Initially, the values were pasted into the **Group A (`BL_AC`)** column within Prism.

2. **Cut and Paste to the Correct Y-Axis Groups**:
   - After pasting all the `AllConfMonitoring_Average` values into Group A, each subset of data was moved (cut and pasted) to the correct Y-axis group based on the session and phase.
   - For instance:
     - **Group A** (`BL_AC`) received the corresponding baseline values.
     - **Group B** (`BL_SC`) received its respective values.
     - **Group C** (`BL_AC`) was populated, and so on for each group.

   This ensured that the correct Y-axis group contained the appropriate data for each phase or session.

##### 4. **Creating Data Tables for Additional Series (`T1_Average`, `T2_Average`)**:
   - Once the `AllConfMonitoring_Average` data was organized in the correct Y-axis groups, the process was repeated for other series.
   - **For `T1_Average` and `T2_Average`**:
     - Separate data tables were created in Prism for the `T1_Average` and `T2_Average` series.
     - These values were copied from Excel and pasted into the appropriate Y-axis groups for each series.

   This resulted in three separate Prism data tables for:
   - **ALL_ALL_Case1_CONF_TrialBlockScoring_v1** (56 entries after the merge)
   - **ALL_T1_Case1_CONF__v1**
   - **ALL_T2_Case1_CONF__v1**

##### 5. **Verifying Data Alignment**:
   After each series was transferred to Prism, the data was cross-referenced for accuracy:
   
   1. **Check Row Configuration**:
      - After moving the data series into their corresponding Y-axis groups, the row configuration was verified to ensure that each row of data was correctly aligned with the corresponding Y-axis group.
      - This confirmed that the data points in each series were properly aligned between Excel and Prism.

   2. **Cross-Reference Check**:
      - For each series (`AllConfMonitoring_Average`, `T1_Average`, `T2_Average`), five random data points were selected and visually compared between the Excel source and Prism to ensure accuracy in the transfer.
      - This step provided assurance that the row order and data values matched perfectly.

#### **Conclusion**:
By carefully merging the **AC_ALL_Case1_CONF_X_V1** and **ALL_ALL_Case1_CONF_TrialBlockScoring_v1** tables into a combined set of 56 entries, and transferring each data series one at a time (starting with `AllConfMonitoring_Average`, followed by `T1_Average` and `T2_Average`), and assigning them to their corresponding Y-axis groups in Prism, the integrity and alignment of the data were maintained. This process ensured that the data was structured and ready for accurate visualization in GraphPad Prism.

### Steps for Python Script to Automate Data Transfer to Prism `TechPT - 2024.09.19 - Script - Translate Excel to Prism`


#### 1. **Introduction**
This section outlines the steps taken to dynamically process a CSV file containing session or trial data. The goal of the script is to dynamically select the last column in the dataset, generate new columns based on session and phase identifiers, for visualization in GraphPad Prism.

### 2. **Loading and Initial Setup**
- **Step 1**: Prepare CSV file with essential columns. The `TechPT - 2024.09.18 - Query - ALL_ALL_Case1_CONF_TrialBlockScoring_v1` query was used to generate the CSV file.
- **Step 2**: The script prompts the user to select a CSV file using a file dialog.
- **Step 3**: The script reads the selected CSV file into a pandas DataFrame (`df`), ensuring that essential columns are present. These include:
  - `DateTimeStamp`
  - `CaregiverID`
  - `SessionNumber`
  - `TrialBlockGroup`
  - `StudyPhase`
  - `SessionType`
  - Last column with the data to be visualized in Prism.

- **Step 3**: The last column of the CSV is identified dynamically, ensuring flexibility regardless of the column header names in the input file.

```python
last_column = df.columns[-1]
```

#### 3. **Processing Session Data**
#### **Step 1: Creating a Phase and Session Identifier**
- A new identifier, `Phase_Part`, is created by combining `StudyPhase` and `SessionType` for each row. This helps in organizing data by the session phase and type.

```python
def get_phase_part(row):
    study_phase = row['StudyPhase']
    session_type = row['SessionType']
    if study_phase == '5_RTB':
        phase_part = 'RTB'
    else:
        phase_part = study_phase.split('_')[-1]
    type_part = session_type.split('_')[-1]
    return f"{phase_part}_{type_part}"

df['Phase_Part'] = df.apply(get_phase_part, axis=1)
```

##### **Step 2: Assigning Row Index**
- Each row is indexed starting from 1 for easier tracking and reference.

```python
df['Row_Index'] = df.index + 1
```

#### 4. **Main Loop: Generating Columns for Each Session**
- The script iterates through the rows of the DataFrame, dynamically creating new columns based on `Phase_Part` and `SessionNumber`. The values from the dynamically identified last column are placed into these new columns. 

- **Loop Initialization**:
  - Each combination of `Phase_Part` and `SessionNumber` starts a new column.
  - Subsequent rows that match the same `Phase_Part` and `SessionNumber` are placed into the same column.

```python
while idx < len(df):
    row = df.iloc[idx]
    phase_part1 = row['Phase_Part']
    session_number1 = row['SessionNumber']
    last_column_value1 = row[last_column]  # Dynamically fetched last column

    column_count += 1
    column_name = f"{phase_part1}_{session_number1}_{column_count}"

    if column_name not in output_df.columns:
        output_df[column_name] = pd.NA

    output_df.at[idx, column_name] = last_column_value1

    # Nested loop for same phase and session
    idx += 1
    while idx < len(df):
        row2 = df.iloc[idx]
        phase_part2 = row2['Phase_Part']
        session_number2 = row2['SessionNumber']
        last_column_value2 = row2[last_column]

        if phase_part2 == phase_part1 and session_number2 == session_number1:
            output_df.at[idx, column_name] = last_column_value2
            idx += 1
        else:
            break
```

#### 5. **Output Formatting**
- Once the loop completes, the script organizes the new columns into a desired order and prompts the user to save the output as a CSV file.

```python
# Reorder columns
desired_columns_order = ['Trial Block Count'] + columns_order
output_df = output_df[desired_columns_order]

# Prompt user to save CSV
output_file = filedialog.asksaveasfilename(defaultextension=".csv",
                                           filetypes=[("CSV Files", "*.csv")],
                                           title="Save CSV as")
if output_file:
    output_df.to_csv(output_file, index=False)
    print(f"Data successfully exported to {output_file}")
```


