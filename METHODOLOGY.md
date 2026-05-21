# Methodology

This document is the operating manual for the investigations published in [`research/`](./research/). It is written as a prompt: the AI agent ([Claude](https://claude.com/claude-code)) reads it, classifies the project, runs the phases, and produces a report in the required format.

The methodology is the showcase. The reports are the evidence that the methodology works.

---

## Epistemological Rules

1. **Guilty until proven innocent.** Every project is assumed adversarial until evidence proves otherwise.
2. **Official communications = marketing.** Whitepapers, blog posts, and team announcements are claims, not evidence.
3. **On-chain data is ground truth** — where verifiable. Privacy architectures (e.g., Canton) make claims unverifiable; treat accordingly.
4. **Absence of evidence ≠ evidence of absence.** No Rekt News entry is a mild positive, not proof of security.
5. **Distinguish between what is verified, what is claimed, and what is inferred.** Label each explicitly.

## Trust Hierarchy

| Rank | Source Type | Trust Level |
| --- | --- | --- |
| 1 | On-chain data (block explorer, DeFiLlama) | Highest — independently verifiable |
| 2 | Auditor reports (read the PDF, not the summary) | High — but check auditor tier and scope |
| 3 | Independent analysts (zachxbt, Rekt News, BlockSec) | High — no financial relationship with subject |
| 4 | Investigative journalism (The Defiant, DL News, CoinDesk) | Medium-High |
| 5 | Community discussion (Discord, Twitter, Reddit) | Medium — useful for leads, not conclusions |
| 6 | Project's own communications | Low — marketing until corroborated |

---

## Step 0: Project Classification

Before any phase, classify the project. Classification modifies investigation emphasis.

| Type | Primary Risk | Phase Emphasis |
| --- | --- | --- |
| Retail DeFi (yield farm, DEX fork, lending) | Rug pull / smart contract exploit | Phase 1 + Phase 3 first |
| Institutional / Permissioned Blockchain | Governance capture, unverifiable claims | Phase 1 (company history) + Phase 2 |
| Stablecoin | Peg mechanics failure | Phase 3 + Phase 4 |
| Derivatives / Perps | Liquidation cascades, funding rate sustainability | Phase 3 + Phase 4 |
| Bridge | Cross-chain attack surface, sequencer risk | Phase 3 priority |
| Yield Aggregator | Operational risk (off-chain automation) | Phase 3 + Operational check + Sub-asset cascade |
| Multi-Asset Vault (Morpho, Euler, Reservoir) | Compositional risk, unvetted collateral | Phase 3 (sub-asset cascade + NAV) + Phase 4 |

**When type = Institutional/Permissioned:** DeFiLlama will likely return null. Replace on-chain verification with regulatory filing review + press release cross-checking + company history investigation.

---

## Step 0.5: Quantitative Pre-Screen

Before committing to a full investigation, check these hard gates. Failure doesn't end the investigation — it elevates severity and changes emphasis.

| Criterion | Threshold | If Failed |
| --- | --- | --- |
| Market Capitalization | ≥ $100M (FDV or circulating) | AUTO HIGH flag — micro-cap = illiquidity + manipulation risk |
| Core Contract Age | ≥ 1 month on mainnet | AUTO HIGH flag — insufficient battle-testing |
| Independent Audits | ≥ 2 completed | AUTO HIGH flag — single audit = incomplete coverage |
| Unresolved Critical Vulns | 0 | AUTO CRITICAL flag — active threat to funds |
| TVL Stability | Current TVL not >25% below 90-day average | AUTO HIGH flag — capital flight signal |
| Collateralization | Fully collateralized; no historical defaults | AUTO CRITICAL flag if undercollateralized |

These thresholds are calibrated from institutional allocation standards. For retail DeFi investigations, apply them as severity anchors rather than exclusion gates — a protocol failing multiple thresholds warrants a stronger adversarial posture throughout.

---

## Phase 1: Team & Entity Assessment

### Individual-Level
- Verify founder identities via LinkedIn, Crunchbase, university records, prior employer verification
- Search for prior projects: successful exits, abandoned launches, regulatory actions
- Social graph: who does the team interact with? Associations with known bad actors?

### Company-Level
- Prior projects by the parent company (not just individuals): failed launches, abandoned integrations, regulatory actions against the entity
- Example: Digital Asset's ASX CHESS failure (~$250M, 7 years, scrapped 2022) was critical context for Canton Network
- Investor/VC background check: who funded it? Do any VCs also hold validator/governance roles (conflict of interest)?

### Search Strings
```
"[project name]" scam rug exit concern
"[founder name]" site:linkedin.com
"[founder name]" "[prior company]"
"[company name]" site:sec.gov OR site:cftc.gov
"[company name]" lawsuit OR "regulatory action" OR fraud
```

---

## Phase 2: Third-Party Intelligence

### Adversarial Sources (check every investigation)
- **@zachxbt** — on-chain fraud/scam investigator
- **rekt.news** — exploit and governance failure post-mortems
- **github.com/SunWeb3Sec/DeFiHackLabs** — known exploit pattern database
- **@peckshield, @blocksecteam** — security monitoring feeds (broke the YO incident before the team disclosed)
- **The Defiant, DL News** — investigative journalism
- **Ethresear.ch** — technical/academic critiques
- **CoinTelegraph, CoinDesk** — broader coverage (verify claims, don't trust headlines)

> Absence from Rekt News is a mild positive. Presence on Rekt News is evidence, not just context.

### Conflict of Interest Detection
Before citing any risk rating or analysis, check whether the rater has a financial relationship with the project. The YO Protocol investigation found that the founders' own risk platform (Exponential.fi) rated their own protocol — an undisclosed conflict of interest. Always ask: does the analyst hold tokens, operate validators, or have an investment relationship with the subject?

---

## Phase 3: On-Chain & Technical Findings

### Standard Checks
- TVL, volume, fees, revenue via DeFiLlama
- Contract source verification on block explorers (Etherscan, Arbiscan, Basescan)
- Proxy/upgrade patterns: who controls upgrades? Timelock duration?
- Multisig composition: how many signers? Are identities published?
- Token holder concentration: top-10 wallets — insiders or exchanges?

### Operational Risk Layer
For any protocol with off-chain components (yield aggregators, bridges, oracle-dependent systems, sequencers):

| Question | Why It Matters |
| --- | --- |
| Who controls the off-chain operator? | YO's $3.71M loss came from a centralized automated harvester, not a smart contract bug |
| Single key, multisig, or smart contract? | Determines single point of failure |
| What happens if the off-chain component fails? | Emergency exit / fallback mechanism (e.g., Lighter's Desert Mode) |
| Has any incident revealed operator competence failure? | The YO harvester bug (17.8M vs ~50 bps slippage) is the canonical example |
| Can the vault/strategy rebalance faster than a user can exit? | If composition changes outpace exit speed, users can be trapped in positions they didn't sign up for. Flag any asset where governance can change portfolio composition at-will and exit takes >1 week |

### Re-hypothecation & Self-Referential Backing
Check whether any portion of an asset's backing includes itself. If >5% of an asset's composition is self-referential (e.g., a stablecoin's reserves partially backed by its own token, or a vault whose collateral includes its own receipt tokens), flag as HIGH — this creates reflexive death spirals during depegs or bank runs. Also flag protocols where significant TVL originates from re-hypothecation loops (distinct from normal user-initiated lend/borrow loops).

### Sub-Asset Diligence Cascade
For any multi-asset strategy (Morpho vaults, Euler vaults, Reservoir strategies, yield aggregators with multiple underlying positions):

- **Every** underlying asset must independently pass diligence for the wrapper strategy to be considered sound
- If the strategy can add new assets without user consent, flag as HIGH — users may end up with exposure to unvetted collateral
- Check: does the protocol provide advance notice before adding new collateral? Best practice is multiple days notice; instant composition changes = worst case
- If a new asset enters an existing strategy after initial review, the strategy's risk assessment is stale until both the new asset and the updated strategy are re-evaluated

### NAV Calculation Method

| NAV Type | Trust Level | Requirements |
| --- | --- | --- |
| On-chain, real-time | Highest | Verifiable by anyone at any block |
| On-chain, periodic | High | Check update frequency and who triggers updates |
| Off-chain, multi-signer | Medium | Multiple independent signers must confirm NAV |
| Off-chain, single reporter | Low | Single point of failure for NAV accuracy |
| Off-chain with 3rd-party attestation | Medium-High | Independent fund admin or auditor attests |
| No NAV reporting | Flag as HIGH | Users cannot verify what they hold |

For any protocol reporting NAV off-chain, check: who calculates it? Who attests? Is there a professional fund admin involved? How frequently is it reported? Can it be independently verified against on-chain state?

### Security Assessment
- Read audit PDFs directly — not summaries, not claims about audits
- Check scope: does the audit cover the deployed version?
- Check remediation: were findings fixed?
- Check bug bounty existence and adequacy vs TVL

---

## Phase 4: Tokenomics & Comparative Analysis

### Tokenomics Adversarial Checklist
- What % of supply is insider-controlled (team + investors + foundation)?
- When is the first cliff unlock, and how large?
- Is the vesting schedule publicly documented with dates, or just described narratively?
- Does "no pre-mine" language mask equivalent distribution via emissions, validator rewards, or points programs? (Canton: Super Validator emissions = functional pre-mine)
- What is the FDV vs. market cap ratio? High ratio = large overhang from unlocks
- What are the top-10 wallet addresses? Can they be identified as insiders or exchanges?

### Narrative Riding Warning
Watch for third parties attaching to project names. Stock symbol pivots, rebrands timed to project launches, and influencer relationships initiated after a token announcement signal speculative capture rather than genuine adoption.

### Yield Source Verification
- Is the yield source identifiable and sustainable?
- What are the revenue mechanics vs. emission mechanics?
- Compare APY claims with actual fee revenue

---

## Timeline Construction

Before writing the report, construct a project timeline. List key dated events in order: founding, funding rounds, audits, launches, incidents, partnerships, token events.

Discrepancies between announced and actual dates, suspiciously clustered events, and long unexplained gaps are patterns visible only in chronological view.

---

## Audit Firm Quality Tiers

| Tier | Firms | Confidence |
| --- | --- | --- |
| **Tier 1** | Trail of Bits, Spearbit, ChainSecurity, zkSecurity, Sigma Prime, OpenZeppelin, Consensys Diligence | Highest |
| **Tier 2** | Cyfrin, SECBIT Labs, Nethermind, Quantstamp, Zokyo, Guardian Audits | High |
| **Tier 3** | Unknown/new firms — verify firm is real and has other credible clients | Verify |

**Red flag:** Audit PDF hosted only on project's own domain, not independently verifiable on the auditor's site.

---

## Red Flag Severity Definitions

| Severity | Definition |
| --- | --- |
| **CRITICAL** | Active or imminent threat to user funds: live exploit vector, admin key compromised, active rug mechanics confirmed |
| **HIGH** | Structural feature enabling fund loss if team acts maliciously or makes a serious error: insufficient timelock, small multisig with unknown signers, prior fraud, unverified insider wallet patterns |
| **MEDIUM** | Significant negative signal without direct fund risk path: prior failed project, weak audit by unknown firm, opaque tokenomics, delayed incident disclosure, no bug bounty |
| **LOW** | Minor concern or unverifiable claim: low community engagement, one negative press mention, small documentation gap |

## Confidence Level Definitions

| Level | Criteria |
| --- | --- |
| **High** | Key team claims independently verified via primary sources; on-chain data fully confirmed; ≥2 independent analyst opinions reviewed; audit reports read (not summarized) |
| **Medium** | Some primary source verification; on-chain data partially confirmed or DeFiLlama-only; 1 independent analyst opinion; audit existence confirmed but full report not read |
| **Low** | Mostly secondary sources; on-chain unverifiable (privacy chain, not on DeFiLlama); anonymous team with no primary verification; no independent analyst coverage found |

---

## Required Report Format

### 1. Executive Summary
- Verdict (1 sentence)
- Top 3 risks
- Top 3 positives
- Confidence level (High / Medium / Low — use definitions above)

### 2. Team Assessment
Three-column structure: Verified | Unverified | Assessment

### 3. Third-Party Consensus
- Audit posture (auditor tier, scope, findings, remediation status)
- Independent analyst coverage
- Community sentiment (with source quality caveats)

### 4. On-Chain Findings
- TVL, volume, fees, revenue (table format)
- Token distribution and vesting
- Contract architecture (proxy, multisig, timelock)
- Incident reconstruction (if applicable)

### 5. Red Flags Register
Mandatory table format:

```markdown
| # | Flag | Severity | Evidence | Source |
|---|------|----------|----------|--------|
| 1 | **[title]** — [1-sentence description] | CRITICAL/HIGH/MEDIUM/LOW | [evidence] | [URL] |
```

### 6. Unresolved Questions
Numbered list of key unknowns that could change the verdict if answered.

### 7. Monitor
Forward-looking watchpoints with specific triggers:

| Trigger | Threshold | Action |
| --- | --- | --- |
| TVL drawdown | >10% from report-date baseline | Re-evaluate — capital flight signal |
| Protocol exploit or hack | Any confirmed | Immediate re-assessment required |
| Smart contract upgrade | Any proxy upgrade | Review new code vs audit scope |
| Governance structure change | Multisig signer changes, timelock modifications | Re-assess admin risk posture |
| New collateral/asset added to strategy | Any addition to multi-asset vault | Sub-asset diligence cascade triggered |
| Token unlock event | Any cliff or major vesting event | Assess selling pressure and insider behavior |
| Audit scope gap | New contract deployed outside audit scope | Flag as unaudited attack surface |

### 8. Data Sources
Full list of sources consulted with URLs.
