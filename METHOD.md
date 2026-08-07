# The Five-Check Method

This audit method applies five checks to any setup that routes questions to answers. Each check tests whether the system actually splits the work — or collapses everything into one undifferentiated signal.

---

## PRISM

### **P** — Partition the Space

Does the system divide the input space into distinct regions? For a store FAQ bot, this means: are "refund" questions handled separately from "shipping" questions, or does everything flow through one undifferentiated path?

### **R** — Run in Parallel

Do multiple checks run at the same time, each looking for its own signal? Or does the system run one check, get a match, and stop — missing the stronger signal that would have fired next?

### **I** — Individuate the Pattern

Does each check have its own pattern to match? A check for "refund/return/cancel" words should fire on those words specifically — not on the product name that happens to appear in the same sentence.

### **R** — Stitch the Spectra

When multiple checks fire, does the system combine their signals into a coherent routing decision? Or does the first match win, even when a later match would be more relevant?

### **M** — Map What Each Head Sees

Can you trace which check saw which part of the input? If the bot answered with shipping times, can you see that it latched onto "Nova Buds" and never noticed "return"?

---

## The Collapse-to-Monochrome Anti-Pattern

When a system fails these checks, it collapses to monochrome: every input looks the same, and the system picks the most common answer regardless of what the shopper actually asked.

**Example:** A shopper asks "how long do i have to return the Nova Buds after they ship" — the bot sees "Nova Buds" and "ship," matches the shipping FAQ, and ignores "return." The refund question becomes invisible.

This is the failure mode the five checks are designed to catch: the system has no dedicated path for refund/return/cancel words, so those signals get drowned out by product-name matches.

---

## Using the Checks

Rate each check 1–5:
- **1** = The system has no capability here
- **5** = The system handles this well

The check with the highest score that still fails on real inputs is your deciding check — the one that determines whether you ship, hold, or ship with conditions.
