# Fluid (Instadapp) — Adversarial Due Diligence Report

**Date:** 2026-03-27 (Updated 2026-06-01 — Merkle distributor key compromise)
**Classification:** Retail DeFi — Unified Lending + DEX Protocol
**Confidence Level:** High — Identified team, on-chain data verified via DeFiLlama, multiple audits read/confirmed, independent analyst coverage from Messari/Nansen/OAK Research, Rekt News absent. Bad debt resolution details verified via Blockonomi, Nexus Mutual incident report, Resolv exploit analysis, Fluid governance forum (May 2026), and Tally on-chain governance (Proposal 129). Merkle distributor key compromise verified on-chain via Etherscan (May 28, 2026).

---

## 1. Executive Summary

**Verdict:** Fluid is one of DeFi's most capital-efficient and battle-tested protocols, built by a known team with a 7-year track record. However, the protocol has now suffered two security incidents in three months: ~USD 19.3M in bad debt from the Resolv USR exploit (March 2026, settled May 11) and a ~USD 258K loss from a Merkle reward distributor key compromise (May 28, 2026). The Resolv settlement was opaque, centralized, and executed without prior governance approval. The Merkle incident — while smaller — represents the first direct exploit of Fluid infrastructure (not contagion from an external protocol), and the team's failure to publicly disclose the loss reinforces transparency concerns.

**Top 3 Risks:**
1. **Treasury depleted to 99.99% own token** — After Proposal 129 executed (withdrawing diversified assets for the Resolv settlement), the governance treasury holds 22M FLUID and ~USD 2,147 in non-FLUID assets. Zero operational reserves. Cannot fund security, audits, or incident response without selling its own token. Self-referential death spiral risk.
2. **Pattern of non-disclosure across security incidents** — Both the Resolv settlement (USD 19.3M, opaque execution) and the Merkle distributor key compromise (USD 258K, characterized as "maintenance pause") were handled without transparent public disclosure. Two incidents in three months with the same communication pattern.
3. **Governance centralization with demonstrated unilateral action** — Instadapp Labs controls protocol IP and admin keys. Treasury was spent without prior governance vote (Resolv), and Merkle distributor keys were compromised under team-controlled infrastructure. Foundation transfer planned but not executed.

**Top 3 Positives:**
1. **7-year track record** — Instadapp/Fluid core lending/DEX contracts have never been directly exploited. The May 2026 Merkle distributor key compromise affected protocol-owned reward tokens (~USD 258K), not user deposits.
2. **Genuine product-market fit** — &#36;694M lending TVL, &#36;91M all-time fees, &#36;10.8M protocol revenue. #2 DEX on Ethereum by 2025 volume (&#36;156B).
3. **Strong institutional backing and audit posture** — 12+ audits (PeckShield, StateMind, MixBytes, Cantina), &#36;500K bug bounty on Immunefi, Certora formal verification in progress, backed by Pantera Capital, Standard Crypto, Coinbase Ventures.

---

## 2. Team Assessment

| Verified | Unverified | Assessment |
| --- | --- | --- |
| **Sowmay Jain** — Co-founder. Won ETHIndia hackathon 2018. From Kota, Rajasthan. Dropped out of CA studies. Active on Twitter (@sowmay_jain). | Prior professional experience beyond Instadapp | **LOW RISK** — Public identity, 7+ year track record in DeFi, no regulatory actions found |
| **Samyak Jain** — Co-founder, younger brother. First-year CS student when Instadapp was founded. | Same | **LOW RISK** — Same rationale |
| **DMH** — COO of Instadapp. Authored the Foundation governance proposal (Feb 2026). | Full identity | **LOW RISK** — Active in governance, public-facing |
| **Company: Instadapp Labs** — Entity behind Fluid. Incorporated details unclear (likely India/Singapore). | Exact jurisdiction, corporate structure | **MEDIUM** — Standard opacity for DeFi teams |

**Funding History (Verified):**
- **Seed (Oct 2019):** &#36;2.4M — Pantera Capital, Coinbase Ventures, Naval Ravikant, Balaji Srinivasan, IDEO CoLab, Robot Ventures
- **Series A (Jun 2021):** &#36;10M — Standard Crypto (lead), Andre Cronje, DeFi Alliance, LongHash Ventures
- **Private Round:** &#36;12.1M at &#36;1.00/token
- **Total raised:** ~&#36;24.5M

**No prior failed projects, no regulatory actions, no scam associations found.**

---

## 3. Third-Party Consensus

### Audit Posture

| Auditor | Scope | Tier |
| --- | --- | --- |
| PeckShield | Pre-launch comprehensive | Tier 2 |
| StateMind | Protocol security + Liquidity Layer updates | Tier 2 |
| MixBytes | Vault, DEX, Liquidity Layer | Tier 2 |
| Cantina | DEX protocol mechanics | Tier 2 |
| Certora | Formal verification (EVM + Solana) — **in progress** | Tier 1 |

