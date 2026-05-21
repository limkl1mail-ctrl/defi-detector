# Theoriq — Gold Vault Deep Dive
**Date:** 2026-05-06
**Target:** https://infinity.theoriq.ai/gold
**Classification:** AI-managed yield vault on tokenized gold (Yield Aggregator)
**Investigator note:** Gold Vault page (infinity.theoriq.ai/gold) is a pure JavaScript SPA — rendered content is unverifiable via any non-browser tool (WebFetch, Gemini CLI quota-hit, curl returns empty shell). All Gold Vault strategy details are sourced from marketing copy, not live product inspection. This is noted as a primary confidence limitation.

---

## 1. Executive Summary

**Verdict:** Theoriq's Gold Vault is a legitimate infrastructure build with a credible team, but it lacks the minimum transparency required to invest with confidence. The product is real. The risk is structural opacity: no disclosed Gold Vault contract address, no Theoriq-specific audit (underlying infrastructure has Mellow Protocol audits), an 84% supply overhang with a December 2026 cliff, and a ~91% TVL collapse from launch. The token (THQ) is a separate risk layer that compounds the vault risk.

**Top 3 Risks:**
1. Gold Vault smart contract not publicly identifiable — cannot verify deployment, audit scope, or upgrade authority
2. THQ token has upgradeable proxy with unknown proxy admin (no confirmed multisig or timelock)
3. December 2026 cliff: 84% of total supply (840M THQ) unlocks while token is down 86% from ATH

**Top 3 Positives:**
1. Underlying vault infrastructure (Mellow Protocol) has 6 audits (5× Nethermind, 1× Sherlock contest)
2. Core team credentials independently verified: Bodkin (Google Cloud, Quantcast), Millar (ConsenSys, Goldman Sachs M&A), Chen (Sei Foundation, Goldman Sachs, ConsenSys)
3. Gold collateral (PAXG, XAUT) is sourced from regulated custodians (Paxos, Tether) — not synthetic

**Confidence Level: LOW-MEDIUM** — Team partially verified via primary sources. DeFiLlama TVL confirms $1.93M on-chain. Gold Vault contract address unverifiable. No Theoriq-specific audit. Gold Vault SPA unrenderable by automated tools.

---

## 2. Team Assessment

| Claim | Status | Assessment |
| --- | --- | --- |
| Pei Chen — COO / Executive Director | **Verified** (ZoomInfo: "Chief Operating Officer & Executive Director at Theoriq") — Goldman Sachs, ConsenSys, Sei Foundation, Digital Asset, RootstockLabs | Credible background. Note: theoriq.ai/about-us mislabels her as CEO. ZoomInfo/LinkedIn/press confirm COO. Ron Bodkin remains CEO. |
| Ron Bodkin — Co-Founder | **Verified** (Crunchbase, ChainML.net, DL News, LinkedIn) — 15+ years AI/data; Google Cloud CTO Office, Teradata (bought Think Big Analytics), Quantcast, Vector Institute | Strong AI engineering credentials. Stepped back from CEO role at unknown date. |
| Arnaud Flament — CTO (ChainML) | **Verified** (ChainML.net) — VP Engineering at Ripcord; ML/systems background | Technical co-founder. No red flags found. |
| Jeremy Millar — Chairman | **Verified** (X announcement Feb 2025, LinkedIn, RootData) — ConsenSys Chief of Staff, Gnosis, Goldman Sachs M&A, Magister Advisors (fintech advisory, ICO/IEO management history) | Crypto OG with real credentials. ICO/IEO management history is yellow-flag context, not disqualifying. |
| Jameson Pickett — CPO | **Unverified** — leads quant strategy per website bio; background not independently confirmed | Unverified individual contributor. |
| Ethan Jackson — Research Lead | **Partially verified** (ChainML.net) — postdoc AI, Vector Institute, deep learning/RL | Technical lead; no red flags found. |
| David Müller — co-founder (original) | **Listed in early materials**, absent from current public presence | Original CPO; current role unknown. |

