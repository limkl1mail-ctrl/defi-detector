# Bankr (BNKR) — Adversarial Due Diligence Report
**Date:** 2026-05-14  
**Contract:** `0x22aF33FE49fD1Fa80c7149773dDe5890D3c76F3b` (Base)  
**Website:** https://bankr.bot  
**Confidence:** Medium

---

## 1. Executive Summary

**Verdict:** Legit — meaningfully more so than a typical Base meme token. Named founder with real GitHub history, immutable fair-launch contract, Coinbase Exchange listing, and $7M+ in documented platform revenue are not things scam projects have. The rug-pull vector does not exist here. What you are buying is a bet on Bankr's terminal surviving and growing; if the platform loses users, the buyback dries up and BNKR is just a meme. Three specific verification gaps remain unresolved (buyback treasury address, Ventures claim, V1 LP lock) and prevent a clean all-clear — but none of them point to fraud.

**Top 3 Risks for BNKR Holders:**
1. **BNKR buyback mechanism unverified** — $15.97M in platform fees cited by DeFiLlama, but how much actually flows to the BNKR buyback treasury (vs. team/Clanker) is not documented with verifiable on-chain evidence; the token's demand story depends on this mechanism being real and ongoing
2. **Platform survival is the token's only demand driver** — BNKR has no protocol revenue of its own; all demand flows from Bankr terminal activity; if Bankr loses market share to competing AI agent terminals (Brian, Virtuals, etc.), the buyback mechanism weakens proportionally; Clanker V1 is deprecated and new tokens launch on Doppler, creating an unresolved question about long-term fee routing for the legacy BNKR token
3. **Coinbase Ventures backing unverified** — the claim originates from clanker.world's About blurb, not from Coinbase, Bankr's official channels, or any press release; if false, this is a misrepresentation cited in third-party contexts

**Top 3 Positives:**
1. **Genuinely fair launch** — 0% dev allocation; 100% of supply sent to Uniswap V3 LP at deployment via Clanker V1 factory; immutable ERC-20 contract with no mint/pause/admin functions
2. **Real product with verifiable revenue** — $7.04M all-time protocol-retained revenue per DeFiLlama; active GitHub (8 repos, 10+ contributors); Coinbase Exchange listing confirmed
3. **Identified team lead** — Igor Yuzovitskiy (@igoryuzo) is publicly named, US-based, GitHub active since 2014; not anonymous

---

## 2. Team Assessment

| Verified | Claimed / Unverified | Assessment |
| --- | --- | --- |
| **Igor Yuzovitskiy (@igoryuzo)** — founder; GitHub since 2014; US-based; public LinkedIn and Twitter presence | "Multi-person team" — referenced in docs and GitHub contributors list | Lead is real and traceable; no prior fraud or abandoned project history found |
| **BankrBot GitHub org** — 8 repos, 10+ committers, active commits through 2026 | Team members beyond Igor largely pseudonymous | Enough for a real engineering team; not a one-man ghost project |
| **Coinbase Exchange listing** — confirmed via CoinGecko platform data | "Backed by Coinbase Ventures' Base Ecosystem Fund" — source is clanker.world About blurb only; no Bankr announcement, no Coinbase press release found | Coinbase relationship is real (listing), but the Ventures claim is unverified; demote to claimed |
| No prior fraud, rug pull, or regulatory action found for Igor or BankrBot org | — | Clean record; absence of adverse history is a mild positive |

---

## 3. Third-Party Consensus

### Audit Posture
- **BNKR contract**: Basescan confirms "No Contract Security Audit Submitted." This is low risk in context: the Clanker V1 ERC-20 is a minimal token (13 standard functions, no admin logic) with a "Similar Match" verified source at `0x1AF14E0F1f37962e7789FAF2D631d7C6bF4d14C9`. The core risk is the platform, not the token contract.
- **Bankr platform**: No third-party security audit of the Bankr backend, API, or wallet infrastructure is publicly documented. The custodied wallet system (Privy-based) represents a centralized attack surface that has no public audit coverage.

### Independent Analyst Coverage
- **Rekt News**: Not listed. No entry found. Mild positive.
- **DeFiHackLabs (SunWeb3Sec)**: No BNKR/Bankr entry found.
- **ZachXBT**: No thread found referencing Bankr or BNKR.
- **BlockSec / PeckShield**: No incident alerts found.
- Coverage is thin — the project operates in the Farcaster/Base ecosystem and has not attracted adversarial scrutiny from major investigators. Absence of red flags is positive but also reflects limited independent oversight.

### Community Sentiment
- **Clanker.world**: Lists BNKR as a "Champagne Clanker" (blue chip designation); 229,672 holders; top-10 concentration 34.82% (likely includes DEX pools and CEX custody — not independently labeled)
- **Farcaster/Warpcast**: Active Bankr community; high cast volume; the Bankr AI agent is a native Farcaster participant
- **CoinGecko**: Community score positive; listed on major aggregators

