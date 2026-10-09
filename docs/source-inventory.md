# Source inventory and provenance

[Back to the case study](../README.md)

## Evidence boundary

The review covered all **22 files** supplied in the project folder: DOCX documents, PPTX decks, PDFs, and standalone PNGs, including embedded diagrams and wireframes. The source folder was not a Git checkout. The existing GitHub repository contained a short README and no implementation. The original local files were left unchanged.

The final report is the primary source for the academic proposal. New Markdown documents organize and critically examine it. The detailed service architecture, role-mapping flow, source-linked LLM output, reliability invariants, risk register, and evaluation protocol are **portfolio refinements**, not claims of original implementation or tested results.

## Reviewed files and disposition

All source files are accounted for below. Selected evidence is published; drafts, template-heavy decks, the unrelated proposal, and edit-invitation links remain local. [SHA-256 manifest](source-manifest.json) records original file hashes and repository destinations.

| Original source path | Portfolio destination or disposition |
| --- | --- |
| `Diagram Links.docx` | Local only: Lucidchart editing/invitation links; publish static diagrams instead of access-grant links. |
| `Draft Presentation.pptx` | Local only: early eight-slide summary; superseded by final report. |
| `Final Medical Note-taking Application Project Report.docx` | [docs/originals/final-project-report.docx](originals/final-project-report.docx) |
| `Final Project.pdf` | Local only: assignment brief, not the project report. |
| `Gnatt chart ref for iteration 1.docx` | Local only: working planning reference; includes 21-day versus four-week discrepancy. |
| `Gnatt chart reference.docx` | Local only: detailed working iteration/task reference; final report retained. |
| `Group 2_ AI-Powered Medical Note Taking App.pptx` | Local only: 58-slide deck with substantial template/sample material. |
| `ISAD Project Activity Diagram.png` | [docs/diagrams/originals/consultation-activity.png](diagrams/originals/consultation-activity.png) |
| `ISAD Project proposal 2.docx` | [docs/originals/medical-app-proposal.docx](originals/medical-app-proposal.docx) |
| `ISAD Project proposal.docx` | Local only: unrelated EngageTrack student-engagement proposal despite filename. |
| `Modified Diagrams.docx` | [docs/originals/workflow-descriptions.docx](originals/workflow-descriptions.docx) |
| `Part 2.docx` | Local only: working requirements/UML drafting notes; final report retained. |
| `Part 3 cost benefit analysis.docx` | Local only: working financial assumptions and drafting notes; discrepancies discussed in roadmap. |
| `Presentation/Group 2_ AI-Powered Medical Note Taking App.pptx.pdf` | Local only: 68-page presentation export with project pages and extensive template material; not a PDF of the final report. |
| `Presentation/Group 2_ AI-Powered Medical Note Taking App.pptx.pptx` | Local only: 17-slide academic presentation; report and extracted original diagrams provide the curated evidence. |
| `Project Iteration Schedule.docx` | [docs/originals/iteration-schedule.docx](originals/iteration-schedule.docx) |
| `Project Tasks.docx` | Local only: two early meeting/planning reminders. |
| `Project Use Case diagram (1).png` | [docs/diagrams/originals/use-cases.png](diagrams/originals/use-cases.png) |
| `Project network diagram.docx` | [docs/originals/project-network.docx](originals/project-network.docx) |
| `Reference for Domain model class diagram.docx` | [docs/originals/domain-model-notes.docx](originals/domain-model-notes.docx) |
| `SSD Diagram.png` | [docs/diagrams/originals/system-sequence.png](diagrams/originals/system-sequence.png) |
| `Untitled document.docx` | Local only: early idea/discussion message, not evidence of implementation. |

## Issues retained transparently

- **Scope:** build, test, and deployment tasks in planning documents are future activities. No code, transcripts from a working pipeline, trained models, or evaluation results were supplied.
- **Attribution:** the final report identifies seven team members, including Trupti Lone, but does not establish individual ownership of deliverables.
- **Identifiers:** the report repeats US-13 and a use-case number. The case study uses descriptive names and its own R1–R9 traceability labels.
- **Consent:** ambiguous false-consent wording in the original sequence diagram conflicts with the written no-recording requirement. The new flow follows the written requirement.
- **Schedule:** 20-week iteration planning, a 40-week subsystem estimate, and an approximately 19-week WBS statement are not reconciled by the sources.
- **Benefits:** documentation-time percentages, accuracy improvements, time savings, and financial outcomes are not validated. They are not presented as achieved outcomes.
- **Financial interpretation:** the final table, working financial draft, and presentation notes differ in discounted values and in how they describe ROI, IRR, and payback. See the feasibility review.
- **Wireframes:** UI content does not prove calibrated confidence, clinical correctness, data deletion, or EHR functionality.

## Figure provenance

Standalone diagrams retain their bytes. Extracted figures retain their embedded image bytes. The [diagram guide](diagrams/README.md) identifies their source documents. Wireframes come from the final report: image7 (dashboard), image10 (consent), image3 (recording), image5 (review), image11 (directory), and image2 (profile). These are existing academic designs, not newly fabricated screens.

## External references used for new analysis

These sources inform the portfolio refinements and are not represented as citations from the original coursework:

- [pyannoteAI: diarization versus recognition and identification](https://www.pyannote.ai/blog/speaker-diarization-vs-recognition-vs-identification), for distinguishing anonymous speaker turns from identity.
- [HHS: HIPAA and cloud computing](https://www.hhs.gov/hipaa/for-professionals/special-topics/health-information-technology/cloud-computing/index.html), for cloud-provider and ePHI considerations.
- [HL7 FHIR overview](https://www.hl7.org/fhir/overview.html), for future interoperability exploration.

References reviewed October 2026. They do not establish vendor selection, clinical performance, or compliance of this proposal.
