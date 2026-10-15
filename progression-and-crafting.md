# Progression and crafting

[Documentation home](README.md) · Reviewed October 15, 2026

## Character and vehicle training

Owned characters and cars have five training upgrades. The server checks ownership, availability, XP and the current training level before quoting the next step. An item committed to a mission or listed for sale is not available for training.

| Training step | HTW |
| --- | ---: |
| 0 → 1 | 1,000 |
| 1 → 2 | 2,000 |
| 2 → 3 | 3,000 |
| 3 → 4 | 5,000 |
| 4 → 5 | 8,000 |

These are the same prices for character and vehicle training. Training does not change an item's rarity or guarantee a financial return.

## Garage upgrades

| Garage step | HTW | Normal active-car capacity after upgrade |
| --- | ---: | ---: |
| 1 → 2 | 8,000 | 2 |
| 2 → 3 | 12,000 | 3 |
| 3 → 4 | 18,000 | 4 |
| 4 → 5 | 25,000 | 6 |
| 5 → 6 | 8,000 | 6 |

Level 1 normally has one active slot. Level 6 improves servicing rather than adding another slot. The account panel shows the effective capacity, including any preserved starter access.

Collection limits remain **120 characters**, **100 reserve cars**, and up to **six active cars**. The equipment inventory holds **200 items**. There is no daily box-opening quota; capacity and unresolved payment recovery still apply.

## Manual vehicle service

Manual full service restores an owned parked vehicle's fuel and condition to 100. The quote is:

`missing fuel × 0.02 HTW + missing condition × 0.05 HTW`

For example, a vehicle with 50 fuel and 80 condition needs 50 fuel points and 20 condition points: **2 HTW** in total. The final charge rounds up to whole token atoms. A fully serviced vehicle needs no new service purchase.

Automatic mission servicing continues to use internal supplies and its configured allowance or recovery wait. Changing that internal budget is a free setting; it is not an HTW transfer.

## Review, payment and recovery

Recall the fleet, turn off automatic operation and wait for all active and reserve cars to be parked before preparing a paid upgrade or manual service. A pursued car must escape and return safely first.

The review names the exact target, upgrade or service benefit, HTW amount and protected reserve destination. These progression purchases add **no SOL studio fee**; the quoted network fee still applies. The benefit is applied once only after the original exact payment is finalized.

While a progression order is unresolved, conflicting fleet and inventory actions are locked so the reviewed benefit cannot change behind the wallet confirmation. Status checks and cosmetic profile edits remain available. Recover or safely release the original order before starting another. A timeout alone does not prove a payment failed; the server checks the original transaction and its validity before releasing the lock.

## Crafting, repair and supplies

Use the recipe shown in the workshop. Crafting and repair consume internal materials, without an HTW payment or wallet transaction. Higher equipment tiers require the named previous-tier item as an ingredient. Unequip items and finish their active missions before consuming, dismantling or repairing them. Repair keeps the original item and restores durability; dismantling consumes the item and returns its stated material yield.

New official crafts receive immutable gameplay provenance recording the exact material balances and verified ingredient origins. They are not labeled as paid purchases. Each crafted supply unit is consumed at one actual mission departure and cannot qualify a second mission. Properly recorded crafted gear and supplies retain mission eligibility; crafting itself does not create HTW earnings.

Bound materials or ingredients can produce bound equipment. Only eligible **unbound Rare-or-higher** equipment may enter the Market, starting at **250,000 HTW**. Its gameplay origin remains traceable through later paid trades. Old, demo or otherwise untracked items and supplies are not retroactively qualified.

The existing supply inventory holds **100 units**, with **1–10 units per crafting action**. Each material has a **1,000,000-unit storage capacity**. These resource and recipe limits are separate from the withdrawal settings and the absence of a daily box quota.

## Implementation and trust

Paid progression policy: `official-progression-v5.1-2026-10-15`. Material policy: `official-gameplay-materials-v1-2026-10-15`. Mission eligibility uses the existing official reward version followed by `-materials-v1`; tariffs, rarity weights and allocation rates are unchanged.

The game server owns material inventories and gameplay results. Receipts provide traceability and prevent conflicting or repeated mutations; they do not turn gameplay into independently verified on-chain computation. [Read the reserve trust boundaries](reserve-and-transparency.md#trust-boundaries-and-operational-risks).

Sources: progression prices (implementation reference: `worker/official-progression-policy.ts`), payment settlement (implementation reference: `worker/official-progression-settlement.ts`), material provenance (implementation reference: `worker/official-material-progression.ts`), equipment recipes (implementation reference: `src/equipment.ts`), consumable recipes (implementation reference: `src/consumables.ts`).
