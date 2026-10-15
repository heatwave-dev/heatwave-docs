# HEATWAVE whitepaper

Version 1.1 · October 15, 2026 · [Documentation home](README.md)

## Product

HEATWAVE is an autonomous fleet-management game set in Sundown Bay. Its focus is preparing a crew, choosing jobs, managing risk and watching a connected 3D city carry out the plan. ARCSOVA is a South American studio with Brazilian and international contributors working on games and other Web3 products.

The player manages the operation rather than manually steering or shooting. Drivers board owned vehicles, travel through the city, work at mission locations and return. The browser renders this activity; the game server owns progression and settlement. A cinematic camera, visible traffic, pedestrians, police pursuits and helicopters make the fleet's activity observable.

## Collection and progression

The collection contains 60 character definitions and 60 vehicle definitions across Common, Uncommon, Rare, Epic, Legendary, Mythic and Exotic. Each has attributes and a contextual effect. Support roles, equipped items and mission choice add decisions beyond acquisition. Character and vehicle training and garage expansion use dedicated official HTW orders, exact finalized payment verification and saved upgrade receipts.

Boxes deliver character/car pairs. Basic costs 25,000 HTW and contains only Common items. Five boxes cost 125,000 HTW and draw from all rarities. Premium costs 500,000 HTW and guarantees both items at Epic or higher. The [box specification](boxes-and-rarities.md) publishes exact per-item probabilities, including the 0.035% Mythic and 0.005% Exotic chances, without implying guaranteed returns.

The first entry uses Basic or Five boxes. Later purchases remain available without a daily opening quota, subject to payment recovery and collection space. Current management limits are 120 characters, 100 reserve vehicles and a configured active capacity within one-to-six vehicles. Garage upgrades normally reach six active slots at level 5; level 6 improves servicing. Six tiers of weapons and vests are sold separately. Manual full vehicle servicing also has an official HTW quote. Equipment crafting/repair and consumable crafting use materials, while service-budget changes configure internal resources without a wallet payment. [The progression specification](progression-and-crafting.md) lists the prices and conditions.

Twenty operations cover delivery, recovery, handoff and security encounters. Each has account-level and preparation requirements. Strategy, fuel, condition, heat, equipment and per-vehicle energy affect actual availability. Automatic repetition and up to eight hours of eligible unattended reconciliation do not bypass those requirements.

## Official HTW and internal resources

The official asset is the six-decimal Token-2022 mint [`HKrTVBPVF9B8LEkNvZDm4PeNScnvoHv8JxNMTahVpump`](https://solscan.io/token/HKrTVBPVF9B8LEkNvZDm4PeNScnvoHv8JxNMTahVpump) on Solana Mainnet.

Internal supplies, materials and XP are distinct from HTW. The official environment does not import playtest balances or convert supplies into redeemable tokens. Paid delivery requires an exact finalized transfer and retains a canonical receipt. Item instances are currently held in the game database and linked to wallet identity; this release does not claim on-chain NFT custody for the collection.

Eligible mission returns create nominal HTW activity. Published operation tariffs, attributes, triggered events and rarity weights determine relative demand. After a UTC day closes, new credits are constrained by a budget of 3% of the free protected reserve after existing obligations and relevant in-flight payments. If demand exceeds the budget, allocations are proportionally reduced. This budget is not a player yield, and pending activity is not a guaranteed receivable.

## Circular payments and fees

Box, equipment and paid progression HTW purchases flow into the reward reserve. The player Market permits eligible Rare-or-higher items from 250,000 HTW, with no commercial maximum beyond protocol numeric limits. Its 10% fee also goes to the reward reserve; sellers receive 90%.

A direct referral earns one free pair after an individual invited player buys at least three physical boxes. The reward occurs once per referred player. Qualified Rare-or-higher referral items may be traded; referrals do not mint withdrawable earnings by themselves.

Paid box purchases charge 0.0005 SOL per purchase. Claims charge 0.0025 SOL and 3% of gross HTW. Studio fees go to separate revenue accounts. Network fees and applicable account rent are quoted additionally. The [fee reference](economy-and-fees.md) explains the exact destinations and arithmetic.

## Protected reserve

The reserve program was made immutable and funded with 66,000,000 HTW on October 15, 2026. Its [public evidence](reserve-and-transparency.md) includes program/configuration/token-account addresses, finalized transaction links and the recorded executable hash. The amount describes the initial deposit, not a continuously updated balance.

The program has no direct administrator-withdrawal handler. A claim needs both player and backend signatures, a minimum 100,000 HTW gross, 2,500 HTW already held by the player, seven days since registration for the first claim, fresh backing and a nonreusable claim receipt. It atomically splits gross HTW into 97% to the player and 3% to revenue. The initialized amount limits are the protocol's u64 maximum, and fixed safety retention is zero; these settings remove additional commercial withdrawal ceilings without removing the backing requirement.

This design separates ordinary operator revenue from direct access to deposited reward tokens. **It does not eliminate backend trust.** The backend can authorize false earnings if compromised or operated dishonestly, and the contract cannot independently verify gameplay. The fixed signer has no replacement path in this immutable instance. No independent security audit is claimed.

## Architecture and recovery

Wallet authentication proves account ownership with a signed challenge. On first access, new players choose a saved display name; it remains a cosmetic profile field, separate from wallet authority. Purchase, registration and claim reviews are separate and require their own approval. The client checks wallet identity across asynchronous steps and rejects altered transaction messages. The server records original requests and signatures before broadcasting, then relies on finalized chain observations to reconcile them.

An uncertain response is not automatically treated as a failed payment. Recovery uses the original order or claim rather than creating a replacement debit. Stable item provenance and trade receipts connect payment, inventory delivery and later ownership changes. Material crafting records exact server inventory debits and verified ingredients; it uses an explicit gameplay-craft source rather than a synthetic payment receipt. Each qualified consumable unit is linked to one actual mission departure. Newly crafted official gear and supplies preserve mission eligibility under the versioned material policy, without changing published tariffs or allocation rates. Paid progression locks conflicting fleet/inventory actions until fulfillment or proven safe release; status checks and cosmetic profile updates remain available. The system does not present a local animation or an HTTP success response as proof of finalized payment.

## Current boundaries

There is no promise of profit, fixed APY, item resale liquidity or token-price support. Rarity guarantees refer only to box contents. The official withdrawal path pays HTW; a prospective external swap or fiat payout must not be represented as a live feature before its own integration is verified.

The game service operates balance, content and product policies. Those off-chain rules can be versioned, whereas the published immutable reserve cannot be rewritten through an administrator control. Future additions must be documented separately from current behavior. Public hosting status, maintenance and completed end-to-end validation are separate from the reserve's deployment evidence.

This whitepaper is a product and implementation description. For exact player steps, current fees and system constraints, use the linked guide and reference pages rather than historical design proposals.
