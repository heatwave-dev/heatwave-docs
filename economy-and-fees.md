# Economy and fees

[Documentation home](README.md) · Reviewed October 15, 2026

## Three different balances

| Balance | Meaning |
| --- | --- |
| Wallet HTW | Actual official tokens in your Solana wallet |
| Credited HTW earnings | Your server-recorded reward entitlement after funded settlement; a withdrawal still needs current eligibility and backing |
| Supplies and materials | Internal gameplay resources for progression and operation; not redeemable or exchangeable for HTW |

The Rewards panel also separates **reserved earnings**, already allocated to an existing withdrawal, from **pending activity estimates**, which have not yet become a credited entitlement. Test credits, simulated starter balances and legacy receipts are not imported into the official economy.

## Prices and payment destinations

| Action | HTW | Studio SOL fee | Where the HTW goes |
| --- | --- | ---: | --- |
| Basic pair box | 25,000 | 0.0005 | Protected reward reserve |
| Five-box package | 125,000 | 0.0005 per package purchase | Protected reward reserve |
| Premium pair box | 500,000 | 0.0005 | Protected reward reserve |
| Open delivered contents | No new payment | 0 | No transfer |
| Redeem qualified referral box | Free | 0 | No transfer |
| Weapon or vest | Listed price below | 0 | Protected reward reserve |
| Character or vehicle training | 1,000–8,000 per level | 0 | Protected reward reserve |
| Garage upgrade | 8,000 / 12,000 / 18,000 / 25,000 / 8,000 by step | 0 | Protected reward reserve |
| Full manual vehicle service | 0.02 per missing fuel point + 0.05 per missing condition point | 0 | Protected reward reserve |
| Craft or repair with materials | No HTW payment; recipe resources are consumed | 0 | No transfer |
| Adjust internal service budget | No HTW payment | 0 | No transfer |
| Buy a Market item | Seller's listed price | 0 | 90% seller; 10% protected reward reserve |
| Register player for claims | 0 | 0 | No HTW transfer |
| Withdraw credited earnings | 3% of gross withheld | 0.0025 | 97% player; 3% revenue token account |

