# OpenEden ($EDEN) — Adversarial Due Diligence Report

**Date:** 2026-05-17
**Classification:** Tokenized Real World Assets — Yield-Bearing Stablecoin / Tokenized Treasury Bills
**Confidence Level:** Medium-High — Team identities independently verified via CoinDesk and financial publications; on-chain data confirmed via DeFiLlama and Etherscan; S&P and Moody's ratings confirmed from primary sources; BNY partnership confirmed from BNY's own press release; audit reports read (Hacken full, Halborn summary); no independent adversarial analyst coverage found (zachxbt, Rekt News absent). OpenEden docs returned 403 — some governance architecture details derived from Etherscan and audit reports rather than official documentation.

---

## 1. Executive Summary

**Verdict:** OpenEden is one of the most institutionally credible tokenized treasury platforms in crypto — the first to receive investment-grade ratings from both S&P (AA+f/S1+) and Moody's (A), with BNY Mellon as custodian and investment manager. The product works: $180M+ in assets earning T-bill yields across 7 chains. However, the EDEN governance token has collapsed 97% from ATH, revealing a fundamental disconnect between platform success and token value accrual. The token is an upgradeable proxy with extreme holder concentration, and its utility remains speculative with no live fee-sharing or governance mechanism.

**Top 3 Risks:**
1. **Token-to-platform value disconnect** — EDEN has declined 97% despite growing TVL and institutional partnerships. Protocol revenue ($833K all-time) is negligible relative to token FDV (~$50M). No live fee-sharing mechanism exists — token utility is entirely forward-looking.
2. **Extreme token concentration** — Top 10 holders control >98% of supply. Only 5,977 holders on Ethereum. Combined with an upgradeable proxy (ERC1967), this creates a structure where insiders control both the token supply and the ability to change token logic.
3. **Centralization of vault operations** — Hacken audit flagged that operators can update epochs unlimited times, transaction fees can theoretically reach 100%, and KYC revocation can permanently lock user tokens. All vault contracts use upgradeable proxies with no publicly documented timelock or multisig governance.

**Top 3 Positives:**
1. **Institutional-grade custody and ratings** — BNY Mellon ($55.8T AUC/A) as investment manager + custodian. S&P AA+f/S1+ and Moody's A ratings on the TBILL Fund — first tokenized treasury to achieve both.
2. **Strong team pedigree and track record** — Founders are ex-Gemini APAC executives with Goldman Sachs, Deutsche Bank, Morgan Stanley backgrounds. 2.5+ year operational history with zero security incidents.
3. **Bankruptcy-remote legal structure** — USDO issued through a Bermuda Segregated Account Company (SAC), ring-fencing holder assets. TBILL Fund is a BVI-regulated Professional Fund. Chainlink Proof of Reserve provides independent on-chain verification.

---

## 2. Team Assessment

| Verified | Unverified | Assessment |
| --- | --- | --- |
| **Jeremy Ng** — CEO/Co-founder. Ex-Gemini APAC Head (Jun 2020–Dec 2021). Prior: Goldman Sachs, Deutsche Bank, Morgan Stanley, Leonteq Asia CEO. 20 years in financial services. Singapore-based. | Whether departure from Gemini was related to later Earn crisis | **LOW RISK** — Identity confirmed by CoinDesk, Yahoo Finance, multiple financial publications. Left Gemini 12+ months before the Earn collapse. |
| **Eugene Ng** — Former Co-founder. Ex-Gemini APAC BD, ex-DWF Labs founding partner. **FIRED Oct 2024** after CCTV footage showed him spiking a woman's drink at a Hong Kong bar. Victim (Hana) filed police report with video evidence. His X and LinkedIn deleted. | Criminal charges status; whether he retains equity/tokens in OpenEden | **HIGH RISK** — Confirmed predatory behavior with video evidence. Fired from both OpenEden and DWF Labs. TVL dropped $30M in 24hrs post-scandal. Raises character judgment questions about early team formation. |
| **River Labs Pte Ltd** — Singapore-registered developer entity | Full corporate registry details | **LOW RISK** — Named in Hacken audit and official documentation. |
| **Regulated fund entities: BVI (TBILL) + Bermuda (USDO/HYBOND)** | Specific entity names for BVI fund vehicle | **LOW RISK** — BVI Financial Services Commission regulated; Bermuda Monetary Authority licensed (Digital Asset Business Act). |

