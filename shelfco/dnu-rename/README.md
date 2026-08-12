# DNU — rename set

**Do not use. Do not render. Do not wire into `incorp-mcp`.**

We are not offering name changes for ShelfCo instant companies. A ShelfCo client
takes the shelf entity's placeholder name, e.g. `GL AgentCo 27, LLC`. A client who
wants a specific name should be routed to a normal from-scratch formation using
the `agent-operated-company` docs instead.

Parked here on 2026-08-11.

## Contents

| File | Role |
|---|---|
| `templates/name-change-consent-llc` | Member's consent approving the new name and designating who signs the certificate |
| `templates/certificate-of-amendment-llc` | filed with Delaware under 6 Del. C. § 18-202 |
| `forms/de-certificate-of-amendment-llc.pdf` | Delaware's official source form |

The C-corp equivalents, `name-change-consent-ccorp` and
`certificate-of-amendment-ccorp`, are parked separately under `dnu-ccorp/`. They
are dead twice over and were left where they are.

## State when parked

Complete, and in the same condition as the rest of the LLC set:

- Both `.docx` render clean through `incorp-mcp`'s
  `src/formations/documents.py::_render_docx`.
- The `.md` mirrors match.
- `certificate-of-amendment-llc` tracks Delaware's official form paragraph for
  paragraph. Do not reword it if this is revived — General Legal has already had a
  filing rejected for departing from an official form.
- Both number their provisions with literal text rather than native Word
  numbering, because the consent restarts at 1 in Part II and the certificate has
  to match Delaware's form exactly.
- Never reviewed by an attorney, and never opened in Word to check page layout.

## Why the economics never worked

Delaware charges $200.00 for an LLC amendment plus expedite fees, and same-day
processing runs roughly $400 all-in. On top of that the rename does not take
effect until Delaware files the certificate, so the client still signs a packet
bearing the placeholder name and waits. A client willing to pay rush fees for a
specific name is better served by a new formation, which is where the decision
landed.

## If this is revived

1. Move the files back to `shelfco/templates/` and a live `forms/` directory, and
   move the `name-change-consent-llc` and `certificate-of-amendment-llc` entries
   from `shelfco/dnu-manifest.json` into the root manifest's `templates`
   (following the live entries' `variant: "shelfco"` pattern).
2. Restore the `llc-shelfco-rename` document set from `shelfco/dnu-manifest.json`
   into the root manifest's `document_sets`. Note that the version recorded there
   still includes `form-8822-b`, which is separately parked in `dnu-prefile-ein/`;
   drop it unless the prefile flow is revived too.
3. `{Current Company Name}`, `{New Company Name}`,
   `{Amendment Authorized Person Name}`, and the three `{Execution ...}` fields
   become live again (they are bookkept in `shelfco/dnu-manifest.json` under
   `dnu_fields_vs_agent_operated_company`), and `amendment-authorized-person`
   becomes a live signature capacity; `incorp-mcp` must be taught to supply all
   of them.
4. Record the signing-order constraint in the root manifest's `shelfco` section:
   the Certificate of Amendment must be signed by the authorized person the Name
   Change Consent designates, so the Member must sign before the Manager.
5. Re-widen the "Documents Delaware reads by hand" and numbering rules in
   `templates/README.md`. Both rules are still written out there in full; they were
   only narrowed to name the parked documents they now bind. Add
   `certificate-of-amendment-llc` back as a live example rather than rewriting the
   rules from scratch.
6. Re-download the form from the Delaware Division of Corporations and confirm it
   has not changed.