Studio SOL fees go to the [separate revenue wallet](reserve-and-transparency.md#public-addresses). **Solana network fees are additional** for on-chain transactions. Registration and claim receipts can require account rent; the review shows it before signature. “No studio fee” does not mean the network processes a transaction for free. Wallet sign-in is a message, not an on-chain payment.

Weapons and vests are sold individually. Account level, item capacity and loadout requirements still apply:

| Tier | Coast Sidearm, HTW | Impact Vest, HTW |
| --- | ---: | ---: |
| Field | 1,500 | 1,800 |
| Improved | 2,500 | 3,000 |
| Precision | 4,000 | 4,800 |
| Advanced | 6,000 | 7,000 |
| Masterwork | 8,500 | 10,000 |
| Signature | 12,000 | 14,000 |

Training, garage upgrades and manual servicing use [official progression orders](progression-and-crafting.md): explicit wallet approval, exact finalized payment and one-time fulfillment. Their legacy credit-spending commands remain blocked, so internal supplies cannot bypass HTW settlement. Material crafting and repair instead use canonical server inventories and recorded ingredient origins; they do not trigger a wallet payment or credit HTW.

## How HTW rewards are allocated

Eligible official missions create a nominal activity estimate only after the server verifies the original departure, qualified item provenance, mission outcome and safe settlement. A failed or unsafe objective does not create the same reward as a secured safe return. The [operation catalog](catalog.md#operations) lists base nominal tariffs, not promised earnings.

For an eligible mission, the base tariff receives definition-specific attribute and matching event bonuses, capped at **25% combined**. The result is multiplied by the average of the assigned character's and car's [rarity weights](boxes-and-rarities.md#what-rarity-changes). Internal supply effects are not directly converted into tokens.

At settlement of a **closed UTC day**, the server reads a fresh finalized reserve observation. It subtracts existing reward obligations and relevant payments made after that observation to avoid counting the same backing twice. The current configuration has **zero fixed safety retention**. What remains is the free reserve.

The day's issuance budget is **3% of that free reserve**, calculated in whole token atoms. This is a budget for new reward credits, not a 3% daily return for players. If total eligible nominal demand is within the budget, it can be credited in full. If demand exceeds it, each allocation is reduced proportionally and rounded down. Unused budget is not automatically distributed, and rounding dust remains unallocated.

Example: a hypothetical free reserve of 1,000,000 HTW supports a budget of 30,000 HTW for that settlement. If aggregate eligible demand is 60,000 HTW, each demand receives approximately half, subject to atomic rounding. If demand is 10,000 HTW, it receives 10,000 in total; the other 20,000 is not a guaranteed bonus.

Settlement happens through the server's reconciliation process after the UTC day closes. It is not a promise that the wallet receives tokens at midnight. Pending activity is an estimate, **not a debt or a redeemable balance**, until funded allocation creates a credited entitlement. Daily settlement receipts are retained, so a retry does not allocate the day twice.

## Withdrawal requirements

- At least **100,000 HTW gross** in eligible credited earnings, excluding amounts already reserved for another request.
- At least **2,500 HTW in the player's canonical official-token wallet account before payout**. The incoming claim cannot satisfy this check; the holding itself is not consumed as a fee.
- For the first claim, **seven days since actual on-chain player registration**. Connecting a wallet or buying a box does not start that clock. There is no new seven-day waiting period between subsequent claims in this contract.
- Sufficient SOL for the **0.0025 SOL studio fee**, the quoted network fee and applicable account rent.
- Freshly verified gross reserve coverage, matching account identity and the signatures of the player and configured game backend on the exact transaction.

The claim's 3% fee is rounded down to token atoms. At the minimum, **100,000 gross = 97,000 to the player + 3,000 to revenue**. Both token transfers and the SOL studio fee are part of one atomic claim transaction. A failed transaction rolls these program effects back but can still incur the network fee.

The deployed configuration sets all four claim amount limits—per claim, per player per UTC day, global per UTC day and lifetime—to the largest supported unsigned 64-bit value. There is **no additional commercial withdrawal ceiling and no fixed 6-million-HTW reserve floor**. Checked arithmetic and the protocol's representable token range still apply. Removing commercial ceilings does not create token backing or bypass registration, holding, earned-balance or signature checks.

If backing is insufficient, the claim remains queued for funding rather than asking you to pay a studio fee for an uncovered payout. A credited balance is not the same as an immediately payable transaction. The 3% issuance budget limits new reward credit; it is separate from withdrawal admission for existing credits.

## Market rules

The official Market supports eligible characters, vehicles and equipment at **Rare or higher**. Items must have verified official provenance, be owned by the seller, be available for listing and pass their item-specific checks. Paid items, qualified referral items, newly recorded official material crafts and their subsequent official trades preserve provenance. Crafted equipment must still be unbound and meet the rarity and availability requirements; bound, legacy or playtest items do not become eligible solely because their rarity is high.

The minimum listing is **250,000 HTW**. There is no commercial maximum price, although the amount must fit the token protocol's numeric range. A **10% seller fee** goes to the protected reward reserve; the seller receives 90%. At a 350,000 HTW price, that is 35,000 to the reserve and 315,000 to the seller.

Listings lock the item against conflicting game actions. A purchase reserves the listing and settles ownership after the exact token transfer is finalized. A technical reservation or expired browser quote is not proof of payment failure. Use the order's recovery/release controls when an attempt is uncertain. The current transaction flow requires the buyer, seller and reserve token accounts to be valid; it does not silently create extra recipient accounts.

The game does not promise buyers for listings or a resale price. A floor on listing prices is not a floor on market value.

## What can change

The deployed reserve bytecode and its initialized configuration cannot be edited by an administrator through this program. Its fixed claim destinations, holding minimum, first-claim age and fee logic are not adjustable switches in the game UI. A different contract/configuration would need to be separately identified and disclosed; it would not rewrite the existing immutable reserve.

Off-chain product availability, game balance, mission tariffs, rarity reward weighting and issuance policy are operated by the game service and can be versioned in future releases. This document is a dated description, not a promise those off-chain rules can never change. Saved transaction reviews remain tied to their original terms.

Sources: official reward policy and allocation (implementation reference: `worker/official-mission-rewards.ts`), claim service (implementation reference: `worker/official-claim-service.ts`), [claim contract](reserve-program.rs), equipment settlement (implementation reference: `worker/official-equipment-settlement.ts`), progression settlement (implementation reference: `worker/official-progression-settlement.ts`), material progression (implementation reference: `worker/official-material-progression.ts`), Market service (implementation reference: `worker/official-market-service.ts`).
