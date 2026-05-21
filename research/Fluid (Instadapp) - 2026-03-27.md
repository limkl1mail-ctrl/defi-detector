# Fluid (Instadapp) — Adversarial Due Diligence Report

**Date:** 2026-03-27 (Updated 2026-05-17 — retroactive treasury governance proposal)
**Classification:** Retail DeFi — Unified Lending + DEX Protocol
**Confidence Level:** High — Identified team, on-chain data verified via DeFiLlama, multiple audits read/confirmed, independent analyst coverage from Messari/Nansen/OAK Research, Rekt News absent. Bad debt resolution details verified via Blockonomi, Nexus Mutual incident report, Resolv exploit analysis, Fluid governance forum (May 2026), and Tally on-chain governance (Proposal 129).

---

## 1. Executive Summary

**Verdict:** Fluid is one of DeFi's most capital-efficient and battle-tested protocols, built by a known team with a 7-year track record and no direct smart contract exploits. The protocol absorbed ~$19.3M in bad debt from the Resolv USR exploit (March 2026) and completed a three-way settlement on May 11, 2026 — but the resolution was opaque, centralized, and executed without prior governance approval, reinforcing existing concerns about team control.

**Top 3 Risks:**
1. **Opaque bad debt resolution** — The ~$19.3M settlement was split between Resolv ($9.7M), Fluid treasury ($8.2M), and team ($1.5M IOU against future revenue). The $8.2M treasury spend had no governance vote. The "short-term loan coverage agreement" cited in initial communications was informal insider lending with no published terms.
2. **Governance centralization** — Instadapp Labs still controls protocol IP and admin keys. The treasury spend decision during the Resolv incident demonstrated that team can unilaterally deploy governance funds. Foundation transfer to Cayman Islands entity planned for mid-2026 but not yet executed.
3. **23% token concentration** — One wallet holds 23% of FLUID supply, creating centralization and regulatory risk.

**Top 3 Positives:**
1. **7-year track record** — Instadapp/Fluid has never lost user funds to a smart contract exploit across any deployment.
2. **Genuine product-market fit** — $694M lending TVL, $91M all-time fees, $10.8M protocol revenue. #2 DEX on Ethereum by 2025 volume ($156B).
3. **Strong institutional backing and audit posture** — 12+ audits (PeckShield, StateMind, MixBytes, Cantina), $500K bug bounty on Immunefi, Certora formal verification in progress, backed by Pantera Capital, Standard Crypto, Coinbase Ventures.

---

## 2. Team Assessment

| Verified | Unverified | Assessment |
| --- | --- | --- |
| **Sowmay Jain** — Co-founder. Won ETHIndia hackathon 2018. From Kota, Rajasthan. Dropped out of CA studies. Active on Twitter (@sowmay_jain). | Prior professional experience beyond Instadapp | **LOW RISK** — Public identity, 7+ year track record in DeFi, no regulatory actions found |
| **Samyak Jain** — Co-founder, younger brother. First-year CS student when Instadapp was founded. | Same | **LOW RISK** — Same rationale |
| **DMH** — COO of Instadapp. Authored the Foundation governance proposal (Feb 2026). | Full identity | **LOW RISK** — Active in governance, public-facing |
| **Company: Instadapp Labs** — Entity behind Fluid. Incorporated details unclear (likely India/Singapore). | Exact jurisdiction, corporate structure | **MEDIUM** — Standard opacity for DeFi teams |

