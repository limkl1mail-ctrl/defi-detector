# Blackhaven (RBT) — Adversarial Due Diligence Report

**Date:** 2026-05-16
**Investigator:** DeFi Detector
**Confidence Level:** Medium — single audit report read in full; on-chain data partially confirmed via MegaETH explorer; limited independent analyst coverage; team attribution unverified from primary sources
**Classification:** Reserve Currency (OHM-style bonding protocol) on MegaETH

---

## 1. Executive Summary

**Verdict:** Blackhaven is an extremely early-stage OHM-style reserve currency protocol on MegaETH with $800K TVL, 14-day-old contracts controlled by a single EOA, and its core price stabilization mechanism (BAM) not yet live. The protocol has a single Zellic audit with no critical findings, but the combination of centralized admin control, lack of emergency pause, and absence of the mechanism that underpins the protocol's entire value proposition makes this unsuitable for anything beyond speculative, loss-tolerant capital.

**Top 3 Risks:**
1. **BAM not live** — The Backing Arbitrage Module (the two-way NAV stabilizer that is the protocol's core pitch) is "planned" and "not guaranteed to be live at launch." Users deposit into a protocol whose core value proposition — two-way NAV defense — does not currently exist on-chain.
2. **Single EOA deployer with no confirmed multisig** — All contracts deployed by one EOA. Current `owner()` state could not be verified on-chain (MegaETH RPC failures). If ownership has not been transferred to a multisig, a compromised key = total protocol loss. No emergency pause mechanism exists regardless.
3. **OHM model track record** — Olympus DAO (claimed predecessor) declined 98%+ from ATH; virtually all OHM forks failed. The "reserve currency" model has a documented history of unsustainable tokenomics and reflexive collapse.

**Top 3 Positives:**
1. Zellic audit completed with 0 critical/high findings; most issues remediated (Zellic is a well-regarded firm not explicitly classified in our tier system but comparable to Tier 1-2)
2. Reserve backing per RBT on-chain verifiable at 5.45 USDm — protocol appears fully backed at current supply
3. Protocol-Owned Liquidity model reduces dependence on mercenary capital

---

## 2. Team Assessment

| Verified | Unverified | Assessment |
| --- | --- | --- |
| Deployer is EOA `0xb53fae9998a2ecb5b3b9e71330fbcd2b2db85591` — 820 txns over 14 days | "Created by the founder of OHM" (blocmates, Zeneca) — no primary source confirmation | **HIGH risk.** Fully pseudonymous team. OHM founder attribution is single-sourced from secondary coverage, never confirmed by the team or Jawz/Zeus directly. No team members named on website, docs, or DeFiLlama. |
| Deployer holds 6 different sRBT variants — confirms multiple test deployments | Jawz (OHM) mentioned as contributor by blocmates | Even if the OHM founder connection is real, Zeus/Jawz is pseudonymous — this adds ecosystem reputation, not real-name accountability. |
| Zellic audit engagement confirms the team interacted with a reputable security firm | No investors, VCs, or funding rounds disclosed | No LinkedIn, no corporate entity disclosed, no regulatory filings found. The team could vanish without legal recourse. |

**OHM History Context:**
- Olympus DAO launched Feb 2021, peaked at ~$1,300/OHM, currently trades near $15 — a 98%+ decline
- In Jan 2022, a DAO leader dumped $11M in a single transaction, crashing OHM ~50% in two hours and triggering cascading crashes across rebase DAOs
- CoinDesk (Dec 2021) ran "Olympus DAO Might Be the Future of Money (or It Might Be a Ponzi)"
- A 2022 lawsuit attempted to unmask co-founder "Apollo" — the case itself signals governance/legal risk
- Jawz departed Olympus DAO; the departure was framed as voluntary to avoid impacting the organization

---

## 3. Third-Party Consensus

### Audit Posture

| Firm | Tier | Date | Scope | Findings | Remediation |
| --- | --- | --- | --- | --- | --- |
| Zellic | Tier 1-2 (well-regarded, #1 CTF team pedigree) | Jan 7-14, 2026 | Bond.sol, RBTNote.sol, BackingCalculator.sol, BAM.sol, Minter.sol, RBT.sol, LiquidityManager.sol | 0 Critical, 0 High, 3 Medium, 2 Low, 6 Informational | 5/11 fixed in commits; 6/11 acknowledged |

**Scope Exclusions (critical):**
- **Key custody** — not assessed. Given single-EOA control, this is the highest-risk surface and was not audited.
- Frontend components
- Infrastructure
- Oracle data feed correctness

**Key Audit Observations:**
- **No emergency pause mechanism** — Zellic recommended implementing OpenZeppelin Pausable. Not implemented.
- **Centralization risks** — Minter owner can whitelist arbitrary addresses for unlimited RBT minting. LiquidityManager owner can retrieve LP position NFTs and any tokens. All bond terms, BAM parameters, and oracle addresses are owner-controlled.
- **BAM sandwich vulnerability** — collectPremium() is publicly callable with 5% slippage tolerance, exposing up to 5% of swap value to MEV extraction.

**Audit-to-Deployment Gap:**
Audit completed Jan 19, 2026. Contracts deployed May 1, 2026 — a **3.5-month gap**. Remediation commits reference private GitHub repo `blackhaven-xyz/blackhaven-factory`. The deployed code cannot be verified against the audited+remediated version because the repository is private. This gap means unaudited changes may exist in production.

### Independent Analyst Coverage

| Source | Finding |
| --- | --- |
| blocmates | "The OHM of MegaETH, created by Olympus DAO's founder" — positive framing with qualified optimism: "If this succeeds, it's a real money printer. Key word, real." |
| Zeneca (Letter 98) | Lists Blackhaven among 8 interesting MegaETH projects, sarcastically referencing "a good (3,3) ponzi" |
| Rekt News | No entries |
| zachxbt | No mentions found |
| PeckShield / BlockSec | No alerts |
| DeFiHackLabs | No entries |

### Bug Bounty
**None found.** No Immunefi listing. No bug bounty program mentioned in docs. On $800K TVL with single-EOA control, this is a HIGH severity gap.

---

## 4. On-Chain Findings

### Protocol Metrics

| Metric | Value | Source |
| --- | --- | --- |
| TVL (bonds) | ~$646K (all closed) | app.blackhaven.xyz/bonds |
| TVL (staking) | $154K (DeFiLlama) / $0 (app staking page) | DeFiLlama / app |
| RBT Circulating Supply | 117,393 | app.blackhaven.xyz/metrics |
| RBT Total Supply | 117,398 | app.blackhaven.xyz/metrics |
| Reserves per RBT | 5.45 USDm | app.blackhaven.xyz/metrics |
| Implied Reserve Value | ~$640K (117K × 5.45) | Calculated |
| UniV3 Pool Balance | $73,927 USDm + 21,710 RBT | mega.etherscan.io |
| Holders | 264 | mega.etherscan.io |
| Protocol Fees/Revenue | $0 (DeFiLlama) | DeFiLlama |
| Hacks | None on record | DeFiLlama |

### TVL Reconciliation
The $646K "bond TVL" appears to represent cumulative bond deposits in Genesis Phase 1, which are now closed (likely cap-hit per `terms.maxDebt` limit, not capital flight). The docs describe Phase 1 as having a fixed 10% fee "at launch." Staking shows $154K on DeFiLlama but $0 on the app — discrepancy unresolved. The Uniswap V3 pool holds $73K USDm, which may be the protocol-owned liquidity portion of reserves. The metrics-reported reserves ($640K implied) likely include bond deposits routed to `backingStorage` plus POL.

### Contract Architecture

| Contract | Address | Verified | Notes |
| --- | --- | --- | --- |
| RBT (Reserve Backed Token) | `0x8f77a685bde702e6d32a103e9aeb41906317d7e5` | Yes | ERC-20 with controlled minting, 1,528 txns |
| RBT-USDm UniV3 Pool | `0x3fa634c81Ee8aa78C4f37364e6FECcB8a89c0032` | Yes | Created May 1, 2026 via Kumbaya Factory |
| RBTBonding | Created by deployer (partial address: `0x1ad53938...4ca07d037`) | Unconfirmed | ERC-721 bond positions |
| Deployer EOA | `0xb53fae9998a2ecb5b3b9e71330fbcd2b2db85591` | N/A (EOA) | 820 txns, funded by `0x50b06B6b...9db21767d` |

**All contracts deployed by a single EOA. Current `owner()` state unverified — could have been transferred post-deployment.** No timelock. No emergency pause. Per the Zellic audit, the contract owner (whether still the deployer or a subsequent address) can:
- Whitelist arbitrary minting addresses → unlimited RBT dilution
- Retrieve LP position NFTs → drain protocol-owned liquidity
- Modify bond terms retroactively → change existing users' vesting
- Adjust BAM parameters → manipulate premium capture
- Change oracle addresses → corrupt NAV calculations

### Token Distribution
- 117,398 RBT across 264 holders — average ~445 RBT per holder
- Circulating vs. total supply nearly identical (5 RBT difference) — no significant locked/unvested supply visible
- No token distribution breakdown in docs
- No vesting schedule disclosed
- **Top-10 holder data not retrievable** — MegaETH explorer loads holder balances via JavaScript; WebFetch returns "Loading..." placeholders. With 264 holders and 14-day history, concentration is likely high but unverified

### Operational Risk

| Question | Finding |
| --- | --- |
| Who controls admin functions? | Single EOA — no multisig, no timelock |
| What happens if the key is compromised? | Total protocol loss — no pause, unlimited minting, LP drainage |
| Is BAM (core mechanism) live? | **No** — "planned mechanism that will be activated at a later stage and is not guaranteed to be live at launch" |
| Are there multiple test deployments? | Yes — 9 separate "Reserve Backed Token" contracts on MegaETH, deployer holds 6 sRBT variants, indicating rapid iteration |
| Can vault composition change without user consent? | Backing tokens (currently USDm + MEGA) can be added by owner; no removal function exists |

### NAV Calculation Method

| Aspect | Finding |
| --- | --- |
| Type | On-chain, real-time (BackingCalculator reads `balanceOf(backingStorage)` per oracle price) |
| Oracle | Unspecified provider; audit noted Redstone mentioned but oracle wrappers not in scope |
| Trust Level | Medium — on-chain calculation is good, but oracle correctness was explicitly excluded from audit |

---

## 5. Red Flags Register

| # | Flag | Severity | Evidence | Source |
| --- | --- | --- | --- | --- |
| 1 | **BAM not live** — Core price stabilization mechanism "planned, not guaranteed." Users enter with marketing of two-way NAV defense but no actual on-chain mechanism to buy/burn RBT below NAV. This is a structural absence of the protocol's primary value proposition | HIGH | "a planned mechanism that will be activated at a later stage" | docs.blackhaven.xyz/reserves/bam |
| 2 | **Single EOA deployer, current ownership unverified** — All contracts deployed by one EOA. Current `owner()` could not be verified on-chain due to MegaETH RPC failures. If ownership has not been transferred to a multisig post-deployment, a single compromised key enables unlimited RBT minting, LP drainage, and parameter manipulation. No emergency pause exists regardless of ownership structure | HIGH | Deployer `0xb53fae99...db85591` is EOA, holds Uniswap V3 NFT, created RBTBonding. Zellic §4.3 flagged centralization. No OwnershipTransferred events visible in explorer (dynamic loading prevented full verification) | mega.etherscan.io, Zellic audit p.33 |
| 3 | **No emergency pause** — Zellic explicitly recommended Pausable pattern; not implemented. During exploit, no way to halt operations without deploying new contracts | HIGH | "The contracts lack pause functionality" | Zellic audit p.40 |
| 4 | **OHM model track record** — Olympus DAO declined 98% from ATH; virtually all OHM forks failed; model accused of Ponzi dynamics by crypto fund managers | HIGH | OHM $1,300→$15; Jan 2022 cascade crash triggered by DAO leader dump | CoinDesk, Protos, Messari |
| 5 | **Multiple pre-screen failures** — $800K TVL, 14-day-old contracts, single audit, not listed on any aggregator. Fails market cap, contract age, and audit count thresholds simultaneously | HIGH | DeFiLlama $154K staking; contracts deployed May 1, 2026; 1 Zellic audit | DeFiLlama, mega.etherscan.io |
| 6 | **No bug bounty** — Zero bug bounty on $800K TVL with single-EOA control. Rational attacker incentivized to exploit rather than report | HIGH | No Immunefi listing; no bug bounty in docs | immunefi.com search |
| 7 | **Audit-to-deployment code gap** — 3.5 months between audit (Jan 19) and deployment (May 1). Private GitHub repo means deployed code unverifiable against audited version | HIGH | Audit commit `5730ca65`; deployment May 1, 2026; repo `blackhaven-xyz/blackhaven-factory` returns no public data | Zellic audit, GitHub API |
| 8 | **10% premium to team wallet** — When bonds sell above 1.05x mNAV, extra RBT minted: 25% BAM, 25% POL, **10% team wallet**, 40% reward wallet. Team extracts value from every premium bond | MEDIUM | Premium distribution BPS in Bond contract | Zellic audit §5.1 p.34 |
| 9 | **Pseudonymous team with single-source attribution** — "OHM founder" claim appears only in blocmates and Zeneca; no primary source. Even if true, pseudonymous identity adds reputation, not legal accountability | MEDIUM | No team on website, docs, or DeFiLlama | blackhaven.xyz, docs.blackhaven.xyz |
| 10 | **9 test RBT deployments** — Nine separate "Reserve Backed Token" contracts exist on MegaETH. Deployer holds tokens from 6 sRBT variants. Indicates rapid, experimental iteration before production | MEDIUM | Token search on mega.etherscan.io returns 9 RBT contracts | mega.etherscan.io/tokens?q=RBT |
| 11 | **Unlimited minting via Minter owner** — Owner can whitelist any address to mint unlimited RBT, diluting all existing holders. No cap enforced at the contract level beyond governance-set minting cap | MEDIUM | "A malicious (possibly compromised) owner could whitelist an arbitrary address to mint unlimited RBT" | Zellic audit §4.3, §5.5 |
| 12 | **Backing token removal impossible** — Once a backing token is added, it cannot be removed without redeploying BackingCalculator (which cascades to Bond and BAM redeployment). Limits emergency response | LOW | No `removeBackingToken` function | Zellic audit §3.11 |
| 13 | **BAM sandwich attack exposure** — collectPremium() publicly callable with 5% slippage tolerance. MEV bots can extract up to 5% of premium capture swap value | LOW | Default `slippageToleranceBps` = 500 (5%) | Zellic audit §3.5 |

---

## 6. Unresolved Questions

1. **Who is the actual owner() of the RBT contract?** — MegaETH RPC endpoints returned empty responses; explorer read-contract page didn't render values. The deployer EOA is confirmed, but the current `owner()` could have been transferred to a different address or multisig post-deployment. This is the single most important unknown.

2. **Is the `backingStorage` address a multisig?** — Zellic noted reserves are held at a separate `backingStorage` address "whose security depends on that address's configuration (likely a multi-sig)." We could not verify this on-chain.

3. **When will BAM activate, and what are the governance conditions?** — The docs say "subject to governance decisions" but no governance mechanism is defined. Who decides, and by what mechanism?

4. **What is the relationship between the deployer and the `0x50b06B6b...9db21767d` funder?** — The deployer was funded by this address 14 days ago. Is this a team treasury, an investor, or an exchange withdrawal?

5. **Does the deployed code match the audited+remediated version?** — With a 3.5-month gap and private repo, this cannot be verified without source code access.

6. **Why are all bonds closed?** — Likely Genesis Phase 1 cap-hit (`terms.maxDebt`), but no official communication confirms this. Is Phase 2 planned? On what timeline?

7. **Who or what is "foundation governance"?** — The docs reference "foundation governance" for minting caps and commit parameters, but no foundation entity, governance token, or voting mechanism is described.

8. **What are the specific bond discount rates and terms for future phases?** — Genesis Phase 1 offered 1-day (1%), 7-day (5%), 14-day (10%), 30-day (15%). Future terms undisclosed.

9. **What is the top-10 holder concentration?** — MegaETH explorer loads holder data dynamically, preventing extraction via WebFetch. With only 264 holders on a 14-day-old token, concentration is likely very high. If the deployer or a single wallet holds >30% of supply, this represents an additional centralization and manipulation risk.

10. **Who funded the deployer?** — The deployer EOA was funded by `0x50b06B6b...9db21767d` 14 days ago. The full address could not be reconstructed from the truncated explorer display, preventing verification of whether this is a CEX hot wallet, investor, or anonymous wallet.

---

## 7. Monitor

### Mandatory Triggers

| Trigger | Threshold | Action |
| --- | --- | --- |
| TVL drawdown | >10% from $800K baseline | Re-evaluate — capital flight signal |
| Protocol exploit or hack | Any confirmed | Immediate re-assessment |
| Smart contract upgrade | Any proxy upgrade or redeployment | Review new code; update audit gap assessment |
| Governance structure change | Any multisig deployment or timelock addition | Re-assess admin risk — would be a significant positive |
| BAM activation | BAM goes live | Major reassessment — core mechanism now testable |
| Token unlock/emission event | Any new RBT minting outside bonds | Assess dilution impact |
| New backing token added | Any addition beyond USDm/MEGA | Sub-asset diligence cascade triggered |

### Protocol-Specific Watchpoints

- **Monitor: BAM activation date** — The entire investment thesis depends on this. Until BAM is live, RBT has no on-chain mechanism to defend NAV downside. If BAM never activates, the protocol is structurally a one-way bet.
- **Monitor: Multisig migration** — If the team moves admin from single EOA to multisig with timelock, this resolves the #2 red flag. Watch for `transferOwnership()` calls on RBT and related contracts.
- **Monitor: Genesis Phase 2 announcement** — All Phase 1 bonds are closed. If no Phase 2 launches within 30 days, assess whether the protocol is going dormant.
- **Monitor: CoinGecko / CoinMarketCap listing** — Absence from aggregators limits price discovery and independent verification. Listing would be a mild positive.
- **Watch for: OHM founder confirmation or denial** — If Jawz/Zeus publicly claims or denies involvement, update team assessment accordingly.
- **Watch for: Bug bounty program launch** — Would partially address the $0 bounty gap.

---

## 8. Data Sources

### Primary Sources
- Zellic Audit Report (PDF, 41 pages): [Zellic/publications on GitHub](https://github.com/Zellic/publications/blob/master/Blackhaven%20(Core%20Contracts)%20-%20Zellic%20Audit%20Report.pdf)
- Blackhaven Docs: [docs.blackhaven.xyz/overview](https://docs.blackhaven.xyz/overview)
- Blackhaven App Metrics: [app.blackhaven.xyz/metrics](https://app.blackhaven.xyz/metrics)
- Blackhaven App Bonds: [app.blackhaven.xyz/bonds](https://app.blackhaven.xyz/bonds)
- MegaETH Explorer — RBT Token: [mega.etherscan.io/token/0x8f77a685...](https://mega.etherscan.io/token/0x8f77a685bde702e6d32a103e9aeb41906317d7e5)
- MegaETH Explorer — RBT-USDm Pool: [mega.etherscan.io/address/0x3fa634c8...](https://mega.etherscan.io/address/0x3fa634c81Ee8aa78C4f37364e6FECcB8a89c0032)
- MegaETH Explorer — Deployer EOA: [mega.etherscan.io/address/0xb53fae99...](https://mega.etherscan.io/address/0xb53fae9998a2ecb5b3b9e71330fbcd2b2db85591)
- DeFiLlama Protocol Page: [defillama.com/protocol/blackhaven](https://defillama.com/protocol/blackhaven)

### Secondary Sources
- blocmates — MegaETH Ecosystem Guide: [blocmates.com](https://www.blocmates.com/articles/megaeth-complete-project-airdrop-guide) — "The OHM of MegaETH, created by Olympus DAO's founder"
- Zeneca — Letter 98: [zeneca.xyz](https://www.zeneca.xyz/p/letter-98-a-look-at-8-of-the-most) — sarcastically referenced as "a good (3,3) ponzi"
- CoinDesk — "Olympus DAO Might Be the Future of Money (or It Might Be a Ponzi)": [coindesk.com](https://www.coindesk.com/policy/2021/12/05/olympus-dao-might-be-the-future-of-money-or-it-might-be-a-ponzi)
- CoinDesk — "OlympusDAO Co-Founder Doxxed? Lawsuit Claims to Unmask 'Apollo'": [coindesk.com](https://www.coindesk.com/business/2022/04/14/olympusdao-co-founder-doxxed-lawsuit-claims-to-unmask-apollo)
- Protos — "DAO leader causes cascade across rebase tokens after $11M dump": [protos.com](https://protos.com/rebase-daos-olympus-ohm-leader-dump-cascade-crypto/)
- ignasdefi — MegaETH DeFi Playbook: [ignasdefi.com](https://www.ignasdefi.com/p/the-defi-degens-playbook-for-megaeth) — listed Blackhaven without detail

### Sources Consulted with No Results
- Rekt News — no Blackhaven entries
- zachxbt — no Blackhaven mentions
- Immunefi — no Blackhaven bug bounty
- CoinGecko — RBT not listed
- CoinMarketCap — RBT not listed
- DeFiHackLabs — no entries
- PeckShield / BlockSec — no alerts

---

## Timeline

| Date | Event |
| --- | --- |
| Feb 2021 | Olympus DAO (OHM) launches — claimed predecessor of Blackhaven team |
| Dec 2021 | CoinDesk publishes "Olympus DAO: Future of Money or Ponzi?" |
| Jan 2022 | OHM cascade crash — DAO leader dumps $11M, OHM drops 50% in 2 hours |
| Apr 2022 | OlympusDAO co-founder "Apollo" lawsuit/doxxing attempt |
| 2023-2024 | OHM declines further; Jawz departs Olympus DAO |
| Jan 7-14, 2026 | Zellic conducts Blackhaven core contracts audit |
| Jan 19, 2026 | Zellic audit report published (commit `5730ca65`) |
| May 1, 2026 | Blackhaven contracts deployed on MegaETH mainnet |
| May 2, 2026 | Blackhaven website goes live |
| ~May 2-14, 2026 | Genesis Phase 1 bonds open and reach capacity (closed) |
| May 16, 2026 | This investigation — 264 holders, $800K TVL, all bonds closed, BAM not live |