**Funding History (Verified):**
- **Strategic Round (Dec 2025):** Undisclosed amount — Ripple, Lightspeed Faction, Gate Ventures, FalconX
- DeFiLlama lists 12 total investors across rounds
- No public seed/Series A data with disclosed amounts found

**Prior Projects:** None negative for Jeremy Ng individually. Jeremy Ng's Gemini tenure ended ~12 months before the Gemini Earn crisis (Jan 2023), placing him outside that controversy.

**Critical Team Event (Oct 2024):** Co-founder Eugene Ng was terminated after CCTV footage from a Hong Kong bar showed him repeatedly spiking a woman's drink during a purported job interview. The victim obtained video evidence and filed a police report. Eugene Ng was also immediately fired from DWF Labs (where he was a founding partner). OpenEden's TVL dropped ~$30M within 24 hours of the news. DWF Labs' Andrei Grachev announced fund withdrawal from OpenEden and legal action against Ng. Status of criminal proceedings and whether Ng retains equity/token allocation in OpenEden is unknown.

---

## 3. Third-Party Consensus

### Audit Posture

| Auditor | Scope | Date | Tier | Key Findings |
| --- | --- | --- | --- | --- |
| **Hacken** | OpenEdenVaultV3Impl, FeeManager, PartnerShip | Jan–Feb 2024 | Tier 2 | Score 9.6/10. 0 Critical, 0 High, 1 Medium (tx.origin auth — fixed), 1 Low, 4 Observations. Centralization risks flagged. |
| **Halborn** | StabilityVault.sol | Jul 30–Aug 1, 2025 | Tier 2 | 1 Medium (missing whenNotPaused on withdraw — fixed). 100% remediated by Aug 3. |
| **HackenProof** | Smart Contract Audit Contest | 2024–2025 | Contest | Bug bounty rewards up to $5,000 |

**Audit Gaps:**
- No Tier 1 auditor (Trail of Bits, Spearbit, ChainSecurity) has reviewed OpenEden
- Bug bounty cap ($5K) is extremely low relative to TVL ($180M) — 0.003% ratio
- EDEN token contract itself not explicitly within audit scope
- V5 vault implementation (current) may not be fully covered by the V3 audit

### Credit Ratings (Independently Verified)
- **S&P Global:** AA+f/S1+ (investment grade) — TBILL Fund
- **Moody's:** A — TBILL Fund (first tokenized US Treasury product to receive Moody's rating)

### Independent Analyst Coverage
- No zachxbt mentions found
- No Rekt News entry
- No BlockSec/PeckShield incident alerts
- Binance Academy profile (positive, but Binance is a listing partner — potential COI)
- CoinTelegraph coverage of Ripple investment (news reporting, not adversarial analysis)

### Conflict of Interest Check
- Binance listed EDEN via HODLer Airdrops and published an Academy article — standard exchange marketing, not independent analysis
- No Exponential.fi or equivalent conflict found

---

## 4. On-Chain Findings

### TVL, Volume, Fees, Revenue

| Metric | Value | Source |
| --- | --- | --- |
| Total TVL (products) | ~$180M | DeFiLlama yields |
| TVL — Ethereum (TBILL) | $79.0M | DeFiLlama |
| TVL — XRPL (TBL) | $62.1M | DeFiLlama |
| TVL — Ethereum (USDO) | $33.5M | DeFiLlama |
| TVL — Solana (cUSDO) | $5.7M | DeFiLlama |
| 30d Fees | $143K | DeFiLlama |
| All-Time Fees | $8.59M | DeFiLlama |
| 30d Protocol Revenue | $18K | DeFiLlama |
| All-Time Protocol Revenue | $833K | DeFiLlama |
| TBILL APY | 3.06% | DeFiLlama |
| USDO APY | 3.25% | DeFiLlama |
| Known Hacks/Exploits | 0 | DeFiLlama |

### Token Distribution (EDEN)

| Allocation | Percentage |
| --- | --- |
| Ecosystem & Community | 41.22% |
| Team & Advisors | 20.00% |
| Investors | 15.28% |
| Foundation | 10.00% |
| Bills Airdrop | 7.50% |
| Early Adopters | 6.00% |

