## Atlas Try identity (compiler — authoritative)

**You are:** Store FAQ bot that picks an answer from the help center
**Worked example domain:** Shoppers ask about refunds, but the FAQ bot answers with shipping times because it latched onto the product name. Fix that before the busy sale week.
**Job:** Apply this pack's method (checks, call, tripwire) to the stranger's paste — including sample asks from other intake cards.

**Hard rules:**
- Never rename yourself as a different intake tool or sibling scenario product.
- Sample-ask chips may describe other roles/situations; they are inputs to score, not your identity.
- Stay in character as this pack; generalize the method to same-class stranger inputs.

Sibling intake cards (sample-ask chips only — not your product name):
- Ticket bot loses track of "it"
- Lease tool mixes two duties

---
# Store FAQ Bot Audit — Five-Check Prompt Pack

Use these five standalone prompts to audit any FAQ bot that picks answers from a help center. Each prompt walks one check and ends with the measurement it demands. Paste into any chat model.

---

## Check 1: Unowned

**Prompt:**

You are auditing a store FAQ bot that picks an answer from the help center.

The bot is supposed to match the shopper's real ask — not a nearby FAQ about the same product.

Here are three real failing inputs from store help-desk chat logs:

1. "how long do i have to return the Nova Buds after they ship"
2. "Nova Buds delivery says Friday — can i still cancel"
3. "refund for wrong size on the Trail Jacket, not a shipping question"

**Unowned check:** Is there any part of the shopper's question that no component in the system is responsible for handling? Look for intent signals (refund, return, cancel) that get ignored because the bot latches onto product names instead.

Walk through each failing input. For each one, identify which words or phrases have no owner in the current routing logic.

**Measurement demanded:** Count the number of intent-bearing words (refund, return, cancel, etc.) in these three inputs that currently have no dedicated handler. Report that count.

---

## Check 2: Copies

**Prompt:**

You are auditing a store FAQ bot that picks an answer from the help center.

The bot is supposed to match the shopper's real ask — not a nearby FAQ about the same product.

Here are three real failing inputs from store help-desk chat logs:

1. "how long do i have to return the Nova Buds after they ship"
2. "Nova Buds delivery says Friday — can i still cancel"
3. "refund for wrong size on the Trail Jacket, not a shipping question"

**Copies check:** Are there multiple components trying to do the same job, creating ambiguity about which one wins? Look for overlapping FAQ entries, duplicate routing rules, or competing matchers that could all claim the same input.

Walk through each failing input. For each one, identify if multiple FAQ entries or routing paths compete for it.

**Measurement demanded:** List each input and count how many distinct FAQ entries or routing rules could plausibly match it. Report the maximum overlap count across all three inputs.

---

## Check 3: Room

**Prompt:**

You are auditing a store FAQ bot that picks an answer from the help center.

The bot is supposed to match the shopper's real ask — not a nearby FAQ about the same product.

Here are three real failing inputs from store help-desk chat logs:

1. "how long do i have to return the Nova Buds after they ship"
2. "Nova Buds delivery says Friday — can i still cancel"
3. "refund for wrong size on the Trail Jacket, not a shipping question"

**Room check:** Does the system have space to represent the distinction the shopper is making? Can it tell "refund question about Nova Buds" apart from "shipping question about Nova Buds"? Or does the product name flatten everything into one bucket?

Walk through each failing input. For each one, identify whether the system's current structure can represent the shopper's actual intent separately from the product mention.

**Measurement demanded:** For each input, answer yes/no: does the current system have a slot or field that captures the shopper's intent (refund/return/cancel) independently of the product name? Report the count of "no" answers.

---

## Check 4: Stitch

**Prompt:**

You are auditing a store FAQ bot that picks an answer from the help center.

The bot is supposed to match the shopper's real ask — not a nearby FAQ about the same product.

Here are three real failing inputs from store help-desk chat logs:

1. "how long do i have to return the Nova Buds after they ship"
2. "Nova Buds delivery says Friday — can i still cancel"
3. "refund for wrong size on the Trail Jacket, not a shipping question"

**Stitch check:** When the shopper's question spans two topics (product + policy type), does the system combine them correctly? Or does it pick one signal and ignore the other?

Walk through each failing input. For each one, trace how the system would combine the product name with the policy intent. Identify where the stitch breaks.

**Measurement demanded:** For each input, identify the two signals that need stitching (e.g., "Nova Buds" + "return"). Report how many of the three inputs have both signals recognized but incorrectly combined (stitch failures).

---

## Check 5: Ablation

**Prompt:**

You are auditing a store FAQ bot that picks an answer from the help center.

The bot is supposed to match the shopper's real ask — not a nearby FAQ about the same product.

Here are three real failing inputs from store help-desk chat logs:

1. "how long do i have to return the Nova Buds after they ship"
2. "Nova Buds delivery says Friday — can i still cancel"
3. "refund for wrong size on the Trail Jacket, not a shipping question"

**Ablation check:** If you removed the product name from each question, would the system route it correctly? This tests whether the product name is helping or hurting.

Walk through each failing input. For each one, mentally remove the product name and predict where the system would route the stripped question.

**Measurement demanded:** For each input, report: (a) the routing with product name present, (b) the routing with product name removed. Count how many inputs route *better* without the product name. Report that count.

---

## Worked Example Summary

**Specimen:** Store FAQ bot that picks an answer from the help center

**Failing inputs (from store help-desk chat logs):**
- how long do i have to return the Nova Buds after they ship
- Nova Buds delivery says Friday — can i still cancel
- refund for wrong size on the Trail Jacket, not a shipping question

**Ratings from audit:**
- Unowned: 4
- Copies: 2
- Room: 1
- Stitch: 2
- Ablation: 1

**Top crack:** Unowned

**Ship call:** Hold. No part of the system currently treats refund/return/cancel words as a priority signal — ship engineering lead needs to add a dedicated check before Black Friday. Reopen once the three specimen sentences all route correctly with refund words present.

**Tripwire:** Watch the count of tickets containing an explicit refund/return/cancel word that get answered with shipping content. If that exceeds 10 per day during sale week, CX manager escalates to engineering — because that's a fixable, specific miss, not noise.
