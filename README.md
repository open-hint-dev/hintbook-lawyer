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

## Modes

| Mode                | Invocation                   | The assistant's role                                                                                                                                                 |
| ------------------- | ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `compile` (default) | `hint <paths>`               | Senior attorney **drafting** the document exactly as specified — defined-term discipline, no invented facts, figures, or citations, gaps reported instead of filled. |
| `fix`               | `hint --mode fix <paths>`    | Senior attorney **revising** an existing document that deviates from the spec: smallest conforming edits, conforming provisions preserved, every revision justified. |
| `review`            | `hint --mode review <paths>` | Senior attorney **auditing** a document against the spec: quoted findings with severity, minimal correcting language, an explicit verdict — no edits.                |

Every mode footer reminds the assistant that the output requires review by licensed counsel — the book makes drafting strict, not lawyers optional.

Details → [docs/modes.md](docs/modes.md).

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