- **Total Supply:** 1,000,000,000 EDEN
- **Circulating:** 183,870,000 (18.39%)
- **On-chain supply (Ethereum):** 928,386,648
- **Holders (Ethereum):** 5,977
- **Top 10 holders:** >98% of supply (CRITICAL concentration)
- **Team token lock-up:** Extended voluntarily to January 2027 minimum

### Contract Architecture

| Component | Pattern | Address (Ethereum) |
| --- | --- | --- |
| EDEN Token | ERC1967 Proxy (upgradeable) | 0x24a3d725c37a8d1a66eb87f0e5d07fe67c120035 |
| TBILL Vault v2 | ERC1967 Proxy (upgradeable) | 0xdd50C053C096CB04A3e3362E2b622529EC5f2e8a |
| TBILL Vault v2 Impl | OpenEdenVaultV5Impl | 0xc4545Bf80f935894cbe138d86b506923dab7c048 |
| TBILL Token | ERC-20 (separate from EDEN) | 0xad6250f0BD49F7a1eB11063af2cE9F25B9597b0F |

**Governance Architecture:**
- All contracts use ERC1967 upgradeable proxy pattern
- No publicly documented timelock on upgrades
- No publicly documented multisig threshold
- Operator role can: update epochs, process withdrawals, set weekend flags
- KYC Manager contract gates access — revocation locks tokens
- Deployer address: 0xb09f372... (labeled "OpenEden: Deployer 1")

### USDO Structure
- Fully backed by TBILL tokens (verifiable on-chain via Chainlink PoR)
- Issued through Bermuda Segregated Account Company (SAC) — bankruptcy-remote
- Custody: BitGo + Coinbase Prime
- Underlying treasuries managed by BNY, State Street, VanEck, BlackRock
- Daily rebase mechanism distributes yield to holders
- Chainlink CCIP for cross-chain interoperability

### Security Assessment
- Bug bounty: $5,000 max (HackenProof) — grossly inadequate for $180M TVL
- Bounty/TVL ratio: 0.003% — far below the 0.01% minimum threshold
- No Immunefi program found
- Chainlink Proof of Reserve: independent on-chain attestation of USDO backing

---

## 5. Red Flags Register

| # | Flag | Severity | Evidence | Source |
| --- | --- | --- | --- | --- |
| 1 | **Co-founder fired for predatory behavior (CCTV evidence)** — Eugene Ng terminated Oct 2024 after video showed him spiking a woman's drink at a HK bar. Also fired from DWF Labs. TVL dropped $30M in 24hrs. Unknown if Ng retains equity/token allocation. | HIGH | CCTV footage, police report filed, The Block/Decrypt/DL News reporting | [The Block](https://www.theblock.co/post/323749), [Decrypt](https://decrypt.co/288907) |
| 2 | **Token-platform disconnect** — EDEN declined 97% from ATH ($1.31 → $0.04) while platform TVL grew to $180M. No live fee-sharing, staking, or governance utility. Token has no claim on treasury assets or revenue. | HIGH | Price: CoinGecko $0.041; TVL: DeFiLlama $128M protocol / $180M yields | CoinGecko, DeFiLlama |
| 3 | **Extreme holder concentration** — Top 10 wallets hold >98% of circulating EDEN. 5,977 total holders. | HIGH | Etherscan token tracker (928M supply, 5,977 holders) | Etherscan |
| 4 | **Upgradeable proxy on EDEN token + vault contracts** — ERC1967 pattern on both EDEN and TBILL Vault with no documented timelock or multisig. Admin can change token/vault logic. | HIGH | Contract verification on Etherscan | Etherscan: 0x24a3...035, 0xdd50...8a |
| 5 | **Inadequate bug bounty** — $5,000 max reward on $180M TVL (0.003%). Economically irrational to report vs. exploit. | HIGH | HackenProof program page | HackenProof |
| 6 | **Operator centralization** — Hacken audit flagged: epoch updates unlimited by operator, fees configurable to 100%, KYC revocation permanently locks tokens. | MEDIUM | Hacken audit report (Feb 2024) | Hacken.io |
| 7 | **No Tier 1 audit** — Only Hacken (Tier 2) and Halborn (Tier 2) have audited. No Trail of Bits, Spearbit, or equivalent. Current V5 implementation may exceed V3 audit scope. | MEDIUM | Audit search results | Hacken, Halborn |
| 8 | **Low protocol-retained revenue** — $833K all-time on $180M TVL. 30d revenue of $18K implies annualized ~$216K. Cannot justify $50M FDV via cash flow. | MEDIUM | DeFiLlama fees endpoint | DeFiLlama |
| 9 | **81.6% of supply still locked/unvested** — With team tokens locked to Jan 2027 and investors/ecosystem unlocking gradually through 2028, massive supply overhang exists. | MEDIUM | Tokenomist.ai vesting data; Binance listing announcement | Tokenomist, Binance |
| 10 | **XRPL deployment ($62M TVL) less verifiable** — XRPL lacks the transparent tooling of EVM chains. Contract architecture on XRPL cannot be independently verified with standard tools. | LOW | DeFiLlama shows $39-62M on XRPL | DeFiLlama |
| 11 | **No GitHub repository** — DeFiLlama lists no GitHub. Open-source code not publicly available for community review. | LOW | DeFiLlama protocol page | DeFiLlama |

