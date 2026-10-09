# Requirements and clinical use cases

[Back to the case study](../README.md)

**Basis:** final academic report, Steps 1.2, 2.1, and 2.2. The acceptance scenarios below are proposed validation criteria, not executed tests. Labels R1–R9 organize this case study and do not replace identifiers in the original files.

## Actors and boundaries

- **Clinician:** reviews history, opens a visit, captures a consented consultation, edits drafts, and approves the record.
- **Patient:** grants or declines recording consent and receives an authorized visit summary.
- **Clinic administrator:** maintains demographics and accesses summaries within a defined administrative role.

The target experience is a mobile clinical workflow. The assignment calls for multiple mobile platforms; the repository contains interface concepts rather than mobile application code. An encounter, its participants, and its documentation must stay associated throughout processing.

## Requirements traceability

| ID | Proposed requirement | Academic source | Acceptance scenario to implement later |
| --- | --- | --- | --- |
| R1 | Display patient history and create a visit | US-01; View Patient Profile; Start Visit Session | Selecting a different patient cannot reuse the previous patient’s recording or draft |
| R2 | Require consent before recording | Patient consent story; Provide Recording Consent | Declined or missing consent blocks recording and offers manual documentation |
| R3 | Capture and associate consultation audio | US-02; Record Consultation | Failed upload cannot display a successful-save confirmation |
| R4 | Transcribe and separate speakers | US-03–04 | Speaker ambiguity remains visible and can be corrected |
| R5 | Generate distinct patient and clinician sections | US-05–06 | Patient-reported symptoms do not become a clinician diagnosis without source evidence |
| R6 | Edit and approve notes | US-09; Review & Edit Notes | A model response alone cannot move a note to Final |
| R7 | Add typed notes and voice narration | US-07–08 | Supplemental input is attributed to the clinician and linked to the same visit |
| R8 | Search history and inspect dashboard summaries | US-10; Search Past Visits | Results respect the user’s access and distinguish draft from final documentation |
| R9 | Maintain demographics and share summaries | US-11–12; patient summary story | Administrators and patients see only the records and fields authorized for them |

The final report repeats US-13 for consent and patient summaries and repeats a use-case number. This document references the story names rather than silently renumbering the original evidence.

## Main clinical workflow

Before recording, the clinician confirms the patient and active visit, checks the microphone, and records the consent decision. While recording, the interface should show an unambiguous recording indicator and stop control. After successful upload, the system would create a transcript and a structured draft. The clinician would review patient narrative separately from assessment and plan, edit any section, and choose Save Draft or Finalize.

The original report defines finalized notes as read-only, with subsequent corrections handled by an addendum. It also describes missing microphones, denied permissions, save failures, crash recovery, and a possible recording-duration limit. These are requirements, not working exception handlers.

## Scenarios that shape the architecture

**Routine follow-up:** earlier medications and allergies are available for context, but the current visit may change them. The proposed refinement keeps historical context labeled so it cannot silently override the new encounter.

**Caregiver or interpreter present:** more than two voices may be audible. A proposed role-mapping step allows additional or unknown roles instead of assigning every segment to doctor or patient.

**Post-visit dictation:** clinician narration supplements the visit. It should not be presented as something the patient said during the encounter.

**Consent declined or processing unavailable:** the clinician can document manually and finalize after review. Consent withdrawal during recording and cancellation of queued processing require additional policy and design work.

## Out of scope for this repository

Autonomous medical decisions, prescribing, billing-code automation, live EHR synchronization, patient monitoring, and deployed analytics are not delivered capabilities. The clinical content shown in the wireframes is interface example material, not a model evaluation dataset.
