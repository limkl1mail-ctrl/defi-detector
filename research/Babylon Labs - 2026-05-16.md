# Babylon Labs — Adversarial Due Diligence Report

**Date:** 2026-05-16
**Classification:** Restaking / Bitcoin Security Layer — Native BTC staking protocol enabling Bitcoin to secure PoS chains
**Confidence Level:** Medium-High — Identified team with academic credentials verified; on-chain Bitcoin staking data confirmed via DeFiLlama ($4.05B TVL); multiple Tier 1-2 audits confirmed (Zellic, Coinspect, Sherlock, Oak Security, Halborn, Informal Systems); no ZachXBT or Rekt News entries; BLS vulnerability patch verified on GitHub (merged Nov 2025); covenant committee member identities not publicly disclosed.

---

## 1. Executive Summary

**Verdict:** Babylon is a technically sophisticated protocol with strong academic provenance and genuine innovation (EOTS-based trustless BTC slashing), but its token ($BABY) has collapsed 89% from ATH due to structural tokenomics issues — BTC stakers paid in BABY (not BTC) face dilutive rewards while 49% of supply is insider-controlled with linear vesting through 2029. The protocol itself (BTC staking layer) is sound; the investment thesis for the BABY token is separate and considerably weaker.

**Top 3 Risks:**
1. **Token-protocol value disconnect** — BTC stakers earn BABY tokens (not BTC), creating structural sell pressure. With ~1% APR in a depreciating token, effective BTC-denominated yield is deeply negative (-89% since launch).
2. **Insider supply overhang** — 49% allocation to team (15%) + investors (30.5%) + advisors (3.5%) with April 2026 cliff now passed. Monthly unlocks of ~227M BABY ($4.3M) continue through April 2029.
3. **Covenant committee opacity** — The 6-of-9 multisig controlling BTC unbonding co-signatures has no publicly identified members, despite custodying co-signature authority over $4B+ in staked BTC.

**Top 3 Positives:**
1. **Genuine cryptographic innovation** — EOTS (Extractable One-Time Signatures) enables trustless BTC slashing via Bitcoin Script without bridges, wrapping, or third-party custody. Published at IEEE S&P 2023 — a top-tier academic venue.
2. **Self-custodial design** — Stakers retain full custody of BTC via Bitcoin UTXO timelocks. No bridge, no wrapped token, no centralized custodian holds user funds.
3. **Strong audit posture and rapid vulnerability response** — 6+ audit engagements across Zellic, Coinspect, Sherlock, Oak Security, Halborn, Informal Systems. BLS vote-ext vulnerability (GHSA-2fcv-qww3-9v6h) patched in v4.1.0 within weeks of discovery. $3M Immunefi bug bounty active.

---

## 2. Team Assessment

| Verified | Unverified | Assessment |
| --- | --- | --- |
| **David Tse** — Co-founder. Stanford University professor of electrical engineering (tenured). Thomas Kailath and Guanghan Xu Professor. Research on blockchain consensus published at IEEE S&P 2023. Advisor to Bain Capital Crypto. | Extent of time split between Stanford and Babylon | **LOW RISK** — Elite academic credentials, publicly identified, long career |
| **Fisher Yu (Mingchao Yu)** — Co-founder & CTO. ANU and Northwestern Polytechnical University degrees. Previously Senior Staff Engineer at Dolby Laboratories (2018-2022). Invented decentralized multimedia delivery system sold to Dolby. | Prior blockchain projects before Babylon | **LOW RISK** — Verified engineering background, public identity |
| **Babylon Labs (formerly Babylonchain Inc., now Byzantine Research Inc.)** — Palo Alto, CA headquarters. | Corporate name change rationale (Babylonchain → Byzantine Research) | **LOW-MEDIUM** — Name change warrants monitoring but likely benign rebrand |
| **Babylon Foundation** — Cayman Islands registered entity. Manages token distribution and ecosystem. | Foundation governance structure, board members | **MEDIUM** — Standard offshore structure but no board transparency |