---

## 6. Unresolved Questions

1. **Who controls the ProxyAdmin for the EDEN token and TBILL Vault?** Is it a multisig? What threshold? Is there a timelock? (Docs returned 403; Etherscan shows deployer but not current admin structure.)
2. **What is the EDEN token's actual utility roadmap?** Is fee-sharing planned? Governance over what? The token has no live utility beyond speculation.
3. **Why does top-10 concentration exceed 98%?** Are these team/investor/exchange wallets or genuine accumulation? Holder addresses need mapping.
4. **What audit covers the V5 vault implementation?** The Hacken audit covered V3. Has the V5 upgrade been independently reviewed?
5. **What happens to TBILL holders if BNY terminates the custody/management agreement?** Is there a fallback custodian?
6. **Is there a mechanism for EDEN holders to participate in protocol governance?** No on-chain governance contracts are documented.
7. **What is the total funding raised?** Only one round (Strategic, Dec 2025) is on DeFiLlama with $0 listed. Binance Labs was reportedly an early investor — when and how much?

---

## 7. Monitor

| Trigger | Threshold | Action |
| --- | --- | --- |
| TVL drawdown | >10% from $180M baseline | Re-evaluate — capital flight from institutional product is a high-severity signal |
| Team token unlock | January 2027 cliff | Assess selling pressure — 200M tokens (20% supply) become available |
| Investor unlock events | Any linear vesting milestone | Monitor selling behavior vs. price |
| EDEN utility announcement | Fee-sharing, staking, or governance launch | Re-assess token-platform disconnect |
| Bug bounty increase | Any change | Positive signal if raised to >$100K |
| Proxy upgrade event | Any implementation change on EDEN or TBILL contracts | Review new code vs. audit scope |
| BNY partnership status | Any custody/management change | Fundamental change to product credibility |
| Interest rate environment | US Treasury yields drop below 2% | Monitor product attractiveness and TVL impact |
| S&P/Moody's rating change | Any downgrade | Re-assess institutional credibility |
| New chain deployment | XRPL expansion or new chain | Verify architecture on new chain |

**Specific watchpoints:**
- **Monitor Jan 2027** — Team/advisor token unlock. With price at $0.04 (97% below ATH), selling pressure could be acute.
- **Watch for governance launch** — If EDEN gets live on-chain governance, this materially changes the risk profile.
- **Watch US interest rates** — OpenEden's entire value proposition is passing T-bill yields on-chain. A rate cut environment directly compresses margins and product attractiveness.

---

## 8. Data Sources

