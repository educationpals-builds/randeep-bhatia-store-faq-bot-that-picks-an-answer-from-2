# Store FAQ bot that picks an answer from the help center

Shoppers ask about refunds, but the FAQ bot answers with shipping times because it latched onto the product name. This audit checks whether the bot's routing actually splits refund questions from shipping questions before the busy sale week.

## Verdict

**Hold.** No part of the system currently treats refund/return/cancel words as a priority signal — ship engineering lead needs to add a dedicated check before Black Friday. Reopen once the three specimen sentences all route correctly with refund words present.

## Tripwire

Watch the count of tickets containing an explicit refund/return/cancel word that get answered with shipping content. If that exceeds 10 per day during sale week, CX manager escalates to engineering — because that's a fixable, specific miss, not noise.

## The standard

The answer matches the shopper's real ask — not a nearby FAQ about the same product

## One-paste rebuild block

Copy these three real messages from store help-desk chat logs and run them through the bot. All three must route to refund/return/cancel content — not shipping:

```
how long do i have to return the Nova Buds after they ship
Nova Buds delivery says Friday — can i still cancel
refund for wrong size on the Trail Jacket, not a shipping question
```

If any of these still return shipping answers after the fix, the check fails.

## What this audit covers

This audit walks five checks against the FAQ bot to see whether it splits refund questions from shipping questions. The deciding check was **unowned** — no part of the system currently owns the job of recognizing refund/return/cancel words as a priority signal.

See [charter.md](charter.md) for the full audit with check ratings and findings.

See [METHOD.md](METHOD.md) for the five-check framework.

See [VERIFY.md](VERIFY.md) to run verification yourself.

<!-- educationpals-build-verified -->
