# Changes from the base templates

> **Scope note.** This file is deliberately kept complete. It documents changes to
> documents that are no longer in use, because if a parked flow is revived this is
> the record of what was changed and why.
>
> This set was authored as the standalone `shelfCo-docs` repo and now lives in
> `agent-operated-company` under `shelfco/`. Manifest sections named below
> (`dnu_templates`, `dnu_document_sets`, `shelf_entity_facts_required`, ...)
> belonged to that repo's own manifest; the parked records now live in
> `shelfco/dnu-manifest.json`, and the live set is `document_sets.llc-shelfco`
> in the root `manifest.json`, where the ShelfCo variants carry `-shelfco` ids.
>
> Three sets are parked, and a path written below as `templates/...` may now
> resolve elsewhere:
>
> | Parked | Where it lives now | Decided |
> |---|---|---|
> | The whole C-corp set | `dnu-ccorp/templates/` | 2026-08-10, JP limited ShelfCo creation to LLCs |
> | `form-8822-b` and the prefiled EIN | `dnu-prefile-ein/` | 2026-08-11, the prefile flow was retired |
> | `name-change-consent-llc`, `certificate-of-amendment-llc` | `dnu-rename/templates/` | 2026-08-11, renames were retired |
>
> **Only Sections 1 and 3 below still describe live documents.** Section 2 (the
> EIN) and Section 4 (renames) describe retired flows, and the edits they record
> to `operating-agreement-llc` have since been reversed — see the 2026-08-11
> entry at the end of this file.
>
> The live set is five documents: `operating-agreement-llc`,
> `membership-interest-purchase-agreement-llc`,
> `indemnification-agreement-llc-manager`, `ai-governance-policy-llc`, and
> `certificate-of-formation-llc`. The client signs the first four; the fifth is an
> unsigned record copy.

Every template in this set starts as a byte-for-byte copy of its counterpart in
`templates/` at the repository root, with one exception noted below
(`certificate-of-formation-llc`, added 2026-08-12). Only the changes strictly
required by the ShelfCo model were made. This file is the complete list, so the
two sets can be re-synced later.

This applies to the `.docx` as much as the `.md`. Each `.docx` is the upstream
file with the edits below applied in place, so styles, fonts, native Word
numbering, headers, footers, and the `GLInstructionBlock` / `GLInstructionInline`
/ `GLSignatureMarker` styles are untouched. The four documents with no upstream
counterpart were built from the `stockholder-consent-ccorp.docx` skeleton for the
same reason, and number their provisions with literal text rather than a second
Word numbering instance, because the consents restart at 1 in Part II and the
Delaware certificates must match the official form exactly.

Five documents are unchanged copies: `common-stock-purchase-agreement-ccorp`,
`stockholder-consent-ccorp`, `indemnification-agreement-ccorp`,
`membership-interest-purchase-agreement-llc`, and `indemnification-agreement-llc-manager`.

Five documents were new and had no counterpart: `name-change-consent-ccorp`,
`name-change-consent-llc`, `certificate-of-amendment-ccorp`,
`certificate-of-amendment-llc`, and `form-8822-b`. All five are now parked.

One charter document is deliberately absent, because General Legal files it before
the client arrives: `certificate-of-incorporation-ccorp`.

`certificate-of-formation-llc` was absent for the same reason until 2026-08-12,
when a copy for the client's records was added. It is the one live document that
is not derived from its upstream counterpart — see the entry at the end of this
file.

---

## Why each change was made

### 1. The entity already exists

The single biggest difference. The new-formation set is written as if the charter
is being filed right now. For a ShelfCo it was filed weeks earlier, under a
placeholder name, by General Legal.

**`action-of-incorporator-ccorp`** — added a recital naming the actual filing
date, and rewrote the drafting note. The Incorporator is now always General
Legal's designated incorporator, never the client. The old note said the
incorporator "is usually the founder," which is wrong here and was the source of
the confusion about who signs what.

**`bylaws-ccorp`** — both dates moved from `{Incorporation Date}` to
`{Effective Date}`. The Bylaws are adopted by the Incorporator when the client
claims the ShelfCo, not when the certificate was filed, and the Secretary
certifies them as of the same day. Leaving these as `{Incorporation Date}` would
have back-dated the adoption of the Bylaws by however long the entity sat on the
shelf.

