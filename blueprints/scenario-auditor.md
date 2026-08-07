# Store FAQ Bot Auditor

**One-paste spec for auditing FAQ bots that misroute refund/return/cancel questions**

---

## What this auditor checks

A store FAQ bot that picks an answer from the help center. When shoppers ask about refunds, the bot answers with shipping times because it latched onto the product name.

**Stakes:** Shoppers get the wrong policy and leave the cart

**Pass standard:** The answer matches the shopper's real ask — not a nearby FAQ about the same product

---

## The failing inputs

Real questions from store help-desk chat logs:

1. `how long do i have to return the Nova Buds after they ship`
2. `Nova Buds delivery says Friday — can i still cancel`
3. `refund for wrong size on the Trail Jacket, not a shipping question`

**Input pattern:** Short mobile questions with product names in the middle

---

## Five-check audit scores

| Check | Score (1–5) | What it measures |
|-------|-------------|------------------|
| Unowned | 4 | Does any part of the system own refund/return/cancel as a priority signal? |
| Copies | 2 | Are there duplicate or competing FAQ entries that confuse routing? |
| Room | 1 | Does the bot have enough context to distinguish refund from shipping? |
| Stitch | 2 | Do the routing steps hand off cleanly, or does intent get lost? |
| Ablation | 1 | If you remove the product name, does the bot still misroute? |

---

## Top crack

**Unowned** — No part of the system currently treats refund/return/cancel words as a priority signal.

---

## Ship call

Hold. No part of the system currently treats refund/return/cancel words as a priority signal — ship engineering lead needs to add a dedicated check before Black Friday. Reopen once the three specimen sentences all route correctly with refund words present.

---

## Tripwire

Watch the count of tickets containing an explicit refund/return/cancel word that get answered with shipping content. If that exceeds 10 per day during sale week, CX manager escalates to engineering — because that's a fixable, specific miss, not noise.

---

## How a stranger uses this auditor

Paste your own FAQ bot failure:
1. Name the bot and what it's supposed to do
2. Describe what goes wrong and who gets hurt
3. Paste three real failing inputs from your logs

The auditor walks all five checks against your specimen, scores each, identifies your top crack, and returns:
- A ship/hold call with an owner on any condition
- A tripwire with a number, a danger line, and who watches it

---

## Worked example

**Specimen:** Store FAQ bot that picks an answer from the help center

**Failing input:** `refund for wrong size on the Trail Jacket, not a shipping question`

**What happened:** Bot matched "Trail Jacket" to shipping FAQ instead of recognizing "refund" and "wrong size" as the actual intent.

**Top crack finding:** Unowned — the word "refund" has no priority weight; product name matching overrides it.

**Measurement to confirm:** Run the three specimen sentences with refund/return/cancel words present. If all three route to refund policy (not shipping), the check passes.

**Call:** Hold until engineering lead adds a dedicated refund-word check.

**Tripwire:** 10+ refund-word tickets answered with shipping content per day → CX manager escalates to engineering.
