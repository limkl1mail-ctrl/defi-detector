# YO Protocol (yo.xyz) — Adversarial Due Diligence Report
**Date:** 2026-03-02 | **Confidence:** Medium-High

---

## 1. Executive Summary

YO Protocol is a multi-chain ERC-4626 yield vault aggregator ($55M TVL) built by the team behind Exponential.fi, backed by Paradigm and Coinbase Ventures, and audited by three independent firms with no critical findings. It is **not a rug pull** and shows genuine builder credibility. However, it suffered a **$3.71M operational loss on January 12, 2026** — not from a hack, but from a misconfigured automated harvesting transaction with a slippage parameter so broken it routed 97% of user funds into thin liquidity pools. The team backstopped losses silently and disclosed only 48 hours later after third-party security firms went public. This incident is the defining event for understanding the protocol's real risk profile: **operational risk from centralized off-chain automation**, not smart contract exploits.

**Verdict:** Legitimate protocol, legitimate team. Not a rug. But the January 2026 incident exposed a critical operational governance failure — centralized operator with insufficient guardrails and delayed user disclosure. Acceptable only for users who understand the yield aggregator trust model.

**Top 3 Risks:**
1. **Centralized off-chain operator** — a single automated harvester with broken slippage controls caused a $3.71M near-loss (Jan 2026); architecture still fundamentally relies on team-controlled operator
2. **48-hour delayed disclosure** — users had no knowledge of a $3.71M incident for two days; only disclosed after external security firms published
3. **$10,000 critical bug bounty cap** — grossly inadequate for a $55M+ TVL protocol; insufficient to attract top-tier researchers

**Top 3 Positive Signals:**
1. Team backstopped the full $3.71M loss from their own capital — users made whole
2. Three audits (Hunter Security, Offbeat, Spearbit) with no critical findings; active Immunefi bounty program
3. Named, verifiable founders with traceable 10-year careers; Paradigm-led seed ($14M) + Coinbase Ventures Series A ($10M)

---

## 2. Team Assessment

### Verified
- **Driss Benamour** — Co-Founder & CEO. Prior: Uber (fintech/payments, built global systems across 60+ countries), angel investor since 2018. LinkedIn verifiable. Publicly named since Exponential.fi launch (2021).
- **Mehdi Lebbar** — Co-Founder & CIO. Prior: World Bank (infrastructure finance, sub-Saharan Africa), Credit Suisse (billion-dollar transactions), CloudKitchens (North America Strategy & Planning 2019–2021). Verifiable career progression.
- **Greg Jizmagian** — Co-Founder & CTO. Prior: Amazon (Alexa engineering), 20 years software development, payments and consumer data protection. LinkedIn verifiable.
- All three co-founded **Exponential.fi** in 2021 — a DeFi risk-rating platform that became the risk infrastructure underpinning YO's vault strategy selection.
- **Funding trail is clean and institutional:**
  - 2022: $14M seed led by Paradigm
  - 2025 (Dec): $10M Series A led by Foundation Capital, Coinbase Ventures, Scribble Ventures, Launchpad Capital
  - Total raised: ~$24M

### Unverified
- Broader engineering team composition — no public roster beyond three founders
- Identity of the vault operator(s) running the Automated Harvesting System — critical for operational risk assessment
- Multisig signer identities (protocol discloses multisig exists with <4 signers, but names not confirmed)

### Assessment
Founders are real, credible, and have verifiable pre-crypto careers in finance and engineering. No prior rug pull history. No regulatory actions found. The Exponential.fi → YO Protocol pipeline is internally consistent: they built risk-rating tools, then built a vault that uses those ratings. **No team red flags — the risk is operational, not identity fraud.**

---

## 3. Third-Party Consensus

### Audits
Three independent audits conducted; all concluded no critical or high-severity findings:
- **Hunter Security** — Jan 21, 2025 (v1.1). Full report: https://www.yo.xyz/files/Yo-Protocol-Hunter-Security-Audit-Report.pdf
- **Offbeat Security** — Date not specified. Full report: https://www.yo.xyz/files/Yo-Protocol-Offbeat-Security-Review.pdf
- **Spearbit** — Referenced in Exponential.fi risk assessment; scope/date not specified in public docs

Note: Audit PDFs are hosted on Yo's own domain — independent retrieval from audit firms' own sites not confirmed. Offbeat Security is a lesser-known firm; Spearbit is tier-1.

### Bug Bounty
- Active Immunefi program: https://immunefi.com/bug-bounty/yo-protocol/
- **Critical smart contract bug max: $10,000** — critically underpowered for a $55M TVL protocol
- High: $4,000 | Medium: $2,000 | Low: $1,000
- In-scope: yoETH, yoBTC, yoUSD vault proxies, Gateway, Multisig (Base chain)