**`organizational-resolutions-ccorp`** — Resolution 1 now ratifies the specific
filing date and the specific pre-claim acts General Legal took (the charter
filing, the EIN application, and the appointment of the registered agent),
instead of ratifying "the filing of the Certificate of Incorporation" in the
abstract.

**`operating-agreement-llc`** — Section 1 now records the formation date, names
the authorized person who filed, has the Member ratify that filing and the
related pre-claim acts, and states that the authorized person's authority
terminated on filing and that they are not a member, manager, or agent. This is
the change described in Slack on Aug 1. It matters more for the LLC than for the
C-corp, because the LLC packet has no General Legal signature anywhere: this
recital is the only place the pre-filing is picked up.

### 2. The EIN already exists — RETIRED 2026-08-11

> This whole section describes the prefile flow, which we are not doing. The shelf
> entity now has no EIN at handoff. The `operating-agreement-llc` edits recorded
> below have been reversed; `form-8822-b` is parked in `dnu-prefile-ein/`. Kept as
> the record of what the flow was, and of what to restore if it comes back.

David's catch. The new-formation resolutions authorize the officers to go get an
EIN, which is wrong for an entity that already has one.

**`organizational-resolutions-ccorp`** Resolution 8 — replaced. It now ratifies
the existing EIN and the application by which General Legal obtained it, names
the client's responsible party, and directs the officers to file Form 8822-B
within the time that form requires. The tax-elections authority is kept.

**`operating-agreement-llc`** Section 7 — same substance, added to the existing
tax section, since the LLC set has no organizational-resolutions document.

**`form-8822-b`** — new. The responsible party of record moves from General Legal
to the client, and the IRS wants that within 60 days. Practically this is on the
critical path for bank onboarding: a shelf entity whose EIN still points at
General Legal will not clear onboarding at Slash or anywhere else.

### 3. Up to three people, not one

David's other catch, and the one that produced documents that were false on their
face. The old set assumed a single founder wearing every hat, and said so in
operative text, while `incorp-mcp` already accepted a separate `director` and
`officer` at intake.

**`ai-governance-policy-ccorp`** Section 3 — deleted "who also serves as the
Corporation's sole director and as its President and Chief Executive Officer,
Secretary, and Treasurer." Replaced with a reference to the Board's designation
in the Organizational Resolutions, which is where the designation actually
happens. Whenever the director and officer were different people, the old
sentence was simply untrue.

**`ai-governance-policy-llc`** Section 3 — deleted "who also serves as the
Company's sole Member and Manager," same reasoning.

Both drafting notes were rewritten to state the role model rather than assume it
away.

Nothing else needed to change for this. The remaining templates already keep
`{Founder Name}`, `{Director Name}`, `{Officer Name}`, `{Member Name}`, and
`{Manager Name}` as separate fields; the only defect was the two policies
asserting they were the same person. The Bylaws certification block stays as
`{Officer Name}, Secretary`, which is correct under a three-person model where
one officer holds every office.

### 4. Renames — RETIRED 2026-08-11

> We are not offering name changes for ShelfCo instant companies. All four
> documents described below are parked, the LLC pair in `dnu-rename/` and the
> C-corp pair in `dnu-ccorp/`. A client who wants a specific name goes to a normal
> formation. Kept as the record of how the documents were built and why.

New documents, all four used only in the rename variant.

**`name-change-consent-ccorp`** and **`name-change-consent-llc`** — converted from
the drafts posted to `#mcp` on Aug 1 into house style: `{Field Name}` instead of
`[BRACKET CAPS]`, `[[GL-SIGNATURE:capacity]]` markers, and the drafting note moved
into the leading blockquote. This matters mechanically, not just cosmetically:
`incorp-mcp` rejects any document that still contains the literal string
"Drafting note," and it substitutes only `{Field Name}` tokens, so the Slack
drafts could not have been rendered as they stood.

Two substantive edits during conversion. The C-corp version no longer offers the
"delete Part II if no shares have been issued" branch, because in this flow the
stock issuance is always in the same envelope, so both parts always sign; that
removes a judgment call the agent would otherwise have to make. The LLC version's
cross-reference was corrected from Section 1 to Section 2 of the Operating
Agreement, which is where the name actually appears.

