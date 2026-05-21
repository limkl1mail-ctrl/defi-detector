# Odyssey Finance — Adversarial Due Diligence
**Date:** 2026-04-30  
**Analyst:** Claude (Sonnet 4.6)  
**Classification:** Yield Aggregator — ERC-4337 DeFi Super-App  
**Confidence:** Medium

---

## 1. Executive Summary

**Verdict:** Odyssey Finance is a legitimate Bloq subsidiary product with a real founding team, credible DeFi history, and two completed security audits — but it carries material unresolved smart contract risks, a governance architecture that contradicts its own documentation, an undisclosed circular-ecosystem conflict of interest, and an imminent-token-airdrop dynamic that is inflating TVL metrics.

**Top 3 Risks:**
1. **Undisclosed ecosystem conflicts of interest** — Fee structure and XP program financially reward users for using Bloq's sister protocols (Vesper, Metronome), while Metronome publicly attributes its own TVL growth to Odyssey adoption. Three Bloq protocols are mutually inflating each other's metrics.
2. **Governance architecture contradicts documentation** — Docs claim "3/5 multisig governor," but the PositionRegistry ProxyAdmin is a single EOA with no timelock, no multisig, and no governor() function on-chain. The same key is the shared Bloq/Hemi ecosystem deployer; compromise of one key would affect Vesper, Metronome, Odyssey, and Hemi simultaneously.
3. **Audits do not cover current deployed code, and excluded financial attack vectors** — Both audits (July–Sep 2024) explicitly excluded "financial-related attack vectors" — the primary risk surface for a yield aggregator. The PositionRegistry has been upgraded 4 times since (most recently Jan 2026), leaving the current code unaudited in its present state.

**Top 3 Positives:**
1. Real parent company (Bloq, est. 2016, founded by Jeff Garzik and Matthew Roszak — named, verifiable, public figures)
2. CEO Zane Huffman has 4+ years of verifiable DeFi track record (Vesper Finance, Metronome Synth) — not anonymous
3. No entries on Rekt News, no zachxbt investigation, no community exploit reports found

**Confidence Level: Medium** — Parent entity (Bloq) is verified. Key on-chain governance claims cannot be independently confirmed to match documentation. Audit firm is mid-tier. Private GitHub repository prevents independent code verification.

---

## 2. Team Assessment

| Claimed | Verified | Assessment |
|---------|----------|------------|
| CEO: Zane Huffman, 10+ years DeFi | LinkedIn confirmed; Apollo/Bloq records confirm role at Vesper Finance and strategy lead for Metronome Synth | Credible — but creates the conflict of interest documented below |
| Parent entity: Bloq (blockchain infra company) | Bloq founded 2016; Jeff Garzik (co-founder, early Bitcoin core developer, Red Hat) and Matthew Roszak (Tally Capital founder, Chamber of Digital Commerce chairman) are public, verifiable | High confidence — Bloq is a known institutional actor in blockchain infrastructure |
| "4 years leading strategy for Vesper and Metronome" (Huffman) | Confirmed via Bloq blog, Medium posts, conference bio (ETHDenver) | Verified |
| Technical contact "Manoj Patidar" (Bloq, audit PoC) | Named in both Resonance Security audit reports as Bloq point of contact | Confirmed Bloq employee |
| Additional team | No other individuals identified in public materials | Unverified — team size and composition opaque |

**Key observation:** Zane Huffman built Metronome Synth as a Bloq employee and is now CEO of Odyssey, which integrates Metronome Synth as a yield strategy and specifically discounts fees for users of Metronome/Vesper. His business incentive to favor Bloq protocols in Odyssey's design is structural, not speculative.

---

## 3. Third-Party Consensus

### Audit Posture

**Audit 1 — Odyssey Protocol Reaudit**  
- Firm: Resonance Security (Tier 3 — credible, mid-market, not top-tier)  
- Date: July 3–17, 2024  
- Scope: `bloqpriv/odyssey-contracts` (private repo), hash `006aef73b219...`  
- Explicitly excluded: Financial-related attack vectors  
- Code/Test/Doc quality: 8/10 · 7/10 · 6/10  