**Funding History (Verified):**
- **Pre-Seed/Seed (2022-2023):** $15M — a16z crypto (lead)
- **Series A (Dec 2023):** $18M — Polychain Capital (co-lead), Hack VC (co-lead), Framework Ventures, Polygon Ventures, OKX Ventures
- **Series B (May 2024):** $70M — Paradigm (lead), Bullish Capital, Polychain Capital, Hashkey Capital, Mantle, Galaxy Digital, Hack VC
- **Total raised:** ~$96M+ across multiple rounds

**Assessment:** Tier-1 investor backing (Paradigm, a16z, Polychain). Academic co-founder with verifiable credentials. No prior failed projects, no regulatory actions, no scam associations found. Corporate name change from "Babylonchain Inc." to "Byzantine Research Inc." visible on LinkedIn — likely related to separating the Labs entity from the protocol brand.

---

## 3. Third-Party Consensus

### Audit Posture

| Auditor | Scope | Tier | Notes |
| --- | --- | --- | --- |
| Zellic | Phase 1 staking contracts (Apr-May 2024) | Tier 1 | PDF published on docs site |
| Zellic | Genesis Chain (Mar 2025) | Tier 1 | **32 findings: 7 critical, 3 high, 7 medium** |
| Coinspect | Phase 2 chain upgrade (Mar 2025) | Tier 2 | PDF published |
| Sherlock | Genesis Chain Phase 1 | Tier 1 | Confirmed on audit page |
| Oak Security GmbH | Genesis V2 upgrade (Jun 2025) | Tier 2 | PDF published |
| Informal Systems | Genesis V2 upgrade | Tier 2 | Cosmos ecosystem specialists |
| Coinspect | V4 upgrade | Tier 2 | Latest upgrade |
| Halborn | V4 upgrade + Frontend staking app | Tier 2 | Both protocol and frontend covered |
| Cantina | Bitcoin staking scripts competition | Tier 1 | Competitive audit format |

**Critical Finding:** Zellic's March 2025 Genesis Chain audit found **7 critical-severity issues**. Remediation status of individual findings not independently verified (PDF not fully read). However, the chain launched successfully on April 10, 2025 and has operated without exploit since — suggesting critical findings were addressed.

### Independent Analyst Coverage
- **Nansen Research** — Published bullish thesis post-TGE (article now redirected/removed)
- **Messari** — "Understanding Babylon: A Comprehensive Overview" — comprehensive coverage
- **Xangle Research** — "Babylon Genesis, The Rise of the BTCFi Capital"
- **No ZachXBT investigations** found
- **No Rekt News entries** found
- **No exploit or hack recorded** on DeFiLlama hacks database

### Bug Bounty
- **$3M hard cap** on Immunefi (increased from initial $1M)
- **Bounty/TVL ratio:** 0.075% ($3M / $4.05B) — below the 0.1% adequacy threshold for protocols >$1B TVL
- **Payout structure:** 10% of funds at risk, capped at $500K per critical

### Community Sentiment
- Significant airdrop backlash (April 2025) — BTC stakers received ~0.6% ROI for 6-month staking period
- Token performance frustration (-89% from ATH)
- Protocol itself has high usage and demand (staking caps filled within blocks)

---

## 4. On-Chain Findings

### TVL & Protocol Metrics

| Metric | Value | Source |
| --- | --- | --- |
| Current TVL | $4.05B | DeFiLlama (May 2026) |
| BTC Staked | ~57,000 BTC | The Defiant (April 2025) |
| Chain | Bitcoin (native) | DeFiLlama |
| Protocol Revenue | Not tracked | DeFiLlama (400 error) |
| Fees Generated | Not tracked | DeFiLlama (400 error) |
| Ranking | #2 restaking protocol by TVL | Behind EigenLayer |

### Token Metrics (BABY)

| Metric | Value | Source |
| --- | --- | --- |
| Price | $0.0188 | CoinGecko (May 16, 2026) |
| Market Cap | $64.3M | CoinGecko |
| FDV | $203M | CoinGecko |
| Circulating Supply | 3.41B (32.6% of max) | CoinGecko |
| Total Supply | 10.78B (inflationary) | CoinGecko |
| ATH | $0.1661 (Apr 12, 2025) | CoinGecko |
| ATL | $0.01072 (Mar 7, 2026) | CoinGecko |
| Decline from ATH | -89% | Calculated |
| 24h Volume | $21.7M | CoinGecko |
| Inflation Rate | 5.5% annually | Babylon Docs |