**`certificate-of-amendment-ccorp`** and **`certificate-of-amendment-llc`** —
transcribed from Delaware's own official forms, which are bundled in `forms/`.
Delaware reviews these by hand, and there is a filed report of a General Legal
certificate being rejected for not matching the official form, so the numbered
paragraphs should not be reworded.

The two consents designate who may sign the certificate, and that person is
appointed by a document signed earlier in the same envelope. See the signing
order note in `manifest.json`.

---

## New fields

| Field | Where it comes from | Status |
|---|---|---|
| `{Formation Date}` | the shelf LLC record | **live**, in prose form, Operating Agreement Section 1 |
| `{Formation Day}` / `{Formation Month}` / `{Formation Year}` | the same shelf LLC record date, split | **live**, certificate only, so Delaware's ordinal phrasing survives |
| `{Incorporation Date}` | the shelf C-corp record | parked with `dnu-ccorp/` |
| `{EIN}` | the shelf entity record | parked with `dnu-prefile-ein/` |
| `{Responsible Party Name}` | client intake | parked with `dnu-prefile-ein/` |
| `{Current Company Name}` | the shelf entity's placeholder name | parked with `dnu-rename/` and `dnu-prefile-ein/` |
| `{New Company Name}` | client intake, rename variant only | parked with `dnu-rename/` |
| `{Amendment Authorized Person Name}` | client intake, LLC rename only | parked with `dnu-rename/` |
| `{Execution Day}` / `{Execution Month}` / `{Execution Year}` | derived from the signing date | parked with `dnu-rename/` |

`{Authorized Person Name}` **no longer exists in the ShelfCo set** (the base
`certificate-of-formation-llc` filing template at the repository root still uses
it). See the 2026-08-12 entry on hard-coding the authorized person, at the end of
this file.

There is now **no** new signature capacity. `amendment-authorized-person` was the
only one, and it is parked with `dnu-rename/`.

## What `{Company Name}` means here

Always the shelf entity's existing placeholder name. It used to be worth saying
because the rename variant kept it true even where the client had asked for a
different name — the rename only took effect when Delaware filed the Certificate
of Amendment, after signing, so the client signed a packet reading
`GL AgentCo 27, LLC` regardless. That was the answer to the question raised in
`#mcp` on Jul 24. With renames retired there is no longer another candidate: the
placeholder name is simply the company's name.

---

## 2026-08-11: the prefile flow and renames retired

Two decisions, taken together, and the second pass of parking after JP limited
ShelfCo creation to LLCs on 2026-08-10.

**No prefile flow.** General Legal will not obtain the shelf entity's EIN in
advance, so there is no responsible party to transfer to the client and no Form
8822-B. The client's agent instead runs the IRS's online EIN application with the
principal at claim time, which issues an EIN immediately; that sits outside this
repo. This reverses the section 2 edits above, for the LLC:

- `operating-agreement-llc` **Section 1** — deleted "the application for the
  Company's Employer Identification Number and" from the list of pre-claim acts
  the Member ratifies. The ratification now covers the Certificate of Formation
  filing and the registered agent, both of which General Legal still does in
  advance.
- `operating-agreement-llc` **Section 7** — deleted the three sentences added for
  the ShelfCo flow: the statement of `{EIN}`, the designation of
  `{Responsible Party Name}` as the Company's IRS responsible party, and the
  direction to the Manager to file Form 8822-B. Section 7 is now identical to the
  `agent-operated-company` text.

No replacement authority was added for applying for an EIN. Upstream does not put
one in the Operating Agreement either, and adding one would apply equally to a
normal formation, which under the rule in `templates/README.md` makes it an
`agent-operated-company` change rather than a ShelfCo one.

The parked C-corp `organizational-resolutions-ccorp` Resolution 8 still carries
the un-reversed version of this edit. See `dnu-ccorp/README.md`.

**No renames.** `name-change-consent-llc` and `certificate-of-amendment-llc` moved
to `dnu-rename/`, along with Delaware's official form. The C-corp pair was already
in `dnu-ccorp/` and stayed there. The signing-order constraint in `manifest.json`
went with them: it existed only because the Certificate of Amendment had to be
signed by someone the Name Change Consent appointed earlier in the same envelope.

Both edits were made in the `.docx` first and mirrored in the `.md`. All four live
`.docx` render clean through `incorp-mcp`'s
`src/formations/documents.py::_render_docx`.

---

## 2026-08-12: Certificate of Formation copy added to the packet

