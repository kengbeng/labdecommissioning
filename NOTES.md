# Project Notes

## Overview

This repository contains a single-file web application used to complete and export a lab decommissioning notification and verification form. The form is based on an Appendix F style workflow and is intended to be used as a practical operational checklist for closing down a lab, workshop, or similar facility.

## File structure

- `index.html` — the main application file containing markup, styles, and application logic
- `README.md` — user-facing documentation
- `NOTES.md` — implementation notes for maintainers

## Application purpose

The app supports the following workflow:

- collection of site and user details
- completion of decommissioning safety and compliance checks
- applicability handling with N/A section support
- action tracking for unresolved issues
- review of checklist completion
- PDF-friendly report generation
- local draft saving and browser recovery

## Implementation characteristics

This is a static front-end application with no external dependencies. The file includes:

- inline CSS for layout and print styling
- inline JavaScript for dynamic form behavior
- runtime generation of checklist rows from data arrays
- draft export/import as JSON files
- localStorage-based recovery to reduce accidental data loss
- A4 print layout logic for generating a printable PDF copy

## Key JavaScript structures

The application defines the decommissioning sections in a JS array near the top of the script. Items are generated dynamically for the form UI and the printable report. This makes the form easy to adjust if the underlying checklist wording changes.

Important runtime behaviors include:

- `SECTIONS` — main checklist definitions by area
- `rows` — generated response rows for each checklist item
- `actions` — follow-up remedial items linked to unresolved entries
- `issues()` — checks for missing or risky responses
- `buildPrint()` — prepares the final printable report
- `saveRecovery()` / `restoreRecovery()` — browser-side draft persistence

## Browser usage model

This application is designed to run entirely in the browser without a server-side backend. It is meant to be a self-contained operational tool, especially for use in a local environment where a user fills out the form and then prints a PDF.

## Operational notes

- No installation or dependency manager is required.
- For best results, open the page in a modern browser such as Chrome, Edge, or Safari.
- When printing to PDF, use the built-in print dialog and select A4 portrait printing at 100% scale.
- Saved drafts can be exported/imported as JSON for portability and backup.

## Customization guidance

If the form needs to be updated for a local policy or regulatory standard, the most likely places to edit are:

- the `SECTIONS` array in `index.html`
- field labels and instructions embedded in the form HTML
- print/report wording and signatures at the end of the generated output

## Risks / considerations

- Since the tool stores state locally in the browser, users should export a JSON draft or print the PDF before closing the tab if they are concerned about losing progress.
- Because the app is a static front-end document, there is no central validation or server-side audit trail unless the user manages export copies externally.

## Summary

This repository is a practical, single-file HTML compliance tool for lab decommissioning. It is focused on usability, clear workflow, and print-ready output rather than backend complexity.
