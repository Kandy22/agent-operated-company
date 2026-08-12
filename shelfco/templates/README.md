# Template authoring rules (ShelfCo)

> Scope: this directory holds the three ShelfCo documents that differ from their
> root counterparts; the other two documents in the `llc-shelfco` set are the
> unchanged root templates, listed once in the root `manifest.json`. Three sets
> are parked and are not to be used: the C-corp set in `dnu-ccorp/`, the
> prefiled-EIN documents in `dnu-prefile-ein/`, and the name change documents in
> `dnu-rename/`. These rules apply to all of them, so they still apply if any
> parked set is revived.

These rules extend `templates/README.md` at the repository root. Keep them
identical wherever possible, so documents can be moved between the base and
ShelfCo sets without rework.

As there, the DOCX files are the authoritative signing sources and the Markdown
files are mirrors. Keep their legal text aligned, and never generate signing
documents from Markdown.

Each DOCX here is a copy of its root-template counterpart with the ShelfCo edits
applied in place, so styles, fonts, numbering, and the three GL styles carry over
unchanged. The exception is `certificate-of-formation-llc`, which arrived as a
finished GL document with its own letterhead and cover page and was templatized in
place; do not re-sync it against `templates/certificate-of-formation-llc.docx`,
which is a different document for a different purpose. The four documents that
were authored new for ShelfCo are all parked now, and each was built from the
`stockholder-consent-ccorp.docx` skeleton for the same reason (that file lives in
`dnu-ccorp/templates/`, but it remains the skeleton to copy). Editing an existing
DOCX is strongly preferred over authoring a new one.

## File format

- Keep filenames in kebab case with an `-ccorp` or `-llc` suffix. Where a
  document has a counterpart in the root `templates/`, use the same filename.
- Use Times New Roman for legal text and native Word numbering for numbered
  provisions.
- Do not embed fonts.

## Fields and signatures

- Write substitution fields as `{Field Name}` and list each field in the root
  `manifest.json`.
- Keep each field in one Word text run. Do not apply formatting to only part of
  a field.
- Write signature locations as `[[GL-SIGNATURE:capacity]]`, using a capacity
  listed in the document's `signature_capacities` manifest entry. A document with
  an empty `signature_capacities` is a record-copy page and must carry no markers
  at all; `certificate-of-formation-llc` is the only one today. It reproduces an
  already-signed certificate, image and all, so leave its signature block literal.
- **General Legal's authorized person is literal, not a field.** John Paul Mohler
  signs and files every shelf entity's Certificate of Formation, and his signature
  image is embedded in `certificate-of-formation-llc`, so the packet only ever
  serves entities he filed. He is named in plain text in both that document and
  `operating-agreement-llc` Section 1. Do not "improve" either one by turning his
  name back into a field: it would buy no flexibility and would let the two
  documents name different people. If General Legal ever adds a second filer, both
  documents change together, and the certificate needs a second signature image.
- Check the header and footer, not just the body. `_render_docx` substitutes
  across every `word/*.xml` part, and `certificate-of-formation-llc` carries
  `{Company Name}` in its running header.
- Watch for fields split across Word runs. Typing a name into Word often leaves it
  in three runs, and the renderer hard-fails on a token it cannot find whole in a
  single run.
- Keep entity suffixes such as `, Inc.` and `, LLC` as literal template text;
  `{Company Name}` contains only the name stem.
- `{Company Name}` is always the shelf entity's existing placeholder name. There
  is no rename variant, so `{Current Company Name}` and `{New Company Name}` must
  not appear in any live template; they survive only in `dnu-rename/` and
  `dnu-prefile-ein/`.

## Name variables are roles, not people

Every name variable stands for a role. Fill in all of them, every time. Where one
person holds several roles, write that same person's name into every variable for
every role they hold: someone who is both the sole Member and the Manager is named
in `{Member Name}`, `{Manager Name}`, and `{Purchaser Name}` alike. Never leave a
role variable blank and never substitute "same as above."

The role model is in the root `manifest.json` under `shelfco.role_model`. When
adding a variable to a template, update that entry and the template's `fields`
list too, or an agent filling the set will not know who it refers to.

## Drafting instructions

- Put a whole-paragraph drafting note in the leading `> **Drafting note — delete
  before use:**` blockquote. In DOCX this is the `GLInstructionBlock` paragraph
  style.
- Check the page count in Word after adding or growing one. The note is stripped
  at render time, so it never reaches the client, but it does take up room in the
  template itself. Adding one to `certificate-of-formation-llc` pushed its cover
  page onto a second page, which was fixed by removing spacer paragraphs. Where a
  document positions content with empty paragraphs, confirm both views: the
  template as Word shows it, and the rendered output.
- Write inline instructions as `[GL INSTRUCTION — ...]`. In DOCX this is the
  `GLInstructionInline` character style.
- `incorp-mcp` strips both, and hard-fails on any document that still contains
  the literal string `Drafting note` or an unresolved `{Field Name}`. Test
  against the renderer, not by eye.

## Documents Delaware reads by hand

Nothing in the live set is filed *by this packet*. `certificate-of-formation-llc`
is marked `filed_with_state: true` because it reproduces a document Delaware
already holds, but it is a record copy: `already_filed: true`, and nothing about it
is submitted to anyone. Since it reproduces an accepted filing, its text must not
be reworded at all.

If you ever add a document that actually gets filed, it must track Delaware's
official form paragraph for paragraph, with the official PDF bundled unmodified
alongside it. A General Legal certificate has already been rejected once for
departing from an official form. That rule currently binds only parked
documents — `certificate-of-amendment-llc` in `dnu-rename/`, and
`certificate-of-amendment-ccorp` in `dnu-ccorp/`, which additionally has to stay on
one page because Delaware charges $9.00 for each page after the first.

## Numbering

Every live document keeps its native Word numbering, inherited untouched from
the root templates. Do not introduce a second numbering instance.

The literal-text numbering convention applies only to the four parked documents —
the two name-change consents and the two amendment certificates. They used literal
text because the consents restart at 1 in Part II and the certificates have to
match Delaware's official form exactly, and both were safer that way than as a
second numbering instance. Keep that convention if any of them is revived.

## Before committing

1. Update both the DOCX and the Markdown mirror.
2. Render the changed DOCX through `incorp-mcp`'s
   `src/formations/documents.py::_render_docx` with every field and signature
   capacity supplied, and confirm it does not raise; `incorp-mcp`'s test suite
   renders the full `llc-shelfco` set against this checkout. Do not rely on
   reading the Markdown: a text edit can silently miss the DOCX, which is how
   the EIN resolution was nearly shipped unchanged.
3. Update the root `manifest.json`: the document's `fields` and
   `signature_capacities`, and `document_sets.llc-shelfco` if the set itself
   changes. Fields that belong to parked flows (renames, the prefiled-EIN
   documents) must not appear in any live template; `incorp-mcp` has nothing to
   fill them with.
4. Confirm the change is required by the ShelfCo model. If it is an improvement
   that also applies to a normal formation, it belongs in the root template
   instead, so the two sets do not drift.
5. Record what changed and why in `docs/changes-from-agent-operated-company.md`.