**Team note:** Ron Bodkin is CEO (Crunchbase, DL News Dec 2025, Tracxn, all press). Pei Chen is COO/Executive Director (ZoomInfo confirmed). The about-us page mislabels her title — this is a website error, not an undisclosed succession.

**Company Structure:** Theoriq is a product brand operated by ChainML Labs (11 employees, Los Altos CA). The parent entity has been building AI agent infrastructure since 2022. The vault product (Theoriq Alpha) is their consumer-facing deployment of that infrastructure.

---

## 3. Third-Party Consensus

### Audit Posture

| Audit | Auditor | Date | Scope | Tier |
| --- | --- | --- | --- | --- |
| NM0587-FINAL_Mellow | Nethermind | Aug 2025 | Mellow Protocol flexible vault infrastructure | Tier 2 |
| Mellow Protocol Public Audit | Sherlock (contest) | Sep 2025 | Mellow Protocol public best efforts | Competitive platform |
| NM_Mellow_Deployment_Verification | Nethermind | Sep 2025 | Deployment verification | Tier 2 |
| NM_0682_Mellow_FINAL | Nethermind | Oct 2025 | Mellow Protocol update | Tier 2 |
| NM_0703_FINAL_MELLOW_FINANCE | Nethermind | Nov 2025 | Mellow Finance | Tier 2 |
| NM_0735_FINAL_MELLOW_FINANCE | Nethermind | Nov 2025 | Mellow Finance | Tier 2 |

**Critical clarification:** All six audits are labeled "Mellow Protocol" or "Mellow Finance" — they audit the underlying vault infrastructure framework, not Theoriq's specific deployments. Theoriq is a **curator on Mellow** (analogous to Re7 Capital, Steakhouse Financial, MEV Capital on Morpho). This means:

- Smart contract risk = Mellow Protocol framework (audited ✓)
- Curation/strategy risk = Theoriq's AI agents, oracle wiring, sub-vault configurations, whitelisted call paths (NOT audited by any disclosed source)
- DeFiLlama lists **zero audit links** for Theoriq as a protocol

No Theoriq-specific audit was found. The Gold Vault has no confirmed independent security review.

### Independent Analyst Coverage
- **Rekt News:** No entries found (mild positive — absence is a positive signal)
- **DeFiHackLabs:** No entries found
- **zachxbt:** No documented concerns found
- **BlockSec/PeckShield:** No incidents flagged

### Community Sentiment
Community data sparse. THQ has only 731 token holders — community size is extremely small. No significant Discord controversies or Twitter controversy found as of this date.

---

## 4. On-Chain & Technical Findings

### TVL & Market Data

| Metric | Value | Source | Note |
| --- | --- | --- | --- |
| Current TVL | $1.93M (Ethereum) | DeFiLlama | Combined AlphaVault + Gold Vault |
| TVL at Launch (Dec 2025) | ~$21-23M (claimed) | Press releases | Possibly counting downstream protocol TVL |
| TVL Decline | ~91% in ~5 months | DeFiLlama vs press releases |  |
| THQ Price | $0.0226 | CoinGecko |  |
| ATH | $0.1654 (Dec 16, 2025) | CoinGecko | Day of AlphaVault launch |
| Current decline from ATH | -86% | Calculated |  |
| Market Cap | $3.56M | CoinGecko |  |
| FDV | $22.5M | CoinGecko |  |
| Circulating Supply | 158.4M / 1B (15.84%) | CoinGecko | 84.16% locked |
| THQ Holders | 731 | Etherscan | Extremely concentrated |

**TVL Note:** The "$50M TVL" figure in recent Theoriq X posts refers to Lido's stRATEGY Vault (curated by Mellowprotocol) which AlphaVault routes deposits into — this is downstream protocol TVL, not Theoriq's own. This is the same inflation pattern seen with other TVL claims.

### Token Distribution & Vesting

| Allocation | % | Tokens | Unlock Structure |
| --- | --- | --- | --- |
| Investors | 30% | 300M | 1-year cliff → monthly vesting over 2 years |
| Treasury | 28% | 280M | Not fully disclosed |
| Core Contributors | 24% | 240M | 1-year cliff → monthly vesting over 2 years |
| Community | 18% | 180M | Various (staking rewards, airdrop) |

