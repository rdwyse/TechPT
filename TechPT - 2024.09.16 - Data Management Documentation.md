TechPT Data Management Documentation
2024.09.17

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

 
# Data Preperation in Excel

## Outline for Data Preparation in Excel

### 1. **Introduction**
   - Brief overview of the purpose of data preparation in Excel.
   - Explain the goal: to clean, filter, and organize data for visualization in GraphPad Prism, using Excel and Power Query.

### 2. **Loading the Master Table**
   - **Step 1**: Open Excel and import the master table.
     - Navigate to the **Data** tab.
     - Select **Get Data** → **From File** → **From CSV** to load the master table into Excel.
   - **Step 2**: Ensure that the table is formatted as a proper Excel table.
     - Click on the table and select **Format as Table** to enable easier filtering and querying.

### 3. **Using Power Query for Data Filtering**
   - **Step 1**: Load the master table into Power Query.
     - Go to the **Data** tab and click **Get Data** → **From Table/Range** to open the table in Power Query: use **master table range A1:BB786**
   - **Step 2**: Apply filters to the dataset.
     - Filter based on specific variables like **CaseID** (e.g., **Case 1**), **SessionType** (e.g., **AC** for Actual Child trials), and **Respondent** (e.g., **CONF** for Confederate).
     - Example of filtering: 
       - Filter for **Case 1**.
       - Filter for **SessionType = AC**.
       - Filter for **Respondent = CONF**.
   - **Step 3**: Select relevant columns.
     - Use `Table.SelectColumns` to keep only necessary columns (e.g., **InstanceID**, **CaregiverID**, **ConfMonitoring1-6**, etc.).
     - This step ensures that only essential data is exported for further analysis.

