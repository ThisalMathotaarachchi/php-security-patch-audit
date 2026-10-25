# Literature and Source Review

**Status:** Initial source list; not a completed literature review.

## PHP2Shell primary/technical sources

1. PHP official security advisory (21 Oct 2026): https://www.php.net/archive/2026.php#2026-10-21-5
   - Primary source for affected components, vulnerability summaries, and fixed releases.
2. PHP 8.5.12 release announcement: https://news-web.php.net/php.announce/513
   - Confirms the security release and recommends upgrading.
3. Wiz Research: https://www.wiz.io/blog/php2shell-php-rce
   - Describes the AI-assisted research context and discovery timeline. Treat vendor claims as attributed claims and cross-check details.
4. JFrog Security Research: https://research.jfrog.com/post/php2shell-all-you-need-to-know-about-cve-2026-109618-and-cve-2026-109619/
   - Independent technical explanation of the two vulnerability paths.
5. Red Hat security advisory: https://access.redhat.com/security/vulnerabilities/RHSB-2026-013
   - Downstream vendor impact and remediation context.

## Literature review questions

- What benchmarks already evaluate LLM/agent vulnerability discovery from source code?
- What benchmarks evaluate patch correctness or regression-test generation for security fixes?
- Are PHP-specific vulnerability datasets already available, and what do they measure?
- What parts of this protocol would duplicate existing work?
- Which metrics are validated in prior studies, and how is reviewer agreement reported?

## Integrity rule

Do not call the topic novel until these questions are investigated. Record each search query, date, inclusion/exclusion decision, and relevant paper in a literature matrix.