---

## 4. On-Chain Findings

### Market Data (as of 2026-05-14)

| Metric | Value | Source |
| --- | --- | --- |
| Price | $0.0004 | Basescan |
| Market Cap (circulating) | ~$41M | Basescan |
| Fully Diluted Valuation | ~$41M (100% circulating) | No unlocks pending |
| All-time protocol fees | $15.97M | DeFiLlama |
| All-time protocol revenue | $7.04M | DeFiLlama |
| Holders | 229,672 | Basescan |
| Top-10 concentration | 34.82% | Clanker.world |

### Token Distribution and Vesting
- **Supply**: 100,000,000,000 BNKR (100B), 100% circulating at deployment
- **Dev allocation**: 0% — Clanker V1 sends all supply to Uniswap V3 LP at deploy time; no vault, no team reserve
- **Vesting**: None — no insider unlocks, no cliff events
- **Cliff risk**: Not applicable
- **Buyback mechanism**: Bankr routes a share of 1.2% swap fees from Bankr-deployed tokens into a BNKR buyback address. Full buyback treasury address was not independently verified on-chain in this investigation; DeFiLlama revenue figures reflect Bankr platform revenue, not specifically the BNKR buyback inflows.

### Contract Architecture
- **Contract**: `0x22aF33FE49fD1Fa80c7149773dDe5890D3c76F3b` — Clanker V1 ERC-20 on Base
- **Proxy**: None — EIP-1967 slot is 0x0; immutable deployment
- **Admin functions**: None — ABI contains only `allowance`, `approve`, `balanceOf`, `castHash`, `decimals`, `deployer`, `fid`, `image`, `name`, `symbol`, `totalSupply`, `transfer`, `transferFrom`. No `mint`, `pause`, `burn`, `blacklist`, or `owner` function.
- **Upgrade risk**: Zero — contract cannot be modified post-deployment
- **LP**: BNKR/WETH Uniswap V3 pool at `0xc16e685de885efc4a01d159db62bbb613a96ba70` (Base); liquidity confirmed active (~28T liquidity units). LP lock status for Clanker V1 specifically was not independently verified; Clanker V3.1+ uses a formal `LpLockerv2` contract but V1 predates this.
- **Deployer field**: `0x128c718152c4da86454547484a43a09ac4ee6e7b` — EOA (not a contract); 325 transactions; this is the Clanker V1 operator wallet, not an insider reserve
- **Bug bounty**: None found

### Platform Architecture (Risk-Relevant)
- **Wallet model**: Bankr creates custodied wallets (Privy infrastructure) for agents and users. Bankr holds the private keys — not the user. This is a platform centralization risk for users of the terminal, not directly for BNKR holders unless Bankr's failure impacts the fee flows that underpin any buyback mechanism.
- **x402 protocol**: Micropayment layer for AI compute costs; experimental standard
- **Skills marketplace**: 30+ integrations (Zerion, Alchemy, ENS, Coinbase OnchainKit, etc.); real integrations confirmed in GitHub
- **Doppler migration**: Clanker is deprecated per Bankr docs; new token launches use Doppler. BNKR itself remains a Clanker V1 token with no migration path.

---

## 5. Red Flags Register

| # | Flag | Severity | Evidence | Source |
| --- | --- | --- | --- | --- |
| 1 | **BNKR buyback mechanism unverified** — the token's entire demand story rests on a fee routing mechanism that has not been confirmed via a published buyback treasury address or on-chain balance verification; DeFiLlama revenue is Bankr platform-level, not BNKR-specific | MEDIUM | DeFiLlama protocol page; Bankr docs describe fee splitting but publish no buyback treasury address | defillama.com |
| 2 | **Clanker V1 deprecated → BNKR fee routing risk** — new Bankr token launches use Doppler, not Clanker; whether the 1.2% fee share continues routing to the BNKR buyback address as platform volume migrates to Doppler-launched tokens is not clarified; BNKR is a legacy V1 token with no migration path | MEDIUM | Bankr docs: "Clanker is deprecated." Doppler is now the default launcher. | docs.bankr.bot |
| 3 | **Coinbase Ventures backing unverified** — claim appears only in clanker.world About blurb; no Bankr announcement, no Coinbase press release, no portfolio listing found | MEDIUM | Clanker.world About text; no corroboration from Coinbase or Bankr primary sources | clanker.world |
| 4 | **No platform security audit** — Bankr's custodied wallet infrastructure, API, and backend have no public third-party security audit; Privy-based custody wallets are a high-value attack target with no public security posture documentation | MEDIUM | BankrBot GitHub — no audit report found | github.com/BankrBot |
| 5 | **Fair-launch snipe check not performed** — "0% dev allocation" via Clanker mechanics is the on-chain claim; first-hour buyer concentration was not traced; team wallet coordination at launch cannot be ruled out without reviewing the first ~50 LP buys after Dec 3, 2024 deployment | MEDIUM | Standard risk for fair-launch tokens; Dune query on BNKR blocks 0–3,600 post-deployment needed | Unresolved |
| 6 | **Custodied wallet model** — Bankr holds private keys for all agent wallets (Privy-based); direct risk to terminal users; indirect risk to BNKR holders via platform survival dependency; a major custody breach would likely impair the platform that drives BNKR demand | MEDIUM | Bankr docs: "Auto-created at signup"; Privy infrastructure | docs.bankr.bot |
| 7 | **Clanker V1 LP lock unverified** — Clanker V3.1+ has formal LpLockerv2 contract; V1 LP lock mechanics for BNKR were not confirmed; LP NFT custodian address unknown | LOW | LpLockerv2.sol exists in v3.1-contracts repo only; BNKR deployed Dec 2024 under V1 | github.com/clanker-devco |
| 8 | **Team pseudonymity beyond Igor** — contributors beyond Yuzovitskiy are not publicly named | LOW | BankrBot GitHub org | github.com/BankrBot |
| 9 | **DeFiLlama referral code in website field** — website URL contains embedded referral parameter | LOW | DeFiLlama protocol page | defillama.com |

