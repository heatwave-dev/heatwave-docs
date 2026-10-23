# HEATWAVE whitepaper

Version 2.1 · October 23, 2026 · [Documentation home](README.md) · [Roadmap](roadmap.md)

HEATWAVE is a Solana browser idle game about collecting cars and managing an automatic fleet in Sundown Bay. This document explains the current game, HTW uses, funded credit and transaction recovery. Use the [live English guide](https://heatwave.gg/codex-en.html) and your transaction review for current rules and exact amounts.

## The fleet you manage

You manage the fleet instead of steering each car. Up to 15 ready cars travel, work and return automatically. Rarer ready cars receive priority for the next active slot. Your collection can exceed 15 cars; waiting and recovering cars do not all work simultaneously.

Each departure uses 5% energy, allowing 20 departures from a full battery, subject to the car’s actual state. Outside recovery is free. Garages and the mechanic are optional purchases that change recovery and readiness, not a rarity’s nominal HTW rate. You can own up to five garages; six garage types are choices, not six ownership slots.

With accepted game presence, eligible activity uses the open-game rate. Up to eight hours of eligible away progress use half the current rate. Energy, mission conditions, recorded activity and reserve funding still matter. More cars improve rotation without increasing the 15-car simultaneous work limit.

Pause stops new departures while current trips finish. Recall is a separate interruption, not a completed mission. Daily assessment can include eligible recorded work in an open mission without completing it or restoring energy. The game does not reconstruct work the server never recorded.

The October 15 whitepaper described manual crews, character/car pairs and older prices. Those descriptions are historical. Current boxes deliver cars and the current player flow is automatic fleet management.

## Wallet, registration and cars

Connect a supported Solana wallet and approve the sign-in message to prove ownership. Sign-in is separate from payment and on-chain registration. Keep the same wallet to recover saved orders and your collection.

Confirmed on-chain registration is required before farming. A new player’s first box purchase includes registration in the same approval, with the SOL account deposit shown. An existing unregistered account activates once separately. HEATWAVE is not presented as a complete free or walletless game.

Paid boxes offer random cars. An eligible player-market car is an alternative when you want a particular listed item. Compare its restrictions and complete review before approving. Delivered cars are recorded game items linked to your account; this release does not claim NFT custody for the collection.

Reference offers are:

| Offer | HTW reference price | Contents |
| --- | ---: | --- |
| Basic | 25,000 | One random car; all seven rarities possible |
| Five boxes | 125,000 | Five separate random car draws |
| Premium | 1,000,000 | One random car, Rare or higher |

Your review quotes SOL fees, network costs and any registration deposit separately. [Per-car odds](boxes-and-rarities.md) describe probabilities, not returns or cumulative pack guarantees. Recover an uncertain original order instead of paying again.

## How HTW is used

HTW is a six-decimal Token-2022 asset on Solana Mainnet. Its official mint is [HKrTVBPVF9B8LEkNvZDm4PeNScnvoHv8JxNMTahVpump](https://solscan.io/token/HKrTVBPVF9B8LEkNvZDm4PeNScnvoHv8JxNMTahVpump). A ticker or logo alone does not identify it.

HTW pays for boxes, eligible market purchases and other reviewed game purchases. Credited game-balance HTW can pay for Car Fusion and the Auto-Farm Pass, each with a separate SOL fee. External tokens, pending activity and available game credits are distinct. A fiat conversion is not a guaranteed cash balance or sale price.

Fusion permanently consumes eligible cars to create one random model of the next rarity:

| Input | Output | Game-balance HTW cost |
| --- | --- | ---: |
| 8 Common cars | 1 Uncommon car | 50,000 |
| 4 Uncommon cars | 1 Rare car | 100,000 |
| 5 Rare cars | 1 Epic car | 300,000 |
| 3 Epic cars | 1 Legendary car | 750,000 |

Fusion also requires 0.005 SOL. Inputs must be eligible parked cars without a listing, scheduled sale or conflicting assignment. The output is drawn from the next rarity’s ten models. Half the HTW is burned in the game and half returns to the reserve. Mythic and Exotic cars cannot be fused or produced by fusion.

The Auto-Farm Pass costs 50,000 credited HTW plus 0.005 SOL for seven days. Twenty percent of its HTW cost is burned in the game and 80% returns to the reserve.

The announced departure-rule change starts **October 24, 2026 at 12:00 UTC / 09:00 Brasília**. Until then, existing farming rules apply. Afterwards, without a pass, new trips start only while the game is open. Trips already underway finish under their recorded terms. An open game works with or without a pass. The pass does not remove energy, offline-progress or funding limits.

## From recorded work to funded credit

The server records eligible work under each trip’s departure terms. Later rate changes apply prospectively; they do not reprice earlier trips or erase confirmed credit. Current account rules and saved reviews determine applicable values.

After the relevant UTC day closes, eligible recorded activity enters daily assessment, including eligible work in an open mission. There is no promise of an instant midnight credit or a fixed assessment time.

New credit depends on reserve coverage and the daily funding budget. The revenue-linked ceiling is 70% of average observed reserve inflows over up to seven settled daily intervals. Demand above the available budget is allocated proportionally. This ceiling is an accounting constraint, not proof of sustainability.

Only the funded allocation becomes confirmed game credit. A partial or zero allocation creates no debt or promise to replenish the difference. A loss known before assessment can reduce the uncredited portion; a later loss does not remove already confirmed credit. Hourly, 24-hour and fiat references are not credited balances or withdrawal promises.

## Withdrawal conditions

Withdrawals pay HTW to the same player’s external Solana wallet. The first-withdrawal wait is seven days from confirmed on-chain player registration, once before the first successful withdrawal. Login and holding do not start that clock. A successful withdrawal does not restart it.

The fixed conditions are:

| Condition | Requirement |
| --- | --- |
| Minimum gross request | 100,000 credited HTW |
| External wallet holding | At least 2,500 HTW in that same wallet before payout |
| HTW fee | 3% of gross HTW; net token amount is 97% |
| SOL game fee | 0.0025 SOL |
| Other SOL costs | Quoted network fee and any applicable account rent |

New requests have a **500,000 HTW gross maximum per request** and a **1,000,000 HTW gross limit per wallet in rolling 24 hours**. The shared **10,000,000 HTW gross global cap** renews in fixed 24-hour cycles anchored to the first finalized withdrawal, **October 22, 2026 at 18:10:58.224 UTC**. Its daily boundary is **18:10:58 UTC / 15:10:58 Brasília**, not midnight. Prior-cycle finalized withdrawals leave the global count together; unfinished requests carry over and still occupy capacity. This is shared withdrawal capacity, not a daily token grant or payment guarantee. Check current amounts, remaining capacity and any pause in the withdrawal review. Existing requests retain their admitted terms, including the older rolling global policy where recorded.

A positive balance, elapsed wait, wallet signature or pending animation is not a successful payout. Credited entitlement, eligibility, holding, backing, limits and network confirmation remain necessary. Observe and recover an uncertain original request before creating another.

## Transaction checks and recovery

The game binds reviews to the authenticated player, wallet, amount, destination and expiry. For new wallet-first withdrawals, it builds and simulates a fresh unsigned transaction before the player’s wallet signs. The game validates the returned transaction and player signature before adding its verifier signature to that exact message. It persists the signed transaction before broadcasting with preflight enabled.

Compatibility with wallet protective assertions is bounded. It does not allow arbitrary transfers, extra spending authority or replacement of the reviewed claim. Fee, simulation, identity, expiry and replay checks remain required. Earlier saved claims retain their recovery path. Deployment or passing tests do not prove that every wallet warning disappeared or every player was paid.

The [published reserve contract](contract.md) requires player and game-verifier signatures and checks accounts, holding, age, amount, backing, expiry and replay. Its upgrade authority was removed on October 15. The recorded initial deposit was 66,000,000 HTW, a historical deposit, not today’s reserve balance. [Deployment evidence](reserve-evidence.json) identifies that snapshot.

The immutable contract and the game’s admission policy are separate layers. Large initialized on-chain numeric ceilings do not disable lower application limits. The server also tracks liabilities and uncertain payouts; a token account balance alone does not reveal all obligations.

## Trust and risks

The backend remains trusted to validate gameplay and authorize credit. A compromised or dishonest backend can authorize fabricated claims, subject to on-chain checks. Removing upgrade authority does not decentralize the server, prove gameplay or guarantee uninterrupted service. Losing the configured signing capability can prevent claims from this immutable instance; it has no replacement-key recovery path.

HTW and item values can fall, and buyers may be unavailable. Purchases, rarity, referrals and gameplay do not guarantee income, liquidity, token-price support or recovery of costs. Game, RPC, wallet and signing-service outages can interrupt transactions. No independent security audit or guarantee of reserve sustainability is claimed.

The [roadmap](roadmap.md) separates available features, an announced scheduled rule and external submissions awaiting confirmation. It promises no additional release dates, exchange approvals or investment returns.
