# HEATWAVE documentation

**Build your crew. Explore Sundown Bay. Trade your collection.**

HEATWAVE is a browser-based 3D fleet-management game by ARCSOVA, a South American studio with Brazilian and international contributors building games and other Web3 products. You prepare drivers, vehicles and equipment; your crews travel, work and return through a simulated coastal city.

This is the English public documentation for the official HTW game. It describes the implementation and verified reserve deployment as reviewed on **October 15, 2026**. It does not declare that every hosting environment is online or that an uncompleted transaction succeeded. Historical playtest documents are not the official pricebook.

| Start here | What it covers |
| --- | --- |
| [Player guide](player-guide.md) | Wallet entry, your first box, assignments, jobs, camera, progression and recovery |
| [Boxes and rarities](boxes-and-rarities.md) | Exact prices, probabilities, duplicates, referral boxes and collection limits |
| [Economy and fees](economy-and-fees.md) | Internal supplies, funded rewards, withdrawals, equipment prices and the Market |
| [Reserve and transparency](reserve-and-transparency.md) | Verified addresses and transactions, immutable code, fee separation and trust assumptions |
| [Whitepaper](whitepaper.md) | Product architecture, economic design and current boundaries |
| [Progression and crafting](progression-and-crafting.md) | Training, garage capacity, servicing, material recipes and payment recovery |
| [Validation record](validation.md) | Dated automated checks and their scope |
| [Catalog](catalog.md) | All 60 characters, 60 vehicles and 20 operations, generated from game definitions |

The official HTW mint is [`HKrTVBPVF9B8LEkNvZDm4PeNScnvoHv8JxNMTahVpump`](https://solscan.io/token/HKrTVBPVF9B8LEkNvZDm4PeNScnvoHv8JxNMTahVpump) on Solana Mainnet. Check the full mint address, not only a ticker or logo.

The initial protected-reserve deposit was **66,000,000 HTW**. It is a historical deposit, not a live balance or a promise of returns. The reserve page links the transaction and explains which controls are enforced on chain and which depend on the game service. No independent security audit is claimed.

The reviewed official version supports box and equipment purchases, eligible Market trades, mission management, paid training and garage upgrades, manual vehicle servicing, internal service-budget settings, material crafting and equipment repair. New players choose a display name on first access. See [progression and its exact prices](progression-and-crafting.md) and the dated [validation record](validation.md).

Game resources and pending activity estimates are not wallet tokens. Rarity, gameplay, purchases and referrals do not guarantee income, resale liquidity, token price or recovery of purchase costs.

This public repository includes the [exact reserve contract source and build files](contract.md) and [deployment evidence](reserve-evidence.json). The rest of the game implementation is not included; source paths named in reference pages identify the reviewed implementation, not public links.
