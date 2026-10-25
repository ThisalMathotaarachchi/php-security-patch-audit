# Draft Experimental Protocol

**Status:** Draft, not preregistered; no experiments run.

## Working title
AI-Assisted Security Patch Auditing: Evaluating Root-Cause Analysis and Regression-Test Quality on PHP Security Fixes

## Research question
How reliably can AI coding agents identify the root cause of real PHP security fixes and propose regression tests that capture the underlying defect, using only the vulnerable source code and relevant context?

## Scope
A source-level evaluation of PHP security-fix cases, with PHP2Shell (CVE-2026-109618 and CVE-2026-109619) as a recent motivating case. The study will not attempt live exploitation or claim to rediscover PHP2Shell.

## Hypotheses (tentative)
- H1: Agent outputs will often identify a broad vulnerability class but be less reliable at locating the specific faulty state transition or lifecycle condition.
- H2: Regression tests proposed by agents will vary in whether they test the underlying security invariant versus merely reproduce visible symptoms.
- H3: Providing surrounding code and project-specific test conventions will improve test usefulness but may not consistently improve root-cause localization.

These are hypotheses to test, not conclusions.

## Dataset plan
- Target 8–15 public PHP security-fix cases, subject to a feasibility and inclusion review.
- Include a case only when a public fix commit, enough pre-fix source context, and a credible advisory or maintainer description are available.
- Record CVE/advisory, affected component, fix commit, changed files, test added/changed, and ground-truth summary.
- Keep at least one case as a held-out evaluation case; avoid selecting only easy or well-documented cases.
- PHP2Shell may be held out if its patch and test structure permit a fair evaluation; this decision must be logged before running models.

## Procedure
1. Freeze the case manifest and rubric before agent runs.
2. For each case, provide only the vulnerable source/context and a standardized task; hide the patch, advisory, CVE identifier, and post-fix test from the model.
3. Ask the agent to (a) identify the suspected root cause and location, (b) state preconditions and impact, (c) propose a safe regression test, and (d) explain expected pass/fail behavior before and after a fix.
4. Run each configuration at least three times per case where feasible; save exact prompts, model/version, settings, timestamps, outputs, and failures.
5. Have two reviewers score outputs independently where possible; resolve disagreements and report inter-rater agreement.
6. Compare predictions against the withheld fix, maintainer test, and advisory. Do not execute exploit payloads.

## Metrics
- Root-cause class accuracy (categorical, rubric-defined)
- Faulty component/function localization (exact / nearby / incorrect)
- Root-cause explanation score (0–3)
- Regression-test quality score (0–4): targets invariant, distinguishes vulnerable/fixed behavior, reproducible, non-destructive
- Unsupported claims and false positives
- Completion rate, runtime, and token/cost data if available

## Threats to validity
- Public advisories and patches may be incomplete ground truth.
- PHP cases are not representative of all languages or vulnerability types.
- Model outputs are stochastic and versions change.
- Reviewer scoring can be subjective; independent scoring and a published rubric are important.
- Small sample sizes support exploratory conclusions, not broad claims about AI security performance.

## Stop/go criteria
Proceed only if at least 8 cases can be assembled with auditable public fixes and a safe evaluation procedure. If not, narrow the claim to an exploratory case study and state that limitation clearly.
