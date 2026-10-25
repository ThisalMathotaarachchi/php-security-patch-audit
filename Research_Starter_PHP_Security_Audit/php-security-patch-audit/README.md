# AI-Assisted Security Patch Audit for PHP

An independent, reproducible research project investigating whether AI coding agents can identify root causes and propose useful regression tests for real PHP security fixes.

## Status

Research plan only. No experiments have been run and no findings are claimed.

## Research question

**How reliably can AI coding agents identify the root cause of real PHP security fixes and propose regression tests that capture the underlying defect, using only the vulnerable source code and relevant context?**

## Case study

PHP2Shell (CVE-2026-109618 and CVE-2026-109619), disclosed on 21 October 2026. These are critical PHP runtime vulnerabilities involving abnormal request termination and memory corruption. This project studies source changes and safe tests, not live exploitation.

## Why this is a research project

The project will use a curated set of PHP security-fix commits, a documented task prompt, a scoring rubric, repeated trials, and a held-out case. The PHP2Shell patches can serve as a recent case study, but they cannot by themselves establish general performance. Claims of novelty must wait until a literature and prior-benchmark review is completed.

## Safety boundaries

- Do not test public or third-party systems.
- Do not build or publish weaponized exploit chains.
- Prefer source-level analysis, patch review, static checks, and regression-test quality.
- If any runtime testing is later needed, use a disposable isolated environment with no public network access.

## First milestone

1. Read the official PHP advisory and one independent technical analysis.
2. Record the exact research question and inclusion criteria in `research/protocol.md`.
3. Collect candidate security-fix commits; do not run an agent until the dataset and scoring rubric are frozen.
4. Create the GitHub repository and publish the research plan with explicit status: planned, not yet tested.

## Primary sources

- PHP official 2026 security advisory: https://www.php.net/archive/2026.php#2026-10-21-5
- PHP 8.5.12 release announcement: https://news-web.php.net/php.announce/513
- Wiz PHP2Shell analysis: https://www.wiz.io/blog/php2shell-php-rce
- JFrog technical overview: https://research.jfrog.com/post/php2shell-all-you-need-to-know-about-cve-2026-109618-and-cve-2026-109619/

## Proposed repository structure

- `research/protocol.md`: research question, sampling, procedure, metrics, and limitations
- `research/literature.md`: related work and overlap review
- `research/decision_log.md`: dated decisions and changes
- `data/`: manifest of selected public fix commits and metadata (no exploit payloads)
- `results/`: raw outputs and analysis only after experiments are run
- `src/`: evaluation and scoring scripts
