# MailCleanup Email Verification Data

Public datasets from two MailCleanup studies: a 12-month single-client list-decay benchmark, and a cross-client email verification statistics report.

## What's here

### `decay/` — Email List Decay Study

One anonymized client's ~1,000,000-address list, re-verified monthly for 12 months (Sept 2025–Aug 2026). Tracks the 912,317 addresses that were Deliverable at first verification, and what happened to them over the following year.

- `monthly_decay.csv` / `decay.json` — deliverable count and cumulative decay %, read monthly
- `quarterly_decay.csv` — the same data rolled up by quarter, showing the decay rate itself rising each quarter
- `decay_causes.csv` — why decayed addresses failed (mailbox deleted, disabled, domain expired, etc.)
- `first_cleaning_composition.csv` — how the original ~1,000,000-address list broke down on its first verification pass. Context only, not a decay figure: this is a different population (the full original list) than the tracked cohort in the other files (just the addresses that started Deliverable), so it isn't comparable to them directly.
- `cohort_first_vs_last.csv` — the tracked cohort's status at the start and end of the 12 months

Full write-up and methodology: https://mailcleanup.com/email-list-decay/

### `verification-stats/` — Email Verification Statistics

Cross-client result shares and detection rates from MailCleanup's verification pipeline, for two periods: a rolling 12-month window and a more recent 2-month sample. This is a different kind of data from `decay/`: many different lists at a point in time, not one list tracked over time.

- `annual_summary.csv` / `recent_2month_summary.csv` — Deliverable / Undeliverable / Accept-All / Unknown as a share of total verified
- `annual_detection_rates.csv` / `recent_2month_detection_rates.csv` — role-based, disposable, and syntax-error rates per 1,000 addresses; spam-trap rate per million
- `annual_ratios.csv` / `recent_2month_ratios.csv` — deliverable-to-undeliverable and deliverable-to-risky ratios
- `verification-stats.json` — all of the above, combined

Full write-up and methodology: https://mailcleanup.com/email-verification-statistics/

## Important: don't combine the two folders

`decay/` follows one client's same list over time. `verification-stats/` aggregates many different clients' lists at a point in time, with no single list held constant. They measure genuinely different things. Don't average, sum, or cross-reference a figure from one against a figure from the other in the same claim.

## What's not included

Absolute total-emails-verified counts for the `verification-stats/` period (the denominator behind the percentages) are withheld from this release pending internal review. The percentages and rates themselves are unaffected and complete as published.

## License

Released under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) — free to use, share, and adapt, with attribution.

Suggested citation:

> MailCleanup, "Email List Decay Report 2026" and "Email Verification Statistics 2026," https://mailcleanup.com

## Source

Compiled by [MailCleanup](https://mailcleanup.com), a bulk email verification and list-cleaning service.
