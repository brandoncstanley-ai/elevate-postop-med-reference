# Post-Op Medication Draft Builder (coursework sample)

A single-file, offline web app that generates a **draft** post-operative medication
reference for staff to review with the supervising surgeon. It is not a prescribing
tool and does not connect to any server, database, or patient record system.

**This is a coursework sample.** The rules engine is grounded in an illustrative,
composite post-op protocol modeled on common oral-surgery prescribing patterns —
not the live, current internal protocol of any specific practice. Drug choices,
doses, and the escalation logic are for demonstrating the workflow-design pattern
(intake → rules engine → cited, flagged draft → human sign-off), not for clinical
use anywhere.

## What it does

Staff fill out a short intake form — age band, weight (pediatric only), allergies,
procedure, medical history, infection risk, and a few situational factors (TMJ pain,
bleeding concerns, refractory pain). The app runs that intake through a rules engine
built from the sample protocol documents described above and produces:

- A patient summary
- Recommended medication options with a rationale and source citation for each
- Flags for anything the protocol doesn't clearly cover, or where source documents
  disagree with each other
- A disclaimer and a signature line for surgeon sign-off

**Every draft requires a licensed prescriber's review and approval before any order
is issued.** This tool does not prescribe.

## Running it

Open `postop-med-reference.html` directly in a browser. No build step, no server,
no dependencies. Everything — including the header logo and imagery — is
self-contained in the one file.

## Privacy / data handling

- No network calls of any kind (no `fetch`, no analytics, no external scripts).
- No data is stored, logged, or transmitted. Nothing persists after the page is
  closed or refreshed.
- Do not enter real patient names or identifiers into the free-text fields — the
  intake is designed to work from clinical attributes only (age band, allergy
  categories, etc.), not identity.

## Status

Coursework prototype demonstrating an intake → rules-engine → cited/flagged-draft →
human-sign-off workflow. Built against an illustrative sample protocol (not
included as a separate source file — the sample content lives directly in the
JavaScript). Not clinically validated, not affiliated with any specific practice's
live protocol, and not for production or clinical use.

If this pattern is ever adapted for real use at a practice, the real protocol
logic should be kept out of a public repo (private repo, or the clinical specifics
moved into a config/data file the repo doesn't include).