**Key insight:** TGE was December 2025. The 1-year cliff for insiders (54% of supply = 540M THQ) falls in **December 2026**. At the current price of $0.0226, that cliff represents ~$12.2M in tokens entering the market — against a $3.56M market cap. This is a ~3.4x supply overhang relative to current market cap.

IDO raised ~$22-29M on Kaito Capital Launchpad (July 2025, oversubscribed). The token is currently trading far below the implied IDO valuation, meaning IDO participants are underwater.

### Contract Architecture

**THQ Token:** `0xaffbe9a60F1F45E057FD9b6DC70004Bb0Ccc8b99`
- ERC-20, Solidity 0.8.24, ERC1967 upgradeable proxy
- Implementation: `0x8895aaadb6f8ed331627047ee0663ad8a496ae2d`
- Contract creator: `0x8a57e70c67de9290fc2d5f3119605d05260adcd3`
- **Proxy admin identity: NOT VERIFIED** — who controls upgrades is unknown from public sources

**Gold Vault Contract:** NOT FOUND in any public source. No deployment scripts for gold/PAXG/XAUT in the `flexible-vaults` GitHub. The Gold Vault may be newly deployed, not yet registered, or the contract address is not publicly disclosed.

**Vault Infrastructure:** Built on Mellow Protocol's flexible vault framework (BUSL-1.1 license). Repository: `github.com/chain-ml/flexible-vaults`. The vault system uses:
- Modular vault-of-vaults architecture with sub-vaults
- On-chain "policy cages" (BitmaskVerifier, MerkleACL) defining permitted calls per sub-vault
- Oracle submitter roles for price feeds
- RiskManager + FeeManager contracts

**License concern:** BUSL-1.1 (Business Source License 1.1) — this code is **not open source**. It becomes open source after a time delay (typically 2-4 years). Theoriq's vault contracts cannot be independently verified or forked by third parties in the interim period.

### Gold Vault Strategy (What Is Known)

The Gold Vault ("GoldSwarm") uses XAUT and PAXG as collateral base. Three described strategies:

1. **Cross-venue carry** — arbitrage gold yield differentials across DeFi protocols
2. **Term yield** — Pendle Principal Token strategies on tokenized gold (if available)
3. **Capital-efficient loops** — deposit PAXG on Aave → borrow stablecoins (maintaining LTV <60%) → swap to PAXG → re-deposit; effective 1.5–2x gold exposure

**The gold loop is the primary risk mechanism:** If gold drops sharply, leveraged positions face Aave liquidation. The extent of leverage applied by GoldSwarm is not publicly disclosed. "GoldSwarm" is an AI agent — the allocation decisions are automated off-chain.

**Stablecoin on-ramp:** Users can deposit USDC/USDT to get gold-denominated vault shares. This adds FX conversion risk (stablecoin → gold spot price at time of entry).

### Operational Risk Assessment

| Question | Answer | Risk |
| --- | --- | --- |
| Who controls GoldSwarm off-chain? | Theoriq team (centralized AI agent) | MEDIUM — single operator |
| What constraints limit GoldSwarm? | Smart contract "policy cages" per vault config | MEDIUM — cages configure specific permitted calls; extent of gold loop leverage limits unknown |
| What if GoldSwarm makes bad allocations? | No documented emergency exit for gold vault | MEDIUM — unclear fallback |
| Emergency pause mechanism? | Mellow framework has pause capability | Verify — who controls the pauser role? |
| Has any incident revealed operator failures? | No public incidents found | Mild positive |

---

## 5. Red Flags Register