### 4. **Loading Data from Power Query Back to Excel**
   - **Step 1**: Load the transformed query data back into Excel.
     - In Power Query, select **Close & Load** → **Load to** to export the query results as a new table in Excel.
   - **Step 2**: Save the query results in a separate worksheet for easy reference.

    - **Change the Query to Load as a Table**
      - If the query is currently a Connection Only query (meaning it's not loaded to a worksheet), you can modify its settings:
      - Go to Data > Queries & Connections.
      - Right-click your query and choose Load To....
      - In the Import Data dialog box that appears, choose Table and select a worksheet where you'd like the data to load.

### Actual Child Confederate Monitoring Power Query Code with Dynamic Parameters


This Power Query code is designed to extract, filter, and compute averages based on **ConfMonitoring** data. It leverages parameters for flexibility, allowing dynamic filtering based on key variables like `CaregiverID`, `Respondent`, `SessionType`, and `EventNote`. The query processes and computes averages for different sets of monitoring data, and it is structured for reusability.

#### **Overview:**
The query dynamically filters rows from the dataset based on parameters and computes custom averages for **T1**, **T2**, and **AllConfMonitoring** sets of monitoring columns. The query uses the following steps:
1. **Define Parameters**: Provides flexibility for different datasets.
2. **Data Transformation**: Adjusts data types for consistency.
3. **Filtering Rows**: Filters based on the defined parameters.
4. **Column Selection**: Retains only the necessary columns.
5. **Custom Calculations**: Calculates averages for T1, T2, and all **ConfMonitoring** columns.

#### Example Power Query Code:



```go
let
	// Define parameters
	CaregiverID = "Case1",        // Parameter: Case1, Case2, Case3, Case4
	Respondent = "1_CONF",        // Parameter: 1_CONF, 2_IOA, CARE (Confederate, IOA, Caregiver)
	SessionType = "0_AC",         // Parameter: 0_AC (Actual Child), 1_SC (Simulated Child)
	EventNote = "3.0_Conf_TX_SC_TrialComplete",  // Parameter: 3.0_Conf_TX_SC_TrialComplete, 2.0_Conf_TX_BL_Start, etc.


    // Source data from Excel table
    Source = Excel.CurrentWorkbook(){[Name="Table2"]}[Content],

    // Change data types for consistency
    #"Changed Type" = Table.TransformColumnTypes(Source, {
        {"InstanceID", type text}, {"EventNote", type text}, {"DateTimeStamp", type datetimezone}, 
        {"ResponseIDx", type text}, {"CaregiverID", type text}, {"Respondent", type text}, 
        {"StudyPhase", type text}, {"SessionType", type text}, {"SessionCount", Int64.Type}, 
        {"TotalSessionTrials", Int64.Type}, {"SessionBlockCount", type number}, {"TrialDirection", type text}, 
        {"CareDirStart", type datetimezone}, {"CareDirEnd", type datetimezone}, 
        {"SelfMonitoring1", Int64.Type}, {"SelfMonitoring2", Int64.Type}, {"SelfMonitoring3", Int64.Type}, 
        {"SelfMonitoring4", Int64.Type}, {"SelfMonitoring5", Int64.Type}, {"SelfMonitoring6", Int64.Type}, 
        {"SelfMonitoring6a_1", Int64.Type}, {"SelfMonitoring6a_2", Int64.Type}, {"SelfMonitoring6a_3", Int64.Type}, 
        {"ConfResponse", type text}, {"ConfMonitoring1", Int64.Type}, {"ConfMonitoring2", Int64.Type}, 
        {"ConfMonitoring3", Int64.Type}, {"ConfMonitoring4", Int64.Type}, {"ConfMonitoring5", Int64.Type}, 
        {"ConfMonitoring6", Int64.Type}, {"ConfMonitoring6a_1", Int64.Type}, {"ConfMonitoring6a_2", Int64.Type}, 
        {"ConfMonitoring6a_3", Int64.Type}, {"ConfChildResponse", type text}, {"ConfederateInteraction", Int64.Type}, 
        {"ConfTrialNote", type text}, {"ConfSessionNote", type text}, {"IOAVideoName", type any}, 
        {"IOADirStart", type any}, {"IOADirEnd", type any}, {"IOAMonitoring1", type any}, 
        {"IOAMonitoring2", type any}, {"IOAMonitoring3", type any}, {"IOAMonitoring4", type any}, 
        {"IOAMonitoring5", type any}, {"IOAMonitoring6", type any}, {"IOAMonitoring6a_1", type any}, 
        {"IOAMonitoring6a_2", type any}, {"IOAMonitoring6a_3", type any}, {"IOAResponse", type any}, 
        {"IOAChildResponse", type any}, {"IOAConfederateInteraction", type any}, {"IOATrialNote", type any}, 
        {"IOASessionNote", type any}}),

    // Apply filtering for CaregiverID, Respondent, SessionType, and EventNote using parameters
    #"Filtered Rows" = Table.SelectRows(#"Changed Type", each 
        ([CaregiverID] = CaregiverID) and 
        ([Respondent] = Respondent) and 
        ([SessionType] = SessionType) and 
        ([EventNote] = EventNote)
    ),

    // Remove unnecessary columns, keeping only relevant ones
    #"Removed Other Columns" = Table.SelectColumns(#"Filtered Rows", {
        "InstanceID", "EventNote", "DateTimeStamp", "ResponseIDx", "CaregiverID", "Respondent", 
        "StudyPhase", "SessionType", "SessionCount", "TotalSessionTrials", "SessionBlockCount", 
        "ConfMonitoring1", "ConfMonitoring2", "ConfMonitoring3", "ConfMonitoring4", "ConfMonitoring5", 
        "ConfMonitoring6a_1", "ConfMonitoring6a_2", "ConfMonitoring6a_3", "ConfChildResponse", 
        "ConfederateInteraction", "ConfTrialNote"
    }),

    // Add a custom column for T1 average (ConfMonitoring1, 2, 6a_1, 6a_2, 6a_3)
    #"Added Custom" = Table.AddColumn(#"Removed Other Columns", "T1_Average", each 
        ([ConfMonitoring1] + [ConfMonitoring2] + [ConfMonitoring6a_1] + [ConfMonitoring6a_2] + [ConfMonitoring6a_3]) / 5
    ),

    // Add a custom column for T2 average (ConfMonitoring3, 4, 5)
    #"Added Custom1" = Table.AddColumn(#"Added Custom", "T2_Average", each 
        ([ConfMonitoring3] + [ConfMonitoring4] + [ConfMonitoring5]) / 3
    ),

    // Add a custom column for AllConfMonitoring average (all ConfMonitoring columns)
    #"Added Custom2" = Table.AddColumn(#"Added Custom1", "AllConfMonitoring_Average", each 
        ([ConfMonitoring1] + [ConfMonitoring2] + [ConfMonitoring3] + [ConfMonitoring4] + [ConfMonitoring5] + 
        [ConfMonitoring6a_1] + [ConfMonitoring6a_2] + [ConfMonitoring6a_3]) / 8
    )

in
    #"Added Custom2"
```

#### **Steps Breakdown:**

##### 1. **Defining Parameters:**
The following parameters are defined at the beginning of the query to allow for dynamic filtering. These parameters can be changed at runtime to accommodate different data sets:

```go
CaregiverID = "Case1",        // Parameter: Case1, Case2, Case3, Case4
Respondent = "1_CONF",        // Parameter: 1_CONF, 2_IOA, CARE (Confederate, IOA, Caregiver)
SessionType = "0_AC",         // Parameter: 0_AC (Actual Child), 1_SC (Simulated Child)
EventNote = "3.0_Conf_TX_SC_TrialComplete"  // Parameter: 3.0_Conf_TX_SC_TrialComplete, 2.0_Conf_TX_BL_Start, etc.
```

- **CaregiverID**: Allows selecting specific caregivers, such as Case1, Case2, etc.
- **Respondent**: Defines the respondent, e.g., `1_CONF` for Confederate, `CARE` for Caregiver, or `2_IOA` for IOA.
- **SessionType**: Distinguishes between Actual Child (0_AC) and Simulated Child (1_SC) session types.
- **EventNote**: Specifies trial events, such as `3.0_Conf_TX_SC_TrialComplete` or others based on the dataset.

##### 2. **Source Data and Type Conversion:**
The query pulls data from an Excel table named `"Table2"` and applies type transformations to ensure consistency across the dataset.

```go
Source = Excel.CurrentWorkbook(){[Name="Table2"]}[Content],
#"Changed Type" = Table.TransformColumnTypes(Source, {
    {"InstanceID", type text}, {"EventNote", type text}, {"DateTimeStamp", type datetimezone}, 
    {"ResponseIDx", type text}, {"CaregiverID", type text}, {"Respondent", type text}, 
    {"StudyPhase", type text}, {"SessionType", type text}, {"SessionCount", Int64.Type}, 
    {"TotalSessionTrials", Int64.Type}, {"SessionBlockCount", type number}, {"ConfMonitoring1", Int64.Type}, 
    {"ConfMonitoring2", Int64.Type}, {"ConfMonitoring3", Int64.Type}, {"ConfMonitoring4", Int64.Type}, 
    {"ConfMonitoring5", Int64.Type}, {"ConfMonitoring6a_1", Int64.Type}, {"ConfMonitoring6a_2", Int64.Type}, 
    {"ConfMonitoring6a_3", Int64.Type}, {"ConfChildResponse", type text}, {"ConfederateInteraction", Int64.Type}, 
    {"ConfTrialNote", type text}, {"ConfSessionNote", type text}})
```
This step ensures proper data types are applied (e.g., text for IDs, integers for monitoring columns, and datetime for timestamps).

##### 3. **Filtering Rows Using Parameters:**
Rows are filtered based on the defined parameters. This ensures that only rows matching the selected `CaregiverID`, `Respondent`, `SessionType`, and `EventNote` are processed further.

```go
#"Filtered Rows" = Table.SelectRows(#"Changed Type", each 
    ([CaregiverID] = CaregiverID) and 
    ([Respondent] = Respondent) and 
    ([SessionType] = SessionType) and 
    ([EventNote] = EventNote)
)
```

##### 4. **Selecting Relevant Columns:**
Unnecessary columns are removed, and only the relevant ones are retained. This reduces the data load and prepares the data for the next steps.

```go
#"Removed Other Columns" = Table.SelectColumns(#"Filtered Rows", {
    "InstanceID", "EventNote", "DateTimeStamp", "ResponseIDx", "

```m
"CaregiverID", "Respondent", "StudyPhase", "SessionType", "SessionCount", "TotalSessionTrials", 
    "SessionBlockCount", "ConfMonitoring1", "ConfMonitoring2", "ConfMonitoring3", "ConfMonitoring4", 
    "ConfMonitoring5", "ConfMonitoring6a_1", "ConfMonitoring6a_2", "ConfMonitoring6a_3", 
    "ConfChildResponse", "ConfederateInteraction", "ConfTrialNote"
})
```
Only the essential columns, including **ConfMonitoring** items and other metadata, are kept for further analysis.

##### 5. **Adding Custom Columns for Average Calculations:**
Custom columns are added to compute the averages for **T1**, **T2**, and **AllConfMonitoring** based on the relevant monitoring items.

- **T1 Average**:
   ```go
   #"Added Custom" = Table.AddColumn(#"Removed Other Columns", "T1_Average", each 
   ([ConfMonitoring1] + [ConfMonitoring2] + [ConfMonitoring6a_1] + [ConfMonitoring6a_2] + [ConfMonitoring6a_3]) / 5)
   ```
   This calculates the average of **ConfMonitoring1**, **ConfMonitoring2**, **ConfMonitoring6a_1**, **ConfMonitoring6a_2**, and **ConfMonitoring6a_3**.

- **T2 Average**:
   ```go
   #"Added Custom1" = Table.AddColumn(#"Added Custom", "T2_Average", each 
   ([ConfMonitoring3] + [ConfMonitoring4] + [ConfMonitoring5]) / 3)
   ```
   This calculates the average of **ConfMonitoring3**, **ConfMonitoring4**, and **ConfMonitoring5**.

- **AllConfMonitoring Average**:
   ```go
   #"Added Custom2" = Table.AddColumn(#"Added Custom1", "AllConfMonitoring_Average", each 
   ([ConfMonitoring1] + [ConfMonitoring2] + [ConfMonitoring3] + [ConfMonitoring4] + [ConfMonitoring5] + 
   [ConfMonitoring6a_1] + [ConfMonitoring6a_2] + [ConfMonitoring6a_3]) / 8)
   ```
   This calculates the average of all eight **ConfMonitoring** columns.


#### **Summary:**

This Power Query code:
- **Defines parameters** for flexible filtering.
- **Filters the data** based on `CaregiverID`, `Respondent`, `SessionType`, and `EventNote`.
- **Selects relevant columns** for analysis.
- **Calculates averages** for T1, T2, and all ConfMonitoring items.


### Simulated Child Confederate Observations Power Query Script



#### Script Overview:
This Power Query script processes trial data for a study, specifically focusing on simulated caregiver trials. It groups trials into blocks of two and calculates scores for each block based on a set of monitoring variables (ConfMonitoring1 to ConfMonitoring6a_3). The script then computes averages for these monitoring scores (T1, T2, and overall averages). The processed data includes information such as session number, study phase, caregiver ID, and the timestamp of the second trial in each block.


### Key Components and Process Steps:

#### 1. **Parameter Definition:**
The script starts by defining key parameters:
- **CaregiverID**: Select the relevant participant ID (e.g., "Case1").
- **Respondent**: Defines whether the trial is related to the confederate, IOA, or caregiver (e.g., "1_CONF").
- **SessionType**: Specifies whether the trial involves a simulated child or an actual child (e.g., "1_SC").
- **EventNote**: Defines the event note for filtering the trial (e.g., "3.0_Conf_TX_SC_TrialComplete").


#### 2. **Data Loading and Type Consistency:**
The raw data is loaded from the Excel workbook and the data types are converted for consistency, ensuring that numeric columns and date-time columns are in the correct format. This step ensures that all monitoring variables, timestamps, and key columns such as `CaregiverID`, `SessionCount`, and `DateTimeStamp` are appropriately typed.

```go
Source = Excel.CurrentWorkbook(){[Name="Table2"]}[Content],
#"Changed Type" = Table.TransformColumnTypes(Source, { ... })
```


#### 3. **Filtering Data:**
The script filters the dataset based on the defined parameters (CaregiverID, Respondent, SessionType, and EventNote). This step ensures that only the relevant data is processed for the specific trial type.

```go
#"Filtered Rows" = Table.SelectRows(#"Changed Type", each 
    ([CaregiverID] = CaregiverID) and 
    ([Respondent] = Respondent) and
    ([EventNote] = EventNote) and
    ([SessionType] = SessionType)
)
```


#### 4. **Sorting and Indexing:**
The data is sorted by `DateTimeStamp` to ensure that the trials are in chronological order. An index column is added to number the trials sequentially.

```go
#"Sorted Rows" = Table.Sort(#"Filtered Rows",{{"DateTimeStamp", Order.Ascending}}),
#"Added Index" = Table.AddIndexColumn(#"Sorted Rows", "Index", 1, 1, Int64.Type),
```


#### 5. **Grouping Trials into Blocks:**
Trials are grouped into blocks of two based on the index, where every two trials are placed into a unique `TrialBlockGroup`. This ensures that each block of trials is treated as a unit for scoring purposes.

```go
#"Added TrialBlockGroup" = Table.AddColumn(#"Added Index", "TrialBlockGroup", each Number.IntegerDivide([Index] - 1, 2) + 1),
```


#### 6. **Computing Trial Block Scores:**
For each block, the script computes scores for each `ConfMonitoring` variable. A score of `1` is assigned if both trials in the block have a value of `1` for a given monitoring variable, otherwise, the score is `0`. If a trial is missing, the score defaults to `0`.

Additional information such as `SessionNumber`, `StudyPhase`, `CaregiverID`, and `DateTimeStamp` (from Trial 2) is also included in the output.

```go
#"Added Custom" = Table.AddColumn(#"GroupedTBRows", "TrialBlockScore", each
    let 
        TrialRows = [ComputedTrialBlockSubTable],
        Trial1 = if Table.RowCount(TrialRows) > 0 then TrialRows{0} else null,
        Trial2 = if Table.RowCount(TrialRows) > 1 then TrialRows{1} else null,

        // Compute scores for ConfMonitoring1 - ConfMonitoring6a_3
        TB_ConfMonitoring1 = if (Trial1[ConfMonitoring1] = 1 and Trial2[ConfMonitoring1] = 1) then 1 else 0,
        ...
        TB_ConfMonitoring6a_3 = if (Trial1[ConfMonitoring6a_3] = 1 and Trial2[ConfMonitoring6a_3] = 1) then 1 else 0,

        // Extract additional fields from Trial2
        SessionNumber = if Trial2 <> null then Trial2[SessionCount] else null,
        StudyPhase = if Trial2 <> null then Trial2[StudyPhase] else null,
        CaregiverID = if Trial2 <> null then Trial2[CaregiverID] else null,
        DateTimeStamp = if Trial2 <> null then Trial2[DateTimeStamp] else null
    in
        [
            SessionNumber = SessionNumber,
            StudyPhase = StudyPhase,
            CaregiverID = CaregiverID,
            DateTimeStamp = DateTimeStamp,
            TB_ConfMonitoring1 = TB_ConfMonitoring1,
            TB_ConfMonitoring2 = TB_ConfMonitoring2,
            ...
            TB_ConfMonitoring6a_3 = TB_ConfMonitoring6a_3
        ]
),
```


#### 7. **Expanding and Cleaning Data:**
The computed trial block scores and additional fields from Trial 2 are expanded into separate columns. The intermediate column (`ComputedTrialBlockSubTable`) is removed after the expansion to keep the table clean.

```go
#"Expanded TrialBlockScore" = Table.ExpandRecordColumn(#"Added Custom", "TrialBlockScore", { ... }),
#"Removed Columns" = Table.RemoveColumns(#"Expanded TrialBlockScore", {"ComputedTrialBlockSubTable"}),
```

---

#### 8. **Calculating Averages:**
The script calculates three averages:
- **T1_Average**: The average score for `TB_ConfMonitoring1`, `TB_ConfMonitoring2`, `TB_ConfMonitoring6a_1`, `TB_ConfMonitoring6a_2`, and `TB_ConfMonitoring6a_3`.
- **T2_Average**: The average score for `TB_ConfMonitoring3`, `TB_ConfMonitoring4`, and `TB_ConfMonitoring5`.
- **AllConfMonitoring_Average**: The average score for all `TB_ConfMonitoring` variables.

```go
#"Added T1_Average" = Table.AddColumn(#"Removed Columns", "T1_Average", each 
    ([TB_ConfMonitoring1] + [TB_ConfMonitoring2] + [TB_ConfMonitoring6a_1] + [TB_ConfMonitoring6a_2] + [TB_ConfMonitoring6a_3]) / 5
),
#"Added T2_Average" = Table.AddColumn(#"Added T1_Average", "T2_Average", each 
    ([TB_ConfMonitoring3] + [TB_ConfMonitoring4] + [TB_ConfMonitoring5]) / 3
),
#"Added AllConfMonitoring_Average" = Table.AddColumn(#"Added T2_Average", "AllConfMonitoring_Average", each 
    ([TB_ConfMonitoring1] + [TB_ConfMonitoring2] + [TB_ConfMonitoring3] + [TB_ConfMonitoring4] + [TB_ConfMonitoring5] + 
    [TB_ConfMonitoring6a_1] + [TB_ConfMonitoring6a_2] + [TB_ConfMonitoring6a_3]) / 8
)
```



### **Version 2 (V2) Update: Counts Calculation**

In **Version 2 (V2)** of the data transfer process, the script was updated to include additional **count-based calculations** for each monitoring group. These counts represent the sum of relevant monitoring values for each trial block group, providing a more detailed breakdown of the data. The following updates were made:

#### **1. Addition of Count Columns**:
   - **T1_Count**: A new column was added to calculate the sum of `ConfMonitoring1`, `ConfMonitoring2`, `ConfMonitoring6a_1`, `ConfMonitoring6a_2`, and `ConfMonitoring6a_3`. This column represents the **T1 Count** for each trial block group.
   
   - **T2_Count**: A column was added to calculate the sum of `ConfMonitoring3`, `ConfMonitoring4`, and `ConfMonitoring5`, representing the **T2 Count** for each trial block group.
   
   - **AllConfMonitoring_Count**: This column sums all `ConfMonitoring` variables (1 through 6a_3), providing a total **AllConfMonitoring Count** for each trial block group.

#### **2. Purpose of the Count Columns**:
   - These count columns provide insight into the total number of monitoring events across the trial blocks for each phase and session type.
   - By including these counts, we can now track both the **average** and the **sum** of monitoring events, offering more robust data for analysis in Prism.

#### **3. Data Transfer**:
   - The updated count columns were included in the final dataset transferred to **GraphPad Prism**, following the same procedure used for transferring average values.
   - These new columns were transferred into the appropriate Y-axis groups in Prism to enable visual comparisons and detailed analyses of monitoring counts across different phases and sessions.

#### **4. Query Code Update**:
   - The Power Query script was modified to include the count calculations for each monitoring group, ensuring that the count columns were correctly computed and added to the final dataset.
   - The script was tested to validate the accuracy of the count calculations and to ensure that the data was correctly processed for visualization in Prism.

   ```go

       // Add a custom column for T1 Count (TB_ConfMonitoring1, 2, 6a_1, 6a_2, 6a_3)
    #"Added T1_Count" = Table.AddColumn(#"Removed Columns", "T1_Count", each 
        ([TB_ConfMonitoring1] + [TB_ConfMonitoring2] + [TB_ConfMonitoring6a_1] + [TB_ConfMonitoring6a_2] + [TB_ConfMonitoring6a_3])
    ),

    // Add a custom column for T2 Count (TB_ConfMonitoring3, 4, 5)
    #"Added T2_Count" = Table.AddColumn(#"Added T1_Count", "T2_Count", each 
        ([TB_ConfMonitoring3] + [TB_ConfMonitoring4] + [TB_ConfMonitoring5])
    ),

    // Add a custom column for AllConfMonitoring Count (all TB_ConfMonitoring columns)
    #"Added AllConfMonitoring_Count" = Table.AddColumn(#"Added T2_Count", "AllConfMonitoring_Count", each 
        ([TB_ConfMonitoring1] + [TB_ConfMonitoring2] + [TB_ConfMonitoring3] + [TB_ConfMonitoring4] + [TB_ConfMonitoring5] + 
        [TB_ConfMonitoring6a_1] + [TB_ConfMonitoring6a_2] + [TB_ConfMonitoring6a_3])
    ),

    ```

### Final Output:
The final table contains:
- **SessionNumber, StudyPhase, CaregiverID, DateTimeStamp** (from Trial 2)
- **TB_ConfMonitoring1 - TB_ConfMonitoring6a_3**: Scores for each monitoring variable.
- **T1_Average, T2_Average, AllConfMonitoring_Average, T1_Count, T2_Count, AllConfMonitoring_Count**: Calculated averages and counts for the monitoring variables.


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



#### **Steps for Data Transfer and Plotting in GraphPad Prism**:

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
