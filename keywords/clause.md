---
description: |
    A contractual provision drafted exactly as specified — scope, carve-outs, and
    cross-references included. Do not merge it away, relocate its substance, or
    add undeclared qualifiers. Nest `obligation`, `prohibition`, `right`,
    `condition`, `exception`, `breach`, and `source` under it to express the full
    anatomy of the provision.
    Example:
        # clause NonCompete
        ## prohibition Restraint
        The Employee shall not engage in any Competing Business.
        ### exception ExistingHoldings
        Passive holdings of less than 3% in listed companies.
synonyms:
    - provision
    - section
    - article
---

<clause name="{name}" id="{id}">

{body}

{children}

</clause>
