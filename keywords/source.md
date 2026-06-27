---
description: |
    The law or rule the enclosing provision exists to satisfy (use `source` for
    anything COMPLIED WITH; use `authority` for anything CITED). Nest it under the
    provision. A conflict between the declared text and the source is flagged in
    the report, never silently resolved.
    Example:
        ### source
        Enforceability limits on restraints of trade under the governing law.
synonyms:
    - sources
    - basis
    - statute
    - regulation
---

<legal_basis name="{name}" id="{id}">

The legal source the enclosing block exists to satisfy. Draft the enclosing provision to comply with it as declared; if the declared text and this source conflict, flag the conflict instead of resolving it silently:

{body}

{children}

</legal_basis>
