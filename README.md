# Lab Decommissioning Notification & Verification Form

This repository contains a single-page browser application for completing a laboratory decommissioning form based on the Appendix F "Lab Decommissioning Notification & Verification Form" workflow.

## What this project does

The app helps users:

- record laboratory or workshop decommissioning details
- complete a checklist of safety, compliance, and operational actions
- flag items as Yes, No, or N/A
- capture follow-up actions and due dates
- review missing responses and warnings before export
- save and restore drafts locally
- print/export a PDF-friendly report for sign-off

## Repository contents

- `index.html` — the complete application, including HTML, CSS, and JavaScript
- `README.md` — project overview and usage notes
- `NOTES.md` — deeper implementation notes for maintainers

## Quick start

Because this is a static HTML application, there is no build step or package installation required.

1. Open `index.html` in a modern web browser, or
2. Serve the folder locally via a simple web server:

```bash
cd labdecommissioning
python -m http.server 8000
```

Then visit:

```text
http://localhost:8000/
```

## Key features

- structured decommissioning checklist by section
- applicability toggles for sections marked Not Applicable
- action tracking for items marked "No"
- draft save/load using JSON export/import
- browser-side recovery draft storage
- printable A4 report generation
- review summary before final PDF export

## Typical user flow

1. Enter site and contact information.
2. Answer the decommissioning checklist.
3. Add follow-up actions where required.
4. Review warnings and missing details.
5. Download or print the final form as a PDF.

## Notes

### Shared form experience

The interface follows the lab commissioning form: required details and conditional additional information are checked beside their fields, review warnings appear in one screen, navigation follows the current section, and mobile controls remain compact. Checklist wording, supporting-document requirements, decommissioning-type selection and references 1–19 and E1–E8 are retained.

Follow-up actions include Open, Overdue and Completed filters, linked question wording, return-to-question links and inline checks for descriptions, owners and target dates. Completed actions are hidden from the default Open view.

Expand Calendar reminders to choose open actions and download an `.ics` file. The default entry is 09:00 Singapore time on the target date with a reminder one day before. Past reminder times are flagged before download. Import the file into the intended calendar to activate reminders; no emails or invitations are sent. Completed actions are excluded. Imported events are copies and do not update automatically when actions change or close. Re-importing may create duplicates.

Older decommissioning JSON drafts remain compatible. Calendar identities are retained in new drafts; temporary export selection and acknowledgement controls are not saved. Device recovery is separate from a downloaded draft backup.

Print output uses A4 pagination with repeated headers and page numbers. It includes all questions required by the selected decommissioning type, supporting references and clearly labelled draft status. Long comments use full-width rows, and supervisor confirmation and verification follow the action table together. Export timestamps use Singapore time.

- The application is browser-based and stores data in the client browser for draft recovery.
- It does not require a backend or database.
- This is intended as a local operational form/tool rather than a server-hosted application.
- For UI or form wording changes, most of the content is defined within the JavaScript data structures in `index.html`.

## License

No explicit license file is present in this repository at this time.

## Purpose summary

This project is designed to support safe and compliant shutdown of labs/workshops by documenting actions, hazards, verification, and approval steps in a structured and printable format.

Biological scope supports multiple categories: Biosafety (BSL1–3), Animal Biosafety (ABSL1–3), Arthropods (ACL1–2) and Plant House (GM BSL1–2), each with an Others option. Selections describe activities covered during occupancy. None excludes the section while retaining containment levels, answers and evidence. Older BSL-only drafts migrate to the Biosafety category. Category and containment summaries appear in print. The existing shared decommissioning questions remain unchanged.

Radiation scope uses the same choices as lab commissioning: radioactive materials, ionising radiation equipment, lasers, MRI, and None. Multiple source types may be selected. Draft and print output retain the selections. Older drafts with only a combined radiation scope retain their answers and evidence but ask the user to identify the actual source types. The existing decommissioning questions are unchanged.

### Scope mapping and exclusions

Scope controls remain visible under the No and Unanswered filters. Choosing None applies NA without a confirmation dialog; existing answers are retained in the applicability snapshot and restored when the scope is selected again.

Radiation question 15 maps to radioactive materials. Questions 16–17 remain shared across the selected sources or systems. Questions 18–19 remain available for radioactive materials and ionising equipment; users may mark an individual check NA where appropriate. Source-excluded questions are omitted from on-screen response totals, but retained in print as NA with an explanation and any previous response or evidence. The original questions do not constitute dedicated laser or MRI shutdown procedures; specialist closure documentation should accompany the record. Biological questions 6–9 are shared checks across the selected categories, with category coverage identified in the supporting details.

The review and printed scope summaries identify included and excluded sections, question ranges and the basis for exclusion. Equipment-only records explicitly state why laboratory-closure questions 1–19 are omitted. Original checklist wording and numbering remain unchanged.

### Optional drawn signatures

Academic Supervisors and verifiers can draw a signature using a mouse, touch screen or stylus. Each drawing is confirmed with a name and signing date. Clear drawing and Cancel do not alter an existing signature; Draw again replaces it only after Use signature is selected. Users may instead sign an exported PDF or printed copy.

The single HTML file generates signature images locally from stored drawing coordinates. Downloaded JSON drafts and device recovery include the drawings and signing details; PDFs include the signature images and capture timestamps. Older unsigned drafts remain compatible. A drawn signature is not identity verification, a certificate-based digital signature or tamper protection. Signed drafts and PDFs contain signatures and should be handled accordingly.

Changes to the recorded details, scope, answers, evidence or actions clear both signatures and display a warning. Verifier signing details affect only the verifier signature. Adding a verifier signature preserves the supervisor signature. Replacing or removing the supervisor signature clears the verifier signature. Calendar reminder settings, calendar export references and screen navigation do not invalidate signatures. Imported signatures that do not match the restored record are cleared for review and re-signing; these checks prevent accidental reuse and do not authenticate the signer.
