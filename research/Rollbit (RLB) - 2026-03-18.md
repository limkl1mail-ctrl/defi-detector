# Rollbit (RLB) — Adversarial Due Diligence Report

**Date:** 2026-03-18
**Classification:** Centralized Crypto Casino / GambleFi
**Confidence Level:** Medium — pseudonymous team with limited primary source verification; no on-chain DeFi protocol to audit; revenue claims from project's own communications; no independent audit of platform or token contract

---

## 1. Executive Summary

**Verdict:** Rollbit is a revenue-generating centralized crypto casino with a functional buy-and-burn token model, but operates under pseudonymous founders with a prior CSGO gambling history, an upgradeable token contract with no published audit, and regulatory exposure across multiple jurisdictions. The platform is legitimate in the sense that it generates real revenue and has obtained multiple gambling licenses, but carries significant counterparty, regulatory, and governance risks.

**Top 3 Risks:**
1. Pseudonymous founders allegedly linked to prior CSGO Diamond gambling site (closed after "unethical practices"); identity partially revealed as Daniel Dixon and José Llisterri but never officially confirmed
2. RLB token uses an upgradeable proxy contract with no published security audit — admin can modify token behavior
3. 1000x crypto futures product operates outside gambling license scope, creating an unregulated derivatives offering with no investor protection

**Top 3 Positives:**
1. Real, verifiable revenue: $18–65M monthly across casino, sportsbook, and futures (self-reported, but corroborated by on-chain burn activity)
2. Aggressive deflationary mechanics: 65% of 5B supply burned (~3.27B RLB), with continuous buy-and-burn from revenue
3. Multi-jurisdictional licensing: Curaçao (primary), UK Gambling Commission, Gibraltar Gaming License — indicates willingness to undergo regulatory scrutiny

---

## 2. Team Assessment

