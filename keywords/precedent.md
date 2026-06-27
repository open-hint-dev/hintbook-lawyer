---
description: |
    A model document or fragment whose structure, numbering, and drafting style
    must be replicated. Use it to fix the form of the output; the operative
    blocks still control substance.
    Example:
        # precedent NDA template
        Follow the structure and clause numbering of `precedents/mutual-nda.docx`
        for this agreement.
synonyms:
    - template
    - model
---

<drafting_precedent name="{name}" id="{id}">

{body}

{children}

</drafting_precedent>
