# Overnight Finance ($OVN) — Adversarial Due Diligence Report

**Date:** 2026-05-06  
**Classification:** Yield Aggregator / Rebasing Stablecoin  
**Confidence Level:** Medium  

---

## 1. Executive Summary

**Verdict:** Overnight Finance presents a governance capture scenario where the founding team is sunsetting the protocol and migrating core technology (xUSD, delta-neutral strategies) to a successor project (Reinforce.fi) without disclosed compensation or governance vote for OVN tokenholders who funded the treasury.

### Top 3 Risks
1. **CRITICAL** — Team launched Reinforce.fi ($55.5M assets) using identical technology while announcing Overnight closure, with no governance vote or tokenholder compensation plan
2. **HIGH** — 77.5% insider token control enables unilateral governance decisions; treasury ($15M claimed) disposition unclear
3. **HIGH** — "nukeSupply" function referenced in recent commits suggests capability to destroy token supply programmatically

### Top 3 Positives
1. Smart contracts are audited (Hacken, Ackee) with no known exploits in USD+ rebase mechanism
2. USD+ maintained peg stability throughout operations — no user fund loss via depegging
3. Protocol operated transparently on-chain for 2+ years across 9 chains with verifiable yield distribution

### Confidence Level: Medium
Some primary source verification completed (GitHub, DeFiLlama, governance contracts). On-chain treasury balance unverified (Arbiscan blocked automated access). Team identities confirmed via multiple sources. No independent analyst coverage of the sunset/migration dispute found.

---

## 2. Team Assessment

| Verified | Unverified | Assessment |
|----------|------------|------------|
| Maxim Ermilov — CEO. LinkedIn confirms identity. GitHub contributor (ovnstable org). Listed as point of contact in Arbitrum LTIPP application. | Prior employment history details | Primary decision-maker for sunset |
| Yaro Pavlov — Co-Founder. Named in Tracxn profile. GitHub contributor. | Exact role in Reinforce.fi | Co-architect of migration strategy |
| Nikita Slezkin — CTO. GitHub contributor (NikitaSlezkin). Named in Tracxn. | Current involvement level | Technical lead for contract upgrades |
| Team downsized from 12+ to 4 employees (per Tracxn data) | Exact timeline of layoffs | Consistent with wind-down, not pivot |
| Team admitted selling 60-65K OVN tokens | Sale timing, price, total proceeds | Direct financial extraction during decline |
| Company registered (likely Eastern Europe based on team names/timezone patterns) | Exact jurisdiction, registration details | Jurisdictional enforcement unclear |