The client now gets a copy of the certificate General Legal already filed. It was
supplied as a finished GL document — letterhead header, a cover page, and a typed
copy of the certificate on page 2 — and was templatized in place rather than
rebuilt from the upstream `certificate-of-formation-llc`, so it keeps its own
layout.

This makes it the one live document that is not derived from its upstream
counterpart. It shares an id with upstream but not a purpose: upstream's is the
certificate you file, this one is a record copy of a certificate already filed.
The two should not be re-synced.

Only what varies between shelf entities became a field:

| Was | Now | Where |
|---|---|---|
| `GL AgentCo 1, LLC` | `{Company Name}, LLC` | FIRST, the IN WITNESS WHEREOF clause, **and the page-2 running header** |
| `this 28th day of July, A.D. 2026` | `this {Formation Day} day of {Formation Month}, A.D. {Formation Year}` | the IN WITNESS WHEREOF clause |

Delaware's ordinal phrasing is kept, because this document reproduces a certificate
already on file rather than drafting a new one, so it should read the way the filed
original reads. That costs three fields instead of one: `{Formation Date}` cannot
be dropped into "this ___ day of ___" without producing nonsense. All three come
from the same shelf record date that feeds `{Formation Date}` in the Operating
Agreement, so it is one value in four shapes, not four facts. `{Formation Day}`
carries its ordinal suffix.

The signature block was left entirely literal — `John Paul Mohler` in print, and
his signature image anchored to the IN WITNESS WHEREOF paragraph, floating over the
`By:` rule. He signed an identical certificate before the client arrived and has
given explicit permission for it to be reproduced programmatically, so the block is
part of the reproduction rather than something to fill in. Upstream uses
`{Authorized Person Name}` in this position; we do not, and as of 2026-08-12 the
Operating Agreement does not either.

The practical consequence: this sheet is complete on its face when it renders. It
belongs in the signature envelope so the client receives it with the rest of the
packet, but it carries no signature markers, so no fields are placed on it and no
recipient is asked to sign it.

Two other edits were needed to make it render:

- The company name was split across three Word runs at every occurrence, a
  spell-check artifact. `_render_docx` hard-fails on tokens split across runs, so
  each occurrence was consolidated into a single run.
- A leftover placeholder line, `[Please see Certificate of Formation attached.]`,
  sat at the foot of the cover page directly under a sentence that already said
  the same thing. Its text was removed. The page break that shared the paragraph
  was kept, so the document is still two pages.

A `GLInstructionBlock` drafting note was added, along with the style definition,
which the document did not previously carry. The renderer strips it.

The registered office and registered agent are left as literal text. They are the
same for every shelf entity, so they do not vary the way the name and date do.
Upstream parameterizes them as `{Registered Office Address}` and
`{Registered Agent Name}`, and `incorp-mcp` already supplies both from
`src/config.py`, so switching to variables later is cheap if Harvard Business
Services is ever replaced.

The document carries **no signature capacities**. It reaches the packet as a
member of the `llc-shelfco` document set in the root manifest, not through
entity-based selection.

---

## 2026-08-12: the authorized person is hard-coded

`{Authorized Person Name}` is gone. Operating Agreement Section 1 now names John
Paul Mohler in plain text, matching `certificate-of-formation-llc`, which has
always named him literally.

Delaware requires an "authorized person" under 6 Del. C. §§ 18-101(3) and 18-201 to
sign and file the Certificate of Formation, because an LLC has no members until the
filing is accepted. Section 1 records who that was, has the Member ratify their
acts, and confirms their authority ended on filing and that they hold no role in
the company. That sentence stays exactly as it was; only the name stopped being a
field.

It was never going to vary. JP files every shelf entity, and
`certificate-of-formation-llc` carries his signature image, so the packet can only
ever serve entities he filed. A field bought no flexibility and created a way for
the two documents to name different people, which is the failure mode worth
avoiding: the Operating Agreement would say one person formed the company while the
certificate showed another's signature on the filing.

This also removes the last non-date wiring item. `template_context` supplies 17 of
the 21 tokens the live set needs, and the 4 it does not are all the formation date
in different shapes, which `incorp-mcp` supplies from the shelf company record.
There is no General Legal constant left to supply.

If General Legal ever adds a second authorized person, both documents change
together and the certificate needs a second signature image. Reintroducing the
field on its own would not be enough, and would reintroduce the mismatch.
