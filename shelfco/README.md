# ShelfCo documents

Documents that delegate control and ownership of a pre-formed Delaware shelf
company (a ShelfCo, `GL AgentCo <n>, LLC`) to a client. Use the templates at the
repository root for a normal, from-scratch incorporation.

The ShelfCo document set is defined in the root `manifest.json` under
`document_sets.llc-shelfco`, and the set-level rules (role model, unsigned pages,
company name, EIN) under `shelfco`. Two of the five documents in the set are the
unchanged root templates (`membership-interest-purchase-llc`,
`indemnification-llc-manager`); this directory holds only the three that differ:

| Document | Why it differs from the root template |
|---|---|
| `operating-agreement-llc` | Section 1 records the shelf entity's formation and has the Member ratify General Legal's pre-claim filing |
| `ai-governance-policy-llc` | Section 3 no longer asserts the AI Oversight Officer is the sole Member and Manager |
| `certificate-of-formation-llc` | A record copy of the certificate already on file with Delaware, not the filing template |

`docs/changes-from-agent-operated-company.md` records every deviation and why.

## Parked flows

Three flows are deliberately not offered. Each `dnu-*` directory keeps the
complete documents and a README recording the decision and what it would take to
undo:

| Not doing | Parked in |
|---|---|
| C-corp ShelfCos | `dnu-ccorp/` |
| Pre-filing the EIN and transferring it on Form 8822-B | `dnu-prefile-ein/` |
| Name changes | `dnu-rename/` |

Nothing live references anything under a `dnu-*` directory.

## Authoring

Template authoring rules, including the ShelfCo-specific ones (the literal
authorized person, the record-copy certificate, filed-form fidelity), are in
`templates/README.md`.
