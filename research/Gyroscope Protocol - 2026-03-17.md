# Gyroscope Protocol (GYD Stablecoin) — Adversarial Due Diligence Report

**Date:** 2026-03-17
**Classification:** Stablecoin (crypto-backed, reserve-based)
**Phase Emphasis:** Phase 3 (peg mechanics) + Phase 4 (tokenomics)

---

## 1. Executive Summary

**Verdict:** Gyroscope is an academically-grounded stablecoin protocol whose strong theoretical foundations have not translated to operational resilience. The protocol was exploited for ~$807K on Jan 30, 2026 via a cross-chain contract vulnerability, has been effectively halted since, and **no co-founder appears to be working on Gyroscope full-time** — with key team members simultaneously running other ventures (TLX, Aurora Labs, L2BEAT, Worldcoin, Imperial College). The academic halo effect masked fundamental operational and commitment risks.

**Top 3 Risks:**
1. **~$807K exploit (Jan 30, 2026) + protocol halted** — Cross-chain contract vulnerability exploited despite 10 audit reports. Pools paused, protocol dormant for 9+ weeks with minimal communication
2. **Founder attention fragmentation** — Daniel Perez co-founded 3 projects in 2021. Jacek Czarnecki is at Worldcoin + co-founded L2BEAT. Lewis Gudgeon lectures at Imperial College. No founder appears full-time on Gyroscope.
3. **Academic credibility contradicted by execution** — Team predicted Terra/UST collapse and Dai Black Thursday in published research, but their own protocol depegged 25% AND got exploited

**Top 3 Positives:**
1. **Extensive audit coverage** — 10 reports from Trail of Bits (Tier 1), Nethermind (Tier 2), and Runtime Verification across multiple protocol components
2. **Novel mechanism design** — PAMM bonding curves, circuit breakers, segregated vault architecture, and Optimistic Approval governance are technically sound innovations
3. **Founders are identifiable and academically credible** — Unlike many DeFi teams, all three co-founders have verifiable PhD credentials (Cornell, Imperial x2) and published research records

**Confidence Level:** Medium-High (upgraded from Medium)
- On-chain data confirmed via DeFiLlama, Etherscan, and CertiK incident analysis
- Audit existence confirmed via GitHub repo (PDFs independently verifiable)
- **Team identities now verified** — all three co-founders have LinkedIn profiles, academic publication records, and conference appearances
- Exploit confirmed by multiple independent sources (CertiK, Parallel Protocol)
- Independent analyst coverage remains sparse for the protocol itself

---

## 2. Team Assessment

### Founders (Updated 2026-04-02)

**Three co-founders identified — all PhD candidates who co-authored stablecoin/DeFi risk papers:**

#### Ariah Klages-Mundt
| Verified | Unverified | Assessment |
| --- | --- | --- |
| BA Mathematics, Amherst College (2012, magna cum laude); visiting student, Oxford (2010-11) | Depth of ongoing involvement in Gyroscope post-GYFI launch | Strong academic credentials but no primary source verification of current day-to-day role |
| PhD-level math coursework at NYU (2015); MSc + PhD Applied Mathematics, Cornell (2016-2023) | Whether academic work continues alongside protocol duties | PhD completed 2023 — but protocol went dormant by early 2026 |
| Analyst at Locus Analytics (2013-15); Technology Engineer at Andrew Davidson & Co. (2015-16) | Current employment status and full-time commitment to Gyroscope | Pre-crypto career in financial modeling is legitimate but brief |
| Published warnings about Terra/UST collapse and Dai Black Thursday *before* they happened | Claims of being a leading stablecoin researcher | Predictive track record is genuinely impressive — but designing a stablecoin that itself depegged 25% undermines the thesis |
| LinkedIn profile active (uk.linkedin.com/in/aklagesmundt); Devcon SEA speaker | — | Public-facing enough to be accountable |

#### Lewis Gudgeon
| Verified | Unverified | Assessment |
| --- | --- | --- |
| BA Philosophy, Politics & Economics, Warwick (2014) | Current time commitment to Gyroscope vs. academic career | PPE background — not technical. Computer Science PhD came later |
| Advanced Diploma + MPhil Economics, Cambridge (2015-17) | Whether guest lecturing at Imperial is his primary role now | Academic trajectory shifted from economics to CS mid-career |
| PhD Computer Science, Imperial College London (completed 2023) | Day-to-day operational role at FTL Labs | PhD completed same year as seed round — was he building a protocol or finishing a degree? |
| Guest Lecturer, Imperial College London (Jan 2023–present), co-teaches "Principles of Distributed Ledgers" | Whether Gyroscope is a side project vs. primary venture | **Holding an academic position while running a $26M stablecoin raises commitment questions** |
| Co-founded Gyroscope July 2020 | — | Medium post authorship confirms ongoing involvement through at least GYD mainnet launch |

