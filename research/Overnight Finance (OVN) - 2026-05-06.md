# Overnight Finance ($OVN) — Adversarial Due Diligence Report

**Date:** 2026-05-06

**Update:** 2026-05-31 — added Zama cUSDC freeze, litigation/RFV recovery analysis, and post-freeze OVN market response

**Classification:** Yield Aggregator / Rebasing Stablecoin

**Confidence Level:** Medium

---

## 1. Executive Summary

**Verdict:** Overnight Finance has escalated from a governance-capture / successor-project dispute into an active asset-recovery fight: a U.S. federal court order caused Circle to freeze ~$12.6M of USDC inside Zama's cUSDC wrapper after plaintiffs alleged Overnight founder Maxim Ermilov moved treasury assets beyond OVN holders' reach.

### Top 3 Risks
1. **CRITICAL** — Team launched Reinforce.fi ($55.5M assets) using identical technology while announcing Overnight closure, with no governance vote or tokenholder compensation plan
2. **CRITICAL** — Plaintiffs allege >$15.77M was moved from treasury-linked wallets before an OVN holder liquidation vote finalized; ~$12.6M is now frozen by Circle in Zama cUSDC pending court review
3. **HIGH** — 77.5% insider token control enables unilateral governance decisions; treasury disposition remains disputed despite active litigation

### Top 3 Positives
1. The emergency freeze materially improves OVN holders' recovery optionality versus the pre-litigation baseline, though it does not prove entitlement to the funds
2. Smart contracts are audited (Hacken, Ackee) with no known exploits in USD+ rebase mechanism
3. USD+ maintained peg stability throughout operations — no user fund loss via depegging

### Confidence Level: Medium
Some primary source verification completed (GitHub, DeFiLlama, governance contracts, Etherscan transaction/address data). Independent reporting now confirms a live civil dispute and Circle freeze, but the actual complaint/TRO docket has not been independently retrieved from PACER. Treat litigation facts as **reported** unless directly tied to on-chain evidence below.

### 2026-05-31 Update: Thesis Change

The investment/recovery thesis changed after Circle froze Zama's cUSDC contract. Prior to the freeze, OVN was mainly a weak optional claim on FORCE/Reinforce conversion terms. After the freeze, OVN also trades as a **litigation recovery option** on the frozen treasury-linked assets.

This is not a clean treasury-distribution right. It is a contingent claim whose value depends on:
- Whether the court accepts plaintiffs' theory that the moved assets were Overnight treasury/community assets
- Whether OVN tokenholders have standing and an enforceable class claim
- Whether insiders/team/foundation balances are included, excluded, or subordinated in any recovery
- Whether Circle/Zama/court narrow the freeze to only the disputed depositor or leave the broader asset freeze intact

---

## 2. Team Assessment

| Verified | Unverified | Assessment |
|----------|------------|------------|
| Maxim Ermilov — CEO. LinkedIn confirms identity. GitHub contributor (ovnstable org). Listed as point of contact in Arbitrum LTIPP application. | Prior employment history details | Primary decision-maker for sunset |
| Yaro Pavlov — Co-Founder. Named in Tracxn profile. GitHub contributor. | Exact role in Reinforce.fi | Co-architect of migration strategy |
| Nikita Slezkin — CTO. GitHub contributor (NikitaSlezkin). Named in Tracxn. | Current involvement level | Technical lead for contract upgrades |
| Team downsized from 12+ to 4 employees (per Tracxn data) | Exact timeline of layoffs | Consistent with wind-down, not pivot |
| Team admitted selling 60-65K OVN tokens | Sale timing, price, total proceeds | Direct financial extraction during decline |
| Maxim Ermilov named as defendant in reported N.D. California class action filed May 28, 2026 | Full complaint and TRO docket not independently retrieved | Legal risk has moved from community dispute to active U.S. litigation |
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
- **zachxbt:** Coverage now reported around the Zama/cUSDC freeze; ZachXBT reportedly characterized Zama as an innocent third party and flagged the case as precedent-setting for pooled contract freezes
- **BlockSec / PeckShield:** No alerts found
- **Exponential.fi:** Listed Overnight — but Exponential.fi was co-founded by the same team (conflict of interest confirmed in prior research). Any rating from Exponential.fi regarding Overnight is compromised.
- **The Block / The Defiant:** Reported the May 2026 class action, Circle blacklist, Zama cUSDC freeze, and Patagon/RFV activist involvement

