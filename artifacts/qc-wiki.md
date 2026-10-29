# Quality Criteria: Wiki

## Metadata
| Key | Value |
| --- | --- |
| ID | QC-WIKI-001 |
| CrossReference | [QC-LANG-001], [QC-WF-001] |

## Version History
| Date | Status | Author | Reviewer | Change | Commit |
| --- | --- | --- | --- | --- | --- |
| 2026-10-29 | Proposed | Jens Tirsvad Nielsen | S02 | Initial version: the sidebar, the language sections and the page set of a wiki | [f175606] |

---

## Purpose

A wiki is read by people who arrive on one page and need to find the others. The sidebar is the map: on Gitea it is the only place that lists the pages, and a visitor who switches language must not have to learn a new layout. This checklist confirms that every wiki of an organisation has the same sidebar shape, that each language is reachable in one click and that the page set is the same in every language.

Apply it to the wiki of a project (`docs/wiki/`) and to the wiki a tool repository generates. The language and domain rules of the pages themselves are checked with [QC-LANG-001].

## Quality Criteria Checklist

Level: **Mandatory** criteria are the baseline every instance must meet; **Optional** criteria are advanced and may be deferred.

### Sidebar

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 1 | The wiki has a `_Sidebar.md`, because the host lists subpages only through it | Mandatory | Interaction Capability | |
| 2 | The sidebar starts with the wiki's title in bold, then one list of the pages in the primary language (English), `Home` first | Mandatory | Interaction Capability, Maintainability | The page list appears once, never once per language |
| 3 | The page list holds a link to every English page of the wiki, and no link points to a page that does not exist | Mandatory | Reliability, Interaction Capability | A page missing from the sidebar cannot be found; a dead link is a defect |
| 4 | A `**Related**` section follows the page list only when the wiki has related wikis (for example the checklists wiki for a framework wiki); each entry is a link to that wiki's Home. A wiki with nothing related has no such section | Mandatory | Interaction Capability | An empty or placeholder section is a defect |
| 5 | A `**Languages**` section is the last section of the sidebar. It has one line per language, the language written in that language, linking to that language's `Home` page | Mandatory | Interaction Capability, Flexibility | For example `English: [Home](Home)`, `Dansk: [Hjem](Home-da)`. The pages of a translation are reached from its Home page, not from the sidebar |
| 6 | The sidebar does not repeat the page list per language | Mandatory | Maintainability, Interaction Capability | Three full lists triple the sidebar and every new page has to be added three times |
| 7 | A sidebar produced by a generator carries a comment that says so and names the generator; the generator is changed, not the page | Mandatory | Maintainability | |
| 8 | The wiki has a `Languages` line on each page (criterion 11), so the sidebar is not the only way to switch language | Optional | Interaction Capability | |

### Languages and pages

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 9 | Every wiki exists in English and, as a minimum, in the language the project's registry names as the PO language; further languages are added on top, never instead of English | Mandatory | Flexibility, Interaction Capability | |
| 10 | Every English page has a page in each other language of the wiki: the page sets are identical | Mandatory | Reliability, Interaction Capability | A page missing in a language is a defect, not a choice |
| 11 | Every page starts with the language line, with the current language in bold and a link to the same page in each other language | Mandatory | Interaction Capability | `**English** · [Dansk](Home-da) · [Bahasa Malaysia](Home-ms)` |
| 12 | A page in a language other than English is named `<Page>-<code>.md`, with a BCP 47 code; English has no suffix | Mandatory | Maintainability, Compatibility | A different separator (`Home.da`) is allowed only where the wiki records it as a known deviation and a plan to remove it |
| 13 | Code blocks, commands, file names and IDs stay in English in every language | Mandatory | Reliability | |

### Publishing

| # | Criterion | Level | ISO/IEC 25010 Characteristic(s) | Notes |
| --- | --- | --- | --- | --- |
| 14 | The sidebar, every page and every link were checked on the published wiki after the change, not only in the repository | Mandatory | Reliability | A link that works in the folder can fail on the host |
| 15 | A change to the layout rules (sections, order, naming) is made in the generator or template and in this checklist's source rules together | Optional | Maintainability | |

## Common Defects

- No `_Sidebar.md`: the host shows a wiki with no map of its pages
- The page list repeated for every language, with no `Languages` section
- A `Languages` section that is not last, or that links to translated pages instead of to each language's Home
- A `Related` section with a placeholder, or with a link that does not open
- A page in the sidebar that does not exist, or an existing page that is not in the sidebar
- A translation that lacks pages the English wiki has
- A page without the language line, or a language line that links to a missing page
- Translation pages named with a different separator than the rest of the organisation, so one tool finds them and another does not

## Traceability Rule

- Backward: Language and Domain checklist ([QC-LANG-001]) for the content of the pages; CI workflow checklist ([QC-WF-001]) where a workflow publishes the wiki
- Forward: the wiki is the end of the QC checklist chain

---

[QC-LANG-001]: ./qc-language-domain.md
[QC-WF-001]: ../code/qc-workflow.md
[f175606]: https://git.tirsystem.com/TirSystem/SQA-QC-Checklists/commit/f1756061a87b5ec8be09599f1f4142cf1e40c04e
