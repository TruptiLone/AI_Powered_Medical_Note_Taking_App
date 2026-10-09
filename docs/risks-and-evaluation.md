# Healthcare risks and evaluation plan

[Back to the case study](../README.md)

**Status:** proposed risk controls and evaluation. No experiments, clinical pilot, compliance assessment, or security implementation are present.

## Risks that determine the design

| Risk | Example | Proposed control | Evidence to collect |
| --- | --- | --- | --- |
| Incorrect transcription | A medication name, number, unit, or negation changes | Source-linked review and targeted flags | Word errors plus separate clinically significant error counts |
| Wrong speaker role | A caregiver’s statement becomes the patient’s history | Role confirmation and unknown-speaker handling | Diarization errors and statement-attribution accuracy |
| Unsupported generation | Draft adds an examination finding never discussed | Constrained sections, missing-value handling, clinician approval | Expert review of unsupported and contradicted claims |
| Omission | A stated follow-up action is absent | Compare critical facts and actions with references | Critical-fact recall and omission severity |
| Historical context contamination | An old medication appears as current | Label historical inputs and surface conflicts | Review across encounters with changed history |
| Consent failure | Capture begins despite declined consent | Server checks plus client capture gating | Consent-state and revocation scenarios |
| Wrong-patient association | A delayed job writes to another encounter | Immutable visit/input IDs and authorization checks | Cross-patient, concurrent-session, and callback tests |
| Privacy exposure | Raw audio or text enters application logs | Minimal logs, scoped retrieval, retention policy | Access-control, log-content, and deletion verification |
| Automation bias | Reviewer accepts a plausible incorrect draft | Show evidence and require explicit approval | Review behavior and residual errors after approval |
| Availability failure | A model provider or upload fails | Bounded retries and manual documentation | Fault injection and recovery measurements |

## Privacy and access design

The proposal would process sensitive audio, transcripts, and clinical notes. Proposed controls include encryption in transit and at rest, organization-scoped authorization, least-privilege access, auditable changes, and separate retention policies for audio and finalized documentation. Provider retention, training use, subprocessors, and data location would need review before sending clinical data.

For a US deployment subject to HIPAA, using a cloud service requires more than choosing encryption or displaying a compliance badge. HHS explains the role of business associate agreements and risk analysis when cloud providers process ePHI. This project makes no compliance claim. See [HHS guidance on cloud computing](https://www.hhs.gov/hipaa/for-professionals/special-topics/health-information-technology/cloud-computing/index.html).

The academic consent screen promises deletion after transcription and physician review. A future implementation must reconcile that promise with audio playback, failed jobs, provider copies, backups, and retention requirements. No deletion policy or retention duration has been validated. Recording-consent requirements also need review for the intended jurisdiction and clinical workflow.

## Proposed evaluation protocol

Start with staged or synthetic encounters whose use is authorized. Define reference transcripts, time-aligned speakers, confirmed roles, and clinician-reviewed reference facts. Use separate development and held-out evaluation encounters. Freeze model, configuration, and prompt versions for each comparison. The supplied UI examples are not an evaluation dataset.

| Layer | Proposed measurement | Interpretation and limits |
| --- | --- | --- |
| Speech recognition | Word error rate: substitutions + deletions + insertions, divided by reference words | Report normalization rules; aggregate WER can hide clinically important errors |
| Speaker diarization | Missed speech, false speech, and speaker-confusion time relative to reference speaker time | Specify overlap handling and boundary tolerance; also measure role-mapping errors |
| Clinical draft | Supported statement precision, critical-fact recall, unsupported statements, contradictions, attribution errors | Use explicit annotation rules and independent clinical reviewers with adjudication |
| Review workflow | Time to approved note, edit burden, residual serious errors, clinician feedback | Compare against manual documentation on equivalent tasks; include review time |
| System behavior | End-to-end p50/p95 latency, job failure/retry rates, duplicate jobs, stale drafts | Define timing start/end and workload before reporting results |
| Cost | Cost per encounter and per approved note | Include audio duration, tokens, retries, storage, and review effort |

Stratify results by audio conditions, encounter length, speaker count, and relevant language/accent coverage where collection is appropriate. Report sample counts and uncertainty. Avoid presenting an overall score as proof of equal performance across groups.

## Release gates to define before a pilot

A future team should agree on thresholds with clinical stakeholders before looking at held-out results. No numerical acceptance thresholds or achieved scores are claimed here.

At minimum, demonstrate that denied consent prevents capture, unauthorized users cannot retrieve another patient’s artifacts, failures preserve a manual route, and an automated response cannot finalize a note. Resolve serious error cases, review access and retention behavior, and confirm that total clinician effort improves without unacceptable residual errors. A controlled clinical pilot would require additional organizational, privacy, and clinical review.