### Community Sentiment
- OVN tokenholders actively contesting treasury disposition on governance forums
- Discord/community reports of team announcing closure without vote
- No formal governance proposal found for protocol sunset
- Extreme holder concentration (106 holders on Arbitrum) means "community" is very small
- Post-freeze price action indicates a new recovery-trade bid, but volume remains thin and does not establish broad market validation

---

## 4. On-Chain Findings

### Protocol Metrics (DeFiLlama)

| Metric | Value | Assessment |
|--------|-------|------------|
| Current TVL (2026-05-06) | $10.2M | Down ~80% from peak >$50M |
| Current TVL (2026-05-31) | $23.59M | CoinGecko/DeFiLlama-linked value; interpret cautiously given protocol wind-down/litigation |
| Peak TVL | ~$50M+ | Achieved during DeFi yield farming boom |
| Chains | 9 (Arbitrum, Base, Optimism, Polygon, BSC, Blast, Linea, ZkSync, Ethereum) | Wide deployment but fragmented liquidity |
| Fees/Revenue | Not available via DeFiLlama | Data gap |
| Category | Yield / CDP | Rebasing stablecoin + governance token |

### Token Distribution

| Metric | Value |
|--------|-------|
| OVN Max Supply | 1,000,000 |
| Base Visible Supply | ~994,249.91 |
| Prior Effective Supply Estimate (2026-05-06 report) | ~407,843 |
| Prior Public Float Estimate | ~92,000 |
| Insider Control | ~77.5% (team + treasury + locked) |
| Holders (Arbitrum, original snapshot) | 106 |
| Holders (Base, 2026-05-22 snapshot) | ~20,970 |
| Price (2026-05-06) | ~$1.35 |
| Price (2026-05-31) | ~$1.32; +79.2% 24h; +45.9% 7d |
| 24h Volume (2026-05-31) | ~$22.9K |
| ATH Price | $116.97 (CoinGecko) |
| Decline from ATH (2026-05-31) | -98.9% |
| FDV at 1M max supply (2026-05-31) | ~$1.32M |

**Interpretation:** The post-freeze OVN move is real but thin. The market is repricing OVN from a weak FORCE-conversion option into a litigation/recovery option. Low volume means the price can move sharply without proving broad confidence.

### Base Holder Behavior Snapshot

Top-holder analysis performed before the Zama freeze showed a mostly static cap table rather than broad accumulation. As of the May 22 snapshot:

| Cohort | Current Holdings | % of Base Supply |
|--------|------------------|------------------|
| Top 10 Base holders | 661,720.5 OVN | 66.55% |
| Top 20 Base holders | 827,643.6 OVN | 83.24% |
| Top 50 Base holders | 942,415.0 OVN | 94.79% |
| Top 100 Base holders | 972,845.6 OVN | 97.85% |

Against May 6 balances, 21 of the current top 100 had materially increased, 8 had decreased, and 71 were effectively unchanged. Several large holders were contracts/pools, not necessarily human whales. This supports the view that pre-freeze buying was concentrated optionality-taking rather than broad outside demand.

### 2026-05-30 Zama cUSDC Freeze / Litigation Event

| Item | Detail |
|------|--------|
| Reported case | Newton AC/DC Fund LP et al. v. Maxim Ermilov et al., filed May 28, 2026 in U.S. District Court for the Northern District of California |
| Judge | P. Casey Pitts |
| Interim order | May 29, 2026 text-only order reportedly directed Circle to block USDC linked to the disputed transfer and set a June 1 hearing |
| Frozen contract | Zama cUSDC token/wrapper: `0xe978F22157048E5DB8E5d07971376e86671672B2` |
| Freeze execution | Circle blacklisted the cUSDC contract around May 30, 2026 01:08 UTC |
| Frozen amount | ~12,606,386 USDC |
| Disputed funding wallet | `0xf7Fcc767dE537953b3519D4b3097A24A6dFE1c84` |
| Wallet provenance | Etherscan shows the wallet was funded by `0xe497285e466227f4e8648209e34b465daa1f90a0` and interacted with Zama cUSDC on May 11 |
| Allegation | Plaintiffs allege Ermilov moved >$15.77M from treasury-linked wallets before an OVN holder liquidation vote finalized |
| Ermilov response | Reportedly disputes plaintiffs' theory, arguing the vote was invalid and the wallets included personal/team funds |

