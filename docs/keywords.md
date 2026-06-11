# Keyword Reference

Every keyword in this hintbook, the tag it compiles into, and how to use it. Write keywords as markdown headings — `# keyword Name {#optional_id}` — at any nesting level; heading depth nests blocks into their parents (an `obligation` under a `clause`, a `deadline` under an `obligation`).

---

## Matter context

| Keyword | Synonyms | Compiles to | Use it for |
| --- | --- | --- | --- |
| `matter` | `case`, `engagement` | `<matter_overview>` | The matter itself: parties' goals, deal background, scope of engagement. Informs every drafting decision. |
| `jurisdiction` | `law` | `<governing_law_and_jurisdiction>` | Governing law and forum. Drafting follows its conventions and mandatory rules; unenforceable requests get flagged. |
| `party` | `parties` | `<party>` | A party: exact legal name, role, capacity — used consistently, never varied. |
| `definition` | `term`, `terms`, `definitions` | `<defined_term>` | A defined term: defined once, capitalized as defined, no synonyms for the concept. |
| `recital` | `whereas`, `background` | `<recital>` | Background for the recitals — context and intent, never operative obligations. |
| `fact` | `facts` | `<established_fact>` | A fact of the matter: relied on as stated, never contradicted or embellished. |
| `read` | | `<read_it>` | Documents the assistant must open and read before drafting anything that relies on them. |
| `precedent` | `template`, `model` | `<drafting_precedent>` | A model document or fragment whose structure, numbering, and style must be replicated. |
| `style` | `tone`, `voice` | `<drafting_style>` | Style and tone requirements for all drafted text. |

## Document structure

| Keyword | Synonyms | Compiles to | Use it for |
| --- | --- | --- | --- |
| `clause` | `provision`, `section`, `article` | `<clause>` | A contractual provision drafted exactly as specified — scope, carve-outs, cross-references. |
| `obligation` | `obligations`, `duty`, `covenant` | `<binding_obligation>` | What a party must do: clear mandatory language, unambiguous who/what/when. |
| `prohibition` | `prohibitions`, `restriction`, `restrictions` | `<prohibited_conduct>` | What a party must not do: clear prohibitory language ("shall not"), unambiguous who is bound and what is prohibited. |
| `right` | `rights`, `entitlement` | `<granted_right>` | A right granted: holder, scope, conditions, duration — neither broadened nor narrowed. |
| `condition` | `conditions` | `<condition>` | A condition precedent or subsequent: trigger, effect, consequence of failure. |
| `exception` | `carveout`, `carve-out`, `proviso`, `unless`, `notwithstanding` | `<exception>` | A narrow carve-out to the enclosing obligation, prohibition, right, or clause. Applies exactly as stated — never swallows the rule it qualifies. |
| `breach` | `violation`, `default` | `<breach>` | What constitutes breach of the enclosing provision. Nest a `remedy` inside to declare the consequence. |
| `source` | `basis`, `statute`, `regulation` | `<legal_basis>` | The law or rule the enclosing provision exists to satisfy. Conflicts between spec and source get flagged, never silently resolved. |
| `representation` | `warranty`, `warranties` | `<representation_and_warranty>` | A rep or warranty with its knowledge/materiality qualifiers exactly as declared. |
| `remedy` | `remedies` | `<remedy>` | Remedies for the described breach — none added, none waived. |
| `indemnity` | `indemnification` | `<indemnification>` | Who indemnifies whom, covered losses, exclusions, procedure. |
| `liability` | `limitation` | `<liability_allocation>` | Caps, exclusions, carve-outs — declared amounts only. |
| `termination` | | `<termination_provision>` | Grounds, notice, and effects of termination. |
| `payment` | `fee`, `fees`, `consideration` | `<payment_terms>` | Amounts, currency, schedule, late-payment consequences. Missing figures are gaps, not blanks to fill. |
| `deadline` | `period`, `periods`, `timing` | `<time_provision>` | Deadlines and periods: exact durations, triggers, business vs calendar days. |
| `notice` | `notices` | `<notice_requirements>` | How notices are validly given: addressees, channels, deemed receipt. |
| `dispute` | `arbitration` | `<dispute_resolution>` | Forum and process: courts or arbitration, seat, rules, language. |
| `exhibit` | `schedule`, `annex`, `appendix`, `attachment` | `<exhibit>` | An attachment, referenced in the body under its declared designation. |
| `signature` | `execution` | `<execution_block>` | Execution requirements: signatories, capacity, witnesses, notarization. |

## Litigation & argument