#### Daniel Perez
| Verified | Unverified | Assessment |
| --- | --- | --- |
| PhD Imperial College London (completed June 2023), supervised by Ben Livshits, sponsored by Ethereum Foundation | Current active involvement in Gyroscope | EF sponsorship is a credibility signal but also creates ecosystem entanglement |
| Master's, University of Tokyo (ML + programming languages) | Whether he's still contributing code to Gyroscope | — |
| **Co-founded TLX** (leveraged token protocol on Optimism) — **acquired by Synthetix Dec 2024** | How much time went to TLX vs. Gyroscope during overlap period (2021-2024) | **Running two DeFi protocols simultaneously is a major split-attention red flag** |
| **Co-founded Aurora Labs** (Virtual Chains on NEAR) in 2021, involved until 2025 | Depth of Aurora Labs involvement | **Three co-founded projects in the same year (2021): Gyroscope, TLX, Aurora Labs** |
| GitHub @danhper — active developer, London-based | — | Technically capable but spread across too many ventures |

### Extended Team

| Member | Background | Verified Role | Concern |
| --- | --- | --- | --- |
| **Dr. Steffen Schuldenzucker** | PhD in complexity and systemic risk in financial networks | FTL Labs team member | No public information on current involvement level |
| **Jonas Klemm** | Formerly at the ECB | FTL Labs team member | No public information on current involvement level |
| **Jacek Czarnecki** | Former Global Legal Counsel, Maker Foundation; Harvard Law LLM; Oxford MSc Law & Finance | FTL Labs team member | **Also co-founder of L2BEAT AND currently at Worldcoin** — another team member spread across multiple high-profile projects. Deputy Chairman of Dai Foundation adds further time commitments |

### Key Concerns (Revised)

1. **FTL Labs receives 35% of GYFI supply** — the entity has no public legal structure, jurisdiction, or accountability framework, yet controls over a third of governance tokens
2. **Founder attention fragmentation** — Daniel Perez co-founded 3 projects in 2021 alone (Gyroscope, TLX, Aurora Labs). Jacek Czarnecki simultaneously works at Worldcoin and co-founded L2BEAT. Lewis Gudgeon holds an academic position at Imperial College. **No founder appears to be working on Gyroscope full-time.**
3. **Academic credentials vs. operational execution** — The team's research predicted Terra/UST collapse and Dai Black Thursday, but their own stablecoin depegged 25%, suffered a ~$807K exploit (Jan 30, 2026), and went dormant. **Theoretical expertise has not translated to operational resilience.**
4. **Post-exploit silence** — The Jan 30, 2026 exploit directly explains the "dormancy" flagged in the original report. The team paused pools but communication has been minimal. The governance proposal to recover 200 ETH from the attacker is the only public resolution effort found.

---

## 3. Third-Party Consensus

### Audit Posture

**10 audit reports** hosted on GitHub (independently verifiable at `github.com/gyrostable/audit-reports`):

| Auditor | Tier | Reports | Scope |
| --- | --- | --- | --- |
| **Trail of Bits** | Tier 1 | 1 (Summary + Fix Review) | Core protocol |
| **Nethermind** | Tier 2 | 8 reports | Core protocol, CEMM, governance, sGYD, GYFI token, dynamic E-CLP |
| **Runtime Verification** | Tier 2 | 1 | Protocol audit |

**Assessment:** This is among the strongest audit coverage seen in a sub-$30M protocol. The breadth (8 Nethermind reports covering different components) suggests iterative security review as the protocol evolved. **However:** Audit PDFs have not been read in full for this report — scope, findings severity, and remediation status are unverified. This is a gap.

### Bug Bounty
- **Status:** Not confirmed via Immunefi or other platforms in this investigation
- **Gap:** For a protocol holding $26.5M in stablecoin reserves, absence of a visible bug bounty program is a concern

### Independent Analyst Coverage
- CoinDesk covered the mainnet launch (Dec 2023) and sGYD launch (Aug 2024) — neutral/positive tone
- The Block covered GYFI token launch (Mar 2025) — factual coverage
- No coverage found from @zachxbt, Rekt News, BlockSec, or PeckShield
- No entry in DeFiHackLabs exploit database
- Consensys published a detailed technical explainer — positive but Consensys has ecosystem alignment with Ethereum projects