---

## 6. Unresolved Questions

1. **What is the full address of the BNKR buyback treasury, and what is its current balance?** Without this, the buyback narrative is unverified marketing. If the address is real and actively accumulating, it substantiates the demand story.
2. **Does the fee routing from Doppler-launched tokens continue to fund the BNKR buyback?** Clanker V1 is deprecated; if new platform volume no longer routes fees to the BNKR treasury, the demand mechanism is weakening even as platform revenue grows.
3. **Did team-adjacent wallets snipe the BNKR launch?** "Fair launch" via Clanker V1 means 0% allocation at the contract level, but first-hour LP buyers are unknown. A Dune query on BNKR transfers in the first 3,600 blocks post-deployment (Dec 3, 2024) would resolve this.
4. **Does the Coinbase Ventures Base Ecosystem Fund actually hold a position?** If verified, this upgrades the institutional backing signal. If false, it is a misrepresentation circulating in third-party contexts.
5. **Is the BNKR/WETH LP NFT locked in a Clanker V1 LP locker contract?** For V3.1+ tokens this is contractually enforced; V1 is ambiguous.
6. **What is Bankr's operational runway and burn rate?** As a custodied platform, Bankr's survival is directly tied to BNKR's value proposition; undisclosed shutdown risk would terminate the buyback mechanism.

---

## 7. Monitor

- **Watch for Coinbase Ventures confirmation** — any announcement from Coinbase Ventures or Bankr citing a formal investment would resolve Red Flag #2; absence of confirmation over time decreases credibility of the claim
- **Monitor buyback treasury address** — if/when the full address is disclosed, check whether BNKR accumulation is occurring proportional to platform revenue
- **Watch for Bankr platform incidents** — any custodied wallet breach would be a critical event for both user funds and BNKR sentiment; follow @igoryuzo and @bankrbot for incident disclosures
- **Clanker V1 → Doppler migration risk** — Bankr docs confirm Clanker is deprecated; if BNKR's liquidity or fee routing becomes impacted by legacy V1 infrastructure, watch for community pressure to migrate or relaunch
- **Token unlock calendar**: None — no cliff events. Monitor top-10 wallet movements for any unexpected large sell pressure from addresses that were originally seeded at launch.
- **Watch for audit announcement** — any third-party security audit of Bankr's backend would significantly reduce Red Flag #4

---

## 8. Data Sources

| Source | URL / Reference |
| --- | --- |
| BNKR contract on Basescan | https://basescan.org/token/0x22aF33FE49fD1Fa80c7149773dDe5890D3c76F3b |
| DeFiLlama protocol page | https://defillama.com/protocol/bankr |
| Clanker.world token page | https://www.clanker.world/clanker/0x22aF33FE49fD1Fa80c7149773dDe5890D3c76F3b |
| Bankr documentation | https://docs.bankr.bot |
| Bankr docs full LLM context | https://docs.bankr.bot/llms-full.txt |
| BankrBot GitHub org | https://github.com/BankrBot |
| Clanker V3.1 contracts (LpLockerv2) | https://github.com/clanker-devco/v3.1-contracts |
| CoinGecko BNKR | https://www.coingecko.com/en/coins/bankrcoin |
| Basescan BNKR/WETH pool | https://basescan.org/address/0xc16e685de885efc4a01d159db62bbb613a96ba70 |
| Base RPC — contract function checks | https://mainnet.base.org (eth_call, EIP-1967 slot, deployer field) |
| Rekt News | https://rekt.news (no entry found) |
| DeFiHackLabs | https://github.com/SunWeb3Sec/DeFiHackLabs (no entry found) |
| Igor Yuzovitskiy GitHub | https://github.com/igoryuzo |
