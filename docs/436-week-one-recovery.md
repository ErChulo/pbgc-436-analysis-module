# §436 generator: week-one recovery plan (v0.3.0)

## Existing project
- Repository: `ErChulo/pbgc-436-analysis-module`.
- Preserve `436 Analysis Memo/436-webapp/pbgc-436-webapp-v0.2.0/` and `aftap-table-legacy/` as historical work. Neither is actuarially validated.
- The v0.2.0 application only collects a memo header, creates empty AFTAP arrays, and relies on external CDNs. It is **not** a compliant offline final generator.
- The legacy AFTAP HTML uses simplified late/missing-certification and restriction rules that must **not** be transplanted into production.

## Usable first increment
Open `release/436-intake-v0.3.0.html` via `file://` in a current browser without a server. It does not need a network connection. It:
1. Collects case header and initial §436(b), (c), (d), (e) screening with supporting document references.
2. Imports typed CSV rows pasted into two text areas: the AFTAP certification inventory and user-substantiated effective periods.
3. Checks dates, basic field formats, missing annual entries, period gaps and overlaps, and provenance omissions.
4. Shows only **possible** AFTAP funding threshold bands, not definitive legal restrictions.
5. Exports a portable case JSON and working-draft text. JSON can be re-imported.
6. Does not store anything remotely, use actual participant data, change official templates, or approve conclusions.

**Important:** It does not yet calculate §436(h) presumptions or fill the official DOCX. It is an intake/QA assistant, NOT a finished Section 436 determination or fully functional DOCX generator. Continue using the official memo template for actual deliverables until independently verified generation is complete.

## Case records to gather
**Initial, always:** case number, plan name, DOPT, plan-year first day, plan adoption and freeze dates, plan provisions and amendment history, relevant benefit forms, full relevant AFTAP history (prefer signed dated certificates; include original, range, amended, recertified and late certifications, with document/IPS locators), and AVR/Form 5500 Schedule SB evidence for corroboration and missing years.

**Conditional:**
- §436(b): shutdown/UCEB triggering event, relevant plans and affected group, dates and payments.
- §436(c): liability-increasing amendment's adoption and effective dates, nature/exception, evidence of application.
- §436(d): optional accelerated forms and paid/unpaid elections; ASD, BCD if retroactive, check register, lump-sum or bifurcated distributions, bankruptcy periods, certified 100% AFTAP where relevant.
- §436(e): accrual, freeze, resumption and restoration periods; §204(h) notices; affected groups.
- CBA ratification/effective/expiration dates and special transition rules; unusual §412(e)(3) conversions; §436 specific contributions, elections, and funding relief.
- Redacted participant-level records only for exceptional affected-benefit investigations; never commit PII or sensitive case material.

## Governing materials
- Official PBGC `436 Evaluation (ASTD Updates Nov 2025).docx` (five parts; precise template styles and layout must be preserved).
- PBGC internal guidance `Benefit Limitations Under PPA 2006 - Section 436` (source of procedure and PBGC case handling).
- IRC §436 and 26 CFR §1.436-1, including §1.436-1(g)–(h), (k), historical transitional/relief provisions.
- Case-specific original certified documents, AVR/Schedule SB, plan and sponsor records.
- **Do not commit** the internal PBGC Book of Job, case evidence, or populated case exports to this public repository.

## Subsequent acceptance gates
1. **Presumption engine (critical):** validated, effective-dated computation of the first-day/prior-year, fourth-month and tenth-month presumed AFTAP, with late/range/material recertification rules and historical relief. Reference cases and synthetic fixtures must be independently checked against 26 CFR §1.436-1 and PBGC guidance. No arbitrary substitution of "59%" or unrestricted pending-certification periods.
2. **Events and effects:** §436(b),(c),(d),(e) determinations depend on benefit availability, applicable dates, bankruptcy, exceptions and actual plan administration; do not infer solely from an AFTAP threshold.
3. **Exact template output:** generate the current five-part official DOCX without reformatting, append source citations and unresolved flags, omit Parts 2–4 only when every Part 1 screening is supported as No/N/A. If a limit affects post-DOPT payable benefits, flag Ask ASD ATR concurrence.
4. **Offline certification:** verify `file://` under actual PBGC Windows browser and build with no CDN, external requests, server or installation.
5. **Tests:** run golden-file, boundary, gap/overlap, late and range certification, 2008–2010 and 2020 relief, CBA, 412(e)(3), sponsor-bankruptcy and no-certification synthetic tests.
6. **Audit:** human actuarial sign-off and provenance for every derived effective period and material judgment.

## Pre-merge manual smoke test
1. Download the standalone HTML from this branch and open it by double-clicking the file without network access.
2. Using **synthetic data only**, enter a valid eight-digit case number, DOPT, four screening answers and a sample AFTAP period.
3. Select Validate; confirm that a missing source, missing year, gap and overlapping period each produce findings.
4. Download JSON, re-import it, and verify all fields are restored.
5. Download draft TXT; verify all five labeled parts and an explicit unapproved status.
6. Inspect network activity to confirm zero external requests.

Status: **draft prototype**, pending workstation/browser test and independent actuarial validation.