| Category | Detail | Status |
|----------|--------|--------|
| **Founders** | Known as "Razer" and "Lucky"; allegedly Daniel Dixon and José Llisterri (British nationals) | Unverified — sourced from social media allegations |
| **Prior projects** | CSGO Diamond (CSGO skins betting site) — reportedly closed after unethical practices discovered | Unverified — multiple sources allege connection |
| **Corporate entity** | Bull Gaming N.V., Curaçao (Company #157086), Abraham de Veerstraat 9, Willemstad | Verified — public registration |
| **Payment processor** | WINGAMING SUPPORT LIMITED, Cyprus (HE406701), Avlonos 1, Maria House, Nicosia | Verified — public registration |
| **Team transparency** | Founders pseudonymous; identities reportedly disclosed during Curaçao licensing due diligence | Claimed, not independently verified |
| **Community presence** | "Lucky" active on X/Twitter; regular product updates | Verified |

**Assessment:** The pseudonymous founder structure is standard for crypto gambling but creates accountability gaps. The alleged connection to CSGO Diamond — a site that shut down after ethics concerns — is the most material team risk. The founders' identities were reportedly disclosed during licensing processes, but this is not publicly verifiable. The fact that they've obtained UK and Gibraltar licenses suggests some level of institutional due diligence has been conducted on the principals.

---

## 3. Third-Party Consensus

### Audit Posture
- **Smart contract audit:** None published for RLB token contract
- **Platform audit:** No publicly available security audit of the casino platform
- **Bug bounty:** No known bug bounty program
- **Assessment:** The complete absence of any published audit for a token with ~$100M+ market cap is a significant gap

### Independent Analyst Coverage
- **zachxbt:** No known investigations or flags against Rollbit
- **Rekt News:** No entry for Rollbit (mild positive)
- **DeFiHackLabs:** No known exploits catalogued
- **Community:** Mixed — Trustpilot shows numerous withdrawal complaints and account freeze reports alongside positive reviews
- **Casino review sites:** Safety ratings range from 4.1/10 (casino.guru) to generally positive (gambling-focused review sites, which may have affiliate relationships)

### Conflict of Interest Detection
- Most positive Rollbit reviews come from gambling affiliate sites that earn commissions from referrals — discount these heavily
- Casino.guru's low 4.1 safety index is notable as they have less direct financial incentive to promote

---

## 4. On-Chain & Technical Findings

### RLB Token Data

| Metric | Value | Source |
|--------|-------|--------|
| Contract | 0x046eee2cc3188071c02bfc1745a6b17c656e3f3d | Etherscan |
| Standard | ERC-20 (Transparent Proxy) | Etherscan |
| Max supply | 5,000,000,000 RLB | Contract |
| Circulating supply | ~1,729,851,556 RLB | Etherscan |
| Burned | ~3,270,148,444 RLB (~65.4%) | Derived |
| Holders | 20,779 | Etherscan |
| Contract verified | Yes | Etherscan |
| Proxy pattern | Transparent Upgradeable Proxy | Etherscan |
| Implementation | 0x0d9bdd2d61a37bc074e59b2801f32deee01307e5 | Etherscan |

### Contract Architecture Concerns
- **Upgradeable proxy:** The RLB token uses a transparent proxy pattern, meaning the admin can upgrade the token implementation at any time. This is a significant centralization vector — the admin could theoretically modify transfer logic, minting rules, or burn mechanics
- **No timelock disclosed:** No evidence of a timelock on proxy upgrades
- **No multisig disclosed:** Admin key structure not publicly documented
- **No audit:** Contract has not been audited by any known security firm

### Revenue & Burn Verification
Revenue claims are partially verifiable through on-chain burn transactions. If Rollbit claims to burn X% of revenue as RLB purchases, the burn transactions on Etherscan can be cross-referenced. However, the revenue figures themselves (casino take rate, futures fees) are entirely self-reported with no independent verification mechanism.

### Price History

| Period | Price | Notes |
|--------|-------|-------|
| Token launch (Spring 2022) | ~$0.002 | Airdropped, no ICO |
| All-time high (Nov 11, 2023) | $0.2625 | 5,578% yearly gain |
| 2024 peak (Apr 26) | $0.1353 | |
| Cycle low | $0.033 | ~87% drawdown from ATH |
| Current (Oct 2025 reference) | ~$0.062 | ~76% below ATH |
| Market cap (current) | ~$118M | |

---

## 5. Red Flags Register

| # | Flag | Severity | Evidence | Source |
|---|------|----------|----------|--------|
| 1 | **Pseudonymous founders linked to defunct CSGO gambling site** — CSGO Diamond reportedly closed after unethical practices; same founders allegedly behind Rollbit | HIGH | Social media allegations name Daniel Dixon and José Llisterri as operators of both CSGO Diamond and Rollbit | [X/Twitter](https://x.com/Nonopancake/status/1782506890817105973); [BitcoinTalk](https://bitcointalk.org/index.php?topic=5384389.0) |
| 2 | **Upgradeable proxy token contract with no audit** — Admin can change token implementation; no published security audit, no timelock, no multisig documentation | HIGH | Etherscan shows transparent proxy pattern; no audit PDF found on any auditor's site | [Etherscan](https://etherscan.io/address/0x046eee2cc3188071c02bfc1745a6b17c656e3f3d) |
| 3 | **1000x futures product outside gambling license scope** — Derivatives trading product operates in regulatory grey zone; not covered by Curaçao gaming license | HIGH | Multiple review sites confirm futures are not covered by gambling license; no financial services license disclosed | [Datawallet](https://www.datawallet.com/crypto/rollbit-review); [GamblingBitcoin](https://gamblingbitcoin.com/rollbit-review/) |
| 4 | **Systematic withdrawal complaints** — Multiple users report account freezes and withheld funds ($2,500–$47,000), with accusations of money laundering used as justification without evidence provided | MEDIUM | Trustpilot reviews, BitcoinTalk complaints | [Trustpilot](https://www.trustpilot.com/review/www.rollbit.com); [BitcoinTalk](https://bitcointalk.org/index.php?topic=5419674.0) |
| 5 | **Alleged fake influencer balances** — Claims that Rollbit provides house money to influencers to display fake winnings, driving affiliate-driven deposits | MEDIUM | Multiple community allegations; pattern is common in crypto gambling but not independently confirmed for Rollbit specifically | [BeInCrypto](https://beincrypto.com/rollbit-allegedly-operates-crypto-casino-without-license/) |
| 6 | **Revenue figures entirely self-reported** — Monthly revenue ($18-65M) claimed by the team with no independent audit or verification mechanism | MEDIUM | Revenue data comes from Rollbit's own X/Twitter posts and blog; no third-party financial reporting | [Rollbit X](https://x.com/rollbit/status/1752998250515145035) |
| 7 | **Opaque corporate structure** — Bull Gaming N.V. has no website or public presence; payment processing through Cyprus entity adds jurisdictional complexity | LOW | Company registration verifiable but entity maintains no public-facing corporate presence | [GoodLuckMate](https://goodluckmate.com/guide/company/bull-gaming-nv-casinos) |
| 8 | **76% drawdown from ATH** — RLB has lost ~76% of its peak value despite continued revenue generation, suggesting disconnect between revenue narrative and token price support | LOW | CoinGecko price data | [CoinGecko](https://www.coingecko.com/en/coins/rollbit-coin) |

---

## 6. Tokenomics Analysis

### Distribution
- **Initial distribution:** 100% airdropped to users — no ICO, no VC allocation, no team pre-mine
- **Current circulating:** ~1.73B / 5B max (34.6%)
- **Burned:** ~3.27B (65.4%)
- **No vesting schedule:** All tokens were distributed at launch

### Burn Mechanics
Revenue allocation to buy-and-burn:
- Casino: 10% of revenue
- Sportsbook: 20% of revenue
- Crypto futures (1000x): 30% of revenue
- 90% of purchased RLB is burned; 10% distributed to Rollbot NFT stakers

### Sustainability Assessment
The burn model is sustainable **only if** Rollbit continues generating revenue at current levels. Unlike emission-based tokenomics (which create sell pressure), Rollbit's model creates continuous buy pressure from operations. This is structurally sound — the revenue source is real casino/gambling rake, which is a proven business model.

**However:** The token's 76% decline from ATH despite ongoing burns suggests that burn rate alone is insufficient to maintain price. The disconnect may be due to:
1. General altcoin bear market conditions
2. Holder concentration allowing large exits
3. Revenue declining from peak levels (Jan 2024 $65M vs. 2025 $18-30M range)

### Competitive Position
- Rollbit: ~$118M market cap, <5% market share
- Stake.com: >62% market share, $1.6B+ monthly deposits (no token)
- GambleFi sector total: ~$465M token market cap

Rollbit is a distant second in crypto gambling but is the dominant GambleFi token by market cap.

---

## 7. Timeline

| Date | Event |
|------|-------|
| 2019 | Founders operate CSGO skins betting site (predecessor) |
| Early 2020 | Rollbit.com launches as crypto-first casino |
| Spring 2022 | RLB token airdropped to users (5B supply, no ICO) |
| 2023 | 1000x crypto futures product launched |
| Aug 2023 | Revamped tokenomics with buy-and-burn program announced |
| Sep 2023 | $38M monthly revenue reported; SSC Napoli partnership |
| Nov 11, 2023 | RLB all-time high: $0.2625 |
| Nov 2023 | $505M market cap; $41.7M monthly fee revenue |
| Jan 2024 | $64.9M monthly revenue reported (peak); FaZe Clan sponsorship |
| Apr 2024 | Social media allegations linking founders to CSGO Diamond |
| Jul 2024 | Southampton FC front-of-shirt sponsorship |
| Aug 2024 | Multi-year FaZe Clan deal renewed |
| 2024 | UK Gambling Commission license obtained; Gibraltar license added |
| Dec 2024 | Curaçao LOK regulatory overhaul passed — all operators need individual licenses |
| 2025 | Revenue declines to $18-30M monthly range; 65% of supply burned |
| Mar 2025 | Account freeze complaints escalate on Trustpilot |

---

## 8. Unresolved Questions

1. **Are the founders actually Daniel Dixon and José Llisterri?** If so, what exactly happened with CSGO Diamond, and was it a regulatory shutdown or voluntary closure?
2. **Who controls the RLB proxy admin key?** Is it a single EOA, multisig, or smart contract? Can they upgrade the token at will?
3. **What is the actual revenue in 2025-2026?** Self-reported figures range widely ($18M–$65M/month). Has revenue genuinely declined, or has reporting become more conservative?
4. **Has Bull Gaming N.V. received its individual Curaçao license under the new LOK framework?** The application (OGL/2024/1260/0494) is listed as "in progress" — what happens if denied?
5. **What portion of trading volume on the 1000x futures platform is genuine vs. wash trading?** No independent analysis exists.
6. **Are the withdrawal freezes systematic (bad-faith revenue retention) or isolated (legitimate AML flags)?** Pattern of complaints suggests the former but evidence is insufficient to conclude.

---

## 9. Monitor

- **Monitor Q1 2026** — Curaçao LOK license application result for Bull Gaming N.V. Denial would create existential risk for primary operations
- **Monitor ongoing** — UK Gambling Commission enforcement actions against crypto gambling operators. UKGC has been increasingly aggressive; any action against Rollbit's UK entity would be material
- **Watch for** — RLB proxy contract upgrades. Any implementation change should be scrutinized immediately
- **Watch for** — Revenue disclosure cadence. If Rollbit stops publishing monthly revenue/burn data, this is a negative signal
- **Monitor** — Southampton FC sponsorship renewal/cancellation — Premier League sponsorship scrutiny of gambling companies is intensifying
- **Watch for** — Any zachxbt or independent investigator coverage of Rollbit — currently absent, which is a mild positive

---

## 10. Data Sources

| Source | URL | Used For |
|--------|-----|----------|
| Etherscan (RLB Token) | https://etherscan.io/token/0x046eee2cc3188071c02bfc1745a6b17c656e3f3d | Contract verification, holder count, proxy architecture |
| CoinGecko | https://www.coingecko.com/en/coins/rollbit-coin | Price history, market cap |
| CoinMarketCap | https://coinmarketcap.com/currencies/rollbit-coin/ | Token data, circulating supply |
| Rollbit Blog | https://blog.rollbit.com/rlb-utility-guide/ | Tokenomics mechanics |
| Rollbit Blog (Burns) | https://blog.rollbit.com/rlb-burns/ | Burn schedule & history |
| Tokenomist | https://tokenomist.ai/rollbit-coin/burn | Burn tracking |
| GoodLuckMate | https://goodluckmate.com/guide/company/bull-gaming-nv-casinos | Corporate entity details |
| Curaçao GCB | https://cert.gcb.cw/ | License verification |
| BeInCrypto | https://beincrypto.com/rollbit-allegedly-operates-crypto-casino-without-license/ | Licensing controversy |
| Trustpilot | https://www.trustpilot.com/review/www.rollbit.com | User complaints |
| BitcoinTalk | https://bitcointalk.org/index.php?topic=5526161.0 | Community warnings |
| CoinDesk | https://www.coindesk.com/tech/2023/10/03/rollbit-recorded-38m-in-september-betting-revenues-rlb-token-climbs | Revenue reporting |
| Blockonomi | https://blockonomi.com/rollbit-review/ | Platform review |
| Casino.guru | https://casino.guru/rollbit-casino-review | Safety rating |
| IQ.wiki (Razer) | https://iq.wiki/wiki/razer-rollbit | Founder profile |
| IQ.wiki (Lucky) | https://iq.wiki/wiki/lucky-rollbit | Founder profile |
| Decrypt | https://decrypt.co/213829/crypto-casino-rollbit-sponsors-faze-clan-multi-million-dollar-esports-deal | FaZe sponsorship |
| OurCryptoTalk | https://web.ourcryptotalk.com/news/rollbit-gamblefi-case-study | GambleFi analysis |
| Datawallet | https://www.datawallet.com/crypto/rollbit-review | Platform review, regulatory analysis |