**Mechanism:** Circle can blacklist USDC-holding addresses. Because Zama cUSDC is a pooled confidential wrapper, the blacklist hit the wrapper contract address, freezing all USDC backing the contract rather than only the alleged depositor's beneficial share. Zama is not reported to be a defendant; Zama CEO Rand Hindi described the protocol as caught in another case's crossfire and said the deposit made up >99% of the wrapper's balance.

**Legal significance:** The freeze preserves recovery optionality for OVN plaintiffs but does not establish that OVN holders own the funds. The June 1 hearing is the first critical checkpoint: if the freeze is narrowed/lifted, the recovery thesis weakens sharply; if maintained, plaintiffs gain leverage for discovery or settlement.

### RFV Claim Estimate Against Frozen Zama USDC

Assumption: only the frozen Zama cUSDC balance is recoverable, with a 25% legal/recovery cost haircut.

| Input | Value |
|-------|------:|
| Gross frozen cUSDC/USDC amount | $12,606,386 |
| Estimated legal/recovery cost (25%) | -$3,151,597 |
| Net recoverable amount | **$9,454,790** |

| Recovery denominator | Estimated RFV / OVN | Use Case |
|----------------------|--------------------:|----------|
| 1,000,000 OVN max supply | **$9.45** | Conservative: all tokens participate equally |
| 994,249.91 Base visible supply | **$9.51** | Base-supply approximation |
| 407,843 OVN prior estimated supply | **$23.18** | If only the previously estimated effective supply participates |
| 92,000 OVN prior estimated public float | **$102.77** | Aggressive: insiders/team/foundation excluded or subordinated |

**Do not underwrite the aggressive numbers unless legal documents show insider/foundation balances are excluded.** If the class includes all OVN, the conservative RFV is ~$9.45/OVN before taxes, settlement haircuts, time value, execution risk, and any additional claims beyond the frozen Zama amount.

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
| 2 | **Treasury Asset Freeze Confirms Live Recovery Fight** — Circle froze ~$12.6M in Zama cUSDC after plaintiffs alleged treasury assets were moved beyond OVN holders' reach | CRITICAL | May 29 court order reported; May 30 Circle blacklist; Zama cUSDC contract frozen | The Block, The Defiant, Etherscan |
| 3 | **Pooled-Contract Collateral Damage** — Freeze locked the whole Zama cUSDC wrapper, sweeping unrelated users into the OVN dispute | HIGH | cUSDC wrapper address blacklisted; frozen amount slightly exceeds disputed deposit | The Defiant, Zama/Rand Hindi statements via reporting |
| 4 | **Insider Token Dominance** — 77.5% of OVN supply controlled by insiders, enabling unilateral governance decisions including treasury disposition | HIGH | Token distribution analysis; 106 holders on Arbitrum | DeFiLlama, on-chain data |
| 5 | **nukeSupply Function** — Recent commit (Feb 2026) adds function to destroy USD+ supply, coinciding with sunset timeline | HIGH | PR #450 commit message "Added nukeSupply func to usd+ contract" | GitHub ovnstable/ovnstable-core |
| 6 | **Treasury Capture Risk** — $15M+ treasury (claimed) accumulated from protocol fees allegedly moved from treasury-linked wallets before liquidation vote finalized | HIGH | Reported complaint alleges >$15.77M transfer; treasury multisig address; no governance vote on disposition | The Block, governance docs, on-chain |
| 7 | **TVL Collapse** — 80%+ decline from peak ($50M+ → $10.2M as of May 6) with no organic recovery trajectory | HIGH | DeFiLlama historical data | DeFiLlama |
| 8 | **Team Token Sales** — Team admitted selling 60-65K OVN while controlling protocol direction and before announcing sunset | HIGH | Team admission in community communications | Community reports |
| 9 | **No Governance Vote on Closure** — Protocol being shut down without formal governance proposal despite having on-chain governance infrastructure | MEDIUM | OvnGovernor contract exists but no sunset proposal found | Governance contract, forum |
| 10 | **Outdated Audits** — Last audits (Hacken, Ackee) from 2022-2023; contracts upgraded since (V3, migration contracts) with no re-audit | MEDIUM | Audit dates vs. PR #450 deployment dates | GitHub, audit reports |
| 11 | **Extreme Holder Concentration** — Top 20 Base holders controlled ~83.24% of Base supply in May 2026 snapshot | MEDIUM | BaseScan holder data and archive `balanceOf` checks | BaseScan, Base RPC |
| 12 | **Hardcoded devAddress in Migration** — Single address can initiate migration without timelock in certain code paths | MEDIUM | UsdPlusTokenMigration.sol source code | GitHub |
| 13 | **Employee Downsizing** — Team reduced from 12+ to 4, consistent with extraction not pivot | MEDIUM | Tracxn employment data | Tracxn |
| 14 | **Exponential.fi Conflict** — Risk platform rating Overnight was connected to same team | MEDIUM | Team overlap between Overnight and Exponential.fi | Prior research, team pages |