### Token Distribution

| Category | Allocation | Vesting |
| --- | --- | --- |
| Early Private Investors | 30.5% (3.05B) | 4-year: 12.5% at year 1, then linear monthly |
| Ecosystem Building | 18% (1.8B) | 3 years: 25% at launch, rest linear |
| R&D + Operations | 18% (1.8B) | 3 years: 25% at launch, rest linear |
| Community Incentives | 15% (1.5B) | Immediate / distributed |
| Team | 15% (1.5B) | 4-year: 1-year cliff, then linear monthly |
| Advisors | 3.5% (350M) | 4-year: 12.5% at year 1, then linear monthly |

**Insider allocation:** 49% (team + investors + advisors)

### April 10, 2026 Cliff Event
- **612.5M tokens unlocked** (~6.1% of total supply) — first unlock for team/investors/advisors
- **37.77% increase** to circulating supply at that time
- Price impact: ATL of $0.01072 was hit on March 7, 2026 (anticipatory selling before cliff); price has stabilized at ~$0.019 post-cliff

### Yield Source Analysis
- BTC stakers earn BABY tokens (50% of 5.5% annual inflation = ~2.75% of total supply directed to BTC stakers)
- At current prices: ~1% APR on BTC denominated in BABY
- **Yield is purely inflationary** — no external fee revenue flows to BTC stakers
- BSNs are not yet live in production (Phase 3 pending late 2025/2026), so there is no real demand-side revenue from chains paying for Bitcoin security
- **Sustainability assessment:** Currently unsustainable without BSN adoption. If BSNs launch and pay meaningful fees, yield source shifts from dilutive to productive. This is the critical path for the protocol.

### Technical Architecture

**Self-Custodial BTC Staking:**
- Users lock BTC in a Bitcoin UTXO with spending conditions enforced by Bitcoin Script
- Timelock: 64,000 blocks (~15 months maximum staking period)
- Unbonding: 1,008 blocks (~7 days)
- No bridges, no wrapping, no third-party custody

**EOTS Slashing (Extractable One-Time Signatures):**
- Validators (Finality Providers) sign with Schnorr-based one-time keys
- Double-signing at same height mathematically exposes private key
- Anyone can then submit slashing transaction to burn 33.33% of staked BTC
- Enforcement via Bitcoin Script — trustless and self-executing

**Covenant Committee:**
- 6-of-9 multisig co-signs unbonding/slashing transactions
- Verifies slashing percentage (33.33%), slashing address, and unbonding period
- **Member identities: NOT publicly disclosed** — significant opacity for $4B custody authority
- Cannot collude against honest stakers (per docs claims) due to limited authority scope
- Committee changes require governance proposal

**Babylon Genesis Chain:**
- CometBFT-based L1 (Cosmos SDK)
- ~100 validators staking BABY for block production
- ~60 Finality Providers staking BTC for finality
- Dual-quorum security model

### Vulnerability History

| Date | Issue | Severity | Status |
| --- | --- | --- | --- |
| Nov 2025 | BLS vote extension nil pointer (GHSA-2fcv-qww3-9v6h) | Critical | **Fixed** — v4.1.0 (Nov 24, 2025) |
| Feb 2026 | CometBFT security fix (GHSA-h598-3g3g-c67c) | High | **Fixed** — v4.2.5 (Feb 4, 2026) |
| Mar 2025 | Zellic Genesis audit: 7 critical findings | Critical | Likely fixed pre-launch (Apr 10, 2025) |

**No exploits in production.** No user funds lost. Protocol survived $1.26B unstaking event (April 2025, Lombard transition) without incident.

### Staking History & Demand