### Community Sentiment
- Limited community discussion found
- The protocol appears to operate quietly with minimal social media presence
- Twitter handle: @GyroStable

---

## 4. On-Chain Findings

### Core Metrics

| Metric | Value | Source |
| --- | --- | --- |
| GYD Circulating Supply | $26,558,619 | DeFiLlama Stablecoins API |
| GYD Holders | 615 | Etherscan |
| GYD 24h Transfers | 0 | Etherscan (as of investigation) |
| Protocol TVL (DEX pools) | $1.81M | DeFiLlama |
| 24h Fees | $1.78K | DeFiLlama |
| All-Time Fees | $297.82K | DeFiLlama |
| All-Time Protocol Revenue | $0 | DeFiLlama |
| Claimed Annualized Revenue | $2M+ | The Block (project claim) |
| Claimed YTD Trading Volume | $4.1B | The Block (project claim) |
| GYD Price | $0.9925 (last updated Feb 1, 2026) | CoinGecko |
| GYD All-Time Low | $0.7445 | CoinGecko |
| Chains Deployed | 10 (Ethereum, Polygon, Gnosis, Base, Optimism, Arbitrum, Avalanche, Sonic, Polygon zkEVM, Sei) | DeFiLlama |

### Critical Data Discrepancies

1. **Revenue discrepancy:** DeFiLlama shows $0 protocol-retained revenue all-time, while The Block article (citing Gyroscope) claims "$2M+ annualized revenue." The $297K all-time fees figure is closer to reality. The $2M claim may include fees that go to LPs rather than the protocol, or may count Balancer pool fees where Gyroscope CLPs are deployed. **This claim needs verification.**

2. **Volume discrepancy:** "$4.1B YTD trading volume" claimed but protocol TVL is only $1.81M. This volume likely comes from Gyroscope's E-CLP pools on Balancer across all chains — the volume flows through Balancer's infrastructure, not a Gyroscope-controlled contract. This is technically accurate but misleading about protocol scale.

3. **Supply stagnation:** GYD supply has been frozen at exactly $26,558,619 since February 1, 2026. Zero minting or redemption for 6+ weeks. CoinGecko price data also stopped updating on the same date. This suggests the protocol is functionally dormant.

### Contract Architecture

| Component | Detail |
| --- | --- |
| GYD Token (Ethereum) | `0xe07f9d810a48ab5c3c914ba3ca53af14e4491e8a` |
| Pattern | Transparent Upgradeable Proxy (EIP-1967) |
| Implementation | `0x511cc903377ef0fffc10434a8eaa06e63e563471` |
| Admin | `0x581aE43498196e3Dc274F3F23FF7718d287BC2C6` |
| Compiler | Solidity 0.8.17, verified source |
| Notable Feature | `freeze()` function — irreversibly sets admin to address(0), permanently preventing upgrades |

**Assessment:** The `freeze()` function is a strong trust-minimization feature — once called, the contract becomes immutable. **However:** It has not been called yet, meaning the admin address currently retains full upgrade authority. Who controls this admin address is critical and unverified.

### Peg Mechanism

**Architecture:**
- **PAMM (Primary-Market AMM):** Permissionless minting/redemption via bonding curve
- **SAMM (Secondary-Market AMMs):** E-CLP pools on Balancer concentrating liquidity around peg
- **Circuit Breakers:** During undercollateralization, redemption quotes decrease to disincentivize bank runs
- **Triangulated Price Feed:** Multiple on-chain oracle sources cross-referenced (Chainlink, TWAP, Balancer LP token oracle)
- **Reserve:** Segregated vaults holding sDAI, USDC (in Aave/Flux), LUSD, crvUSD, USDT

**Stress Test Record:**
- GYD hit $0.7445 (25% depeg) at some point in its history — date unknown
- The circuit breaker mechanism is *designed* to allow temporary depeg during stress (decreasing redemption quotes), so this may be "working as intended"
- **However:** A 25% depeg on an "all-weather" stablecoin marketed for resilience is a significant mark against the product thesis

### Oracle Design
- Chainlink (external price feeds)
- TWAP (time-weighted average price — manipulation-resistant but lagging)
- Balancer Pool LP token oracle (for vault share pricing)
- Triangulated Price Feed cross-references multiple sources — reduces single oracle dependency