| Keyword | Synonyms | Compiles to | Use it for |
| --- | --- | --- | --- |
| `claim` | `claims`, `count` | `<claim>` | A cause of action: its elements and supporting facts as declared, and only those. |
| `argument` | `arguments` | `<legal_argument>` | An argument developed issue → rule → application → conclusion from the declared body. |
| `authority` | `citation`, `citations`, `caselaw` | `<legal_authority>` | Authorities to cite — precisely, only for the stated point. Unverifiable citations are reported, never invented. |

## Positions & constraints

| Keyword | Synonyms | Compiles to | Use it for |
| --- | --- | --- | --- |
| `redline` | `redlines`, `rule`, `rules` | `<non_negotiable_position>` | Client red lines, honored without exception in every provision. The template carries explicit never-trade-away language. |
| `never` | `forbidden`, `banned` | `<strict_prohibition>` | Content that must never appear in or be permitted by the document — enforced with the strongest language in the book. |
| `fallback` | `fallbacks`, `alternative` | `<fallback_position>` | An ordered negotiation fallback to the enclosing position. Conceded in declared order, never past the last one, never across a red line. |
| `standard` | `standards`, `boilerplate` | `<required_drafting_standards>` | Required boilerplate and drafting standards, applied without substitution. |
| `risk` | `risks` | `<risk_to_mitigate>` | A known risk the document must address — the report must say which provision mitigates it. |
| `checklist` | `verification` | `<verification_checklist>` | Items that must each hold true in the final document, verified explicitly. |

## Drafting discipline

Cross-cutting guardrails that keep the assistant inside strict borders:

| Keyword | Synonyms | Compiles to | Use it for |
| --- | --- | --- | --- |
| `example` | `examples`, `sample` | `<drafting_example>` | A worked example of the expected output — form to match, not substance to copy. |
| `good` | `prefer`, `preferred` | `<enforced_drafting_patterns>` | Mandatory drafting patterns, applied consistently in every provision. |
| `bad` | `avoid` | `<prohibited_drafting_patterns>` | Drafting patterns that must never be used — absolute, even where a precedent uses them. |
| `action` | `procedure`, `procedures` | `<reusable_procedure>` | A step-by-step procedure executed exactly as written when invoked — conflict checks, defined-term sweeps, filing routines. |
| `res` | `resource`, `resources` | `<static_asset>` | Material used verbatim — letterhead, riders, standard schedules. Never retyped, paraphrased, or "improved". |

## Spec-internal

| Keyword | Synonyms | Compiles to | Use it for |
| --- | --- | --- | --- |
| `notes` | | *(nothing — excluded)* | Author-facing notes — open questions for the client, reminders — that must never reach the compiled prompt. |

---

## Nesting patterns

The whole anatomy of a legal norm is expressed by nesting — no new syntax, just heading depth:

```markdown
# clause NonCompete

## prohibition Restraint

The Employee shall not engage in any Competing Business.

### condition Scope

Applies within the Territory during the Restricted Period.

### exception ExistingHoldings

Passive holdings of less than 3% in listed companies.

### breach

Any breach of the Restraint, directly or through affiliates.

#### remedy

Injunctive relief without proof of damages.

### source

Enforceability limits on restraints of trade under the governing law.
```

| Pattern | Meaning |
| --- | --- |
| `condition` under a provision | when the provision applies — its trigger. |
| `exception` under a provision | a carve-out — applies exactly as stated, never swallows the rule. |
| `breach` → `remedy` chain | what breaks the provision, and what follows when it breaks. |
| `source` under a provision | why the provision exists — the law it must satisfy; conflicts get flagged. |
| `fallback` under a position | the negotiation order — concede in sequence, never past the last fallback. |

## Choosing keywords

- **Declare terms before you use them.** A `definition` block per defined term gives the assistant something it can enforce mechanically — consistent capitalization, no synonyms.
- **Name the bound party.** Every `obligation`, `prohibition`, and `right` should say which declared `party` performs, refrains, or holds it — a deontic block with no identifiable bearer is reported as a gap.
- **Duties not to act go in `prohibition`; banned document content goes in `never`; client red lines go in `redline`.** All three carry explicit enforcement language; prose buried in a clause body does not.
- **Figures belong in `payment` and `deadline` blocks.** The glossary forbids inventing amounts and dates — but only declared blocks make a missing figure visibly a gap.
- **Use `authority` for anything cited, `source` for anything complied with.** `authority` is what the document argues from; `source` is what a provision answers to. Both are anti-hallucination guards: cite precisely or report the gap.
- **Unknown keywords don't fail** — their bodies pass through as plain markdown — but only declared vocabulary carries the binding tag language defined in the system glossary.
