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

## Table Naming Convention:

```plaintext
<CaseID or GroupDescription>_<SessionType>_<StudyPhase>_<Respondent>_<Version>
```

### Components Breakdown:
1. **CaseID or GroupDescription**: 
   - Either a specific case ID (e.g., **Case1**, **Case2**) or a group descriptor (e.g., **AllCases**, **BaselineGroup**).
   
2. **SessionType**: 
   - **AC**: Actual Child trials.
   - **SC**: Simulated Child trials.
   
3. **StudyPhase**:
   - **BL**: Baseline.
   - **T1**, **T2**, **T3**, **T4**: Training Phases 1 to 4.
   - **RTB**: Reversal to Baseline.

4. **Respondent**:
   - **CARE**: Caregiver.
   - **CONF**: Confederate.
   - **IOA**: Interobserver Agreement.
   
5. **Version**: 
   - **V1**, **V2**, etc., for different versions of the table.

### Example Table Names:

1. **All Actual Child Trials for Case 1 (Caregiver as Respondent)**:
   - `Case1_AC_ALL_CARE_V1`: All actual child trials for **Case 1**, **AC** session type, across all phases, with **Caregiver (CARE)** as the respondent, version 1.

2. **Simulated Child Trials for Training Phase 2 (T2) for Case 1 (Confederate as Respondent)**:
   - `Case1_SC_T2_CONF_V1`: Simulated child trials for **Case 1**, in **SC** session type, during **T2** (Training Phase 2), with **Confederate (CONF)** as the respondent, version 1.

3. **All Trials for Baseline Phase (BL) Across All Respondents**:
   - `Case1_ALL_BL_AllRespondents_V1`: All trials during the **Baseline phase (BL)** for **Case 1**, across all session types and respondents, version 1.

4. **Actual Child Trials for All Cases in Training Phases**:
   - `AllCases_AC_ALL_AllRespondents_V1`: Aggregated table of **all actual child trials** for all cases, across all phases and respondents, version 1.

5. **Simulated Child Trials for Reversal to Baseline Phase (RTB) for IOA Respondent**:
   - `Case1_SC_RTB_IOA_V1`: Simulated child trials during the **Reversal to Baseline (RTB)** phase for **Case 1**, with **IOA** as the respondent, version 1.

### Broader Aggregated Examples:
1. **All Actual Child Trials for All Cases Across All Phases**:
   - `AllCases_AC_ALL_AllRespondents_V1`: All actual child trials for all cases, across all phases and respondents, version 1.

2. **All Records for Case 1 Across All Phases and Respondents**:
   - `Case1_ALL_ALL_AllRespondents_V1`: Aggregated table of all records for **Case 1**, across all phases and respondents, version 1.

This simplified structure retains all necessary components and makes it easier to handle and categorize tables efficiently. Let me know if you’d like to move forward with organizing or managing your data using this structure!