---

## 6. Unresolved Questions

1. **What is the exact treasury balance?** $15M is claimed by tokenholders but could not be verified on-chain (Arbiscan blocked automated access). What assets comprise this treasury (USDC, veAERO, OVN, other)?

2. **Does `nukeSupply` exist in deployed bytecode?** The function is referenced in a commit message but not confirmed in reviewed source files. If deployed, what are its access controls?

3. **What is the legal relationship between Overnight Finance entity and Reinforce.fi?** Same team? Same company? New entity? This determines whether technology transfer was authorized.

4. **Were veAERO positions transferred to Reinforce?** Overnight's Aerodrome governance positions were accumulated with protocol treasury. Their current disposition is unknown.

5. **What exactly did plaintiffs plead in the May 28 N.D. California complaint?** The reporting states a class action and emergency freeze request, but the full docket/complaint has not been retrieved. Claims, class definition, causes of action, and requested relief are decisive.

6. **Will the June 1 hearing preserve, narrow, or lift the Circle freeze?** This is the near-term binary catalyst for OVN's recovery-trade value.

7. **Is any recovery distributed to all OVN holders, only non-insider holders, or plaintiffs/class members who held at a specific record date?** This determines whether RFV is ~$9.45/OVN or much higher for the public float.

8. **Can Zama isolate the disputed deposit without leaving unrelated cUSDC users frozen?** If the court or Circle narrows the freeze, unrelated-user collateral damage may be resolved while preserving the disputed amount.

9. **What assets remain outside the frozen cUSDC wrapper?** Etherscan currently shows the disputed wallet holding WBTC/cbBTC/ETH value outside the frozen cUSDC amount; whether those are part of the claim is unresolved.

10. **What are the 2/3 multisig signers' identities?** Are all three team members, or is there an independent signer?

11. **Has any governance proposal been submitted and rejected, or has governance simply been bypassed?**

12. **What is the timeline for Reinforce.fi's launch relative to Overnight's decline?** Did assets flow from one to the other?

---

## 7. Monitor

- **Monitor immediately** — Treasury multisig (`0x08d89e98ec5d7261d182130e25EB281A01E348fc`) for any outbound transfers. Large transfers to addresses connected to Reinforce.fi would confirm technology/asset migration.
- **Monitor 2026-06-01** — N.D. California TRO hearing in Newton AC/DC Fund LP et al. v. Maxim Ermilov et al. Outcome determines whether the cUSDC freeze remains a credible recovery path.
- **Monitor immediately** — Zama cUSDC contract (`0xe978F22157048E5DB8E5d07971376e86671672B2`) and Circle blacklist status. Unfreeze/narrowing would materially reduce recovery optionality unless disputed funds are separately restrained.
- **Monitor immediately** — Disputed wallet (`0xf7Fcc767dE537953b3519D4b3097A24A6dFE1c84`) for movement of WBTC/cbBTC/ETH or any non-USDC assets not trapped in Zama cUSDC.
- **Watch for** — Full complaint, TRO order, declarations, and any amended order. Critical variables: class definition, record date, claim basis, whether insiders are excluded, and whether plaintiffs posted/offer bond or funds to make unrelated Zama users whole.
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
| CoinGecko API | api.coingecko.com/api/v3/coins/overnight-finance | 2026-05-31 OVN price (~$1.32), 24h/7d change, 24h volume, TVL |
| The Block | theblock.co/post/403091/court-ordered-circle-freeze-traps-12-6-million-in-zama-cusdc-contract-amid-overnight-finance-suit | Reported class action, Circle freeze, plaintiffs, Patagon/RFV background, hearing date |
| The Defiant | thedefiant.io/news/defi/circle-freeze-on-zamas-confidential-usdc-locks-12-6m-of-user-funds-in-defi-crossfire | Pooled-wrapper freeze mechanics; Zama not defendant; ZachXBT/Rand Hindi statements |
| Etherscan | etherscan.io/address/0xf7fcc767de537953b3519d4b3097a24a6dfe1c84 | Disputed wallet activity, funding by `0xe497...90a0`, Zama cUSDC interactions, remaining WBTC/cbBTC/ETH |
| Etherscan | etherscan.io/address/0xe978F22157048E5DB8E5d07971376e86671672B2 | Zama cUSDC contract address |
| Etherscan | etherscan.io/tx/0x27a86c415e22625e8dce385c3cd6c53d4ce87484cdadc1a4fc7dc6552daae079 | Example May 11 Zama cUSDC wrap transaction from disputed wallet |
| Zama Docs | docs.zama.org/protocol/zama-protocol-litepaper | Confidential wrapper / FHE protocol architecture context |
| BaseScan / Base RPC | basescan.org, public Base RPC | Top holder concentration and May 2026 holder movement snapshot |