**Funding History (Verified):**
- **Seed (Oct 2019):** $2.4M — Pantera Capital, Coinbase Ventures, Naval Ravikant, Balaji Srinivasan, IDEO CoLab, Robot Ventures
- **Series A (Jun 2021):** $10M — Standard Crypto (lead), Andre Cronje, DeFi Alliance, LongHash Ventures
- **Private Round:** $12.1M at $1.00/token
- **Total raised:** ~$24.5M

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
- **$500K governance request** for Certora formal verification approved
- **Bug bounty:** Immunefi — up to $500K for critical smart contract vulnerabilities (10% of affected funds), $100K for high severity
- Bug bounty-to-TVL ratio: $500K / $694M = 0.072% — **adequate** for this TVL range

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
| Lending TVL | $694.27M | DeFiLlama |
| Fluid Lite TVL | $163.68M | DeFiLlama |
| Active Loans | $798.95M | DeFiLlama |
| Total Market Size | ~$5.1B (incl. Jupiter Lend) | Messari |
| 30d Fees | $2.80M | DeFiLlama |
| All-Time Fees | $91.28M | DeFiLlama |
| 30d Protocol Revenue | $495.96K | DeFiLlama |
| All-Time Protocol Revenue | $10.84M | DeFiLlama |
| Annualized Revenue | ~$15M+ | Multiple sources |
| DEX 2025 Volume (Ethereum) | $156.45B (#2 behind Uniswap) | Messari |

### Chain Distribution (Lending TVL)
| Chain | TVL | Borrowed |
| --- | --- | --- |
| Ethereum | $491.70M | $645.77M |
| Arbitrum | $104.79M | $85.85M |
| Plasma | $69.78M | $48.40M |
| Base | $22.72M | $16.70M |
| Polygon | $5.28M | $2.23M |

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
- **FDV:** ~$164M | **Market Cap:** ~$129M | **FDV/MCap ratio:** 1.27x — **healthy**
- **Price:** ~$1.65 | **ATH ROI from private:** 10.74x

**Token migration:** INST → FLUID at 1:1 ratio. 12% of treasury earmarked for growth initiatives.

### Contract Architecture
- **Unified Liquidity Layer** — Singleton architecture where lending, vault, and DEX share a common liquidity pool
- **Governance multisig** — Community multisig with pause capabilities
- **Admin control** — Currently Instadapp Labs; Foundation transfer planned mid-2026
- **Oracle:** Not specified on DeFiLlama; protocol uses custom oracle aggregation

### Resolv USR Bad Debt Incident (March 2026)

**What happened:** On March 22, 2026, an attacker compromised Resolv's AWS Key Management Service (KMS) environment holding the SERVICE_ROLE private key. Using this key, the attacker authorized two mint transactions — 50M USR at 02:21 UTC and 30M USR at 02:25 UTC — depositing only ~$100K–$200K in USDC collateral (500:1 return). The 80M unbacked USR was dumped across DEXs, crashing USR to $0.025 on Curve by 02:38 UTC. The attacker converted proceeds to 11,409 ETH (~$23.7M).

**Oracle failure mechanism:** Fluid and other lending protocols were using Resolv's NAV-based oracle, which hadn't updated in ~15 hours before the exploit. With the oracle still reporting USR at $1.00 while the token traded at $0.15–$0.40 on DEXs, opportunistic actors purchased depegged wstUSR and deposited it as collateral at inflated oracle prices. They borrowed stablecoins against these positions at face value and abandoned them, creating bad debt.

**wstUSR structural insolvency:** wstUSR has a fixed 0.1725 wrapping ratio (0.1725 USR per wstUSR token). At 6x leverage, borrowers deposited $1 of wstUSR and borrowed ~$5 in stablecoins. Even if USR fully repegged to $1.00, wstUSR would only recover to $0.1725 — meaning $0.1725 collateral against $5 debt, still 97% underwater. This made the wstUSR bad debt mathematically irreversible regardless of USR price recovery.

**Impact on Fluid:**
- ~$100M total risk exposure
- ~$70M in USR-related debt repaid normally by borrowers who closed positions
- **\~$19.3M in residual bad debt** — positions where borrowers profited from the oracle arbitrage and had no incentive to repay
- $300M+ net outflows in a single day (largest daily outflow ever)
- 98% of wstUSR supply was locked in Fluid at 6x leverage
- Fluid paused operations within ~30 minutes of detecting the depeg

**Resolution — Three-Way Settlement (executed May 11, 2026):**

| Party | Amount | Mechanism |
| --- | --- | --- |
| Resolv Labs | ~$9.7M | RLP junior tranche absorption + on-chain token burn (36.73M wstUSR/stUSR burned via contract upgrade to zero address) |
| Fluid governance treasury | ~$8.2M | Direct treasury spend — **no prior governance vote** |
| Fluid core team | ~$1.5M | Personal/entity commitment — to be reimbursed from future protocol revenue (effectively an IOU) |

Additional measures: FLUID token buyback program paused (~1.3% of supply already repurchased). FLUID emissions significantly reduced or eliminated to cut sell pressure. Oracle and pricing risk control systems upgraded.

**The "Short-Term Loan Coverage Agreement" — Debunked:**

The original report cited Fluid's claim that "100% of bad debts are covered by the short-term loan coverage agreement." Investigation reveals this was **not a formal financial instrument.** The term originated from a WEEX article editorially summarizing an X/Twitter post. The actual mechanism was emergency liquidity commitments from insiders: funds "committed by Lomashuk, cyberfund, weremeow, and the Fluid core team." No loan terms, interest rates, duration, or legal documentation have been published. Several investors also "expressed interest in purchasing FLUID from the treasury when additional funds are needed." This was informal insider backstopping presented as a structured agreement.

**On-chain traceability of settlement:**
- **Traceable:** The exploit itself (mint txns, DEX dumps, ETH conversion), Resolv's token burn (contract upgrade to zero address)
- **Not traceable:** The $8.2M treasury contribution and $1.5M team contribution have no published transaction hashes, contract addresses, or auditable on-chain trail. The governance forum post-mortem ("Post-Mortem, Treasury Actions, and Forward Strategy Following Resolv Incident" by DMH, May 11, 2026) was published **after** settlement execution, as disclosure rather than proposal.

**Retroactive Governance Proposal — Proposal 129 (May 15, 2026):**

On May 15, 2026, **Proposal 129: "Withdraw Treasury iETHv2 and fGHO Balances to Team Multisig"** was submitted on-chain (Tally). This proposal seeks retroactive governance approval to transfer treasury-held yield positions to the team multisig for clearing Resolv bad debt. It contains two actions:

1. **iETHv2 transfer** — Withdraws the entire Treasury DSA iETHv2 balance (ETH lending vault shares) to the Team Multisig via the BASIC-A connector, using `type(uint256).max` to capture all holdings.
2. **fGHO redemption** — Redeems the entire Treasury fGHO position (GHO stablecoin lending vault shares) into GHO tokens, directing proceeds to the Team Multisig via the BASIC-D-V2 connector.

The proposal references the DMH post-mortem as context. **Notably, the proposal does not specify the dollar amounts being transferred** — it uses max-balance withdrawals. The proposer address is `0x3dAff...1841`, and the execution target is `0x2386DC45AdDed673317eF068992F19421B481F4c`. As of May 17, 2026, the vote is active.

**This triggers the Monitor watchpoint from the prior report update:** "Watch for — Governance proposal retroactively ratifying the $8.2M treasury spend. Absence of retroactive ratification would confirm governance is purely advisory." The proposal's existence is a partial positive — the team is seeking formal approval — but it comes 4+ days after the May 11 settlement was already executed, making this ratification rather than authorization.

@jpn_memelord characterized the proposal as "both confirm[ing] and omit[ting] several important things" in a May 16 thread, though the full thread content was not accessible at time of writing.

**Updated Assessment:** The protocol survived its largest stress test and user funds were reportedly unaffected — a genuine positive. However, the resolution process revealed that: (1) the team can unilaterally spend governance treasury funds without a vote, (2) the "coverage agreement" was informal insider lending misrepresented as a formal mechanism, (3) the settlement lacks on-chain transparency for a $19.3M event, and (4) Fluid's collateral listing process allowed a relatively new stablecoin (USR) at 6x leverage with a stale NAV oracle — aggressive parameters that amplified contagion risk. The subsequent Proposal 129 represents an attempt at retroactive ratification, which partially addresses the governance gap but does not change the precedent that treasury funds were deployed before any vote.

---

## 5. Red Flags Register

| # | Flag | Severity | Evidence | Source |
| --- | --- | --- | --- | --- |
| 1 | **Unilateral treasury spend with only retroactive ratification** — $8.2M deployed from governance treasury with no prior vote. Proposal 129 ("Withdraw Treasury iETHv2 and fGHO Balances to Team Multisig") submitted May 15 seeking retroactive approval — 4 days after settlement execution. Amounts not specified in proposal (uses max-balance withdrawals). | HIGH | DMH governance post May 11; Proposal 129 active on Tally as of May 15 | [gov.fluid.io](https://gov.fluid.io), [Tally Proposal 129](https://www.tally.xyz/gov/instadapp/proposal/129), [Blockonomi](https://blockonomi.com/fluid-covers-21m-bad-debt-after-resolv-exploit-outlines-recovery-plan/) |
| 2 | **"Short-term loan coverage agreement" was informal insider lending** — Emergency funds committed by Lomashuk, cyberfund, weremeow, and core team with no published terms, rates, duration, or legal docs. Presented publicly as a formal mechanism. | HIGH | WEEX article quotes X post; no formal agreement documentation exists | [WEEX](https://www.weex.com/news/detail/fluid-100-of-bad-debts-are-covered-by-the-short-term-loan-coverage-agreement-and-user-funds-are-not-affected-399991) |
| 3 | **Settlement lacks on-chain transparency** — $8.2M treasury and $1.5M team contributions have no published tx hashes or auditable trail for a $19.3M event | HIGH | No on-chain evidence found across multiple sources; only Resolv's token burn (36.73M wstUSR/stUSR to zero address) is verifiable | [Resolv Exploit Analysis](https://resolv-usr-exploit.vercel.app/), [Nexus Mutual](https://nexusmutual.io/blog/resolv-protocol-incident-report-by-nexus-mutual) |
| 4 | **Governance centralization** — Instadapp Labs controls IP, admin keys, and upgrades. Resolv incident demonstrated team can unilaterally deploy governance funds. Foundation not yet formed. | HIGH | Foundation proposal submitted Feb 23, 2026; treasury spent without vote in May 2026 | [The Defiant](https://thedefiant.io/news/defi/fluid-proposes-creating-foundation), [gov.fluid.io](https://gov.fluid.io/t/proposal-establish-fluid-foundation/1768) |
| 5 | **Stale NAV oracle enabled exploitation** — Resolv's oracle hadn't updated in ~15 hours; Fluid continued pricing wstUSR at $1.00 while it traded at $0.025–$0.40 on DEXs, allowing oracle arbitrage that created the bad debt | HIGH | Confirmed by multiple post-mortem analyses | [CryptoNews](https://cryptonews.net/news/security/32852681/), [Resolv Exploit Analysis](https://resolv-usr-exploit.vercel.app/) |
| 6 | **Aggressive collateral parameters** — wstUSR listed at up to 6x leverage with a 0.1725 wrapping ratio, creating 34x effective loss amplification. Made bad debt mathematically unrecoverable regardless of repeg. | MEDIUM | 98% of wstUSR supply locked in Fluid at 6x leverage; structural insolvency due to wrapping ratio | [Resolv Exploit Analysis](https://resolv-usr-exploit.vercel.app/) |
| 7 | **Team $1.5M IOU against future revenue** — Core team contribution to settlement depends on future protocol revenue with no published repayment schedule | MEDIUM | Confirmed by Blockonomi | [Blockonomi](https://blockonomi.com/fluid-covers-21m-bad-debt-after-resolv-exploit-outlines-recovery-plan/) |
| 8 | **23% token concentration in single wallet** — Creates governance capture risk and regulatory exposure | MEDIUM | Reported by CoinMarketCap CMC AI analysis | [CoinMarketCap](https://coinmarketcap.com/cmc-ai/instadapp/latest-updates/) |
| 9 | **DEX Lite and certain operations out of bug bounty scope** — "DexLite Protocol" explicitly excluded from Immunefi program | LOW | Immunefi scope page | [Immunefi](https://immunefi.com/bug-bounty/instadapp/) |
| 10 | **No GitHub listed on DeFiLlama** — Source code repos not linked, though Instadapp has public GitHub | LOW | DeFiLlama protocol page shows "None listed" for GitHub | DeFiLlama |

---

## 6. Unresolved Questions

1. **What are the exact dollar amounts of the iETHv2 and fGHO positions in Proposal 129?** The proposal uses `type(uint256).max` (all holdings) without specifying amounts. Do these balances correspond to the previously reported $8.2M, or a different figure?
2. **What is the composition and identity of the "Team Multisig" receiving the positions?** How many signers, what threshold, and are their identities published? This is the destination for governance treasury funds.
3. **What does @jpn&#95;memelord's thread claim the proposal "omits"?** The full thread was not accessible at time of writing. The critique may identify material gaps.
4. **What are the exact terms of the "short-term loan" from Lomashuk, cyberfund, and weremeow?** Interest rate, duration, repayment triggers, collateral (if any)? Has the loan been repaid from the settlement, or is it still outstanding?
5. **What is the $1.5M team IOU repayment schedule?** Is it contractual or informal? What happens if protocol revenue doesn't cover it?
6. **What oracle changes were implemented post-incident?** The post-mortem mentions per-key pricing configurations, multi-source feeds, deviation checks, and sequencer uptime monitoring for L2 — have these shipped?
7. **What collateral listing criteria** will be implemented post-Resolv to prevent future aggressive leverage on new assets?
8. **What is the exact multisig configuration** (signers, threshold) for Fluid's admin keys? How many signers, and are their identities published?
9. **Which wallet holds 23% of FLUID?** Is it team, treasury, or an external entity?
10. **Will the Foundation proposal pass governance?** What happens if it doesn't — does Instadapp Labs retain indefinite control? The treasury spend incident makes this question more urgent.
11. **DEX V2 audit status** — Originally planned Q2 2026 but postponed per post-mortem. When it launches, have all new DEX types been audited?

---

## 7. Monitor

- **ACTIVE — Proposal 129 vote outcome.** "Withdraw Treasury iETHv2 and fGHO Balances to Team Multisig" is currently in active voting. If it passes: retroactive ratification of the treasury spend is complete — a partial governance positive, though the spend-first-vote-later precedent remains. If it fails: governance has rejected the team's handling of the Resolv settlement, which would be a significant escalation.
- **Monitor Q2 2026** — DEX V2 launch. Postponed per post-mortem pending market stabilization. New contract surface area = new risk. Check audit completion before using.
- **Monitor mid-2026** — Foundation formation. Now more urgent: the Resolv incident demonstrated the team will spend treasury funds without governance approval. Foundation must include treasury controls to be meaningful.
- **Watch for** — Publication of on-chain transaction details for the settlement. Transparency improvements would partially mitigate opacity concerns.
- **Watch for** — Repayment status of the $1.5M team IOU from protocol revenue. Continued non-disclosure = continued risk.
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
| Blockonomi — Fluid $21M Recovery Plan | https://blockonomi.com/fluid-covers-21m-bad-debt-after-resolv-exploit-outlines-recovery-plan/ |
| Halborn — Resolv Hack Explained | https://www.halborn.com/blog/post/explained-the-resolv-hack-march-2026 |
| Nexus Mutual — Resolv Incident Report | https://nexusmutual.io/blog/resolv-protocol-incident-report-by-nexus-mutual |
| CryptoNews — Fluid Oracle Failure Analysis | https://cryptonews.net/news/security/32852681/ |
| Governance Forum — Post-Mortem & Treasury Actions | https://gov.fluid.io (DMH, May 11, 2026) |
| Phemex — Fluid $70M Repayments | https://phemex.com/news/article/fluid-commences-70m-repayments-following-resolv-incident-68934 |
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

---

## Timeline

| Date | Event |
| --- | --- |
| Aug 2018 | Sowmay & Samyak Jain win ETHIndia hackathon with Instadapp concept |
| Oct 2019 | Seed round: $2.4M (Pantera, Coinbase Ventures, Naval Ravikant) |
| Jun 2021 | Series A: $10M (Standard Crypto lead, Andre Cronje) |
| Jun 2021 | INST token launch |
| 2021–2024 | Instadapp operates as DeFi management layer; grows to billions in TVL |
| 2024 | Fluid protocol launches (lending + vault) |
| Oct 2024 | Fluid DEX launches on Ethereum |
| 2024 | INST → FLUID token migration (1:1) |
| 2025 | Fluid DEX becomes #2 on Ethereum by volume ($156B annual) |
| 2025 | All FLUID token vesting completes — fully unlocked |
| Aug 2025 | Protocol revenue hits record $1.52M monthly |
| Feb 2026 | Foundation proposal submitted (Cayman Islands entity, $250K/month grant) |
| Feb 2026 | Venus Protocol partnership for BNB Chain deployment |
| Mar 2026 | Jupiter Lend integration on Solana ($1.6B via Jupiter) |
| Mar 22, 2026 02:21 UTC | Resolv exploit begins — attacker mints 50M USR via compromised AWS KMS key |
| Mar 22, 2026 02:25 UTC | Second mint — 30M additional USR (80M total unbacked) |
| Mar 22, 2026 02:38 UTC | USR hits $0.025 on Curve (97.5% depeg) |
| Mar 22, 2026 ~03:00 UTC | Fluid pauses affected markets (~30 min response time) |
| Mar 22–23, 2026 | $300M+ net outflows from Fluid in single day; ~$70M in USR debt repaid by borrowers |
| Mar 25, 2026 | Fluid announces "short-term loan coverage agreement" via X — emergency funds committed by Lomashuk, cyberfund, weremeow, core team |
| Apr 6, 2026 | Resolv deploys contract upgrade to burn 36.73M wstUSR/stUSR from hacker wallets (on-chain) |
| May 11, 2026 | Three-way settlement executed: Resolv $9.7M, Fluid treasury $8.2M, team $1.5M |
| May 11, 2026 | DMH publishes "Post-Mortem, Treasury Actions, and Forward Strategy" on governance forum — after settlement execution |
| May 12, 2026 | Fluid publicly confirms full $19.3M bad debt coverage |
| May 15, 2026 | Proposal 129 submitted on-chain: "Withdraw Treasury iETHv2 and fGHO Balances to Team Multisig" — retroactive ratification of treasury spend |
| May 16, 2026 | @jpn_memelord thread characterizes proposal as "confirm[ing] and omit[ting] several important things" |
| Q2 2026 (postponed) | DEX V2 launch — delayed per post-mortem pending market stabilization |
| ~6 weeks from May 11 (planned) | Solana DEX launch |
| Mid-2026 (planned) | Foundation IP transfer completion |
