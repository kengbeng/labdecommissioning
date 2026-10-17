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

- The application is browser-based and stores data in the client browser for draft recovery.
- It does not require a backend or database.
- This is intended as a local operational form/tool rather than a server-hosted application.
- For UI or form wording changes, most of the content is defined within the JavaScript data structures in `index.html`.

## License

No explicit license file is present in this repository at this time.

## Purpose summary

This project is designed to support safe and compliant shutdown of labs/workshops by documenting actions, hazards, verification, and approval steps in a structured and printable format.
