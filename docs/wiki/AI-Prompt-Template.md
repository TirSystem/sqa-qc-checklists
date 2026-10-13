# AI Prompt Template

🌐 **English** · [Dansk](AI-Prompt-Template-da) · [Bahasa Melayu](AI-Prompt-Template-ms)

Prompts for reviewing with an AI agent. Run the review in a **fresh session**
if the same agent wrote the document: the reviewer must not be the author.

## Review a document

```text
Review <path/to/document.md> against the checklist <path/to/qc-type.md>.
For every numbered criterion give Pass, Fail or N-A with the evidence (quote
the line of the document). Then list the failed Mandatory criteria first,
give a verdict (Go, Go-with-conditions, No-Go) and the smallest change that
would make each failed criterion pass. Do not edit the document.
```

## Review code

```text
Review the changes in <path or diff> against <path/to/qc-programming-lang.md>
and our coding conventions in <path>. Report each criterion as Pass, Fail or
N-A with file and line. Do not fix anything; list the findings by severity.
```

## Review the language and domain

```text
Review <document> against qc-language-domain.md. The Product Owner's language
is <language> and the domain is <domain>. Check that every PO term used in the
document appears in the dictionary <path> and that no IT term leaks into a
PO-facing section. List each mismatch with the line.
```

## Re-review after fixes

```text
Re-review only the criteria that failed in <previous review record>. For each,
state whether the new <document> now passes and quote the evidence.
```

## Tips

- Give the agent **one** checklist per review.
- Ask for evidence per criterion; a bare "Pass" is not a review.
- Treat the agent's verdict as input. The reviewer decides.
