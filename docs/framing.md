# Prompt framing

By default `hint <paths>` returns the knowledge that applies to a matter or document and nothing else — no persona, no closing checklist. That is what an assistant already mid-session needs.

For an assistant starting cold, `hint --prompt <paths>` wraps that same knowledge in this book's framing:

```bash
hint contracts/nda.md                      # knowledge only (default)
hint --prompt contracts/nda.md             # + drafting role and closing checklist
hint --standalone contracts/nda.md         # implies --prompt, + the tag glossary
```

Framing is a wrapper, not part of the compiled form. Removing it loses no recorded knowledge.

---

## `__header__` — the role

Opens `--prompt` output. Casts the assistant as a senior attorney drafting from a binding specification: defined terms used with total discipline, no invented facts, figures, parties, or citations, and gaps reported rather than filled with something plausible.

## `__footer__` — the close

Ends `--prompt` output with a verification walk over the declared parties, clauses, obligations, and exhibits, a required report of what was drafted and where the spec was silent, and the standing reminder that the output requires review by licensed counsel.

## `__changes__` — reconciliation

Rendered inside `--prompt` output **only** when a `hint.lock` exists and blocks have drifted since the document was generated. It carries the block-level drift list and scopes the revision to it: change only the provisions governed by a listed block and leave conforming language untouched.

This is contextual, not selected. There is no mode to pass — HINT renders it exactly when there is drift to reconcile.

> **Note for users of `@openhint/cli` 1.0.x.** This book previously shipped `fix` (revise) and `review` (audit) modes selected with `--mode`. The mode system was removed in 1.1: the mechanical half of `review` is `hint verify` (deterministic and token-free), and `fix` became the automatic behaviour described above. See the [migration guide](https://github.com/open-hint-dev/hint/blob/main/docs/07-migration.md).

## `__system__` — the tag glossary

The authoritative meaning of every tag this book renders. `hint apply` installs it once into `AGENTS.md` / `CLAUDE.md`, so the default output can be knowledge alone; `--standalone` prepends it for an assistant that never loaded those files.