### Sources Attempted But Blocked
- Arbiscan (403 — treasury balance unverified)
- X/Twitter (402 — community posts unverified)
- Forcefi.io (ECONNREFUSED — not the correct successor)
- PACER / court docket direct retrieval not completed — litigation details rely on independent reporting plus on-chain corroboration

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
| 2026-05-06 | TVL at $10.2M; OVN at ~$1.35; tokenholder dispute ongoing |
| 2026-05-11 | Wallet `0xf7Fcc...1c84` reportedly receives/bridges treasury-linked assets and deposits bulk USDC into Zama cUSDC; Etherscan shows Zama cUSDC wrap interactions from this wallet |
| 2026-05-22 | Base holder snapshot: top 20 holders control ~83.24% of Base supply; current top 100 mostly maintained positions since May 6 |
| 2026-05-28 | Reported class action filed in N.D. California: Newton AC/DC Fund LP et al. v. Maxim Ermilov et al. |
| 2026-05-29 | Judge P. Casey Pitts reportedly issues interim order directing Circle to block disputed USDC and sets June 1 hearing |
| 2026-05-30 01:08 UTC | Circle blacklists Zama cUSDC contract (`0xe978...72B2`), freezing ~12.6M USDC |
| 2026-05-31 | OVN trades around $1.32 with +79.2% 24h move on ~$22.9K volume; litigation/RFV bid evident but thin |

---

## 10. Conclusion

This investigation reveals a pattern consistent with **governance capture, technology extraction, and now contested asset recovery**:

1. Team builds protocol with tokenholder capital
2. Treasury accumulates to ~$15M
3. Team sells personal token holdings
4. Team downsizes (extraction complete, maintenance mode)
5. Team launches successor (Reinforce.fi) using same technology
6. Team announces closure without governance vote
7. Treasury-linked assets allegedly move before an OVN holder liquidation vote finalizes
8. Activist/RFV plaintiffs obtain an emergency court order causing Circle to freeze ~$12.6M in Zama cUSDC

The presence of upgradeable contracts, hardcoded dev addresses in migration code, a "nukeSupply" commit, and 77.5% insider token control creates the technical capability for the team to unilaterally dispose of protocol assets. The Zama cUSDC freeze materially changes recovery odds because a large portion of disputed assets is now restrained, but it does **not** answer the legal question: whether those assets belong to OVN holders or to team/personal/foundation wallets.

**Updated recommendation for OVN holders:** Monitor the June 1 TRO hearing, Circle blacklist status, and any court filing defining the class/record date. The conservative RFV against the frozen Zama amount is ~$9.45/OVN after a 25% legal-cost haircut if all 1M tokens share equally. Higher RFV scenarios require insider/foundation balances to be excluded or subordinated; do not assume that without court documents.

---

*Report generated following DeFi Detector adversarial due diligence methodology. Original report date: 2026-05-06. Updated 2026-05-31 with litigation/freeze developments that may become outdated after the June 1, 2026 court hearing.*
