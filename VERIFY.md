# Verification: Store FAQ bot that picks an answer from the help center

Use this checklist to confirm the audit tool works correctly when a stranger runs it against their own failing FAQ setup.

---

## What to verify

A stranger describes their own FAQ bot that misroutes questions. The tool must:

1. **Surface the deciding-check finding** — In this build, the deciding check is **unowned**: no part of the system treats refund/return/cancel words as a priority signal. When a stranger runs /play, the tool should identify which check is the decider for their specimen and explain why.

2. **Demand a numeric measurement** — The tool must not accept vague findings. For the unowned check, the measurement is concrete: count of tickets containing an explicit refund/return/cancel word that get answered with shipping content. The stranger's audit must name a specific number and threshold for their own specimen.

---

## Run the verification

### Step 1: Open /play with a stranger's failing setup

Paste a description of a different FAQ bot failure — same class as the builder's specimen (a bot that latches onto the wrong signal and misroutes questions).

Example stranger paste:
> "Our product support bot answers warranty questions with setup instructions because it sees the model number and assumes the customer wants installation help. Last week a customer asked about a warranty claim for the X200 Router and got a guide on how to reset it."

### Step 2: Confirm the tool walks all five checks

The tool should score each check and identify which one decides the stranger's case — not assume it's the same as the builder's (unowned).

### Step 3: Confirm the tool demands a numeric measurement

The stranger's audit must include:
- A specific count or rate (e.g., "12 warranty questions misrouted to setup content per day")
- A danger line (e.g., "if that exceeds 5 per day")
- A watcher (e.g., "support lead escalates to product team")

If the tool accepts "we'll keep an eye on it" or "monitor for issues," the verification fails.

### Step 4: Confirm the call has an owner

The stranger's ship/hold call must name who owns any condition. Example passing call:
> "Hold. Support engineering lead adds a warranty-keyword check before the product launch. Reopen once warranty/claim/replacement words route correctly."

Example failing call:
> "Hold until it's fixed." (No owner, no specific action)

---

## Builder's specimen as worked example

The tool should show the builder's audit as the worked example:

- **Specimen**: Store FAQ bot that picks an answer from the help center
- **Deciding check**: unowned
- **Call**: Hold. No part of the system currently treats refund/return/cancel words as a priority signal — ship engineering lead needs to add a dedicated check before Black Friday. Reopen once the three specimen sentences all route correctly with refund words present.
- **Tripwire**: Watch the count of tickets containing an explicit refund/return/cancel word that get answered with shipping content. If that exceeds 10 per day during sale week, CX manager escalates to engineering — because that's a fixable, specific miss, not noise.

The stranger sees this discipline applied to their own case — same rigor, their domain.

---

## Pass criteria

| Check | Pass |
|-------|------|
| Tool identifies the deciding check for the stranger's specimen | ☐ |
| Finding includes a numeric measurement, not vague language | ☐ |
| Call names an owner for any condition | ☐ |
| Tripwire has a number, a danger line, and a watcher | ☐ |
| Builder's audit visible as worked example | ☐ |

All boxes checked = verification passes.
