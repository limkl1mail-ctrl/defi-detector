# DeFi Detector

Adversarial due-diligence research on DeFi protocols, conducted with a structured AI-assisted methodology.

---

## What this is

A public archive of due-diligence investigations into DeFi protocols, stablecoins, derivatives, bridges, and yield aggregators. Each report applies a consistent adversarial framework: every project is treated as guilty until evidence proves otherwise.

The investigations are produced by [Claude](https://claude.com/claude-code) (Anthropic) operating against the methodology defined in [`METHODOLOGY.md`](./METHODOLOGY.md). The methodology file is, in effect, the system prompt. The reports in [`research/`](./research/) are the outputs.

## Why this exists

To demonstrate, with worked examples rather than claims:

1. **AI can perform credible adversarial research** when constrained by an explicit epistemology and source-trust hierarchy.
2. **Structured prompting** — defining classification, phases, severity tiers, and a required report format — produces consistent, comparable outputs across projects.
3. **The work product is the proof.** Read the reports; judge the methodology by what it found.

## Highlight reports

A small curated set showing what the framework catches. The full archive is in [`research/`](./research/).

- [**Theoriq Gold Vault**](research/Theoriq%20Gold%20Vault%20-%202026-05-06.md) — CEO succession (Bodkin → Chen), ~91% TVL collapse, Gold Vault contract address undisclosed, December 2026 cliff.
- [**Overnight Finance (OVN)**](research/Overnight%20Finance%20%28OVN%29%20-%202026-05-06.md) — Updated 2026-05-31 for the reported N.D. California class action, Circle's ~$12.6M Zama cUSDC freeze, and the new litigation/RFV recovery thesis.
- [**YO Protocol**](research/YO%20Protocol%20-%202026-03-02.md) — $3.71M loss from a centralized off-chain harvester (17.8M slippage vs. expected ~50 bps). Cited in the methodology as the canonical example of operational risk distinct from smart-contract bugs.
- [**Canton Network**](research/Canton%20Network%20-%202026-03-06.md) — Institutional permissioned chain. The investigation surfaced the parent company's prior ASX CHESS failure (~$250M, seven years, scrapped 2022) as critical context that official communications omitted.
- **Lighter DEX** — [Pre-token-launch institutional pre-screen](research/Lighter%20DEX%20-%202026-03-02.md), with a [follow-up two months later](research/Lighter%20DEX%20-%202026-05-14.md) showing how the picture changed (January 2027 cliff = $345M overhang).

## How to read a report

Every report follows a 7-section structure:

1. **Executive Summary** — verdict, top 3 risks, top 3 positives, confidence level
2. **Team Assessment** — verified / unverified / assessment
3. **Third-Party Consensus** — audits, independent analysts, community
4. **On-Chain Findings** — TVL, tokenomics, contract architecture
5. **Red Flags Register** — severity-tagged table (CRITICAL / HIGH / MEDIUM / LOW)
6. **Unresolved Questions** — what could change the verdict
7. **Monitor** — forward-looking triggers with thresholds

Severity definitions and confidence levels are in [`METHODOLOGY.md`](./METHODOLOGY.md).

## Methodology

See [`METHODOLOGY.md`](./METHODOLOGY.md). It defines:

- Epistemological rules (e.g., *official communications = marketing*)
- Source trust hierarchy (on-chain data > auditor reports > independent analysts > journalism > community > project communications)
- Project classification (retail DeFi, institutional, stablecoin, derivatives, bridge, yield aggregator, multi-asset vault)
- Quantitative pre-screen (market cap, contract age, audit count, TVL stability, collateralization)
- Four investigation phases (team, third-party intelligence, on-chain, tokenomics)
- Operational risk layer (off-chain operator, re-hypothecation, sub-asset cascade, NAV verification)
- Required report format, severity definitions, and confidence definitions

## Disclaimer

See [`DISCLAIMER.md`](./DISCLAIMER.md). Short version: this is research, not investment advice. Findings are based on public information as of each report's date. Claims, inferences, and verified facts are labeled distinctly.

## License

MIT — see [`LICENSE`](./LICENSE). Attribution appreciated if you reuse the methodology.
