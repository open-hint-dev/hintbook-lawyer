# Modes

A mode selects the role wrapper around the compiled specification — who the assistant is and what "done" means. The keyword templates are shared across modes; what changes is the `__header__` that opens the prompt and the `__footer__` that closes it.

```bash
hint <paths>                  # compile (default) — draft
hint --mode fix <paths>       # revise
hint --mode review <paths>    # audit
```

Any instruction missing from a mode falls back to the default mode, so each mode only defines what differs.

---

## `compile` — draft (default)

The assistant is a **senior attorney drafting a legal document from a binding specification**.

- Read the whole specification first: parties, defined terms, governing law, red lines.
- Draft exactly what is specified; fill silence with the conventions of the declared governing law and document type — never with invented rights, obligations, or qualifiers.
- Total defined-term discipline; no invented facts, names, amounts, dates, or citations — gaps are reported, not filled.
- Complete documents only: no bracketed stubs unless the spec declares them.
- Conflicts between blocks: the more specific block wins, and the conflict is reported.

The footer is a verification checklist — every block reflected, defined terms consistent, figures exact, prohibitions absent, cross-references resolving — followed by a report mapping document sections to specification blocks, listing gaps with their risk, and noting that the draft requires review by licensed counsel.

## `fix` — revise

The assistant is a **senior attorney revising an existing document against the specification**, anchored on one principle: _where the document and the specification disagree, the document is wrong_.

- Diagnose each deviation and its violated block before proposing language.
- Smallest conforming revision; structure, numbering, defined terms, and style preserved.
- Conforming provisions are never broken; gaps are never papered over with invented content.
- A defective specification — unlawful, contradictory, unenforceable — stops the revision and gets reported.

The footer requires each revision reported as: violated block → original language → revised language → rationale, plus confirmation that nothing else changed.

## `review` — audit

The assistant is a **senior attorney reviewing a document against the specification** — findings, never redlines.

- Walks the specification block by block; quotes the document's exact language in every finding.
- Hunts prohibited content and red-line violations explicitly.
- Judges against the spec and the mandatory rules of the declared governing law — not drafting taste.

The footer defines the report: findings ordered by severity (`violation` / `gap` / `risk`) with document section, quoted language, related block, and minimal correcting language — closed by an explicit conforms / does-not-conform verdict.

---

## Running instructions

| Instruction  | Renders                                                                                                                                                                    |
| ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `__file__`   | `<document_context path="...">` around each document spec — `path` is the target document (e.g. `contracts/nda.md`).                                                       |
| `__folder__` | `<matter_context path="...">` around each folder — `path` is the folder (`.` for the matter root). Matter context visibly encloses every document beneath it.              |
| `__system__` | The tag glossary. Not part of compiled prompts — `hint config` emits it for `AGENTS.md` / `CLAUDE.md`, teaching assistants that every tag is a binding drafting directive. |

## Adding a mode

Create `__header__.<mode>.md` and `__footer__.<mode>.md` in `keywords/` — the file-name suffix is the mode name (e.g. `__header__.negotiate.md` for a `--mode negotiate` that drafts counter-positions). Override individual keywords per mode the same way when one needs different rendering; otherwise the default-mode templates apply.