| ID | Severity | Finding | Status |
|----|----------|---------|--------|
| RES-01 | HIGH | Missing Cross-Contract Call Return Validation → Incorrect Accounting (AjnaBorrowStrategy) | Resolved |
| RES-02 | HIGH | Creating Order Executions With Invalid Return Values (CallOrderExecutor) | **Acknowledged — not fixed** |
| RES-04 | MEDIUM | Missing Access Control For External Functions (Aave, Compound, Ajna, Synth, Vesper components) | **Acknowledged — team said "if users break the rules they deal with the loss"** |
| RES-05 | MEDIUM | Incorrect Approval Amount → Denial of Service (Ajna) | Resolved |
| RES-06 | MEDIUM | Integer Underflow on `_totalAllocated()` (AjnaBorrowStrategy) | Resolved |
| RES-07 | MEDIUM | Missing Validation of `amountOutMaxDeviation` | Resolved |
| RES-08 | LOW | Insufficient Validation of `amountIn` in `_fill()` | Resolved |
| RES-09 | LOW | Insufficient Validation in `quoteAllocatedInFee()` | **Acknowledged — team declared "wont-fix"** |
| RES-10 | INFO | Missing Zero Address Validations | Resolved |

**Audit 2 — SWA (SwapAggregator) Review**  
- Firm: Resonance Security  
- Date: September 16–30, 2024  
- Scope: SwapAggregator integration only  
- Explicitly excluded: Financial-related attack vectors  

| ID | Severity | Finding | Status |
|----|----------|---------|--------|
| SWA-01 | LOW | Missing Access Control on SwapAggregator (any user can call `swap()` directly, enabling proxy for malicious requests) | **Acknowledged — not fixed** |
| SWA-02 | INFO | Missing Zero Value Validation of `amountIn` | Resolved |
| SWA-03 | INFO | Missing Validation of `tokens_` Array Length | Resolved |

**Critical audit limitations:**
- Both audits are 19–22 months old (July–Sep 2024)
- PositionRegistry upgraded 4× since (most recently January 2026). Current deployed code has no audit coverage
- "Financial-related attack vectors" explicitly excluded from scope — for a yield aggregator, this is the primary risk surface
- Code is in a private repository (`bloqpriv/`) — independent verification is impossible

### Independent Analyst Coverage
- **Rekt News:** No entries found
- **zachxbt:** No investigation or mention found
- **BlockSec/PeckShield:** No incident alerts found
- **Messari:** Report exists ("Odyssey Finance: A Multichain DeFi Hub Built On ERC-4337") but access was blocked (403) — unable to assess content

### Community Sentiment
- No exploit reports, community warnings, or negative press identified
- XP/points farming community appears active — standard for pre-token protocols
- Source quality caveat: absence of negative coverage on a small protocol ($11M TVL) is weak evidence; most community discussion is farming-related

---

## 4. On-Chain Findings

### TVL, Volume, Fees, Revenue

| Metric | Value | Notes |
|--------|-------|-------|
| Total TVL | ~$11.25M | Ethereum $9.80M, Base $1.44M, Plasma $107K, Optimism $217 |
| All-Time Fees | $5.87K | Extremely thin relative to TVL |
| 30d Fees | $1.54K | Revenue is almost entirely performance-based |
| 7d Fees | $1.41K | |
| 24h Fees | $51 | |
| Funding Rounds | 0 | None recorded on DeFiLlama or Crunchbase |
| DeFiLlama Yield Pools | None found | — |

**Revenue reality check:** $5.87K all-time fees on $11.25M TVL implies <0.06% annualized revenue yield. At this rate, the protocol is a loss-leader. The inflated TVL relative to revenue is consistent with XP/airdrop farming behavior rather than organic yield-seeking capital.

### Token Distribution and Vesting
- **No token issued.** Universe SZN1 XP program is clearly an airdrop precursor, but no token is announced or documented
- "Redacted" future rewards in the XP program documentation — placeholder for future token utility
- XP earned by: looping positions ($1 per $50/day), holding esMET (Metronome), holding esVSP (Vesper), referrals
- **XP farming incentivizes Bloq ecosystem token accumulation** (esMET, esVSP) — users who hold Bloq governance tokens receive preferential airdrop positioning

