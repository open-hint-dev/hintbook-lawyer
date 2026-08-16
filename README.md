# @openhint/hintbook-lawyer

A [hintbook](https://github.com/open-hint-dev/hint/blob/main/docs/05-hintbooks.md) for [HINT](https://github.com/open-hint-dev/hint#readme) that turns `.hint` specifications into binding **legal drafting prompts** for AI assistants.

HINT is not only for software. The same structure — companion specs, typed blocks, strict borders — serves anyone whose work demands structured thinking. This book applies it to legal documents: you declare parties, defined terms, clauses, obligations, red lines, and prohibitions in plain markdown next to the documents they govern; the compiler turns them into a prompt where every declaration is a binding drafting directive, and the assistant drafts inside the borders instead of improvising around them.

```
matter/
├── hint.yml                  ← project root, registers this book
├── _.hint                    ← the matter: parties' goals, governing law, red lines
└── contracts/
    ├── nda.md.hint           ← defines contracts/nda.md
    └── spa.md.hint           ← defines contracts/spa.md
```

## Installation

```bash
hint install @openhint/hintbook-lawyer
```

This registers the book in your project's `hint.yml`. Then `hint config | claude -p` adds the book's system glossary to your agent context files so assistants know how to read the compiled tags.

## Vocabulary at a glance

Write any of these as a markdown heading — `# keyword Name {#optional_id}` — at any nesting level:

| Area                    | Keywords                                                                                                                                                                              |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Matter context          | `matter`, `jurisdiction`, `party`, `definition`, `recital`, `fact`, `read`, `precedent`, `style`                                                                                      |
| Document structure      | `clause`, `obligation`, `prohibition`, `right`, `condition`, `exception`, `breach`, `source`, `representation`, `remedy`, `indemnity`, `liability`, `termination`, `payment`, `deadline`, `notice`, `dispute`, `exhibit`, `signature` |
| Litigation & argument   | `claim`, `argument`, `authority`                                                                                                                                                      |
| Positions & constraints | `redline`, `never` (banned content), `fallback`, `standard`, `risk`, `checklist`                                                                                                      |
| Drafting discipline     | `example`, `good`, `bad`, `action`, `res`                                                                                                                                             |
| Spec-internal           | `notes` (excluded from compiled output)                                                                                                                                               |

Natural long forms work as synonyms: `provision`/`section`/`article` → `clause`, `warranty` → `representation`, `whereas` → `recital`, `schedule`/`annex`/`appendix` → `exhibit`, `carveout`/`proviso`/`unless`/`notwithstanding` → `exception`, `violation`/`default` → `breach`, `rule` → `redline`, and more.

Full reference → [docs/keywords.md](docs/keywords.md).

## Output

| Invocation                  | What you get                                                                                                                                                     |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `hint <paths>`              | The knowledge that applies to that matter or document, rendered through this book's tags. No persona, no footer — what an assistant already mid-session needs.    |
| `hint --prompt <paths>`     | The same knowledge wrapped in the drafting role and closing checklist: defined-term discipline, no invented facts, figures, or citations, gaps reported not filled. |
| `hint --standalone <paths>` | Implies `--prompt`, and prepends the tag glossary for an assistant that never loaded `AGENTS.md`.                                                                 |

When a `hint.lock` exists and clauses have drifted, `--prompt` output additionally carries the drift list and scopes the revision to it — automatically, with no mode to select.

The `--prompt` footer reminds the assistant that the output requires review by licensed counsel — the book makes drafting strict, not lawyers optional.

Details → [docs/framing.md](docs/framing.md).

> Requires `@openhint/cli` 1.1+. This book no longer ships `--mode fix` / `--mode review`; see the [migration guide](https://github.com/open-hint-dev/hint/blob/main/docs/07-migration.md).

## Emit: the document itself

This hintbook also ships an **emit pack** — `emit/markdown/` — so `hint emit` can assemble the document a matter spec describes, deterministically and without a model:

```bash
hint emit clients/acme/nda/agreement.md      # write it
hint emit --check                            # CI: the document still matches the matter spec
```

Because a legal document *is* prose, this target has no holes at all: emission is complete. The templates assemble the structure and reproduce your text — they never rewrite a sentence.

| Keyword | Renders as |
| --- | --- |
| `matter` | an `#` heading, then its body and children |
| `clause` `exhibit` `signature` | a `##` heading, then its body and children |
| `party` | `**Name** — body` |
| `recital` | `WHEREAS, body` |
| `definition` | the body as written — the defined term is already stated in your own sentence |
| `obligation` `prohibition` `right` `condition` `breach` `remedy` `indemnity` `liability` `termination` `payment` `notice` `deadline` `jurisdiction` `representation` | `**Name.** body` — the run-in label is dropped when the block is unnamed |
| `exception` | `*Exception — Name:* body` |

**What is deliberately left out is the point.** `redline`, `never`, `bad`, `risk`, `fallback`, `precedent`, `authority`, `standard`, and `style` have no template, so they never reach the document. They are your negotiating position and house drafting rules — exactly the material that must not travel to the counterparty in the file you send them. Blocks with no template become constraints on the drafting instead, which is where they belong.

## Example

```markdown
# clause Confidentiality

## obligation NonDisclosure

The Receiving Party shall not disclose Confidential Information to any third party.

### exception Advisors

Disclosure to professional advisors bound by equivalent confidentiality duties.

### breach

Any disclosure outside the declared exceptions.

#### remedy

Injunctive relief without proof of damages.

## deadline Term

Five (5) years from the Effective Date; calendar days.
```

compiles (inside the matter/document context chain, header, and footer) into:

```markdown
<clause name="Confidentiality" id="">

<binding_obligation name="NonDisclosure" id="">

The Receiving Party shall not disclose Confidential Information to any third party.

<exception name="Advisors" id="">

A narrow exception to the enclosing block. It applies exactly as stated and no further — never broaden it, and never let it swallow the rule it qualifies:

Disclosure to professional advisors bound by equivalent confidentiality duties.

</exception>

<breach name="" id="">

What constitutes a breach of the enclosing provision. Draft so that exactly this conduct — no more, no less — triggers the consequences declared inside:

Any disclosure outside the declared exceptions.

<remedy name="" id="">

Injunctive relief without proof of damages.

</remedy>

</breach>

</binding_obligation>

<time_provision name="Term" id="">

Five (5) years from the Effective Date; calendar days.

</time_provision>

</clause>
```

The whole anatomy of a norm — trigger (`condition`), carve-out (`exception`), what breaks it (`breach`), what follows (`remedy`), the law it answers to (`source`), the negotiation order (`fallback`) — is expressed by nesting headings a lawyer already writes. No new syntax, ever.

The `__system__` glossary defines every tag as a binding drafting directive — including the anti-hallucination rules that matter most in legal work: defined terms used with total discipline, and citations never invented.

## License

MIT