---

## 5. GYFI Tokenomics

### Token Distribution

| Allocation | Percentage | Notes |
| --- | --- | --- |
| Community | 65% | Via SPIN points conversion (airdrop) |
| FTL Labs (developer) | 35% | Insider allocation to anonymous entity |

### Key Parameters

| Parameter | Value |
| --- | --- |
| Total Supply | 13,700,000 GYFI |
| Inflation | 2% per year starting March 2029 |
| SPIN Conversion Rate | 1,066 SPIN → 1 GYFI |
| Snapshot Date | March 14, 2025 |
| GYFI Contract | `0x70c4430f9d98b4184a4ef3e44ce10c320a8b7383` |

### Vesting Options (GIP-1 Airdrop)

| Option | Lock Period | Bonus | Unlock |
| --- | --- | --- | --- |
| 1 | None | Baseline | Fully liquid |
| 2 | 9 months | +40% | Linear over 9 months |
| 3 | 18 months | +150% | 9-month cliff, then linear |

Holdings >10,000 GYFI face additional 6-month linear vesting on excess.

### Assessment

- **35% to FTL Labs is a large insider allocation** for an anonymous entity with no public legal structure
- The vesting bonuses (up to +150%) heavily incentivize long lockups — this delays sell pressure but concentrates future supply release around Dec 2026 (18-month cliff from Mar 2025)
- GYFI token is a governance token for a protocol with $1.81M TVL and 615 stablecoin holders — the token launch appears premature relative to protocol adoption
- CoinMarketCap shows 0 circulating supply — token may not be actively trading yet or lacks market maker support

---

## 6. Red Flags Register

| # | Flag | Severity | Evidence | Source |
| --- | --- | --- | --- | --- |
| 1 | **~$807K exploit via cross-chain contract (Jan 30, 2026)** — Arbitrary-input vulnerability in cross-chain contract allowed attacker to extract ~$807K from GYD liquidity pools. 6M GYD impacted. CertiK confirmed six-figure to low-seven-figure loss. Pools paused, protocol effectively halted since. | **CRITICAL** | Pools paused Jan 30, 2026; governance proposal to recover 200 ETH from attacker | CertiK incident analysis, Parallel Protocol (X), CryptoAdventure |
| 2 | **Protocol dormant post-exploit** — Zero GYD minting/redemption since Jan 30, 2026; price data stale; 0 transfers. Original report flagged "dormancy since Feb 1" — this was the exploit aftermath, not mysterious inactivity | HIGH | Supply frozen at $26,558,619 for 9+ weeks | DeFiLlama stablecoins API, Etherscan |
| 3 | **Founders running multiple projects simultaneously** — Daniel Perez co-founded 3 projects in 2021 (Gyroscope, TLX, Aurora Labs), involved in all through 2025. Jacek Czarnecki simultaneously at Worldcoin + L2BEAT co-founder. Lewis Gudgeon holds academic position at Imperial College. No founder appears full-time on Gyroscope. | HIGH | LinkedIn profiles, project announcements, Synthetix TLX acquisition (Dec 2024) | LinkedIn, The Block, daniel.perez.sh |
| 4 | **Discord server compromised** — Gyroscope's Discord was hacked, fake mint/phishing links posted targeting users. CertiK issued warning. | HIGH | CertiK security alert | CoinLive, CertiK |
| 5 | **Revenue claims don't match on-chain data** — "$2M+ annualized revenue" claimed vs. $0 protocol-retained revenue on DeFiLlama, $297K all-time fees | MEDIUM | Discrepancy between project claims and independently verifiable data | DeFiLlama fees endpoint, The Block |
| 6 | **25% historical depeg** — GYD hit $0.7445 ATL, undermining "all-weather" marketing. Team members published academic papers predicting exactly this kind of failure in other protocols. | MEDIUM | All-time low price data | CoinGecko |
| 7 | **Opaque entity with 35% token allocation** — FTL Labs receives 35% of GYFI but has no public legal identity, jurisdiction, or accountability structure. Team members verified as individuals but the corporate entity remains a black box. | MEDIUM | GYFI tokenomics documentation | docs.gyro.finance |
| 8 | **Admin key controls upgradeable proxy** — `freeze()` function exists but hasn't been called; admin can still upgrade GYD contract | MEDIUM | Proxy admin at `0x581aE...` retains upgrade authority | Etherscan |
| 9 | **Academic credibility vs. operational failure** — Team predicted Terra/UST collapse and Dai Black Thursday, yet their own protocol suffered a 25% depeg AND a ~$807K exploit. 10 audit reports did not prevent the cross-chain vulnerability. | MEDIUM | Team publication history vs. protocol incident record | Scholar profiles, CertiK |
| 10 | **$4.1B volume claim is misleading** — Volume flows through Balancer E-CLP infrastructure, not Gyroscope-controlled contracts; implies larger protocol than $1.81M TVL suggests | LOW | DeFiLlama TVL vs. claimed volume | DeFiLlama, The Block |
| 11 | **No confirmed bug bounty** — Not found on Immunefi for a protocol that managed $26.5M in stablecoin reserves and then got exploited | LOW | Absence from Immunefi | Investigation finding |
| 12 | **sGYD yield target (12-15%) may be unsustainable** — Relies on DeFi strategy yields that compress over time; actual protocol revenue is $0 retained | LOW | sGYD launch announcement | gyro.finance blog |

