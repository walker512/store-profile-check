# A Narrow Comparison: Preserve Differences Between Chinese Store Names

Direct baseline: [Citewatch / local-seo-citation-tracker-mvp](https://github.com/bensblueprints/local-seo-citation-tracker-mvp), fixed commit `dfb6f5df5e1ff190bd33378ac772c010f0f433bd`. Reviewed on 2026-11-16.

## Identical inputs

The Chinese strings below are intentionally preserved as input examples, because the distinction being checked depends on their characters.

| Field | Baseline | Observed | Our executed result |
| --- | --- | --- | --- |
| Store name | 青山书店 | 海岸书店 | `different`, needs review |
| Address | 青山路1号 | 海岸路1号 | `different`, needs review |
| Phone formatting | 010-00000000 | ０１０－００００００００ | Formatting only, not an unresolved action |

Our implementation preserves Chinese characters and applies Unicode NFKC plus limited whitespace normalization. Phone comparison additionally ignores spaces, ASCII parentheses, and hyphens. Internal automated tests verified these results.

The competitor's [fixed normalize.js](https://github.com/bensblueprints/local-seo-citation-tracker-mvp/blob/dfb6f5df5e1ff190bd33378ac772c010f0f433bd/server/normalize.js) retains only English letters, digits, whitespace, and apostrophes for names; its address normalization also removes Chinese characters. Both names above therefore become empty strings, and both addresses retain only the digit `1`. When original values differ but normalized values match, its `compareField` returns `formatting`.

**Supported conclusion:** compared with that fixed version, this tool preserves the differences requiring human review in these Chinese-name/address cases. This does not establish which record is correct.

## Evidence limits and missing capabilities

Our tool executed original test cases. The competitor comparison is a fixed source-path review, not a run of its entire Electron/Express application. There was no speed or complete-feature benchmark. This is not proof of overall superiority or uniqueness.

Citewatch already supports multiple businesses, directory templates, automated tasks, and optional platform integrations. This tool does not reproduce that full feature set. Its scope is manual, multi-source review for one store: Chinese character preservation, evidence dates, documented exceptions, recoverable projects, and CSV action lists.

US address abbreviations, equivalent opening hours, international phone numbers, and website redirects are not inferred. This may increase manual review.

No search-ranking, AI-visibility, business-outcome, or paid-demand claim has been validated. The tool uses no WeChat API, scrapes no third-party data, and does not modify platform information.