- **12+ audits completed or in progress** across all protocol components
- **&#36;500K governance request** for Certora formal verification approved
- **Bug bounty:** Immunefi — up to &#36;500K for critical smart contract vulnerabilities (10% of affected funds), &#36;100K for high severity
- Bug bounty-to-TVL ratio: &#36;500K / &#36;694M = 0.072% — **adequate** for this TVL range

### Independent Analyst Coverage
- **Messari** — Two comprehensive reports: "Re-Architecting DeFi Liquidity" and "Understanding Fluid: A Comprehensive Overview"
- **Nansen** — "Fluid: An Update on Usage, Architecture, and Roadmap"
- **OAK Research** — "Fluid: A new DeFi standard to unify DEX and lending"
- **MixBytes** — Technical deep dives on both Lending/Vault and DEX architecture
- **cyber•Fund** — Two-part analysis including macro design

**Rekt News:** No entry for Fluid or Instadapp. **Mild positive.**

**zachxbt:** No flags found for Fluid or Instadapp.

### Community Sentiment
- Generally bullish. Active governance forum at gov.fluid.io
- Foundation proposal drew constructive debate, not adversarial
- Resolv incident generated concern but protocol handled it without user fund loss (Resolv committed to covering USR positions)

---

## 4. On-Chain Findings

### TVL & Financial Metrics

| Metric | Value | Source |
| --- | --- | --- |
| Lending TVL | &#36;694.27M | DeFiLlama |
| Fluid Lite TVL | &#36;163.68M | DeFiLlama |
| Active Loans | &#36;798.95M | DeFiLlama |
| Total Market Size | ~&#36;5.1B (incl. Jupiter Lend) | Messari |
| 30d Fees | &#36;2.80M | DeFiLlama |
| All-Time Fees | &#36;91.28M | DeFiLlama |
| 30d Protocol Revenue | &#36;495.96K | DeFiLlama |
| All-Time Protocol Revenue | &#36;10.84M | DeFiLlama |
| Annualized Revenue | ~&#36;15M+ | Multiple sources |
| DEX 2025 Volume (Ethereum) | &#36;156.45B (#2 behind Uniswap) | Messari |

### Chain Distribution (Lending TVL)
| Chain | TVL | Borrowed |
| --- | --- | --- |
| Ethereum | &#36;491.70M | &#36;645.77M |
| Arbitrum | &#36;104.79M | &#36;85.85M |
| Plasma | &#36;69.78M | &#36;48.40M |
| Base | &#36;22.72M | &#36;16.70M |
| Polygon | &#36;5.28M | &#36;2.23M |

### Token Distribution & Vesting

| Allocation | % | Tokens |
| --- | --- | --- |
| Community | 55% (51% per CryptoRank) | ~55M |
| Team (Current) | 23.79% | ~23.8M |
| Investors | 12.09% | ~12.1M |
| Future Team + Ecosystem | 7.85% | ~7.9M |
| Advisors | 1.27% | ~1.3M |

- **Total supply:** 100,000,000 FLUID
- **Circulating supply:** ~78.5M (78.5%)
- **Fully unlocked** — vesting completed in 2025. No upcoming cliff risk.
- **FDV:** ~&#36;164M | **Market Cap:** ~&#36;129M | **FDV/MCap ratio:** 1.27x — **healthy**
- **Price:** ~&#36;1.65 | **ATH ROI from private:** 10.74x

**Token migration:** INST → FLUID at 1:1 ratio. 12% of treasury earmarked for growth initiatives.

### Treasury Composition (verified June 1, 2026)

**Address:** `0x28849D2b63fA8D361e5fc15cB8aBB13019884d09` (labeled "InstaDApp: Treasury" on Etherscan)

| Asset | Amount | USD Value | % of Treasury |
| --- | --- | --- | --- |
| FLUID | 22,053,003 | ~USD 30.4M | 99.99% |
| GHO | 439.61 | USD 439 | <0.01% |
| MKR | 0.26 | USD 405 | <0.01% |
| stETH | 0.15 | USD 304 | <0.01% |
| LINK | 31.98 | USD 292 | <0.01% |
| CRV | 1,088.17 | USD 235 | <0.01% |
| All others | dust | <USD 500 | <0.01% |
| ETH | 0 | USD 0 | 0% |
| **Total** | | **~USD 30.4M** | |
| **Total non-FLUID** | | **~USD 2,147** | **0.007%** |

**Context:** In November 2023, the treasury held ~USD 2.2M in non-INST assets (primarily stETH + stablecoins). The diversified holdings (iETHv2 + fGHO) were withdrawn to the team multisig via Proposal 129 (executed May 2026) to cover the USD 8.2M Resolv settlement contribution. Post-execution, the treasury is left with nothing but its own governance token.

