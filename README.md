# Elevate Oral Surgery — Post-Op Medication Draft Builder

A single-file, offline web app that generates a **draft** post-operative medication
reference for staff to review with the supervising surgeon. It is not a prescribing
tool and does not connect to any server, database, or patient record system.

## What it does

Staff fill out a short intake form — age band, weight (pediatric only), allergies,
procedure, medical history, infection risk, and a few situational factors (TMJ pain,
bleeding concerns, refractory pain). The app runs that intake through a rules engine
built from the practice's own protocol documents and produces:

- A patient summary
- Recommended medication options with a rationale and source citation for each
- Flags for anything the protocol doesn't clearly cover, or where source documents
  disagree with each other
- A disclaimer and a signature line for surgeon sign-off

**Every draft requires a licensed prescriber's review and approval before any order
is issued.** This tool does not prescribe.

## Running it

Open `postop-med-reference.html` directly in a browser. No build step, no server,
no dependencies. Everything — including the practice logo and imagery — is
self-contained in the one file.

## Privacy / data handling

- No network calls of any kind (no `fetch`, no analytics, no external scripts).
- No data is stored, logged, or transmitted. Nothing persists after the page is
  closed or refreshed.
- Do not enter real patient names or identifiers into the free-text fields — the
  intake is designed to work from clinical attributes only (age band, allergy
  categories, etc.), not identity.

## ⚠️ Before making this repository public

This file embeds the practice's actual dosing/substitution logic (drug choices,
doses, durations, and the escalation cascade) directly in the JavaScript source.
Anyone with read access to this repo can read that protocol logic in full. If that's
not something the practice wants publicly visible, keep this repository **private**,
or strip the clinical specifics into a separate config the repo doesn't include.

## Status

Draft/development tool built against the practice's own protocol documents
(not included in this repo). Not clinically validated for production use.
