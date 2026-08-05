# Template authoring rules

The DOCX files are the authoritative signing sources. The Markdown files are
human- and agent-readable mirrors; keep their legal text aligned with the DOCX,
but never generate signing documents from Markdown.

## File format

- Keep matching `.docx` and `.md` filenames in kebab case with an `-ccorp` or
  `-llc` suffix.
- Use Times New Roman for legal text and native Word numbering for numbered
  provisions.
- Do not embed fonts. Preserve headers, footers, page breaks, and signature-page
  layout when editing the DOCX.

## Fields and signatures

- Write substitution fields as `{Field Name}` and list each field in
  `manifest.json`.
- Keep each field in one Word text run. Do not apply formatting to only part of
  a field.
- Write signature locations as `[[GL-SIGNATURE:capacity]]`, using a capacity
  listed in the document's `signature_capacities` manifest entry.
- Apply the `GLSignatureMarker` character style to the complete signature
  marker. The signing service assigns capacities to recipients.
- Keep entity suffixes such as `, Inc.` and `, LLC` as literal template text;
  `{Company Name}` contains only the name stem.

## Drafting instructions

- Use the `GLInstructionBlock` paragraph style when the entire paragraph is an
  instruction.
- Use the `GLInstructionInline` character style only on instruction text within
  a paragraph. Leave punctuation needed by the final sentence outside it.
- Word comments may contain authoring guidance. They are removed from signing
  copies.
- Resolve all tracked changes before committing. The renderer rejects DOCX
  files containing insertions, deletions, or moved text.

## Before committing

1. Update both the DOCX and Markdown mirror.
2. Update the document's fields and signature capacities in `manifest.json`.
3. Confirm every field and signature marker is a single Word run.
4. Confirm instruction styles are applied correctly and tracked changes are
   resolved.
5. Open the DOCX in Word or LibreOffice and check page layout.

`incorp-mcp` removes styled instructions and comments, substitutes all fields,
converts signature markers to PandaDoc fields, and fails if authoring content or
unresolved fields remain.
