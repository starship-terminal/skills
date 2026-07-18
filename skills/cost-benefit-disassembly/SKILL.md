---
name: cost-benefit-disassembly
version: 1.0.0
description: |
  Use when a solution is bundled up and the user must take it or leave it as
  a whole. Decompose the bundle into component costs and benefits, evaluate
  each independently, re-assemble with only justified pairs. Goal: the best
  cost/benefit pairing, which may mean increasing one cost to unlock several
  benefits, not "cost down."
triggers:
  - "is this worth it"
  - "decompose the trade-offs"
  - "cost-benefit bundle to restructure"
  - "what am I really paying for"
  - "quote too high"
tools: []
mutating: false
family: first-principles
---

# Cost-Benefit Disassembly

Decompose a solution into its component costs and benefits, evaluate each independently, then re-assemble optimally rather than treating the package as take-it-or-leave-it.

## Contract

- The skill lists every cost the current approach incurs (money, time, risk, attention, opportunity).
- The skill lists every benefit it delivers (primary value plus secondary gains).
- The skill questions whether each cost is *necessary* for that benefit, or only attached to it.
- The skill identifies pairs that can be restructured — same benefit at lower cost, or higher benefit at same cost.
- The skill proposes a re-assembled design with only justified cost/benefit pairs.

## Phases

1. **State the bundle.** What's being proposed / currently in place.
2. **List every cost.** Money, time, risk, attention, opportunity cost. Be exhaustive.
3. **List every benefit.** Primary value, secondary gains, intangibles. Be exhaustive.
4. **For each line item, ask: is this cost necessary for that benefit, or only attached to it?** Mark each.
5. **Identify restructure pairs.** Same benefit at lower cost? Higher benefit at same cost?
6. **Propose the re-assembled design.** Only justified cost/benefit pairs.

## Output Format

```
BUNDLE: <one line>

COSTS:
  - <cost 1>
  - <cost 2>
  ...

BENEFITS:
  - <benefit 1>
  - <benefit 2>
  ...

DISASSEMBLY TABLE:
| Component   | Cost            | Benefit          | Necessary? | Restructure? | New design            |
|-------------|-----------------|------------------|------------|--------------|----------------------|
| <comp 1>    | <cost>          | <benefit>        | yes/no     | yes/no       | <restructured pair> |
| <comp 2>    | ...             | ...              | ...        | ...          | ...                  |

REASSEMBLED DESIGN:
  <prose description with only justified pairs>
```

## Worked example (bundle: vendor SaaS quote at $X/month)

```
BUNDLE: Vendor SaaS at $50K/year, includes analytics, SSO, 24/7 support, training seats, dedicated CSM

COSTS:
  - $50K/year license
  - 2 weeks onboarding time
  - SSO setup effort (IT, one-time)
  - Lock-in: 12-month contract
  - Data residency: vendor-controlled

BENEFITS:
  - Analytics dashboard (primary)
  - SSO (primary)
  - 24/7 support
  - 4 training seats
  - Dedicated customer success manager

DISASSEMBLY TABLE:
| Component   | Cost              | Benefit            | Necessary? | Restructure? | New design                |
|-------------|-------------------|--------------------|------------|--------------|---------------------------|
| License     | $50K/yr           | All above          | partial    | yes          | Modular — pay per feature |
| SSO         | setup effort      | SSO                | yes        | no           | Keep                      |
| 24/7 suppt  | in license cost   | Support            | no         | yes          | Drop to business hrs       |
| 4 training  | in license cost   | Training           | maybe      | yes          | 2 seats, half cost        |
| Dedicated CSM| in license cost  | White-glove        | no         | yes          | Drop — shared CSM enough  |

REASSEMBLED DESIGN:
  Negotiate modular pricing: analytics + SSO only, business-hours support,
  2 training seats, shared CSM. Expected cost ~$30K/yr — same primary
  benefit at 40% lower cost. Keep SSO setup effort — it's necessary for the
  SSO benefit. Drop the dedicated CSM — the cost is real, the benefit is
  marginal at our scale.
```

## Anti-Patterns

- Treating "cost down" as the goal. Goal is best cost/benefit pairing. Increasing one cost to unlock several benefits is a win.
- Hiding intangible costs (risk, lock-in, attention). They're real and often dominate.
- Listing only primary benefits. Secondary gains (training, network, signal) often justify keeping a cost.
- Skipping the "Necessary?" column. Without it, the restructure has no logic — it's just cost-cutting.

## Tools Used

(none — pure reasoning skill)
