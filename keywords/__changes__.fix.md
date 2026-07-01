---
description: |
    Injected automatically in fix mode when a hint.lock exists: the block-level drift
    report listing which specification blocks changed since the document was last drafted.
    You never write this block yourself — the compiler renders it from the lock.
---

<specification_drift>

The blocks listed below changed since this document was last drafted against the lock. This is the scope of your revision: reconcile the document with these blocks, and treat every other block in the specification as already satisfied.

{body}

Rules for this scope:

- Revise only the provisions governed by a listed block. Leave conforming provisions, numbering, cross-references, and defined terms untouched — they already conform.
- A block marked `inherited` means the document's own spec is unchanged but its folder or root context shifted; re-verify the whole document against that context.
- A block marked `new` has no prior language; draft it in full.
- If restoring a listed block genuinely forces a change to language governed by an unlisted block, make it — but call it out in your report rather than widening the revision silently.

</specification_drift>
