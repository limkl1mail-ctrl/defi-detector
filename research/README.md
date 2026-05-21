# Research Archive

Investigations are filed as `[Project Name] - [YYYY-MM-DD].md`. The date is the report's publication, not the project's launch.

Each report follows the structure defined in [`../METHODOLOGY.md`](../METHODOLOGY.md): Executive Summary → Team → Third-Party Consensus → On-Chain Findings → Red Flags Register → Unresolved Questions → Monitor → Data Sources.

---

## Highlight reports

The most useful entry points for a new reader. These were chosen because they illustrate distinct categories of finding that the methodology surfaces.

| Report | Category | What it surfaced |
| --- | --- | --- |
| _Theoriq Gold Vault_ | Multi-asset vault | CEO succession, ~91% TVL collapse, undisclosed Gold Vault contract address, December 2026 cliff |
| _YO Protocol_ | Yield aggregator | $3.71M loss from a centralized off-chain harvester (operational risk, not a contract bug) |
| _Canton Network_ | Institutional / permissioned chain | Parent company's prior ASX CHESS failure (~$250M, scrapped 2022) — context omitted from official communications |
| _Lighter DEX_ | Derivatives / perps | Pre-launch institutional pre-screen, with follow-up showing how the picture changed two months later |

_(Add relative links once reports are placed in this directory.)_

---

## Full archive

List reports in reverse chronological order. Suggested column structure:

| Date | Project | Type | Verdict | Confidence |
| --- | --- | --- | --- | --- |
| YYYY-MM-DD | [Project Name](./Project%20Name%20-%20YYYY-MM-DD.md) | Retail DeFi / Institutional / Stablecoin / … | Pass / Conditional / Fail | High / Medium / Low |

---

## How reports are curated

Not every internal investigation is published. A report appears here only if:

1. The subject is a public protocol with material TVL or attention (no point publishing on something nobody is asking about).
2. The findings are based on public information only — no privileged sources, no NDA material.
3. The report has been reviewed for: factual accuracy against cited sources, distinction between *verified* / *claimed* / *inferred*, and adversarial framing kept inside what the evidence supports.
4. Sensitive details (private notes, internal task lists, working drafts) have been stripped.

Drafts and unpublished material live elsewhere and are excluded by [`.gitignore`](../.gitignore).