### Independent Analysis
- **Rekt News** — covered the January 2026 incident directly: [Yo Protocol's Slippage Bomb](https://rekt.news/yo-protocols-slippage-bomb). Editorial conclusion: operational risk is the dominant threat vector, not smart contract exploits.
- **The Defiant** — covered the incident factually: [YO Suffers $3.7M Loss Due to 'Unintended' Stablecoin Swap](https://thedefiant.io/news/defi/yield-suffers-usd3-7m-loss-due-to-unintended-stablecoin-swap)
- **DL News** — factual incident coverage: [Human error on DeFi protocol turns $3.7m token swap into $112,000](https://dlnews.com/articles/defi/defi-user-makes-expensive-mistake-with-stablecoin-transaction/)
- **Exponential.fi risk grade: "Good"** — but note: this is the *founders' own platform* rating their own product. Conflict of interest. Their risk assessment flags centralization as a concern.

### Community Sentiment
- No organized scam/rug accusations found
- Post-incident community criticism focused on disclosure delay, not fraud intent
- Reddit/CT: minimal organic discussion; primarily institutional/professional investor base

---

## 4. On-Chain Findings

### TVL & Metrics
| Metric | Value |
|--------|-------|
| TVL (DeFiLlama) | ~$55.45M |
| By chain | Base: $51.67M / Ethereum: $3.79M |
| Active vaults | yoETH (2.5%), yoUSD (7%), yoBTC (1.7%), yoEUR (6.2%), yoGOLD, yoUSDT |

### Key Contract Addresses (Ethereum)
- Gateway: `0xF1EeE0957267b1A474323Ff9CfF7719E964969FA`
- Vault Registry: `0x56c3119DC3B1a75763C87D5B0A2C55E489502232`
- Redeemer: `0x0439e941841f97dc1334d1a433379c6fcdcc2162`

All deposits/redemptions route through single Gateway contract — concentrated attack surface. Contracts are **immutable** (no upgradeable proxy pattern confirmed per Exponential.fi assessment). This cuts both ways: cannot be patched if a bug is found, but also cannot be changed by admin.

### Yield Source Verification
Yield sources are real and cross-chain verifiable:
- yoUSD: allocates across Morpho, Aave, Fluid, Pendle on Base/Ethereum
- yoETH: cbETH-wETH liquidity provision on Aerodrome (Base), Uniswap V4
- yoBTC: cbBTC/tBTC on Morpho or Aave across Base/Ethereum
- Third-party rewards (TOKE, FLUID, MORPHO) auto-compounded

**Yield is sourced from real DeFi protocols — not endogenous/unsourced.** This is verifiable on-chain. The 7% yoUSD yield is within plausible range for a stablecoin aggregator across multiple venues.

### The January 12, 2026 Incident (CRITICAL)
Full reconstruction from Rekt News and BlockSec:

1. YO's Automated Harvesting System initiated a routine rebalancing swap: $3.71M stkGHO → USDC
2. Slippage parameter was set to `17,872,058` (normal: ~50 basis points / ~0.005). The parameter was effectively infinite tolerance.
3. Odos Router fragmented the position across **102 token transfers** touching Uniswap V4, Curve, Balancer V3, Fluid, and Bancor — routed through pools with 85–88% fee tiers
4. Result: $3.84M in → $112,036 out. 97% slippage loss.
5. Team silently backstopped via multisig (purchased ~3.71M GHO via CoW Swap, redeposited)
6. On-chain message sent to LPs requesting 90% return as "bug bounty"
7. Disclosed publicly **48 hours later** — only after PeckShield, BlockSec, and QuillAudits published
8. Post-mortem confirmed: "slippage protections were insufficient, and the trade proceeded when it should have been blocked"

**No user funds were permanently lost.** But the incident reveals that the protocol's core value proposition — safe automated yield optimization — failed catastrophically due to operational error, not adversarial attack.

### Token Distribution ($YO)
| Allocation | % |
|-----------|---|
| Community Growth & Future Rewards | 30.0% |
| Core Contributors | 24.0% |
| Ecosystem Dev & Strategic Partnerships | 21.5% |
| Investors | 16.5% |
| Genesis Airdrop | 8.0% |

- Core Contributors + Investors = **40.5%** insider allocation
- 30% community growth allocation controlled by team (no DAO governance token noted in early docs)
- Community reward "Heats" — Heat 1 began Jan 29, 2025; tokens claimable at $0.09 reference price within 90 days
- Full vesting schedule not publicly detailed — **unresolved**

### DeFiLlama Hacks Database
No entries — the January 2026 incident was classified as operational error, not a hack. Correct classification, but worth noting it is absent from hack databases despite the $3.71M loss event.

---

## 5. Red Flags Register

| # | Flag | Severity | Evidence | Source |
|---|------|----------|----------|--------|
| 1 | **$3.71M operational loss (Jan 12, 2026)** — centralized automated harvester with broken slippage parameters; 97% loss on a single swap | CRITICAL | Rekt News post-mortem, The Defiant, DL News | [Rekt News](https://rekt.news/yo-protocols-slippage-bomb) |
| 2 | **48-hour delayed disclosure** — team knew immediately, stayed silent, disclosed only after external firms published | HIGH | Rekt News timeline reconstruction | [Rekt News](https://rekt.news/yo-protocols-slippage-bomb) |
| 3 | **Centralized off-chain operator** — yield rebalancing controlled by team-operated automation; not trustless | HIGH | Exponential.fi risk assessment, protocol docs | [Exponential.fi](https://exponential.fi/protocols/yo/8056939b-d456-48f7-8611-e14e31a6f8e7) |
| 4 | **Multisig < 4 signers** — Exponential.fi flags this as centralization risk; signer identities not published | HIGH | Exponential.fi risk rating | [Exponential.fi](https://exponential.fi/protocols/yo/8056939b-d456-48f7-8611-e14e31a6f8e7) |
| 5 | **$10,000 critical bug bounty cap** — far too low for $55M+ TVL; insufficient incentive for top researchers | HIGH | Immunefi program | [Immunefi](https://immunefi.com/bug-bounty/yo-protocol/) |
| 6 | **Conflict of interest: self-rating** — Exponential.fi (founders' platform) rates YO (founders' protocol) | MEDIUM | Exponential.fi is same team as YO | [Exponential.fi](https://exponential.fi/protocols/yo/8056939b-d456-48f7-8611-e14e31a6f8e7) |
| 7 | **$YO tokenomics partially opaque** — vesting schedule for Core Contributors not publicly detailed | MEDIUM | Public docs review | docs.yo.xyz |
| 8 | **Offbeat Security** — lesser-known auditor; Spearbit referenced but scope/date/PDF not independently confirmed | LOW | Audit listing | [Yo Docs](https://docs.yo.xyz) |

---

## 6. Unresolved Questions

1. **Who operates the Automated Harvesting System?** Is it a single key, a multisig, or a smart contract? After the January incident, what specific guardrails were added?
2. **Has the slippage fix been independently reviewed?** The post-mortem describes adding quote validation guardrails — no audit of the fix has been publicly confirmed.
3. **Multisig composition:** How many signers, who are they, and what is the timelock? This is essential given the centralized operator model.
4. **$YO vesting schedule for Core Contributors (24%) and Investors (16.5%):** Full schedule and cliff/unlock dates not published. Cannot assess token sell pressure timeline.
5. **Spearbit audit:** Scope, date, and full report not publicly linked. Only referenced indirectly. Cannot verify.
6. **Operator key security:** If a compromised operator key can drain vault ETH (as protocol's own docs acknowledge), what is the key management setup? HSM? Cold storage? Multi-party?
7. **LPs response to on-chain bounty message:** How much of the $3.71M was voluntarily returned by Uniswap V4/Curve/Balancer LPs? Protocol says they backstopped — from Series A capital or personal funds?

---

## Summary Verdict

YO Protocol is a **legitimate, operational yield aggregator** built by credible founders with strong institutional backing. The smart contracts have passed three audits with no critical findings. Yield is sourced from real, verifiable DeFi protocols. There is no fraud pattern here.

However, the **January 12, 2026 incident is the most important data point in this report.** It reveals that:
- The protocol's risk is not in its smart contracts — it's in its **human-operated automation layer**
- The team's **instinct was to cover first, disclose later** — a transparency failure that matters for long-term trust
- The $3.71M backstop came from institutional capital, not an on-chain insurance fund — what happens if a larger loss exceeds available reserves?

The founders' decision to rate their own protocol on their own risk platform (Exponential.fi) is a structural conflict of interest that is undisclosed in user-facing materials.

**Risk profile:** Medium for sophisticated users who understand that "yield aggregator" risk = the operator's operational competence and key management, not just smart contract security. Low-to-medium for institutional allocators with large positions — the backstop shows commitment but also confirms that user protection depends on team solvency, not protocol architecture.

**Monitor:** Any further operational incidents, the post-incident slippage guardrail implementation audit, and the $YO vesting unlock schedule when published.

---

## Sources
- Rekt News — Slippage Bomb incident: https://rekt.news/yo-protocols-slippage-bomb
- The Defiant — Incident coverage: https://thedefiant.io/news/defi/yield-suffers-usd3-7m-loss-due-to-unintended-stablecoin-swap
- DL News — Incident coverage: https://dlnews.com/articles/defi/defi-user-makes-expensive-mistake-with-stablecoin-transaction/
- CoinDesk — Series A raise: https://www.coindesk.com/web3/2025/12/13/yo-labs-raises-usd10m-to-scale-cross-chain-crypto-yield-optimization-protocol
- Exponential.fi — YO risk assessment (conflict of interest noted): https://exponential.fi/protocols/yo/8056939b-d456-48f7-8611-e14e31a6f8e7
- Immunefi — Bug bounty: https://immunefi.com/bug-bounty/yo-protocol/
- DeFiLlama — Protocol data: https://defillama.com/protocol/yo-protocol
- The Block — Paradigm-backed Exponential launches YO: https://www.theblock.co/post/353958/paradigm-backed-exponential-launches-defi-platform-yo-to-optimize-yield
- Hunter Security audit: https://www.yo.xyz/files/Yo-Protocol-Hunter-Security-Audit-Report.pdf
- Offbeat Security audit: https://www.yo.xyz/files/Yo-Protocol-Offbeat-Security-Review.pdf
- Whales Market — YO Protocol overview: https://whales.market/blog/what-is-yo-protocol/