---

## 7. Unresolved Questions

1. **Who controls the GYD proxy admin address (`0x581aE...`)?** Is it a multisig? How many signers? Are identities public?
2. **What is the full post-mortem on the Jan 30, 2026 exploit?** The cross-chain contract vulnerability was described as "arbitrary-input style" — has the root cause been publicly disclosed in technical detail? Was this contract covered by any of the 10 audits?
3. **Was the 200 ETH recovery request successful?** The governance proposal asked the attacker to return funds — has any been returned?
4. **What is the protocol restart plan?** Pools have been paused since Jan 30 — is there a timeline for resuming operations, or is the protocol effectively abandoned?
5. **Which founders are still actively working on Gyroscope?** Daniel Perez's TLX was acquired by Synthetix (Dec 2024) — did he return full-time to Gyroscope, or move on? Is Jacek Czarnecki's Worldcoin role his primary commitment?
6. **What caused the $0.7445 depeg?** When did it occur, and did the circuit breaker mechanism function as designed?
7. **What is FTL Labs' legal structure?** Where is it incorporated? What obligations does it have to GYFI holders?
8. **What is the actual composition of the GYD reserve today?** Post-exploit, what remains in the reserve vaults?
9. **Is GYFI actively trading?** CoinMarketCap shows 0 circulating supply. What market exists for governance participation?
10. **Where does the "$2M annualized revenue" come from?** Is this protocol-retained revenue or total fees including LP share?

---

## 8. Monitor

- **Monitor Dec 2026** — 18-month GYFI vesting cliff (Option 3 from Mar 2025 snapshot). Large supply unlock could create significant sell pressure on a potentially illiquid token
- **Monitor Mar 2029** — 2% annual GYFI inflation begins
- **Watch for** GYD supply changes — if the $26,558,619 figure remains frozen for months, the protocol may be effectively abandoned
- **Watch for** admin key activity on `0x581aE43498196e3Dc274F3F23FF7718d287BC2C6` — any contract upgrades warrant immediate investigation
- **Watch for** `freeze()` function call on GYD proxy — would be a strong positive signal for trust minimization
- **Watch for** Balancer governance changes affecting E-CLP pools — Gyroscope's liquidity infrastructure depends on Balancer
- **Watch for** sGYD yield performance vs. 12-15% target — sustained underperformance would undermine the value proposition

---

## 9. Timeline

| Date | Event |
| --- | --- |
| 2020-07 | Gyroscope co-founded by Klages-Mundt, Gudgeon, and Perez (all PhD candidates) |
| 2021 | Daniel Perez also co-founds TLX and Aurora Labs in the same year |
| 2022 (est.) | Gyroscope development begins; testing on Polygon |
| 2023-03-09 | $4.5M seed round (Placeholder, Galaxy, Maven 11, Archetype, Robot Ventures) |
| 2023 | All three co-founders complete their PhDs (Cornell, Imperial, Imperial) |
| 2023-12-07 | GYD stablecoin launches on Ethereum mainnet |
| 2024-04-25 | First DeFiLlama stablecoin tracking entry ($20M supply) |
| 2024-08-07 | sGYD (yield-bearing stablecoin) launches; targets 12-15% APY |
| 2024-08-07 | SPIN Phase 2 points program begins |
| 2024 (est.) | Gyroscope Discord server compromised — fake mint/phishing links; CertiK warning |
| 2024-10 – 2024-12 | GYD supply grows from $23M to $26M |
| 2024-12 (est.) | Daniel Perez's TLX acquired by Synthetix — unclear if he returns full-time to Gyroscope |
| 2025-03-14 | GYFI governance token snapshot (SPIN → GYFI conversion) |
| 2025-03 (est.) | GYFI token launch announced alongside "$2M+ annualized revenue" and "$4.1B YTD volume" claims |
| 2025-06-12 | GYD supply peaks at $26.8M |
| **2026-01-30** | **CRITICAL: Cross-chain contract exploit. ~$807K extracted from GYD liquidity pools. Pools paused.** |
| 2026-01-31 | Supply data drops to $19.8M — **now understood as exploit impact, not data artifact** |
| 2026-02-01 | Protocol effectively halted; price data stops updating on CoinGecko |
| 2026-02 (est.) | Governance proposal floated to recover 200 ETH from attacker |
| 2026-03-17 | Original investigation: protocol dormant (cause now identified as exploit aftermath) |
| 2026-04-02 | Updated investigation: founder deep-dive reveals team fragmentation |

