# Audit: Store FAQ bot that picks an answer from the help center

## Specimen

Store FAQ bot that picks an answer from the help center

**What goes wrong if this never gets fixed:** Shoppers get the wrong policy and leave the cart

## Standard

The answer matches the shopper's real ask — not a nearby FAQ about the same product

## Real inputs

**What the real inputs look like:** Short mobile questions with product names in the middle

**Pasted failing messages:**

```
how long do i have to return the Nova Buds after they ship
Nova Buds delivery says Friday — can i still cancel
refund for wrong size on the Trail Jacket, not a shipping question
```

**Source:** Store help-desk chat logs

## Check findings

| Check | Rating |
|-------|--------|
| Unowned | 4 |
| Copies | 2 |
| Room | 1 |
| Stitch | 2 |
| Ablation | 1 |

## Deciding check

**Top crack:** unowned

No part of the system currently treats refund/return/cancel words as a priority signal. The bot latches onto product names ("Nova Buds," "Trail Jacket") and routes to shipping FAQs, ignoring the actual intent words in the question.

## Call

Hold. No part of the system currently treats refund/return/cancel words as a priority signal — ship engineering lead needs to add a dedicated check before Black Friday. Reopen once the three specimen sentences all route correctly with refund words present.

## Tripwire

Watch the count of tickets containing an explicit refund/return/cancel word that get answered with shipping content. If that exceeds 10 per day during sale week, CX manager escalates to engineering — because that's a fixable, specific miss, not noise.
