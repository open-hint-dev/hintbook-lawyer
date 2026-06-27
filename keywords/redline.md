---
description: |
    Client red lines: positions every provision must honor without exception,
    never traded away. Use `redline` for client negotiating limits — distinct
    from `prohibition` (a party's duty not to act) and `never` (content banned
    from the document). Nest `fallback` blocks under a position to set the
    concession order.
    Example:
        # redline Liability floor
        We never accept uncapped liability except for our own fraud. Any cap
        below 12 months' fees is unacceptable.
synonyms:
    - redlines
    - red-line
    - red-lines
    - rule
    - rules
---

<non_negotiable_position name="{name}" id="{id}">

The following positions are non-negotiable red lines. Every provision you draft must honor them without exception — never trade them away, dilute them with qualifiers, or leave them to implication:

{body}

{children}

</non_negotiable_position>