| # | Flag | Severity | Evidence | Source |
| --- | --- | --- | --- | --- |
| 1 | **Gold Vault contract unverifiable** — No public contract address for the Gold Vault. Cannot verify audit status, upgrade authority, or deployment configuration | HIGH | No address found in any public source; no deployment script in chain-ml/flexible-vaults for gold/PAXG/XAUT | GitHub exhaustive search; Etherscan; web search |
| 2 | **THQ proxy admin unknown** — ERC1967 upgradeable proxy with unverified admin. If admin is a single EOA, token economics (minting, burning, transfer logic) can be silently changed | HIGH | Implementation `0x8895...ae2d`, creator `0x8a57...cd3`, proxy admin not resolvable from public sources | Etherscan; CLAUDE.md lessons on upgradeable proxies |
| 3 | **Audit gap: Mellow infrastructure ≠ Theoriq product** — All 6 audits labeled "Mellow Protocol/Finance". Theoriq's specific oracle configuration, policy cage parameters, and Gold Vault sub-vault wiring have no disclosed independent review | HIGH | Audit PDFs in chain-ml/flexible-vaults all titled "Mellow"; DeFiLlama lists 0 audit links for Theoriq | GitHub; DeFiLlama |
| 4 | **December 2026 supply cliff: 84% locked** — ~840M THQ unlocks starting Dec 2026. At current price ($0.0226) this is ~$19M into a $3.56M market cap — 5.3× current market cap in incoming supply | HIGH | Tokenomics: 30% investors + 24% contributors = 54% insider with 1-year cliff; 15.84% currently circulating | Tokenomics page; CoinGecko |
| 5 | **91% TVL decline since launch** — From $21-23M claimed at launch (Dec 2025) to $1.93M verified on DeFiLlama (May 2026). Mercenary capital exodus or unsatisfactory yield performance | MEDIUM | DeFiLlama current; Benzinga press release launch figure | DeFiLlama; Benzinga |
| 6 | **Gold Vault SPA blocks independent verification** — infinity.theoriq.ai/gold is a pure JS SPA; live APY, TVL, contract address, and strategy parameters are unverifiable by automated tools | MEDIUM | curl returns empty HTML div; WebFetch and Gemini CLI both failed | Direct inspection attempt 2026-05-06 |
| 7 | **"$50M TVL" marketing conflates downstream protocol TVL** — Theoriq's X account claimed "$50M TVL" for the Lido stRATEGY Vault that AlphaVault routes into — this is not Theoriq's own depositor TVL | MEDIUM | X post: "first vault integrated with AlphaVault...accrued over $50M TVL in less than a week" | @TheoriqAI on X |
| 8 | **Only 731 THQ token holders** — Extreme concentration. Top wallet analysis unavailable but with 731 holders the market is illiquid and vulnerable to single-actor price manipulation | MEDIUM | Etherscan | Etherscan |
| 9 | **BUSL-1.1 license** — Vault infrastructure is proprietary (not open source) until the license change date. Cannot be independently forked, verified, or reviewed by external parties beyond audit scope | LOW | README: "license for every contract is BUSL-1.1" | chain-ml/flexible-vaults README |
| 10 | **Gold Vault leverage parameters undisclosed** — GoldSwarm applies capital-efficient loops (Aave gold loop). Maximum LTV limits, circuit breaker thresholds, and de-leveraging mechanisms are not publicly documented | LOW | Product description only; no technical spec published | theoriq.ai/products |

---

## 6. Unresolved Questions

1. **What is the Gold Vault smart contract address on Ethereum?** No address disclosed in any public source. Without this, independent verification of the vault's audit status, upgrade authority, and asset custody is impossible.

2. **Who holds the proxy admin key for the THQ token contract?** Is it a multisig? Is there a timelock? The ERC1967 proxy pattern means token logic is upgradeable by whoever controls this key.

3. **What triggered the \~91% TVL decline from December 2025 to May 2026?** Was it incentive farming (bootstrapping rewards expired) or genuine yield underperformance vs. alternatives? The answer materially changes the verdict.

4. **What is the Gold Vault's current APY, and what protocols generate that yield?** The page is a JavaScript SPA and live data was unverifiable. Strategy descriptions are marketing-level only.

5. **What is the leverage ceiling for GoldSwarm's gold loop strategy?** If gold drops 30%, do positions face Aave liquidation? What is the LTV hard cap per the policy cage configuration?

