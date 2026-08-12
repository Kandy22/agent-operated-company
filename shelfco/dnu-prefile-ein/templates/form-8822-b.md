> **Drafting note — delete before use:** This is not a General Legal document. It is the IRS's own fillable form, and it must be filed on the IRS's PDF rather than retyped. This file is the field map: it tells the renderer which AcroForm field on `forms/f8822b.pdf` receives which value, and it is the specification for the corresponding entry in `manifest.json`. Every ShelfCo transfer needs one, whether or not the client renames the company, because the responsible party of record changes from General Legal to the client. Form 8822-B must be filed **within 60 days** of the change. A ShelfCo whose EIN still lists General Legal as the responsible party will fail bank onboarding, so this form is on the critical path for getting the client a bank account.

# Form 8822-B — Change of Address or Responsible Party (Business)

Source form: `forms/f8822b.pdf` (Rev. December 2019, OMB No. 1545-1163). Download the current revision from <https://www.irs.gov/Form8822B> before each batch and replace the bundled copy if the revision date has moved.

## Signature

Line 10 is signed by an owner, officer, or representative of the company. In the ShelfCo packet that is the client, not General Legal, so this form belongs in the same signing envelope as the rest of the packet.

Signature capacity: `[[GL-SIGNATURE:manager]]`. (If the C-corp set in `dnu-ccorp/` is ever revived, the capacity there is `[[GL-SIGNATURE:officer]]`.)

The IRS accepts this form only on paper. Sign it in the envelope with the rest of the packet, then print and mail it. Because the shelf entity's old business address is General Legal's address, the mailing destination is determined by General Legal's state, not the client's.

## Field map

| Line | AcroForm field | Value |
|---|---|---|
| Tax-exempt checkbox | `c1_1[0]` | leave unchecked |
| 1 — Employment, excise, income, and other business returns | `c1_2[0]` | check |
| 2 — Employee plan returns | `c1_3[0]` | leave unchecked |
| 3 — Business location | `c1_4[0]` | check |
| 4a — Business name | `f1_1[0]` | `{Current Company Name}, LLC` |
| 4b — Employer identification number | `f1_2[0]` | `{EIN}` |
| 5 — Old mailing address | `f1_3[0]` | General Legal's address of record for the shelf entity |
| 5 — foreign country / province / postal | `f1_4[0]`, `f1_5[0]`, `f1_6[0]` | leave blank |
| 6 — New mailing address | `f1_7[0]` | `{Principal Office Address}` |
| 6 — foreign country / province / postal | `f1_8[0]`, `f1_9[0]`, `f1_10[0]` | leave blank |
| 7 — New business location | `f1_11[0]` | `{Principal Office Address}` |
| 7 — foreign country / province / postal | `f1_12[0]`, `f1_13[0]`, `f1_14[0]` | leave blank |
| 8 — New responsible party's name | `f1_15[0]` | `{Responsible Party Name}` |
| 9 — New responsible party's SSN, ITIN, or EIN | `f1_16[0]` | collected from the client at intake; see the note below |
| 10 — Daytime telephone (optional) | `f1_17[0]` | optional |
| 10 — Title | `f1_18[0]` | the signer's office, i.e. `Manager` |

Line 9 is the only place in the whole ShelfCo packet that asks for a client's SSN or ITIN. Confirm the intake, storage, and retention treatment for it before this form goes live; do not route it through the same path as ordinary formation fields.

## Name changes

A name change is reported to the IRS separately from this form, and not on it. Line 4a takes the company's name **as it currently appears in IRS records**, which for a ShelfCo is the placeholder name, even in the rename variant. Report the new name on the entity's next return, or by signed letter to the IRS campus where the return is filed.

## Where to file

Determined by the **old** business address. Delaware and the other states listed on page 2 of the form file to Internal Revenue Service, Kansas City, MO 64999. The remaining states file to Internal Revenue Service, Ogden, UT 84201-0023. Confirm against page 2 of the bundled PDF, and re-confirm if General Legal's address of record changes.
