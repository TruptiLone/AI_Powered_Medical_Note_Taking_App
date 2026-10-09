# Proposed documentation lifecycle

[Architecture](../architecture.md) · [Original diagrams](README.md)

This is a **portfolio refinement** of the academic visit state model. It makes manual documentation and processing failures explicit; it does not represent an implemented state machine.

```mermaid
stateDiagram-v2
    [*] --> VisitCreated
    VisitCreated --> ConsentPending
    ConsentPending --> Recording: Consent granted
    ConsentPending --> ManualDraft: Consent declined
    Recording --> Recorded: Upload verified
    Recording --> ManualDraft: Recording fails or is stopped after withdrawal
    Recorded --> Processing: Authorized job starts
    Processing --> GeneratedDraft: Transcript and draft ready
    Processing --> ProcessingFailed: Speech or generation failure
    ProcessingFailed --> Processing: Authorized retry
    ProcessingFailed --> ManualDraft: Clinician continues manually
    GeneratedDraft --> Review: Clinician opens current version
    ManualDraft --> Review: Clinician opens manual note
    Review --> Review: Edit and save draft
    Review --> Final: Explicit approval of reviewed version
    Final --> Addendum: Authorized correction
    Addendum --> Review: Review supplemental version
```

For readability, this view omits upload substates and individual STT/diarization/generation jobs. A detailed implementation must track those separately, including cancellation and in-flight results after consent withdrawal. Reviewing an addendum does not unlock or replace the original final note.
