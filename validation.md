# Validation record

[Documentation home](README.md) · Local source review, October 15, 2026

This record describes automated checks of the reviewed implementation. It is not an independent security audit, a claim of zero defects, or proof that every real player's wallet and network conditions have been exercised. Production availability is checked separately from the reserve's finalized deployment evidence.

| Targeted run | Result | Scope |
| --- | ---: | --- |
| Expanded finance regression | 230 / 230 passed | Official authentication, payment verification, settlement, claims, reward backing, recovery, progression and material provenance |
| Latest Market regression | 19 / 19 passed | Listings, exact payment, ownership transfer, recovery and newly crafted Rare equipment sale/resale |
| Box-flow and related UI regression | 31 / 31 passed | Entry and box transaction flow, interface binding and recovery behavior |
| TypeScript and production build | Passed | Type checks and the production build for the reviewed source |

These runs overlap; their counts are not a combined total. Tests use isolated databases, generated test keys and controlled network observations. They do not sign or broadcast Mainnet payments.

Progression checks cover single fulfillment after finalized payment, unchanged targets while a wallet approval is pending, conflicting orders, stale or foreign inventory, exact signed-message recovery after restart, and rejection of incomplete failure evidence. Actual game-service tests confirm that dispatch is blocked during an upgrade while polling and profile-name edits remain available.

Material tests earn resources through server-simulated official missions, craft a weapon and a supply, and confirm that the following legitimate mission keeps nonzero nominal reward eligibility. They also check failed-save rollback, altered client inventories, untracked legacy items, one-time supply consumption, and retained craft provenance after a paid sale and resale. A successful nominal-reward test does not promise a player a payout; funded allocation and claim eligibility still apply.

First-access profile checks cover saving a player name through the authenticated game command, existing-profile preservation, validation and recovery. Names remain cosmetic identity fields; changing one cannot change wallet authority, inventory, progression prices or paid-order targets.

The separately published [reserve deployment evidence](reserve-evidence.json) describes actual on-chain facts. [Reserve trust boundaries](reserve-and-transparency.md#trust-boundaries-and-operational-risks) explain the remaining dependence on the game backend, signing service and network availability.
