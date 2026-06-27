---
description: |
    An ordered negotiation fallback to the enclosing position. Conceded only when
    the primary position cannot be held, in the declared order — never past the
    last fallback, never across a red line. Nest under a `redline` (or other
    position); list fallbacks in concession order.
    Example:
        # redline Liability floor
        Cap at 24 months' fees.
        ## fallback
        1. 18 months' fees
        2. 12 months' fees (last acceptable)
synonyms:
    - fallbacks
    - alternative
    - alternatives
---

<fallback_position name="{name}" id="{id}">

A fallback to the enclosing position, for negotiation or revision. Concede to it only when the primary position cannot be held, in the order declared — and never retreat past the last declared fallback or across any red line:

{body}

{children}

</fallback_position>