### Team Red Flags
- Same individuals appear connected to both Overnight and Reinforce
- xUSD (Overnight's cross-chain stablecoin product) appears as a core Reinforce offering
- No public disclosure of the relationship between Overnight team and Reinforce founding team
- Team sold governance tokens while still controlling protocol direction

---

## 3. Third-Party Consensus

### Audit Posture

| Auditor | Tier | Date | Scope | Status |
|---------|------|------|-------|--------|
| Hacken | Tier 3 | 2022-2023 | Core contracts | Likely outdated — contracts upgraded since |
| Ackee Blockchain | Tier 2-3 | 2023 | USD+ mechanism | Likely outdated — V3 deployed post-audit |

**Assessment:** Audits exist but are 2-3 years old. The UUPS proxy pattern means deployed bytecode has changed since audits were conducted. PR #450 ("Dev 747") introduced new contract versions (UsdPlusTokenV2.sol, V3, WithLock) in February 2026 — post-audit. No evidence of re-audit after these changes.

### Independent Analyst Coverage
- **Rekt News:** No entry found (mild positive for exploit risk; does not address governance capture)
- **zachxbt:** No coverage found
- **BlockSec / PeckShield:** No alerts found
- **Exponential.fi:** Listed Overnight — but Exponential.fi was co-founded by the same team (conflict of interest confirmed in prior research). Any rating from Exponential.fi regarding Overnight is compromised.

### Community Sentiment
- OVN tokenholders actively contesting treasury disposition on governance forums
- Discord/community reports of team announcing closure without vote
- No formal governance proposal found for protocol sunset
- Extreme holder concentration (106 holders on Arbitrum) means "community" is very small

---

## 4. On-Chain Findings

### Protocol Metrics (DeFiLlama)

| Metric | Value | Assessment |
|--------|-------|------------|
| Current TVL | $10.2M | Down ~80% from peak >$50M |
| Peak TVL | ~$50M+ | Achieved during DeFi yield farming boom |
| Chains | 9 (Arbitrum, Base, Optimism, Polygon, BSC, Blast, Linea, ZkSync, Ethereum) | Wide deployment but fragmented liquidity |
| Fees/Revenue | Not available via DeFiLlama | Data gap |
| Category | Yield / CDP | Rebasing stablecoin + governance token |

### Token Distribution

| Metric | Value |
|--------|-------|
| OVN Total Supply | ~407,843 |
| Circulating Supply | ~92,000 (estimated) |
| Insider Control | ~77.5% (team + treasury + locked) |
| Holders (Arbitrum) | 106 |
| Price (current) | ~$1.35 |
| ATH Price | ~$150 |
| Decline from ATH | -99.1% |
| FDV | ~$550K |

### Contract Architecture

**USD+ Token (UsdPlusTokenV3.sol)**
- UUPS upgradeable proxy pattern
- Key roles: DEFAULT_ADMIN_ROLE (can upgrade), PORTFOLIO_AGENT_ROLE (can pause), onlyExchanger (mint/burn), onlyPayoutManager (rebase)
- Fork of Origin Protocol's OUSD — rebasing mechanism distributes yield via creditsPerToken adjustment

**Governance Infrastructure**
- OvnTimelock: `0xA4fc2F25CA4dFEc08F07eE92d3173BA21A01E9f8`
- OvnGovernor: `0x279a30ed284D49D32De901acfC0004B2dB1c091E`
- Treasury Multisig (Arbitrum): `0x08d89e98ec5d7261d182130e25EB281A01E348fc` (2/3 signers)
- Per-chain AgentTimelocks with 6-hour delay
- Gnosis Safe multisig: 3/5 quorum

**Migration Contract (UsdPlusTokenMigration.sol)**
- Contains `blocked()` modifier (reverts with 'migration-pause')
- `migrationInit()` restricted to devAddress (`0x05129E3CE8C566dE564203B0fd85111bBD84C424`) or timelock (`0xD09ea5E276a84Fa73AE14Ae794524558d43F7fdC`)
- Hardcoded devAddress = single point of control for migration initiation

**Critical: PR #450 "nukeSupply"**
- Commit message explicitly references "Added nukeSupply func to usd+ contract"
- February 2026 — coincides with sunset announcement timeline
- Function not confirmed in reviewed source code (may be in unreviewed file or renamed)
- If deployed: would allow programmatic destruction of USD+ supply

### Reinforce.fi Connection

| Evidence | Source |
|----------|--------|
| xUSD product (Overnight's cross-chain stablecoin) listed on Reinforce.fi | reinforce.fi website |
| Same strategy types (delta-neutral, funding rate) | Product descriptions |
| Same primary chain (Arbitrum) | Deployment data |
| $55.5M in assets under management | reinforce.fi (self-reported) |
| Medium announcement confirming Overnight closure | overnight.fi Medium blog |
| Same team members connected | GitHub, LinkedIn cross-references |

### veAERO Holdings
- Overnight held veAERO tokens for voting on Aerodrome liquidity gauges
- These governance positions have value and were accumulated using protocol treasury
- Disposition of veAERO positions in sunset unclear

---

## 5. Red Flags Register

| # | Flag | Severity | Evidence | Source |
|---|------|----------|----------|--------|
| 1 | **Technology Migration Without Consent** — Team launched Reinforce.fi using Overnight's core xUSD technology and strategies while announcing Overnight closure, with no governance vote or tokenholder compensation | CRITICAL | xUSD on Reinforce.fi; Medium announcement of closure; no governance proposal found | reinforce.fi, Medium blog, governance contract |
| 2 | **Insider Token Dominance** — 77.5% of OVN supply controlled by insiders, enabling unilateral governance decisions including treasury disposition | HIGH | Token distribution analysis; 106 holders on Arbitrum | DeFiLlama, on-chain data |
| 3 | **nukeSupply Function** — Recent commit (Feb 2026) adds function to destroy USD+ supply, coinciding with sunset timeline | HIGH | PR #450 commit message "Added nukeSupply func to usd+ contract" | GitHub ovnstable/ovnstable-core |
| 4 | **Treasury Capture Risk** — $15M treasury (claimed) accumulated from protocol fees belongs to tokenholders but disposition controlled by 2/3 multisig team controls | HIGH | Treasury multisig address; 2/3 quorum with team signers; no governance vote on disposition | Governance docs, on-chain |
| 5 | **TVL Collapse** — 80%+ decline from peak ($50M+ → $10.2M) with no recovery trajectory | HIGH | DeFiLlama historical data | DeFiLlama |
| 6 | **Team Token Sales** — Team admitted selling 60-65K OVN while controlling protocol direction and before announcing sunset | HIGH | Team admission in community communications | Community reports |
| 7 | **No Governance Vote on Closure** — Protocol being shut down without formal governance proposal despite having on-chain governance infrastructure | MEDIUM | OvnGovernor contract exists but no sunset proposal found | Governance contract, forum |
| 8 | **Outdated Audits** — Last audits (Hacken, Ackee) from 2022-2023; contracts upgraded since (V3, migration contracts) with no re-audit | MEDIUM | Audit dates vs. PR #450 deployment dates | GitHub, audit reports |
| 9 | **Extreme Holder Concentration** — Only 106 OVN holders on primary chain (Arbitrum) | MEDIUM | On-chain holder count | Block explorer |
| 10 | **Hardcoded devAddress in Migration** — Single address can initiate migration without timelock in certain code paths | MEDIUM | UsdPlusTokenMigration.sol source code | GitHub |
| 11 | **Employee Downsizing** — Team reduced from 12+ to 4, consistent with extraction not pivot | MEDIUM | Tracxn employment data | Tracxn |
| 12 | **Exponential.fi Conflict** — Risk platform rating Overnight was connected to same team | MEDIUM | Team overlap between Overnight and Exponential.fi | Prior research, team pages |

---

## 6. Unresolved Questions

1. **What is the exact treasury balance?** $15M is claimed by tokenholders but could not be verified on-chain (Arbiscan blocked automated access). What assets comprise this treasury (USDC, veAERO, OVN, other)?

2. **Does `nukeSupply` exist in deployed bytecode?** The function is referenced in a commit message but not confirmed in reviewed source files. If deployed, what are its access controls?

3. **What is the legal relationship between Overnight Finance entity and Reinforce.fi?** Same team? Same company? New entity? This determines whether technology transfer was authorized.

4. **Were veAERO positions transferred to Reinforce?** Overnight's Aerodrome governance positions were accumulated with protocol treasury. Their current disposition is unknown.

5. **Is there a formal legal claim structure for OVN holders?** What jurisdiction governs the protocol? Do tokenholders have legal standing to contest treasury disposition?

6. **What are the 2/3 multisig signers' identities?** Are all three team members, or is there an independent signer?

7. **Has any governance proposal been submitted and rejected, or has governance simply been bypassed?**

8. **What is the timeline for Reinforce.fi's launch relative to Overnight's decline?** Did assets flow from one to the other?

---

## 7. Monitor

- **Monitor immediately** — Treasury multisig (`0x08d89e98ec5d7261d182130e25EB281A01E348fc`) for any outbound transfers. Large transfers to addresses connected to Reinforce.fi would confirm technology/asset migration.
- **Monitor immediately** — USD+ proxy contract for upgrade transactions. Any upgrade deploying nukeSupply would be an emergency signal.
- **Watch for** — Governance proposal submission on OvnGovernor. Absence of any proposal while treasury is drained would confirm governance bypass.
- **Watch for** — Reinforce.fi TVL growth correlated with Overnight TVL decline. If Reinforce grows by approximately what Overnight loses, migration is confirmed.
- **Monitor** — veAERO token transfers from Overnight-controlled wallets to any Reinforce-associated address.
- **Watch for** — Legal filings by OVN holders in relevant jurisdictions. Community coordination for class action.
- **Watch for** — Team wallet activity (`0x05129E3CE8C566dE564203B0fd85111bBD84C424`) — migration initiation or large transfers.

---

## 8. Data Sources

| Source | URL/Reference | Data Obtained |
|--------|---------------|---------------|
| DeFiLlama | defillama.com/protocol/overnight | TVL ($10.2M), chains (9), category, raises |
| GitHub | github.com/ovnstable/ovnstable-core | Contract source, PR #450, migration contracts |
| Overnight Docs | docs.overnight.fi | Governance addresses, architecture, team |
| Reinforce.fi | reinforce.fi | Successor project confirmation, $55.5M assets |
| Overnight Medium | medium.com/@overnight.fi | Closure announcement |
| Tracxn | tracxn.com | Team size (4), founding info |
| Arbitrum LTIPP | forum.arbitrum.foundation | Team confirmation (Maxim Ermilov as contact) |
| Hacken Audit | Referenced in docs | Audit existence (PDF not independently verified) |
| Ackee Audit | Referenced in docs | Audit existence (PDF not independently verified) |
| CoinGecko | coingecko.com | OVN price data, ATH, market cap |

### Sources Attempted But Blocked
- Arbiscan (403 — treasury balance unverified)
- X/Twitter (402 — community posts unverified)
- Forcefi.io (ECONNREFUSED — not the correct successor)

---

## 9. Timeline

| Date | Event |
|------|-------|
| 2022 | Overnight Finance launches USD+ rebasing stablecoin |
| 2022-2023 | Hacken and Ackee audits completed |
| 2023 | Multi-chain expansion (9 chains); TVL peaks >$50M |
| 2023 | OVN governance token launch |
| 2024 | TVL begins sustained decline |
| 2024 | Team begins selling OVN tokens (60-65K admitted) |
| 2024 | Team size reduces from 12+ to 4 (per Tracxn) |
| Feb 2026 | PR #450 "Dev 747" — "Added nukeSupply func to usd+ contract" |
| Early 2026 | Reinforce.fi launches with xUSD and identical strategy types |
| 2026 | Medium announcement: Overnight is closing |
| 2026-05-06 | TVL at $10.2M; OVN at $1.35 (99.1% below ATH); tokenholder dispute ongoing |

---

## 10. Conclusion

This investigation reveals a pattern consistent with **governance capture and technology extraction**:

1. Team builds protocol with tokenholder capital
2. Treasury accumulates to ~$15M
3. Team sells personal token holdings
4. Team downsizes (extraction complete, maintenance mode)
5. Team launches successor (Reinforce.fi) using same technology
6. Team announces closure without governance vote
7. Treasury disposition remains unclear

The presence of upgradeable contracts, hardcoded dev addresses in migration code, a "nukeSupply" commit, and 77.5% insider token control creates the technical capability for the team to unilaterally dispose of protocol assets. Whether this constitutes fraud depends on jurisdiction, the protocol's legal structure, and whether tokenholders have enforceable governance rights — questions that remain unresolved.

**Recommendation for OVN holders:** Monitor treasury multisig transactions immediately. Document the team's relationship to Reinforce.fi. Seek legal counsel regarding governance rights and potential claims. Consider whether a governance proposal forcing treasury distribution is technically possible given the 77.5% insider control.

---

*Report generated following DeFi Detector adversarial due diligence methodology. This report represents findings as of 2026-05-06 and may become outdated as events develop.*