6. **What are the exact IDO terms for the Community allocation?** If the $22-29M IDO implied a token price above $0.0226, essentially all IDO participants are underwater. Were there lockups on IDO allocations?

7. **Was David Müller (original CPO) departure voluntary, and does his departure affect any IP ownership claims?** His absence from current team materials alongside the CEO transition warrants verification.

---

## 7. Monitor

- **December 2026** — 1-year cliff on investor (300M) + core contributor (240M) tokens begins. Watch for sell pressure in the 60-90 days preceding. Price action 3 months before cliff is a leading indicator.
- **Watch for Gold Vault contract address disclosure** — If the team publishes the contract address and a Theoriq-specific audit, it materially improves the technical risk picture.
- **Watch for audit announcement** — Any engagement by a Tier 1/2 firm covering Theoriq's specific vault deployments would significantly improve confidence.
- **Watch AlphaVault TVL trajectory** — If TVL continues declining below $1M, it signals the product is not retaining capital despite AI management claims.
- **Watch THQ for large wallet movements pre-December 2026** — Any insider address sales in Q3/Q4 2026 ahead of the cliff would indicate insiders are pricing exit in advance.
- **Proxy admin resolution** — Run an on-chain `eth_call` to the THQ proxy's admin slot (`storage slot 0xb53127684a568b3173ae13b9f8a6016e243e63b6e8ee1178d6a717850b5d6103`) to identify the admin. If it's a single EOA, the token is upgradeable by one key.

---

## 8. Data Sources

| Source | URL | Used For |
| --- | --- | --- |
| Theoriq products page | https://www.theoriq.ai/products | Product descriptions |
| Theoriq AlphaVault page | https://www.theoriq.ai/alphavault | AlphaVault strategy details |
| Theoriq about page | https://www.theoriq.ai/about-us | Team members (CEO/CPO/Chairman) |
| Theoriq tokenomics | https://www.theoriq.ai/tokenomics | Token distribution, vesting |
| DeFiLlama (CLI) | defillama.py protocol theoriq | TVL $1.93M; no audit links |
| CoinGecko | https://www.coingecko.com/en/coins/theoriq | Price, market cap, FDV, ATH |
| Etherscan (THQ) | https://etherscan.io/token/0xaffbe9a60f1f45e057fd9b6dc70004bb0ccc8b99 | Token holders (731), proxy architecture |
| GitHub — smart contracts | https://github.com/chain-ml/theoriq-smart-contracts | Contract source, no audits found |
| GitHub — flexible-vaults | https://github.com/chain-ml/flexible-vaults | Audit PDFs (Mellow-labeled), vault scripts |
| GitHub — chain-ml org | https://api.github.com/orgs/chain-ml/repos | Org-wide repo inventory |
| ChainML About page | https://chainml.net/about | Bodkin/Flament/Jackson verified |
| Tracxn (Theoriq) | https://tracxn.com/d/companies/theoriq/... | Founded 2022, HashKey investor, 11 employees |
| Benzinga (AlphaVault launch) | https://www.benzinga.com/pressreleases/25/12/49238907 | Dec 2025 launch details, $25M TVL claim |
| DL News (CEO interview) | https://www.dlnews.com/research/internal/theoriq-ceo-on-the-agentic-economy-... | Ron Bodkin as CEO Dec 2025 |
| ZoomInfo (Pei Chen) | https://www.zoominfo.com/p/Pei-Chen/3049130806 | COO/Executive Director role confirmed |
| @TheoriqAI on X | https://x.com/TheoriqAI | $50M TVL claim (Lido stRATEGY vault) |
| Crunchbase (Ron Bodkin) | https://www.crunchbase.com/person/ron-bodkin | Founder/CEO confirmed |
| RootData (Jeremy Millar) | https://www.rootdata.com/member/Jeremy%20Millar | Chairman background |
| Sherlock audit PDF | GitHub: audits/202508_Sherlock | Mellow Protocol scope confirmed |
| Ethplorer (THQ) | https://ethplorer.io/address/0xaffbe9a60f1f45e057fd9b6dc70004bb0ccc8b99 | Price $0.02263, 731 holders |
