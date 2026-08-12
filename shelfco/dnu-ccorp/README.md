# DNU — C-corp ShelfCo set

**Do not use. Do not render. Do not wire into `incorp-mcp`.**

JP limited ShelfCo creation to LLCs on 2026-08-10. These are the C-corp ShelfCo
documents, parked here so the live `templates/` directory contains only documents
that are cleared for use.

Nothing in the root manifest's `document_sets` refers to anything in this folder.
The template entries and document-set orderings recorded at parking are preserved
in `shelfco/dnu-manifest.json`, which exists for reference only.

## State when parked

Complete, and in the same condition as the LLC set:

- All nine `.docx` render clean through `incorp-mcp`'s
  `src/formations/documents.py::_render_docx`.
- The `.md` mirrors match.
- The ShelfCo edits are applied: the pre-filing ratification and its date, the
  EIN ratification and Form 8822-B authorization in place of a new EIN
  application, and the removal of the AI Governance Policy sentence asserting
  that one person held every role.
- Never reviewed by an attorney, and never opened in Word to check page layout.

## Contents

| File | Role |
|---|---|
| `action-of-incorporator-ccorp` | signed by General Legal's designated incorporator at claim time |
| `bylaws-ccorp` | adopted by the incorporator; certified by the client's Secretary |
| `organizational-resolutions-ccorp` | signed by the director |
| `common-stock-purchase-agreement-ccorp` | officer for the company, founder as purchaser |
| `stockholder-consent-ccorp` | sole stockholder |
| `indemnification-agreement-ccorp` | one rendering per director and per officer |
| `ai-governance-policy-ccorp` | director and AI Oversight Officer |
| `name-change-consent-ccorp` | rename only; board Part I and stockholder Part II |
| `certificate-of-amendment-ccorp` | rename only; filed with Delaware, signed by an authorized officer |
| `forms/de-certificate-of-amendment-stock-corporation.pdf` | Delaware's official source form |

`form-8822-b` was shared with the LLC flow and stayed in `templates/` when this
set was parked. It has since been parked itself, in `dnu-prefile-ein/`, when the
prefile flow was retired on 2026-08-11. Its field map still covers both entity
types. The `ccorp-shelfco` and `ccorp-shelfco-rename` sets recorded in
`shelfco/dnu-manifest.json` still list it, because they record the state at
parking.

## If this is revived

1. Move the files back to `shelfco/templates/` and a live `forms/` directory, and
   fold the entries and sets from `shelfco/dnu-manifest.json` into the root
   manifest's `templates` (following the live entries' `variant: "shelfco"`
   pattern) and `document_sets`.
2. Add `{Incorporation Date}` to the shelf entity facts (the root manifest's
   `shelfco.shelf_entity_facts` and the shelf company record in `incorp-mcp`),
   and widen `shelfco.role_model` to three people.
3. Record in the root manifest's `shelfco` section that the C-corp charter, like
   the LLC's, is filed before the client arrives.
4. Re-read `docs/changes-from-agent-operated-company.md`, which still documents
   every C-corp change and why it was made.
5. Deal with the prefile flow, which was retired after this set was parked. These
   documents still assume it: `organizational-resolutions-ccorp` Resolution 8
   ratifies an existing EIN and directs a Form 8822-B filing, and the sets in
   `shelfco/dnu-manifest.json` still include `form-8822-b`. Unless the prefile flow is
   revived too (see `dnu-prefile-ein/README.md`), Resolution 8 has to be rewritten
   to authorize a new EIN application — the same edit made to
   `operating-agreement-llc` Section 7 on 2026-08-11 — and `form-8822-b` has to
   come out of both C-corp sets.
6. Drop `name-change-consent-ccorp` and `certificate-of-amendment-ccorp` unless
   renames are revived too. They were parked here for being C-corp documents, but
   renames were separately retired on 2026-08-11; see `dnu-rename/README.md`.

The two structural reasons the C-corp path is harder are worth remembering: a
C-corp ShelfCo needs General Legal's incorporator to sign the Action of
Incorporator at claim time, so a human is in the loop before the client can sign
anything, and C-corps carry Delaware franchise tax where an LLC pays a flat
annual fee.