| Event | Date | Details |
| --- | --- | --- |
| Cap-1 | Aug 2024 | 21,000 staking txs in 6 Bitcoin blocks from 12,720 stakers; >50 BTC in fees |
| Cap-2 | Oct 2024 | 10-block cap, filled quickly |
| Cap-3 | Dec 2024 | 1,000 BTC block cap; building to $2B+ TVL |
| Genesis Launch | Apr 10, 2025 | First BSN live; $4.6B TVL; BABY token launched |
| Lombard Unstake | Apr 17, 2025 | $1.26B (14,929 BTC) unstaked for FP transition; TVL dropped 32% temporarily |

---

## 5. Red Flags Register

| # | Flag | Severity | Evidence | Source |
|---|------|----------|----------|--------|
| 1 | **Covenant committee member identities undisclosed** — 6-of-9 multisig with co-signature authority over $4B+ BTC unbonding has no publicly named members | HIGH | Extensive search of docs, governance forums, and community posts found no named members. Only public keys in genesis file. | Babylon Docs, community research |
| 2 | **Token-protocol value mismatch** — BABY token has declined 89% while protocol TVL remains $4B+. BTC stakers paid in depreciating BABY token, not BTC. | HIGH | ATH $0.1661 → current $0.0188. Staking APR ~1% in BABY = deeply negative BTC-denominated returns. | CoinGecko, Babylon staking docs |
| 3 | **49% insider allocation with 4-year linear vesting** — Team (15%) + investors (30.5%) + advisors (3.5%) create sustained monthly sell pressure through April 2029 | HIGH | 612.5M tokens unlocked Apr 10, 2026 (cliff); ~227M BABY ($4.3M) monthly thereafter. Circulating supply doubled within first year. | Tokenomist, TradingView, Babylon docs |
| 4 | **No BSN revenue yet** — Yield for BTC stakers is 100% inflationary BABY emissions. No external chain is paying for Bitcoin security in production. Phase 3 (BSN multi-staking) still pending. | MEDIUM | Osmosis, XPLA, BOB announced as BSN partners but not live. All current BTC staker yield comes from token inflation. | Babylon roadmap, BSN announcements |
| 5 | **Bug bounty/TVL ratio below adequacy threshold** — $3M cap on $4.05B TVL = 0.074%. Industry standard for responsible disclosure incentives is ≥0.1% for protocols >$1B. | MEDIUM | Immunefi program page shows $3M hard cap. Calculation: $3M/$4.05B = 0.074%. | Immunefi |
| 6 | **7 critical findings in Zellic Genesis audit** — Pre-launch audit found 7 critical-severity issues. Individual remediation status not independently verified from PDF. | MEDIUM | Zellic audit report (March 2025) on Babylon docs. Chain launched Apr 2025 without exploit. | docs.babylonlabs.io/assets/files/zellic_babylon_genesis_chain_audit_2025_03.pdf |
| 7 | **Corporate name change without public announcement** — Babylonchain Inc. → Byzantine Research Inc. visible on LinkedIn/Tracxn. No blog post or community announcement explaining the change. | LOW | David Tse's LinkedIn shows "Byzantine Research Inc. (formerly Babylonchain Inc.)" | LinkedIn |
| 8 | **David Tse dual role: Stanford professor + Bain Capital Crypto advisor** — Academic credibility leveraged alongside VC advisory role. Not a direct conflict but noteworthy overlap. | LOW | Self-disclosed on personal website and LinkedIn | davidtse.io, LinkedIn |

---

## 6. Unresolved Questions

1. **Who are the 9 covenant committee members?** — For a $4B+ BTC custody mechanism, the identities of co-signers should be public. Are they institutional partners? Foundation members? Can they be socially pressured or legally compelled to deny unbonding?

2. **What is the BSN revenue model at scale?** — When Osmosis/XPLA/BOB go live as BSNs, how much will they pay for Bitcoin security? Is there a committed minimum fee, or is it market-driven? The entire sustainability thesis depends on this.

3. **Why did Babylon not publicly comment on the BLS vulnerability disclosure?** — The fix was already deployed (v4.1.0, Nov 2025) before the January 2026 media coverage, but no public acknowledgment was issued. Silent patching is preferable to no patching, but transparency would build confidence.

4. **What is the actual BTC-denominated yield path?** — If BABY continues to depreciate, BTC stakers face negative real returns indefinitely. Is there a governance path to distributing BSN fees in BTC rather than BABY?

