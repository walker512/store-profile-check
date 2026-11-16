# StoreProof

## Store Profile Consistency Checker

An experimental v0.2 offline tool for manually reviewing store information. Compare collected records field by field against a baseline you have checked, while retaining evidence, dates, and review notes. No dependencies or API keys. The application interface remains in Simplified Chinese. MIT licensed.

**This is not a WeChat or Xiaowei platform scanner, a search-ranking monitor, or an AI-visibility measurement tool.** It does not connect to platforms, scrape, edit, or verify live listings. A difference is not necessarily an error, and your baseline is not certified fact.

## Start locally

Download and extract the complete repository ZIP. In the directory containing `index.html`, run:

```sh
python3 -m http.server 8000 --bind 127.0.0.1
```

On Windows with Python Launcher installed, use `py -3 -m http.server 8000 --bind 127.0.0.1`. Open `http://127.0.0.1:8000`; stop the server with Ctrl+C when finished. Do not serve a parent directory containing private files. Python only serves local static files; no paid endpoint or account is required.

A downloaded and extracted copy has been tested in real Chromium over localhost on the cloud computer. Direct `file:///` opening has not been verified.

## Complete a review

1. Start with the blank form. Enter an analysis date, review interval (1-365 days), and the store baseline you have checked.
2. For each source, enter a unique name, manual observation date, evidence URL or note, and the five observed fields. Evidence is stored as text and is not opened automatically.
3. Generate the report. Review missing or different values, stale sources, and the original field text. Do not treat the report as verified platform facts.
4. If you manually confirm a difference is an acceptable exception, record the reason. The exception remains visible and is included in CSV; **it does not pretend the platform was changed**. A change to the baseline, observed value, or observation date invalidates the earlier review.
5. Download a CSV action list or JSON report. Save a project to preserve all inputs and review history for later restoration. A report is not a recoverable project file.

Creating a new project or loading an example replaces unsaved input. Save first. Closing the page discards unsaved data. All examples are fictional.

## Rules and boundaries

- Fields: store name, address, phone number, opening hours, and website.
- Chinese characters are preserved. Normalization uses Unicode NFKC, trims surrounding whitespace, and collapses repeated whitespace. Phone comparison additionally ignores spaces, ASCII parentheses, and hyphens.
- Country codes, US address abbreviations, equivalent opening hours, redirects, and Simplified/Traditional aliases are not inferred. Formatting differences may still need human judgment.
- Missing data is explicitly marked. A missing or entirely blank baseline cannot produce a report, so unknown information is not silently treated as correct.
- Review age is calculated from the manually entered analysis and observation dates. There are no background reminders.
- One store per project; at most 200 sources, 500 characters per field, and 1,000 review-history records.
- Project save and restore share a **500,000 UTF-8 byte** limit. Saving checks the complete serialized file. Non-ASCII characters commonly use multiple bytes.
- CSV export prefixes formula-like text with an apostrophe to reduce spreadsheet formula execution. JSON projects preserve the original text. HTML-like input is displayed as text.

## Privacy

No network requests, tracking, automatic local persistence, or third-party dependencies. Only selected project files are read; you trigger downloads. Projects, reports, and CSV files may contain business information. Store them securely and do not upload private records or original customer files to public issues.

## Verification

**63 internal automated tests passed**, covering rules, Chinese text, dates, invalidated reviews, UTF-8 boundaries, and 19 minimal-DOM workflow simulations. Simulated tests are not browser acceptance. Test scripts and dedicated fixtures are not included in the public package.

A ZIP was downloaded and extracted, then tested in real Chromium over localhost on the cloud computer. Checks covered Chinese information across multiple sources, invalidation after reviewed data changed, saving followed by closing and restoring, CSV/report downloads, and 1180 px / 400 px layouts.

Direct `file:///` opening, physical phones, and other browsers remain unverified. The 400 px check is a narrow browser window, not a physical-phone test.

## Comparison, contributions, and license

[COMPARISON.md](COMPARISON.md) describes a Chinese-character scenario using the source code of a fixed competitor version. It is not a claim of overall superiority or a complete side-by-side application benchmark.

Report false positives and edge cases with redacted minimal examples. Do not add API-key requirements, telemetry, or unverified ranking promises.

MIT; see [LICENSE](LICENSE).
