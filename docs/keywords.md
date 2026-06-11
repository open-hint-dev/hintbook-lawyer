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
| `right` | `rights`, `entitlement` | `<granted_right>` | A right granted: holder, scope, conditions, duration — neither broadened nor narrowed. |
| `condition` | `conditions` | `<condition>` | A condition precedent or subsequent: trigger, effect, consequence of failure. |
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
| `rule` | `rules`, `redline`, `redlines` | `<non_negotiable_position>` | Client red lines, honored without exception in every provision. The template carries explicit never-trade-away language. |
| `prohibition` | `restriction`, `restrictions` | `<strict_prohibition>` | Content that must never appear in or be permitted by the document — enforced with the strongest language in the book. |
| `standard` | `standards`, `boilerplate` | `<required_drafting_standards>` | Required boilerplate and drafting standards, applied without substitution. |
| `risk` | `risks` | `<risk_to_mitigate>` | A known risk the document must address — the report must say which provision mitigates it. |
| `checklist` | `verification` | `<verification_checklist>` | Items that must each hold true in the final document, verified explicitly. |

## Spec-internal

| Keyword | Synonyms | Compiles to | Use it for |
| --- | --- | --- | --- |
| `notes` | | *(nothing — excluded)* | Author-facing notes — open questions for the client, reminders — that must never reach the compiled prompt. |

---

## Choosing keywords

- **Declare terms before you use them.** A `definition` block per defined term gives the assistant something it can enforce mechanically — consistent capitalization, no synonyms.
- **Red lines go in `rule`, prohibited content in `prohibition`.** Both carry explicit enforcement language; prose buried in a clause body does not.
- **Figures belong in `payment` and `deadline` blocks.** The glossary forbids inventing amounts and dates — but only declared blocks make a missing figure visibly a gap.
- **Use `authority` for anything cited.** Its template is the anti-hallucination guard: cite precisely or report the gap.
- **Unknown keywords don't fail** — their bodies pass through as plain markdown — but only declared vocabulary carries the binding tag language defined in the system glossary.
