# Roadmap and feasibility

[Back to the case study](../README.md)

## What the academic planning establishes

The original project includes a cost/benefit model, subsystem estimates, a work breakdown structure, a dependency network, and an iteration plan. These demonstrate planning exercises. They do not establish that the listed development, clinician interviews, acceptance tests, or deployment activities occurred.

The five-iteration schedule allocates 4, 4, 5, 4, and 3 weeks, totaling **20 weeks**. A separate subsystem estimate assumes **40 weeks**, including hardening. The report also describes the WBS as approximately 19 weeks. The artifacts do not provide enough staffing and dependency detail to reconcile these into one reliable delivery commitment.

## Financial assumptions and limitations

The final report assumes **$1,175,000** development cost, **$295,000** annual operating cost, and **$1,268,000** annual benefits for a ten-doctor clinic. These are academic estimates, not incurred costs, validated market prices, revenue, or observed savings.

The benefits assume two hours saved per doctor per day and one additional patient per doctor per day. Monetized time savings and additional appointment revenue may overlap, so they should not automatically be added. Gross appointment revenue also does not equal incremental profit. Claim-denial and billing-cycle benefits need independent evidence. Vendor costs need a workload-based estimate rather than historical classroom pricing assumptions.

The four benefit lines in the report total **$1,268,000** ($720,000 + $110,000 + $150,000 + $288,000), giving **$973,000** after the assumed annual expenses. The embedded table distinguishes ROI from an approximately 78% IRR, while presentation notes call approximately 78% an ROI and describe payback differently. The working financial draft also uses different discounted values from the final table. These results are retained in the original materials but are not promoted as portfolio outcomes.

A future feasibility model should explicitly define time horizon, discounting, salary assumptions, adoption, review effort, inference volume, retention, and whether benefits represent cash savings or released capacity. Recalculate NPV and payback only after agreeing on those assumptions and reconciling the source calculations. No current pricing or investment recommendation is made here.

## Proposed path to a prototype

All phases below are future work; durations are deliberately uncommitted.

| Phase | Deliverable | Exit evidence |
| --- | --- | --- |
| 1. Establish scope and evaluation | One encounter type, agreed note structure, staged audio set, reference annotation protocol | Clinical reviewers agree on what the prototype should and should not document |
| 2. Validate speech processing | Batch STT, diarization, timestamp alignment, editable role mapping | Reproducible text and attribution error analysis on held-out encounters |
| 3. Validate draft generation | Evidence-linked sections and review UI | Unsupported claims, omissions, and clinician editing effort are measured |
| 4. Exercise system controls | Consent gating, versioning, retry handling, access controls, retention behavior | Recovery, stale-version, wrong-patient, and authorization scenarios pass |
| 5. Consider a controlled pilot | End-to-end workflow and operational review | Required clinical, privacy, and organizational approvals plus agreed evaluation gates |

## Potential enhancements

**EHR interoperability:** investigate an authorized integration using the target EHR’s supported interface. [HL7 FHIR](https://www.hl7.org/fhir/overview.html) is an interoperability standard worth evaluating; using it would still require patient/encounter matching, profile mapping, permissions, and reconciliation. No EHR integration is present.

**Streaming assistance:** explore interim transcripts or drafts only after the batch path is evaluated. Partial statements, changing speaker assignments, and incomplete context require explicit provisional states.

**Specialty and multilingual workflows:** evaluate distinct templates and language coverage with suitable clinical reviewers. Do not assume accuracy transfers between specialties or languages.

**Operational dashboards:** derive authorized summaries from approved records, with data lineage and correction propagation. Aggregation does not by itself make data anonymous.

**Provider comparison:** compare managed services and self-hosted options on the same reference set. Treat deployment overhead, data governance, and failure recovery as part of the tradeoff alongside model quality.