**Notable patterns:**
1. The GYFI token launch (with revenue/volume claims) occurred when GYD supply had plateaued — the token launch may have been an attempt to reignite growth, but it was followed by an exploit that halted the protocol entirely.
2. The Jan 31, 2026 "anomalous supply data point" was the exploit impact, not a data artifact. The original report missed this because the exploit was not surfaced in DeFiLlama data.
3. **The team's academic credentials created a halo effect that masked operational risk.** Ten audit reports, peer-reviewed publications, and correct predictions about other protocols' failures did not prevent a cross-chain vulnerability in their own protocol.
4. **Founder attention was split across multiple ventures throughout Gyroscope's entire lifecycle** — this is not a post-launch drift, it was the operating model from day one (2021).

---

## 10. Data Sources

| Source | URL | Trust Level |
| --- | --- | --- |
| DeFiLlama Protocol Data | defillama.com (protocol, stablecoins, fees endpoints) | Highest |
| Etherscan (GYD Contract) | etherscan.io/token/0xe07f9d810a48ab5c3c914ba3ca53af14e4491e8a | Highest |
| CoinGecko (GYD Price) | coingecko.com/en/coins/gyroscope-gyd | High |
| GitHub Audit Reports | github.com/gyrostable/audit-reports | High (independently verifiable) |
| GitHub Organization | github.com/gyrostable | High |
| CoinDesk (Mainnet Launch) | coindesk.com/markets/2023/12/07/ | Medium-High |
| CoinDesk (sGYD Launch) | coindesk.com/business/2024/08/08/ | Medium-High |
| The Block (GYFI Token) | theblock.co/post/346897/ | Medium-High |
| Consensys Blog | consensys.io/blog/gyroscope-... | Medium (ecosystem-aligned) |
| ICO Drops | icodrops.com/gyroscope/ | Medium |
| CoinMarketCap | coinmarketcap.com/currencies/gyroscope/ | Medium |
| Gyroscope Docs | docs.gyro.finance | Low (project's own) |
| Gyroscope Blog | gyro.finance/blog/ | Low (project's own) |

### Sources Added 2026-04-02 (Founder Deep-Dive)

| Source | URL | Trust Level |
| --- | --- | --- |
| CertiK Incident Analysis (GYD exploit) | certik.com (referenced via CryptoAdventure) | High |
| CryptoAdventure (exploit resolution) | cryptoadventure.com/gyroscope-governance-floats-resolution-path-after-gyd-contract-incident/ | Medium-High |
| Parallel Protocol (X post on exploit) | x.com/ParallelMoney/status/2017582678007243197 | High (affected party confirmation) |
| CoinLive (Discord hack CertiK alert) | coinlive.com/news-flash/16895 | Medium |
| Ariah Klages-Mundt LinkedIn | uk.linkedin.com/in/aklagesmundt | High (primary source) |
| Lewis Gudgeon LinkedIn | uk.linkedin.com/in/lewis-gudgeon-21364267 | High (primary source) |
| Daniel Perez personal site | daniel.perez.sh | High (primary source) |
| The Block (TLX/Synthetix acquisition) | theblock.co/post/330311 | Medium-High |
| Google Scholar (Klages-Mundt) | scholar.google.com | High |
| Google Scholar (Gudgeon) | scholar.google.com/citations?user=U5XZlvoAAAAJ | High |
| Google Scholar (Perez) | scholar.google.com/citations?user=W2XsCqwAAAAJ | High |
| Lossless DeFi Medium (Czarnecki profile) | losslessdefi.medium.com | Medium |