5. **What triggered the Babylonchain → Byzantine Research rebrand?** — Timing (likely 2024-2025) and rationale unclear.

6. **Zellic 7 critical findings: what were they specifically?** — The full audit PDF should be read to assess whether these were theoretical or practically exploitable in production.

---

## 7. Monitor

| Trigger | Threshold | Action |
| --- | --- | --- |
| BSN Phase 3 launch | First external chain (Osmosis) goes live with Bitcoin finality | Re-evaluate yield sustainability. If fee revenue materializes, upgrade token outlook. |
| Monthly token unlock | ~227M BABY each month through Apr 2029 | Monitor for insider selling patterns vs. staking behavior. If insiders stake, bullish signal. |
| TVL drawdown | >20% from $4.05B baseline within 30 days | Re-evaluate — capital flight from BTC staking indicates loss of confidence in BABY rewards |
| Covenant committee disclosure | Any public identification of members | Reduce severity of flag #1 if members are reputable institutions |
| Bug bounty increase | Increase above $10M | Reduces flag #5 severity |
| BABY price below ATL ($0.01072) | New ATL | Assess whether BTC staking continues to make economic sense for participants |
| EVM mainnet launch | Babylon Genesis EVM compatibility (planned Q4 2025) | Expands DeFi composability — could increase BABY demand |
| Protocol exploit or hack | Any confirmed | Immediate re-assessment — EOTS slashing has never been battle-tested at scale |

**Key date:** June 10, 2026 — Next monthly unlock (~227M BABY for advisors, team, R&D, ecosystem, investors)

---

## 8. Data Sources

- DeFiLlama Protocol Page: https://defillama.com/protocol/babylon-protocol
- CoinGecko: https://www.coingecko.com/en/coins/babylon
- Tokenomist Vesting: https://tokenomist.ai/babylon
- CryptoRank Vesting: https://cryptorank.io/price/babylon-chain/vesting
- Babylon Docs — Tokenomics: https://docs.babylonlabs.io/guides/overview/babylon_genesis/baby_tokenomics/
- Babylon Docs — Audit Reports: https://docs.babylonlabs.io/guides/security/audit_reports/
- Babylon Foundation Blog — Tokenomics Guide: https://babylon.foundation/blogs/baby-tokenomics-guide
- Zellic Genesis Audit PDF: https://docs.babylonlabs.io/assets/files/zellic_babylon_genesis_chain_audit_2025_03.pdf
- Zellic Phase 1 Audit PDF: https://docs.babylonlabs.io/assets/files/zellic-phase1-audit.pdf
- Coinspect Phase 2 Audit PDF: https://docs.babylonlabs.io/assets/files/coinspect_babylon_phase_2_audit_2025_03.pdf
- GitHub Releases: https://github.com/babylonlabs-io/babylon/releases
- GitHub PR #1873 (vote-ext fix): https://github.com/babylonlabs-io/babylon/pull/1873
- Immunefi Bug Bounty: https://immunefi.com/bug-bounty/babylon-labs/
- CoinDesk — $70M Raise: https://www.coindesk.com/business/2024/05/30/bitcoin-staking-project-babylon-raises-70m-led-by-paradigm/
- The Defiant — Genesis Launch: https://thedefiant.io/news/defi/babylon-genesis-launches-bitcoin-staking-57k-btc-staked-4b-tvl-7-6m-baby-tokens-89b69af8
- BeInCrypto — Token Launch Controversy: https://beincrypto.com/babylon-baby-token-airdrop-launch-controversy/
- Cointelegraph — TVL Drop: https://cointelegraph.com/news/babylon-unstaking-1-billion-tvl-drops-30-percent
- CoinMarketCap — Unstaking Event: https://coinmarketcap.com/academy/article/babylon-labs-sees-dollar126-billion-in-bitcoin-unstaked-dropping-tvl-by-32percent
- Crypto-Economy — Vulnerability Acknowledgment: https://crypto-economy.com/babylon-acknowledges-vulnerability-in-block-signature-scheme/
- BTCC — Vulnerability Details: https://www.btcc.com/en-US/amp/square/Cryptonews/1398177
- David Tse personal site: https://www.davidtse.io/
- Fisher Yu personal site: https://www.fisheryu.io/
- Babylon Labs (Tracxn): https://tracxn.com/d/companies/babylon-labs/__SuoZpld3foROZb15hriwpp58sPjjOwM8h9kSHrT6ZsE
- TradingView — April 2026 Unlock: https://www.tradingview.com/news/coinmarketcal:9dbe1f439094b:0-babylon-baby-612-5mm-token-unlock-10-apr-2026/
- Figment — BTC Staking Contract: https://www.figment.io/insights/babylons-bitcoin-staking-contract-explained/
- Blockdaemon — Cap-3 Guide: https://www.blockdaemon.com/blog/institutional-guide-to-babylon-cap-3

