# Boxes and rarities

[Documentation home](README.md) · Reviewed October 15, 2026

Characters and cars enter the official collection through fleet boxes or eligible player-market purchases. The shop does not sell a randomly selected individual character or car as a separate direct-hire product.

| Package | HTW price | Contents | Availability |
| --- | ---: | --- | --- |
| Basic | 25,000 | One Common character and one Common car | First entry and later purchases |
| Five boxes | 125,000 | Five characters and five cars; all rarities possible | First entry and later purchases |
| Premium | 500,000 | One character and one car; **both Epic or higher** | After initial entry |

Every paid purchase carries **0.0005 SOL**, plus the quoted network fee. Buying the Five-box package is one purchase, so its studio fee is 0.0005 SOL for the package. Opening or replaying delivered contents is free. There is no daily purchase/opening quota. Full collection capacity or unresolved payment orders can temporarily prevent another purchase.

## Exact probabilities

These probabilities apply **separately to each character and each car**, not to the pair as a single rarity. A Five-box package contains ten independent item rarity draws. It does not guarantee a Rare item. Repeated definitions and repeated rarities are possible; no pity counter is implemented.

| Rarity | Basic, per item | Five boxes / referral box, per item | Premium, per item |
| --- | ---: | ---: | ---: |
| Common | 100% | 82.87% | 0% |
| Uncommon | 0% | 10.36% | 0% |
| Rare | 0% | 5.18% | 0% |
| Epic | 0% | 1.04% | 70% |
| Legendary | 0% | 0.51% | 29.96% |
| Mythic | 0% | 0.035% | 0.035% |
| Exotic | 0% | 0.005% | 0.005% |

Each column totals 100%. Within a selected rarity and item kind, the server chooses among that tier's available definitions. The catalog contains ten characters and ten cars in each tier from Common through Legendary, and five of each in Mythic and Exotic: **60 characters and 60 cars** overall.

Box draws use server-side random sampling and saved results. Reopening a delivered reveal does not reroll it. This is **not an on-chain verifiable-randomness system**. The game service remains responsible for applying the published distribution and delivering the saved results. A cinematic reveal presents the canonical delivery; it is not evidence of payment on its own.

## What rarity changes

Rarity is a collection tier. Individual definitions also have different attributes and contextual effects; two items of the same rarity need not have identical utility. See the [complete catalog](catalog.md) for attributes and perk descriptions.

Rarity also affects **nominal HTW activity weighting**, before funded allocation:

| Rarity | Weight |
| --- | ---: |
| Common | 1× |
| Uncommon | 2.5× |
| Rare | 6× |
| Epic | 10× |
| Legendary | 15× |
| Mythic | 20× |
| Exotic | 40× |

The assigned character and car weights are averaged. Definition-specific attribute and triggered-event bonuses are added separately, capped at 25% in aggregate, before the pair weight is applied. These are weights in the game's reward calculation; they are not guaranteed payment multipliers or guaranteed investment returns. Daily allocation can reduce the credited amount when total eligible activity exceeds the funded budget.

## Referral boxes

A direct referrer earns **one free pair box per referred player** after that player completes payment for at least **three physical boxes**. A Five-box purchase counts as five. Purchases by different invited people are not pooled; free boxes do not qualify, and a single invited player does not keep generating another reward after every subsequent three boxes.

The reward uses the all-rarity distribution shown above and contains one character and one car. Redeeming it has no HTW price or studio SOL fee. The referrer must complete initial entry and have room for the pair. Rare-or-higher items from these qualified referral boxes can enter the Market under the same ownership and readiness checks as paid items.

## Ownership, trading and room for delivery

The current inventory is stored by the game service and linked to your authenticated wallet. These item instances are not represented as freely transferable on-chain NFTs. Token-payment proofs, item provenance and in-game trade receipts connect purchases and ownership changes.

Common and Uncommon items cannot be listed. Rare, Epic, Legendary, Mythic and Exotic items may be eligible at **250,000 HTW or more**, subject to the Market's ownership, origin and availability checks. New official material-crafted equipment can be eligible when unbound and Rare or higher. Rarity alone does not make bound, legacy or test items transferable.

Collections support 120 characters and 100 reserve cars, plus the account's configured active slots within a one-to-six ceiling. [Paid garage upgrades](progression-and-crafting.md#garage-upgrades) normally reach six active slots at level 5; level 6 improves servicing without adding more slots. A purchase reserves capacity for every item in the package. Resolve existing pending orders before creating more; the service allows at most five unresolved purchase orders per product flow as a recovery safeguard. This is not a daily sales quota.

Source: box prices and weights (implementation reference: `src/box-economy-policy.ts`), draw implementation (implementation reference: `src/pair-boxes.ts`), official delivery and referrals (implementation reference: `worker/official-box-settlement.ts`), reward weighting (implementation reference: `worker/official-mission-rewards.ts`).