### Contract Architecture

| Contract | Address (Mainnet) | Notes |
|---------|------------------|-------|
| PositionRegistry Proxy | `0xeE156D8ea7b96a5524CcC3CF9283ab85E80E9534` | TransparentUpgradeableProxy |
| PositionRegistry Implementation | `0x3416311BBAeD3cf69c494C2BAdF5ceB4b201E4F9` | Single-owner, no governor(), no timelock |
| ProxyAdmin | `0x3F6da0A118B3A0ddfdbaB4690cC96b2cF73B488D` | Owned by single EOA (see below) |
| SwapAggregator | `0xc67Abc3FBa59860B2Dbf77FD1Cf59d5455D6Ed14` | Access control finding unresolved |

**ProxyAdmin owner:** `0xf5f5195cf6998c57c651f9f0bbfa7cfc72a6fac1` — labeled "Hemi: Deployer 1" on Etherscan  
- Standard EOA (not a multisig)  
- 623 transactions over 4 years  
- Deployed VUSDArbitrage (Vesper's VUSD = Bloq project), LayerZero bridge contracts, and ERC-20 contracts across 8+ networks  
- Jeff Garzik founded both **Bloq** (Odyssey's parent) and **Hemi Labs** (Hemi Network)  
- **This is Bloq's shared ecosystem deployer.** A single private key controls upgrade authority over Odyssey, Vesper, Metronome, and Hemi infrastructure simultaneously

**Upgrade history (PositionRegistry):**
- Jan 29, 2025 — Initial deployment  
- Sep 12, 2025 — Upgrade #2  
- Oct 10, 2025 — Upgrade #3  
- Jan 7, 2026 — Upgrade #4 (most recent, 113 days ago)

All 4 upgrades executed with no timelock and no multisig approval requirement.

### Incident History
No exploits or incidents found in DeFiLlama hacks database or independent reporting.

---

## 5. Red Flags Register

| # | Flag | Severity | Evidence | Source |
|---|------|----------|----------|--------|
| 1 | **Circular ecosystem conflict of interest** — Fee structure (10%→2% discount) and XP program (esMET/esVSP holdings earn XP) financially reward users for using Bloq sister protocols Vesper and Metronome. Metronome publicly credits its TVL growth to Odyssey adoption. CEO built both Vesper and Metronome. No disclosure of these relationships to users. | HIGH | Fee table (docs.odyssey.finance/architecture/protocol-revenue); XP rules (universe-szn1); Metronome August 2025 Performance Report (paragraph.com/@metronomedao) | DeFiLlama, Odyssey docs, Bloq blog |
| 2 | **Governance claim contradicts on-chain reality** — Docs state "3/5 multisig wallet" controls the governor. On-chain: PositionRegistry implementation has no governor() function, no timelock, single owner with immediate transferability. ProxyAdmin (upgrade authority) is a single EOA, not a multisig. | HIGH | PositionRegistry: 0x3416311...; ProxyAdmin: 0x3F6da0A...; owner: 0xf5f5195... | Etherscan, Odyssey docs |
| 3 | **Single EOA controls upgrade authority across entire Bloq ecosystem** — The "Hemi: Deployer 1" EOA is Bloq's shared deployer across Odyssey, Vesper, Metronome, and Hemi infrastructure. One key compromise = cross-protocol catastrophic failure affecting all Bloq DeFi products simultaneously. | HIGH | ProxyAdmin owner 0xf5f5195 has 623 txns across 8+ chains, deployed VUSDArbitrage (Vesper) and Hemi contracts | Etherscan |
| 4 | **Current code is unaudited** — Audits dated July–Sep 2024. PositionRegistry upgraded 4 times since, most recently January 7, 2026 (113 days ago). Financial-related attack vectors were explicitly excluded from both audit scopes. | HIGH | Both Resonance audit PDFs (docs.odyssey.finance/resources/audits); Etherscan upgrade history | Resonance Security, Etherscan |
| 5 | **Two HIGH audit findings left unresolved** — RES-02 (Creating Order Executions With Invalid Return Values) acknowledged-not-fixed. RES-04 (Missing Access Control For External Functions across Aave/Compound/Ajna/Synth/Vesper components) acknowledged with dismissive response: "if users break the rules they deal with the loss." | MEDIUM | Audit_Report_Odyssey_REVIEW.pdf pages 12, 14 | Resonance Security (Oct 2024) |
| 6 | **No bug bounty program** — No Immunefi listing found for Odyssey Finance. With $11.25M TVL and a leveraged looping architecture (amplified liquidation risk), absence of a bounty is a meaningful gap. | MEDIUM | Immunefi.com search; docs don't reference a bug bounty | Immunefi |
| 7 | **Private codebase** — Both audits target `bloqpriv/odyssey-contracts` — a private GitHub repository. Independent security researchers cannot audit or verify the deployed code matches the audited hash. | MEDIUM | Both Resonance audit PDFs cite `bloqpriv/` private repo | Resonance Security audits |
| 8 | **Airdrop farming is inflating TVL** — XP program rewards are "Redacted" (strongly implying future token airdrop). The XP formula ($1 per $50 deposited/day via looping) incentivizes TVL inflation through leveraged positions. All-time fees of $5.87K on $11.25M TVL suggest the capital is farming-motivated, not yield-seeking. | MEDIUM | Universe SZN1 documentation; DeFiLlama fees ($5.87K all-time) | Odyssey docs, DeFiLlama |
| 9 | **SwapAggregator access control unresolved** — SWA-01 (LOW) left acknowledged-not-fixed: any external user can call `swap()` directly on the SwapAggregator, enabling use as a proxy for malicious swap requests. | LOW | Audit_Report-SWA_REVIEW.pdf page 11 | Resonance Security (Oct 2024) |
| 10 | **No funding rounds disclosed** — Odyssey presents as an independent DeFi product; no VC or investor funding visible on DeFiLlama or Crunchbase. Bloq itself was funded, but there are no disclosed investor relationships for Odyssey specifically. Fee revenue ($5.87K all-time) cannot sustain operations — the funding model is opaque. | LOW | DeFiLlama (0 funding rounds); Crunchbase | DeFiLlama |

---

## 6. Unresolved Questions

1. **Does the 3/5 multisig actually exist?** The docs claim it controls "the governor." On-chain, the PositionRegistry and its ProxyAdmin show no multisig. Is the multisig controlling a separate treasury or parameter contract not yet checked? If not, the docs are materially misrepresenting governance.

2. **What does "Redacted" in Universe SZN1 actually map to?** If this is a future Odyssey token airdrop, the timing (relative to unlock schedules, supply, and insider allocation) needs to be assessed before the token launches.

3. **Are the audited commits (hash `006aef73b2...` and `915e55c859...`) actually deployed?** The PositionRegistry has been upgraded 4 times since July 2024. Without access to the private `bloqpriv/` repo, there is no way to verify whether the Jan 2026 deployment matches any audited state.

4. **Who holds the "Hemi: Deployer 1" private key?** Is it under hardware wallet cold storage? A single custodian? A shared secret? The answer determines whether the single-EOA upgrade authority is catastrophic (hot wallet) or merely concerning (hardware wallet with process controls).

5. **What is Bloq's revenue model for Odyssey?** $5.87K all-time fees cannot pay a team. How is Odyssey funded — is it loss-led toward a token launch, or sustained by Bloq's enterprise business?

6. **Does the acknowledged RES-02 vulnerability (invalid return values in order execution) create exploitable paths in the current codebase?** The finding was acknowledged in July 2024 but the code has been upgraded 4 times. Has it been silently fixed, or is it still present in the Jan 2026 deployment?

---

## 7. Monitor

- **Watch for token announcement** — Any Odyssey token launch will trigger immediate need to assess supply, vesting, insider allocation, and whether XP converts to tokens. XP farming behavior will spike at launch.
- **Monitor January 2027** — If Metronome/Vesper have cliff unlock events, the circular ecosystem dynamics could unwind: insider selling in sister protocols could trigger TVL withdrawal from Odyssey.
- **Watch for governance architecture update** — If Bloq implements a genuine multisig for the ProxyAdmin (or deploys a timelock), this would substantially reduce the HIGH governance finding. No visible action taken in the 113 days since last upgrade.
- **Watch for next PositionRegistry upgrade** — Each upgrade to unaudited code with no timelock is a new risk event. At 4 upgrades/year cadence, monitor for upgrade transactions on `0xeE156D8...`
- **Monitor Metronome and Vesper TVL correlation** — If they move in lockstep with Odyssey TVL (both up and down), it confirms circular counting rather than independent growth.

---

## 8. Data Sources

| Source | URL | Used For |
|--------|-----|---------|
| Odyssey Docs | https://docs.odyssey.finance/ | Protocol mechanics, fee structure, risks, audits |
| DeFiLlama | https://defillama.com/protocol/odyssey-finance | TVL, fees, revenue, chains, funding |
| Resonance Security — SWA Audit | (GitBook PDF, docs.odyssey.finance/resources/audits) | Audit findings, firm identity, scope |
| Resonance Security — Protocol Reaudit | (GitBook PDF, docs.odyssey.finance/resources/audits) | Audit findings, firm identity, scope |
| Etherscan — PositionRegistry Proxy | https://etherscan.io/address/0xeE156D8ea7b96a5524CcC3CF9283ab85E80E9534 | Upgrade history |
| Etherscan — PositionRegistry Implementation | https://etherscan.io/address/0x3416311BBAeD3cf69c494C2BAdF5ceB4b201E4F9 | Owner, governor, timelock |
| Etherscan — ProxyAdmin | https://etherscan.io/address/0x3F6da0A118B3A0ddfdbaB4690cC96b2cF73B488D | Ownership, upgrade authority |
| Etherscan — Hemi: Deployer 1 | https://etherscan.io/address/0xf5f5195cf6998c57c651f9f0bbfa7cfc72a6fac1 | EOA identity, transaction history |
| Zane Huffman LinkedIn | https://www.linkedin.com/in/zanehuffman/ | CEO background |
| Bloq company | https://bloq.com/solutions/solutions-for-defi/ | Parent entity verification |
| Bloq — Metronome announcement | https://sync.bloq.com/bloq-defi-team-to-launch-powerful-synthetics-platform-metronome-synth/ | Metronome = Bloq project |
| Metronome Performance Analysis Aug 2025 | https://paragraph.com/@metronomedao/metronome-performance-analysis-august-2025 | Metronome TVL driven by Odyssey |
| RootData | https://www.rootdata.com/Projects/detail/Odyssey%20Finance | Team cross-reference (limited) |
| Immunefi | https://immunefi.com/bug-bounty/ | Bug bounty absence |
| Rekt News | https://rekt.news/ | No entries found |

---

## Appendix: Timeline

| Date | Event |
|------|-------|
| 2016 | Bloq founded by Jeff Garzik and Matthew Roszak |
| 2023 | Metronome Synth launched by Bloq DeFi team |
| Jul 3–17, 2024 | Resonance Security audit of Odyssey Protocol (private repo) — 2 HIGH findings, multiple unresolved |
| Sep 16–30, 2024 | Resonance Security audit of Swap Aggregator — 1 LOW finding acknowledged-not-fixed |
| Jan 29, 2025 | PositionRegistry Proxy deployed by Hemi: Deployer 1 EOA |
| Apr 2025 | Zane Huffman transitions to CEO role at Odyssey |
| Aug 2025 | Metronome reports TVL growth driven by Odyssey adoption |
| Sep 12, 2025 | PositionRegistry Upgrade #2 |
| Oct 10, 2025 | PositionRegistry Upgrade #3 |
| Jan 7, 2026 | PositionRegistry Upgrade #4 (most recent) |
| Apr 2026 | TVL: $11.25M; All-time fees: $5.87K; No bug bounty; No token announced |