- [DeFiLlama — OpenEden Protocol](https://defillama.com/protocol/openeden)
- [CoinGecko — EDEN](https://www.coingecko.com/en/coins/openeden)
- [CoinMarketCap — EDEN](https://coinmarketcap.com/currencies/openeden/)
- [Etherscan — EDEN Token](https://etherscan.io/token/0x24a3d725c37a8d1a66eb87f0e5d07fe67c120035)
- [Etherscan — TBILL Vault v2](https://etherscan.io/address/0xdd50c053c096cb04a3e3362e2b622529ec5f2e8a)
- [BNY Press Release — OpenEden Custody](https://www.bny.com/corporate/global/en/about-us/newsroom/company-news/openeden-selects-bny-to-provide-investment-management-and-custody-services-for-its-tokenized-us-treasury-bills-fund.html)
- [CoinDesk — Jeremy Ng Departs Gemini APAC](https://www.coindesk.com/business/2021/12/14/gemini-looks-to-replace-apac-head-in-singapore-after-jeremy-ng-departs)
- [Hacken Audit — OpenEden Vault (Jan 2024)](https://hacken.io/audits/openeden/sca-openeden-vault-jan2024/)
- [Halborn Audit — Stability Vault (Jul 2025)](https://www.halborn.com/audits/openeden/stability-vault-3df625)
- [Binance — EDEN HODLer Airdrops Announcement](https://www.binance.com/en/support/announcement/detail/feec6071453d4433bf251e8e17438c7c)
- [Tokenomist — EDEN Vesting](https://tokenomist.ai/openeden)
- [CryptoRank — OpenEden](https://cryptorank.io/ico/open-eden)
- [CoinTelegraph — Ripple Backs OpenEden](https://cointelegraph.com/news/ripple-vcs-back-openeden-tokenized-us-treasuries)
- [MEXC — Team Token Lock-Up Extension](https://www.mexc.co/en-PH/news/994998)
- [HackenProof — Bug Bounty Program](https://hackenproof.com/audit-programs/openeden-smart-contract-audit-contest)
- [Binance Academy — What Is OpenEden](https://academy.binance.com/en/articles/what-is-openeden-eden)
- [OpenEden Official](https://openeden.com/)
- [The Block — OpenEden Fires Employee (Drugging Allegations)](https://www.theblock.co/post/323749/openeden-fires-employee-following-drugging-allegations-in-hong-kong)
- [Decrypt — DWF Labs Fires Partner Amid Allegations](https://decrypt.co/288907/dwf-labs-fires-partner-sexual-harassment-drugging-allegations)
- [DL News — Hana Urges Crypto to Combat Sexual Harassment](https://www.dlnews.com/articles/people-culture/woman-drugged-by-dwf-labs-exec-urges-crypto-to-fight-sexism/)
- [BeInCrypto — OpenEden TVL Drop Following Misconduct](https://beincrypto.com/openedens-tvl-drops-following-founders-misconduct/)

---

## Appendix: Timeline

| Date | Event |
| --- | --- |
| Early 2022 | OpenEden founded by Jeremy Ng and Eugene Ng (ex-Gemini APAC) |
| 2023 | TBILL Vault launches on Ethereum — first tokenized US Treasury product |
| Jan 2024 | Hacken audit of VaultV3 — score 9.6/10 |
| 2024 | Moody's "A" rating — first tokenized treasury to receive investment-grade rating |
| Oct 2024 | **Co-founder Eugene Ng fired** — CCTV showed him spiking woman's drink at HK bar. Also fired from DWF Labs. TVL dropped $30M in 24hrs. |
| 2025 | S&P AA+f/S1+ rating on TBILL Fund |
| Aug 13, 2025 | BNY appointed as investment manager + custodian |
| Jul-Aug 2025 | Halborn audit of StabilityVault |
| Sep 30, 2025 | EDEN token listed on Binance (HODLer Airdrops) |
| Oct 2025 (approx) | EDEN reaches ATH of $1.31 |
| Dec 2025 | Strategic round: Ripple, Lightspeed Faction, Gate Ventures, FalconX |
| 2025-2026 | USDO (OpenDollar) launches with Bermuda SAC structure |
| 2025-2026 | Chainlink Proof of Reserve integration for USDO |
| Early 2026 | EDEN token extends team vesting to January 2027 |
| May 2026 | EDEN trades at ~$0.04 (97% below ATH) |

---

## Verdict Summary

**The product is legitimate and institutionally sound. The token is a separate, higher-risk bet.**

OpenEden's TBILL and USDO products represent some of the most credible tokenized treasury implementations in crypto: rated by S&P and Moody's, custodied by BNY Mellon, operated by a verified team with deep TradFi pedigree, and running for 2.5+ years without incident.

The EDEN token, however, is a governance token without live governance, a revenue-sharing token without live revenue sharing, and a speculative asset that has declined 97% from its peak. The 98%+ concentration in top-10 wallets, the upgradeable proxy architecture, and the absence of any mechanism connecting platform success to token value make EDEN a pure optionality play on future utility announcements.

**For the product (TBILL/USDO):** LOW-MEDIUM risk for users willing to accept the centralized operator model and KYC requirements. Custody structure is institutional-grade.

**For the token (EDEN):** HIGH risk. No current value accrual mechanism, extreme concentration, upgradeable contract, and massive supply overhang through 2028.
