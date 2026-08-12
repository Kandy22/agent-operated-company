# DNU — prefile EIN set

**Do not use. Do not render. Do not wire into `incorp-mcp`.**

We are not doing the prefile flow. General Legal will not obtain the shelf
entity's EIN before the client arrives, so there is no responsible party to
transfer and no Form 8822-B to file. The shelf entity is handed over **without an
EIN**.

The replacement is the IRS's online EIN application, which the client's agent runs
with the principal at claim time and which issues an EIN immediately. Those
instructions are at `filing-instructions/delaware-llc-ein-filing-instructions.md`
at the repository root. The online application requires the responsible party to
have an SSN or ITIN, which is why the agent runs it with the principal rather than
on its own.

Parked here on 2026-08-11.

## Contents

| File | Role |
|---|---|
| `templates/form-8822-b.md` | field map for the IRS form; not a General Legal document |
| `forms/f8822b.pdf` | the IRS's own fillable form (Rev. December 2019) |

## What else the decision changed

Form 8822-B was the visible half. The operative half was in the LLC's Operating
Agreement, and it was edited in the same pass:

- **Section 1** ratified "the application for the Company's Employer
  Identification Number" among the authorized person's pre-claim acts. That
  clause is gone; the ratification now covers the Certificate of Formation filing
  and the registered agent only.
- **Section 7** stated `{EIN}`, designated `{Responsible Party Name}` as the
  Company's IRS responsible party, and directed the Manager to file Form 8822-B.
  The whole passage is gone, which returns Section 7 to the `agent-operated-company`
  text word for word.

Both edits were made in the `.docx` and mirrored in the `.md`. The result renders
clean through `incorp-mcp`'s `src/formations/documents.py::_render_docx`.

`{EIN}` and `{Responsible Party Name}` are no longer live fields anywhere in the
repo. They survive only in the parked C-corp `organizational-resolutions-ccorp`,
whose Resolution 8 is written for this same prefile flow and would need the
equivalent rewrite if that set were revived.

Nothing here was ever reviewed by an attorney.

## The open SSN question, now moot

Line 9 of Form 8822-B asks for the new responsible party's SSN or ITIN. It was
the only place in the entire ShelfCo packet that asked a client for one, and the
intake, storage, and retention treatment for it was still unresolved when this
was parked. Retiring the prefile flow retires that question with it. If the flow
comes back, the question comes back first.

## If this is revived

1. Move `templates/form-8822-b.md` back to `shelfco/templates/` and
   `forms/f8822b.pdf` to a live `forms/` directory, and fold the `form-8822-b`
   entry from `shelfco/dnu-manifest.json` into the root manifest's `templates`.
   Add it to `document_sets.llc-shelfco`.
2. Restore the two Operating Agreement passages described above, in the `.docx`
   first and then the `.md`, and re-render both through `_render_docx`.
3. Add `{EIN}` to the shelf entity facts (the root manifest's
   `shelfco.shelf_entity_facts` and the shelf company record in `incorp-mcp`).
   `{EIN}`, `{Responsible Party Name}`, `{Principal Office Address}`, and
   `{Current Company Name}` become live fields again; they are bookkept in
   `shelfco/dnu-manifest.json` under `dnu_fields_vs_agent_operated_company`.
4. Record in the root manifest's `shelfco` section that the client should
   receive the IRS CP 575 assignment letter as an unsigned packet page.
5. Re-download the form from <https://www.irs.gov/Form8822B> and replace the
   bundled copy if the revision date has moved past December 2019.
6. Settle the SSN handling question before any of this goes live.
