# Quality Criteria: Language and Domain

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-LANG-001 |
| CrossReference | [QC-DICT-001] |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-10 | Deprecated | Jens Tirsvad Nielsen | S07 | Common Defects: added a line for criterion 4 (register) and one for criterion 10 (abbreviations); the Commit cell of the first row is now a link | [1d1988f] |
| 2026-10-10 | Accepted | Jens Tirsvad Nielsen | S07 | Accepted by the author as stand-in for S07, through the pull request that merges this row, without an independent review; the first review is recorded in the project (Go-with-conditions, the two conditions are this change) | [7024240] |

---

## Purpose

Every artifact of a type written in the Product Owner's (PO's) language exists once, in that language and in the vocabulary of its professional domain (for example medical or construction engineering, even when the language is English). This checklist decides whether such an artifact can be read and reviewed by the people it is for. It is cross-cutting: apply it in addition to the checklist of the artifact's own type, to every artifact type the project registry marks as written in the PO language.

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | The Metadata table has a `Language` row and a `Domain` row, and neither is a placeholder | Mandatory | Usability, Maintainability | A reviewer must see at once how to read the document |
| 2 | `Language` is a BCP 47 code and `Domain` is a value from the registry's domain list | Mandatory | Maintainability | Free-text values cannot be listed or compared |
| 3 | The content (prose and table cells) is written in the stated language | Mandatory | Usability | Quoted source text and established technical terms may stay in another language; a document half in one language and half in another fails |
| 4 | The register matches the one the registry gives for the artifact type | Mandatory | Usability | The register fixes the reader the text assumes and how much it explains |
| 5 | Domain terms are the PO terms of the domain's dictionary, with no synonyms | Mandatory | Usability, Maintainability | A second word for a dictionary term is a defect |
| 6 | Metadata keys, section headings, IDs and statuses are in English | Mandatory | Maintainability, Compatibility | The scripts read them; only the content is in the PO language |
| 7 | No translated twin (`<name>.<language>.md`) exists beside the document | Mandatory | Maintainability | One file per artifact; two files drift apart |
| 8 | A change of language or domain since the previous accepted version has a Version History row and was reviewed again | Mandatory | Maintainability | Changing the language of an artifact is a material change |
| 9 | A reviewer competent in the domain, and in the language, has confirmed that the domain terms are used correctly | Mandatory | Functional Suitability | May be a second reviewer named on the review record when the first does not read the language or know the domain |
| 10 | Abbreviations are spelled out on first use, in the stated language | Optional | Usability | |

## Common Defects

- A `Domain` or `Language` row left as a placeholder, or a free-text domain
- Sections in two languages, or headings translated so that a script cannot find them
- A PO term in the domain's dictionary replaced by a near-synonym in one section
- The English document replaced by a translation without a Version History row or a new review
- A translated copy kept beside the document "for convenience"
- Domain terms used loosely because the reviewer does not know the domain
- A document in the right language but the wrong register, for example a milestone written as an engineering note, or a business case full of implementation detail
- An abbreviation used without being spelled out on first use, or spelled out in another language than the document's

## Traceability Rule

- Backward: Every PO term traces to a row of the Domain Dictionary ([QC-DICT-001]) of the same domain
- Forward: Applies together with the checklist of the artifact's own type; it feeds no other checklist

---

[QC-DICT-001]: ./qc-dictionary.md
[1d1988f]: https://git.tirsystem.com/TirSystem/sqa-qc-checklists/commit/1d1988f8af73c29f0945bdf8e2b9c80eda99a53c
[7024240]: https://git.tirsystem.com/TirSystem/sqa-qc-checklists/commit/70242402e2c93842a1c099e1cb6d902af0d79ef2