---

## Timeline

| Date | Event |
| --- | --- |
| 2022 | Babylon (Babylonchain Inc.) founded by David Tse and Fisher Yu |
| 2023 | IEEE S&P paper published; $15M raised from a16z crypto |
| Dec 2023 | Series A: $18M (Polychain, Hack VC) |
| May 2024 | Series B: $70M (Paradigm lead) |
| Apr-May 2024 | Zellic Phase 1 audit |
| Aug 2024 | Phase 1 mainnet Cap-1: 21,000 txs, 12,720 stakers |
| Oct 2024 | Cap-2 launched and filled |
| Dec 2024 | Cap-3 launched; TVL passes $2B |
| Mar 2025 | Zellic & Coinspect Genesis Chain audits completed |
| Apr 10, 2025 | **Genesis mainnet launch; BABY TGE; airdrop (600M tokens)** |
| Apr 12, 2025 | BABY hits ATH: $0.1661 |
| Apr 17, 2025 | Lombard unstakes $1.26B (14,929 BTC); TVL drops 32% |
| Nov 24, 2025 | BLS vote-ext vulnerability patched (v4.1.0, PR #1873) |
| Dec 2025 | v4.2.0-v4.2.2 releases |
| Jan 9, 2026 | BLS vulnerability publicly disclosed by GrumpyLaurie55348 |
| Feb 4, 2026 | CometBFT security fix in v4.2.5 |
| Mar 7, 2026 | BABY hits ATL: $0.01072 (pre-cliff selling) |
| Apr 10, 2026 | **First cliff unlock: 612.5M tokens (team/investors/advisors)** |
| May 5, 2026 | v4.3.0 released |
| May 16, 2026 | Current: BABY at $0.0188; TVL $4.05B |

---

## Comparative Analysis

| Protocol | TVL | Token Price vs ATH | Insider % | Bug Bounty/TVL |
| --- | --- | --- | --- | --- |
| **Babylon** | $4.05B | -89% | 49% | 0.074% |
| EigenLayer | ~$11B | -75% | ~55% | 0.05% |
| ether.fi | $5.77B | -60% | ~40% | 0.003% |

Babylon's token decline is severe but not unprecedented for restaking protocols post-TGE. The pattern — high TVL sustained by staking mechanics while the token trades down — is consistent with EigenLayer's EIGEN trajectory. The distinguishing factor for Babylon is whether BSN revenue materializes to provide non-inflationary yield.

---

## Conclusion

**Protocol assessment: MEDIUM-LOW risk.** Babylon's BTC staking design is genuinely innovative, self-custodial, and has not been exploited despite holding $4B+ in BTC. The academic team, Tier-1 investors, multiple audits, and novel EOTS cryptography represent real engineering quality. The protocol survived a $1.26B unstake without panic.

**Token assessment: HIGH risk.** BABY's 89% decline from ATH reflects structural problems: yield paid in BABY creates sell pressure, 49% insider allocation with monthly unlocks through 2029, no BSN fee revenue yet, and a ~$200M FDV on a protocol securing $4B+ BTC (market doesn't value governance token highly relative to TVL).

**Key discriminator:** BSN Phase 3. If external chains (Osmosis, XPLA, BOB) go live and pay meaningful fees for Bitcoin security, the yield source shifts from inflationary to productive. Until then, BTC stakers are earning a depreciating asset for locking BTC.