**Implications:**
1. **Self-referential treasury** — Treasury value is 100% correlated with FLUID token price. A price crash simultaneously creates the need for emergency spending AND destroys the treasury's ability to fund it.
2. **Operational funding requires token sales** — Any future security audit, bug bounty payout, incident response, or grant program requires selling FLUID, creating sell pressure on the governance token.
3. **No incident reserve** — If another Resolv-scale event occurred, the treasury has no diversified assets to deploy. It would need to sell 22M FLUID tokens into the market.
4. **Overhang risk** — 22M FLUID (22% of supply) in treasury represents potential sell pressure if governance ever approves operational spending.

**Note:** The "23% token concentration in single wallet" previously flagged (Red Flag #8) refers to this treasury address. It is not an unknown whale — it is the governance treasury itself, but the risk profile shifts from "governance capture" to "undiversified self-referential treasury with zero operational reserves."

### Contract Architecture
- **Unified Liquidity Layer** — Singleton architecture where lending, vault, and DEX share a common liquidity pool
- **Governance multisig** — Community multisig with pause capabilities
- **Admin control** — Currently Instadapp Labs; Foundation transfer planned mid-2026
- **Oracle:** Not specified on DeFiLlama; protocol uses custom oracle aggregation

### Resolv USR Bad Debt Incident (March 2026)

**What happened:** On March 22, 2026, an attacker compromised Resolv's AWS Key Management Service (KMS) environment holding the SERVICE_ROLE private key. Using this key, the attacker authorized two mint transactions — 50M USR at 02:21 UTC and 30M USR at 02:25 UTC — depositing only ~&#36;100K–&#36;200K in USDC collateral (500:1 return). The 80M unbacked USR was dumped across DEXs, crashing USR to &#36;0.025 on Curve by 02:38 UTC. The attacker converted proceeds to 11,409 ETH (~&#36;23.7M).

**Oracle failure mechanism:** Fluid and other lending protocols were using Resolv's NAV-based oracle, which hadn't updated in ~15 hours before the exploit. With the oracle still reporting USR at &#36;1.00 while the token traded at &#36;0.15–&#36;0.40 on DEXs, opportunistic actors purchased depegged wstUSR and deposited it as collateral at inflated oracle prices. They borrowed stablecoins against these positions at face value and abandoned them, creating bad debt.

**wstUSR structural insolvency:** wstUSR has a fixed 0.1725 wrapping ratio (0.1725 USR per wstUSR token). At 6x leverage, borrowers deposited &#36;1 of wstUSR and borrowed ~&#36;5 in stablecoins. Even if USR fully repegged to &#36;1.00, wstUSR would only recover to &#36;0.1725 — meaning &#36;0.1725 collateral against &#36;5 debt, still 97% underwater. This made the wstUSR bad debt mathematically irreversible regardless of USR price recovery.

**Impact on Fluid:**
- ~&#36;100M total risk exposure
- ~&#36;70M in USR-related debt repaid normally by borrowers who closed positions
- **\~&#36;19.3M in residual bad debt** — positions where borrowers profited from the oracle arbitrage and had no incentive to repay
- &#36;300M+ net outflows in a single day (largest daily outflow ever)
- 98% of wstUSR supply was locked in Fluid at 6x leverage
- Fluid paused operations within ~30 minutes of detecting the depeg

**Resolution — Three-Way Settlement (executed May 11, 2026):**

| Party | Amount | Mechanism |
| --- | --- | --- |
| Resolv Labs | ~&#36;9.7M | RLP junior tranche absorption + on-chain token burn (36.73M wstUSR/stUSR burned via contract upgrade to zero address) |
| Fluid governance treasury | ~&#36;8.2M | Direct treasury spend — **no prior governance vote** |
| Fluid core team | ~&#36;1.5M | Personal/entity commitment — to be reimbursed from future protocol revenue (effectively an IOU) |

Additional measures: FLUID token buyback program paused (~1.3% of supply already repurchased). FLUID emissions significantly reduced or eliminated to cut sell pressure. Oracle and pricing risk control systems upgraded.

**The "Short-Term Loan Coverage Agreement" — Debunked:**

The original report cited Fluid's claim that "100% of bad debts are covered by the short-term loan coverage agreement." Investigation reveals this was **not a formal financial instrument.** The term originated from a WEEX article editorially summarizing an X/Twitter post. The actual mechanism was emergency liquidity commitments from insiders: funds "committed by Lomashuk, cyberfund, weremeow, and the Fluid core team." No loan terms, interest rates, duration, or legal documentation have been published. Several investors also "expressed interest in purchasing FLUID from the treasury when additional funds are needed." This was informal insider backstopping presented as a structured agreement.

**On-chain traceability of settlement:**
- **Traceable:** The exploit itself (mint txns, DEX dumps, ETH conversion), Resolv's token burn (contract upgrade to zero address)
- **Not traceable:** The &#36;8.2M treasury contribution and &#36;1.5M team contribution have no published transaction hashes, contract addresses, or auditable on-chain trail. The governance forum post-mortem ("Post-Mortem, Treasury Actions, and Forward Strategy Following Resolv Incident" by DMH, May 11, 2026) was published **after** settlement execution, as disclosure rather than proposal.

**Retroactive Governance Proposal — Proposal 129 (May 15, 2026):**

On May 15, 2026, **Proposal 129: "Withdraw Treasury iETHv2 and fGHO Balances to Team Multisig"** was submitted on-chain (Tally). This proposal seeks retroactive governance approval to transfer treasury-held yield positions to the team multisig for clearing Resolv bad debt. It contains two actions:

1. **iETHv2 transfer** — Withdraws the entire Treasury DSA iETHv2 balance (ETH lending vault shares) to the Team Multisig via the BASIC-A connector, using `type(uint256).max` to capture all holdings.
2. **fGHO redemption** — Redeems the entire Treasury fGHO position (GHO stablecoin lending vault shares) into GHO tokens, directing proceeds to the Team Multisig via the BASIC-D-V2 connector.

The proposal references the DMH post-mortem as context. **Notably, the proposal does not specify the dollar amounts being transferred** — it uses max-balance withdrawals. The proposer address is `0x3dAff...1841`, and the execution target is `0x2386DC45AdDed673317eF068992F19421B481F4c`. As of May 17, 2026, the vote is active.

**This triggers the Monitor watchpoint from the prior report update:** "Watch for — Governance proposal retroactively ratifying the &#36;8.2M treasury spend. Absence of retroactive ratification would confirm governance is purely advisory." The proposal's existence is a partial positive — the team is seeking formal approval — but it comes 4+ days after the May 11 settlement was already executed, making this ratification rather than authorization.

@jpn_memelord characterized the proposal as "both confirm[ing] and omit[ting] several important things" in a May 16 thread, though the full thread content was not accessible at time of writing.

**Updated Assessment:** The protocol survived its largest stress test and user funds were reportedly unaffected — a genuine positive. However, the resolution process revealed that: (1) the team can unilaterally spend governance treasury funds without a vote, (2) the "coverage agreement" was informal insider lending misrepresented as a formal mechanism, (3) the settlement lacks on-chain transparency for a &#36;19.3M event, and (4) Fluid's collateral listing process allowed a relatively new stablecoin (USR) at 6x leverage with a stale NAV oracle — aggressive parameters that amplified contagion risk. The subsequent Proposal 129 represents an attempt at retroactive ratification, which partially addresses the governance gap but does not change the precedent that treasury funds were deployed before any vote.

### Merkle Distributor Key Compromise (May 28, 2026)

**What happened:** On May 28, 2026, an attacker exploited compromised proposer and approver keys for Fluid's Merkle reward distribution system. The attack sequence:

1. Compromised proposer (`0x4f104710f8d9F6EFB28c4b2f057554928Daa3a83`) submitted a malicious Merkle root
2. Compromised approver (`0x85dC44E0c3AfdFedCa52678bD4C000917C6597B2`) approved the root
3. Exploiter (`0x4925120CbE5A78Bf08F26f6E8cdF820f4c1D3dfB`) claimed rewards using empty-proof Merkle claims ~24 seconds after proposal — indicating pre-coordination or single-entity control of all three roles
4. GHO claim followed minutes later
5. Attacker swapped claimed FLUID and GHO, bridged Base/Arbitrum proceeds, and deposited ETH into Tornado Cash Router

**Funds stolen:**
- 125,000 FLUID (~USD 206K at USD 1.65)
- 51,900 GHO (~USD 51.9K)
- **Total: ~USD 258K**

**Affected contracts (Merkle distributors):**
- `0xbabb3f87424d900abd83c807c1e01a22a54e726f` (Fluid: Merkle Distributor)
- `0xd833484b198d3d05707832cc1c2d62b520d95b8a`
- `0x9d694b7f2ab2c1f328ca3e334ab74afc2814240e`

**Remediation:** Several hours post-exploit, Instadapp's Avocado Broadcaster (`0x44C437CC3c57596Da98b8e059eE2CC0604cf8717`) executed a batched transaction removing the compromised proposer and approver roles across all three Merkle distributor contracts. Tx: `0x5240aca9dd893f0ffbc9797cba23f9cf5eeacfd57350ffc86857f1695f5847e8` (Block 25,192,233, May 28, 2026 07:05:23 UTC).

**Team communication:** Fluid told users that "Merkle reward claiming is temporarily paused for a few days, potentially up to a week, while updates are made" and that "rewards will continue accumulating retroactively." **No public disclosure of the key compromise or loss of funds.** The incident was characterized as a maintenance pause, not a security event.

**Significance:** This is the first direct exploit of Fluid-controlled infrastructure (as opposed to the Resolv incident, which was contagion from an external protocol's exploit). While the loss is relatively small (~USD 258K vs USD 19.3M Resolv bad debt) and affected protocol-owned reward tokens rather than user deposits, the incident reveals: (1) the proposer/approver key management for reward distribution was a single point of failure, (2) the 24-second proposal-to-claim timeline indicates inadequate timelock or challenge period on reward roots, (3) the team chose not to disclose the exploit publicly — a pattern consistent with the opacity observed in the Resolv settlement.

---

## 5. Red Flags Register

| # | Flag | Severity | Evidence | Source |
| --- | --- | --- | --- | --- |
| 1 | **Unilateral treasury spend with only retroactive ratification** — &#36;8.2M deployed from governance treasury with no prior vote. Proposal 129 ("Withdraw Treasury iETHv2 and fGHO Balances to Team Multisig") submitted May 15 seeking retroactive approval — 4 days after settlement execution. Amounts not specified in proposal (uses max-balance withdrawals). | HIGH | DMH governance post May 11; Proposal 129 active on Tally as of May 15 | [gov.fluid.io](https://gov.fluid.io), [Tally Proposal 129](https://www.tally.xyz/gov/instadapp/proposal/129), [Blockonomi](https://blockonomi.com/fluid-covers-21m-bad-debt-after-resolv-exploit-outlines-recovery-plan/) |
| 2 | **"Short-term loan coverage agreement" was informal insider lending** — Emergency funds committed by Lomashuk, cyberfund, weremeow, and core team with no published terms, rates, duration, or legal docs. Presented publicly as a formal mechanism. | HIGH | WEEX article quotes X post; no formal agreement documentation exists | [WEEX](https://www.weex.com/news/detail/fluid-100-of-bad-debts-are-covered-by-the-short-term-loan-coverage-agreement-and-user-funds-are-not-affected-399991) |
| 3 | **Settlement lacks on-chain transparency** — &#36;8.2M treasury and &#36;1.5M team contributions have no published tx hashes or auditable trail for a &#36;19.3M event | HIGH | No on-chain evidence found across multiple sources; only Resolv's token burn (36.73M wstUSR/stUSR to zero address) is verifiable | [Resolv Exploit Analysis](https://resolv-usr-exploit.vercel.app/), [Nexus Mutual](https://nexusmutual.io/blog/resolv-protocol-incident-report-by-nexus-mutual) |
| 4 | **Governance centralization** — Instadapp Labs controls IP, admin keys, and upgrades. Resolv incident demonstrated team can unilaterally deploy governance funds. Foundation not yet formed. | HIGH | Foundation proposal submitted Feb 23, 2026; treasury spent without vote in May 2026 | [The Defiant](https://thedefiant.io/news/defi/fluid-proposes-creating-foundation), [gov.fluid.io](https://gov.fluid.io/t/proposal-establish-fluid-foundation/1768) |
| 5 | **Stale NAV oracle enabled exploitation** — Resolv's oracle hadn't updated in ~15 hours; Fluid continued pricing wstUSR at &#36;1.00 while it traded at &#36;0.025–&#36;0.40 on DEXs, allowing oracle arbitrage that created the bad debt | HIGH | Confirmed by multiple post-mortem analyses | [CryptoNews](https://cryptonews.net/news/security/32852681/), [Resolv Exploit Analysis](https://resolv-usr-exploit.vercel.app/) |
| 6 | **Aggressive collateral parameters** — wstUSR listed at up to 6x leverage with a 0.1725 wrapping ratio, creating 34x effective loss amplification. Made bad debt mathematically unrecoverable regardless of repeg. | MEDIUM | 98% of wstUSR supply locked in Fluid at 6x leverage; structural insolvency due to wrapping ratio | [Resolv Exploit Analysis](https://resolv-usr-exploit.vercel.app/) |
| 7 | **Team &#36;1.5M IOU against future revenue** — Core team contribution to settlement depends on future protocol revenue with no published repayment schedule | MEDIUM | Confirmed by Blockonomi | [Blockonomi](https://blockonomi.com/fluid-covers-21m-bad-debt-after-resolv-exploit-outlines-recovery-plan/) |
| 8 | **Treasury is 99.99% FLUID with zero operational reserves** — Post-Proposal 129, treasury holds 22M FLUID (USD 30.4M notional) and only ~USD 2,147 in non-FLUID assets (dust). No ETH, no stablecoins, no diversified holdings. Cannot fund operations, audits, bug bounties, or incident response without selling its own governance token. Self-referential death spiral risk: price crash simultaneously creates spending need AND destroys treasury value. | HIGH | Treasury address `0x28849D2b63fA8D361e5fc15cB8aBB13019884d09` verified on Etherscan June 1, 2026 | [Etherscan](https://etherscan.io/address/0x28849D2b63fA8D361e5fc15cB8aBB13019884d09), [Tally](https://www.tally.xyz/gov/instadapp) |
| 9 | **Merkle distributor key compromise (May 28, 2026)** — Proposer and approver keys for Fluid's reward distribution system were compromised. Attacker submitted malicious Merkle root, approved it, and claimed 125K FLUID + 51.9K GHO (~USD 258K) using empty-proof claims within 24 seconds of proposal. Funds routed to Tornado Cash. First direct exploit of Fluid infrastructure. | HIGH | Exploiter: `0x4925120CbE5A78Bf08F26f6E8cdF820f4c1D3dfB`; Remediation tx: `0x5240aca9...5847e8` (Block 25,192,233) | [Etherscan](https://etherscan.io/tx/0x5240aca9dd893f0ffbc9797cba23f9cf5eeacfd57350ffc86857f1695f5847e8), [DeBank](https://debank.com/profile/0x4925120CbE5A78Bf08F26f6E8cdF820f4c1D3dfB/) |
| 10 | **No public disclosure of Merkle exploit** — Team characterized the incident as a routine "maintenance pause" for reward claiming. No acknowledgment of key compromise or USD 258K loss. Pattern consistent with Resolv settlement opacity. | HIGH | Fluid community communications; absence of any security disclosure or post-mortem | @0xMakima_ on-chain analysis thread |
| 11 | **24-second proposal-to-claim window** — Merkle reward roots could be proposed, approved, and claimed within seconds, with no timelock or challenge period. Enabled instant drain once keys were compromised. | MEDIUM | On-chain timing: root proposed → approved → claimed in ~24 seconds | On-chain block timestamps |
| 12 | **DEX Lite and certain operations out of bug bounty scope** — "DexLite Protocol" explicitly excluded from Immunefi program | LOW | Immunefi scope page | [Immunefi](https://immunefi.com/bug-bounty/instadapp/) |
| 13 | **No GitHub listed on DeFiLlama** — Source code repos not linked, though Instadapp has public GitHub | LOW | DeFiLlama protocol page shows "None listed" for GitHub | DeFiLlama |

---

## 6. Unresolved Questions

1. **Team multisig: address, signers, threshold, and current holdings?** This single entity received the iETHv2/fGHO from Proposal 129 (~USD 8.2M), controls admin keys, and executed the Merkle distributor role revocation. Its address, signer identities, threshold configuration, and current balance are all undocumented publicly.
2. **What does @jpn&#95;memelord's thread claim Proposal 129 "omits"?** The full thread was not accessible at time of writing. The critique may identify material gaps in the settlement disclosure.
3. **What are the exact terms of the insider "short-term loan"?** Funds committed by Lomashuk, cyberfund, weremeow, and core team — interest rate, duration, repayment triggers, collateral, and current outstanding balance are all unknown. Has the Proposal 129 execution repaid this loan, or is it still outstanding?
4. **Team USD 1.5M IOU repayment status?** Contractual or informal? What happens if protocol revenue doesn't cover it? With the treasury now empty of non-FLUID assets, is this IOU effectively written off?
5. **Oracle and collateral listing changes post-Resolv — have they shipped?** The post-mortem mentioned per-key pricing, multi-source feeds, deviation checks, sequencer monitoring for L2, and more conservative leverage limits. Six weeks later — what's live vs. still planned?
6. **Foundation status?** Two security incidents and an empty treasury make Foundation formation (with treasury controls, key management policies, and disclosure requirements) more urgent than ever. What's the timeline? Does Instadapp Labs retain indefinite control if it doesn't pass?
7. **DEX V2 audit status?** Originally planned Q2 2026, postponed per post-mortem. Has audit work begun? Which firms?
8. **Merkle distributor key compromise — root cause?** Were the proposer/approver keys hot keys, HSM-protected, or multisig-controlled? Was this an insider action or external compromise? What key management changes are being implemented?
9. **Will the redesigned Merkle reward system include a timelock?** A 24-second proposal-to-claim window provided zero defense. The "updates" mentioned in the pause announcement should include a mandatory delay — will they?
10. **Will the team publish a post-mortem for the May 28 exploit?** As of June 1, no public acknowledgment of the key compromise or fund loss. Two undisclosed/opaquely-disclosed incidents in three months establishes a pattern.
11. **Total value at risk in remaining reward distributor contracts?** If other contracts use the same propose → approve → claim architecture with no delay, they remain exploitable until redesigned.
12. **Treasury re-diversification plan?** With only FLUID remaining, how will the protocol fund Certora verification (USD 500K approved), bug bounties, grants, and future incident response without selling its own token? Is there a governance proposal in progress?

---

## 7. Monitor

- **RESOLVED — Proposal 129 executed.** "Withdraw Treasury iETHv2 and fGHO Balances to Team Multisig" passed and executed. Retroactive ratification of the treasury spend is complete. Result: treasury now holds only FLUID tokens (~USD 2,147 in non-FLUID). The spend-first-vote-later precedent is confirmed and ratified by governance.
- **ACTIVE — Treasury re-diversification.** With only FLUID remaining, the protocol needs a treasury management strategy. Watch for governance proposals to sell FLUID for stablecoins/ETH, or to establish an operational reserve. Absence of any such proposal = the protocol is flying without a safety net.
- **ACTIVE — Merkle distributor post-mortem and system redesign.** Team has paused reward claiming "for a few days, potentially up to a week." Watch for: (a) public disclosure of the key compromise, (b) introduction of timelocks or challenge periods on Merkle root proposals, (c) independent audit of the new reward distribution mechanism. Absence of (a) would confirm a pattern of non-disclosure across multiple security incidents.
- **Monitor Q2 2026** — DEX V2 launch. Postponed per post-mortem pending market stabilization. New contract surface area = new risk. Check audit completion before using.
- **Monitor mid-2026** — Foundation formation. Now more urgent: the Resolv incident demonstrated the team will spend treasury funds without governance approval. Foundation must include treasury controls to be meaningful.
- **Watch for** — Publication of on-chain transaction details for the settlement. Transparency improvements would partially mitigate opacity concerns.
- **Watch for** — Repayment status of the &#36;1.5M team IOU from protocol revenue. Continued non-disclosure = continued risk.
- **Watch for** — Oracle architecture documentation post-upgrade. Confirmation of market-price oracles with liquidity-weighted averaging (replacing stale NAV) would be a significant positive.
- **Watch for** — Post-Resolv collateral listing policy changes. More conservative leverage limits and oracle requirements on new assets would be a positive signal.
- **Watch for** — 23% wallet activity. Large sell pressure or governance voting from this wallet would confirm centralization concern.
- **Monitor** — Certora formal verification completion. When published, this would be a major security positive (Tier 1 verification).
- **Watch for** — FLUID buyback program resumption. Currently paused to cover settlement costs; resumption signals treasury recovery.

---

## 8. Data Sources

| Source | URL |
| --- | --- |
| DeFiLlama — Fluid Lending | https://defillama.com/protocol/fluid-lending |
| DeFiLlama — Fluid Fees | DeFiLlama fees API |
| Fluid Docs — Audits & Security | https://docs.fluid.instadapp.io/audits-and-security.html |
| Immunefi — Instadapp Bug Bounty | https://immunefi.com/bug-bounty/instadapp/ |
| Tokenomist — FLUID Tokenomics | https://tokenomist.ai/instadapp |
| CryptoRank — Instadapp ICO | https://cryptorank.io/ico/instadapp |
| Governance Forum — Foundation Proposal | https://gov.fluid.io/t/proposal-establish-fluid-foundation/1768 |
| Governance Forum — Security Budget | https://gov.fluid.io/t/security-budget-request/1754 |
| Messari — Fluid Reports | https://messari.io/project/fluid-instadapp |
| The Defiant — Foundation Coverage | https://thedefiant.io/news/defi/fluid-proposes-creating-foundation |
| Blockworks — Fluid Coverage | https://blockworks.co/news/defi-superapp-competitor-to-aave-uniswap |
| CoinDesk — Instadapp Seed Round | https://www.coindesk.com/markets/2019/10/01/instadapp-defi-site-raises-24-million-from-prominent-crypto-investors |
| The Block — Series A | https://www.theblock.co/linked/108224/defi-startup-instadapp-raises-10-million-in-new-funding |
| Resolv USR Exploit Analysis | https://resolv-usr-exploit.vercel.app/ |
| WEEX — Fluid Bad Debt Coverage | https://www.weex.com/news/detail/fluid-100-of-bad-debts-are-covered-by-the-short-term-loan-coverage-agreement-and-user-funds-are-not-affected-399991 |
| Blockonomi — Fluid &#36;21M Recovery Plan | https://blockonomi.com/fluid-covers-21m-bad-debt-after-resolv-exploit-outlines-recovery-plan/ |
| Halborn — Resolv Hack Explained | https://www.halborn.com/blog/post/explained-the-resolv-hack-march-2026 |
| Nexus Mutual — Resolv Incident Report | https://nexusmutual.io/blog/resolv-protocol-incident-report-by-nexus-mutual |
| CryptoNews — Fluid Oracle Failure Analysis | https://cryptonews.net/news/security/32852681/ |
| Governance Forum — Post-Mortem & Treasury Actions | https://gov.fluid.io (DMH, May 11, 2026) |
| Phemex — Fluid &#36;70M Repayments | https://phemex.com/news/article/fluid-commences-70m-repayments-following-resolv-incident-68934 |
| MixBytes — Fluid DEX Technical Analysis | https://mixbytes.io/blog/modern-dex-es-how-they-re-made-fluid-dex |
| MixBytes — Fluid Vault Technical Analysis | https://mixbytes.io/blog/modern-defi-lending-protocols-how-its-made-fluid-vault |
| Nansen — Fluid Research | https://research.nansen.ai/articles/fluid-an-update-on-usage-architecture-and-roadmap |
| OAK Research — Fluid Analysis | https://oakresearch.io/en/reports/protocols/fluid-new-defi-standard-unify-dex-lending |
| Instadapp Blog — Fluid Launch | https://blog.instadapp.io/fluid/ |
| Instadapp Blog — DEX V2 | https://blog.instadapp.io/fluid-dex-v2/ |
| DL News — Foundation Coverage | https://www.dlnews.com/articles/defi/why-fluid-devs-want-to-give-a-dao-ultimate-authority/ |
| Tally — Proposal 129 (Treasury iETHv2/fGHO Withdrawal) | https://www.tally.xyz/gov/instadapp/proposal/129 |
| Tally — InstaDapp Governance Overview | https://www.tally.xyz/gov/instadapp |
| @jpn_memelord — Proposal 129 Analysis Thread (May 16, 2026) | https://x.com/jpn_memelord/status/2055723380142145632 |
| Ethplorer — fGHO Token Contract | https://ethplorer.io/address/0x6a29a46e21c730dca1d8b23d637c101cec605c5b |
| Etherscan — Merkle Distributor Key Revocation Tx | https://etherscan.io/tx/0x5240aca9dd893f0ffbc9797cba23f9cf5eeacfd57350ffc86857f1695f5847e8 |
| DeBank — Exploiter Wallet | https://debank.com/profile/0x4925120CbE5A78Bf08F26f6E8cdF820f4c1D3dfB/ |
| @0xMakima_ — Merkle Distributor Exploit Analysis (May 2026) | https://x.com/0xMakima_/status/2061150535638798724 |
| Etherscan — InstaDApp Treasury Address (verified Jun 1, 2026) | https://etherscan.io/address/0x28849D2b63fA8D361e5fc15cB8aBB13019884d09 |
| Tally — Proposal 129 Executed | https://www.tally.xyz/gov/instadapp/proposal/129 |
| Fluid Governance Forum — Treasury Usage Discussion | https://gov.fluid.io/t/discussion-instadapp-treasury-usage/669 |

---

## Timeline

| Date | Event |
| --- | --- |
| Aug 2018 | Sowmay & Samyak Jain win ETHIndia hackathon with Instadapp concept |
| Oct 2019 | Seed round: &#36;2.4M (Pantera, Coinbase Ventures, Naval Ravikant) |
| Jun 2021 | Series A: &#36;10M (Standard Crypto lead, Andre Cronje) |
| Jun 2021 | INST token launch |
| 2021–2024 | Instadapp operates as DeFi management layer; grows to billions in TVL |
| 2024 | Fluid protocol launches (lending + vault) |
| Oct 2024 | Fluid DEX launches on Ethereum |
| 2024 | INST → FLUID token migration (1:1) |
| 2025 | Fluid DEX becomes #2 on Ethereum by volume (&#36;156B annual) |
| 2025 | All FLUID token vesting completes — fully unlocked |
| Aug 2025 | Protocol revenue hits record &#36;1.52M monthly |
| Feb 2026 | Foundation proposal submitted (Cayman Islands entity, &#36;250K/month grant) |
| Feb 2026 | Venus Protocol partnership for BNB Chain deployment |
| Mar 2026 | Jupiter Lend integration on Solana (&#36;1.6B via Jupiter) |
| Mar 22, 2026 02:21 UTC | Resolv exploit begins — attacker mints 50M USR via compromised AWS KMS key |
| Mar 22, 2026 02:25 UTC | Second mint — 30M additional USR (80M total unbacked) |
| Mar 22, 2026 02:38 UTC | USR hits &#36;0.025 on Curve (97.5% depeg) |
| Mar 22, 2026 ~03:00 UTC | Fluid pauses affected markets (~30 min response time) |
| Mar 22–23, 2026 | &#36;300M+ net outflows from Fluid in single day; ~&#36;70M in USR debt repaid by borrowers |
| Mar 25, 2026 | Fluid announces "short-term loan coverage agreement" via X — emergency funds committed by Lomashuk, cyberfund, weremeow, core team |
| Apr 6, 2026 | Resolv deploys contract upgrade to burn 36.73M wstUSR/stUSR from hacker wallets (on-chain) |
| May 11, 2026 | Three-way settlement executed: Resolv &#36;9.7M, Fluid treasury &#36;8.2M, team &#36;1.5M |
| May 11, 2026 | DMH publishes "Post-Mortem, Treasury Actions, and Forward Strategy" on governance forum — after settlement execution |
| May 12, 2026 | Fluid publicly confirms full &#36;19.3M bad debt coverage |
| May 15, 2026 | Proposal 129 submitted on-chain: "Withdraw Treasury iETHv2 and fGHO Balances to Team Multisig" — retroactive ratification of treasury spend |
| May 16, 2026 | @jpn_memelord thread characterizes proposal as "confirm[ing] and omit[ting] several important things" |
| May 28, 2026 | **Merkle distributor key compromise** — attacker drains 125K FLUID + 51.9K GHO (~USD 258K) via compromised proposer/approver keys. Empty-proof claims executed 24 seconds after malicious root proposal. Funds routed to Tornado Cash. |
| May 28, 2026 07:05 UTC | Instadapp Avocado Broadcaster removes compromised proposer/approver roles from 3 Merkle distributor contracts (Block 25,192,233) |
| May 28, 2026 (approx) | Fluid announces "Merkle reward claiming temporarily paused for a few days" — no disclosure of exploit or fund loss |
| Q2 2026 (postponed) | DEX V2 launch — delayed per post-mortem pending market stabilization |
| ~6 weeks from May 11 (planned) | Solana DEX launch |
| Mid-2026 (planned) | Foundation IP transfer completion |
