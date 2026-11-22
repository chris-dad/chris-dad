# Chris (Cheung Kailun)

**I build the tooling that decides whether a backtest is allowed to be believed.**

A backtest is a claim about the future, written by me, on data I picked. That is not a reliable narrator. So I stopped polishing the number and started interrogating the narrator — including when the liar turned out to be my own code.

## Three times the audit turned on me

- **My options backtest was inflated by 36%.** A sign error in cash-settled put assignment had the seller *receiving* the buyer's intrinsic value — value created out of nothing, which violates zero-sum before you even look at a chart. Fixing it took the headline from `3.06x` to `1.94x`, and `1.17 BTC` — 62% of the old ending balance — turned out to be coins that never existed. I published the smaller number.
- **I pre-registered six gates for my own strategy improvement, then rejected it.** Four passed. Two failed: fold count `3/6` against a `>=4` requirement, and out-of-sample degradation of `19.7%` against an `11.7%` ceiling. 4 out of 6 is not a pass. The shipped baseline stayed untouched, byte for byte.
- **I turned the missing checks into open tooling — and froze the exam before writing the detectors.** A 38-sample acceptance corpus with a fixed answer key, so the tools are graded by the exam instead of the exam being rewritten to suit the tools.

## Two things to look at

**[`backtest-lint`](https://github.com/chris-dad/backtest-lint)** — guardrails for backtests that would otherwise lie to you.
*The pain it kills:* almost all backtest tooling helps you **compute** a result and almost none helps you decide whether the result is **allowed to be believed**. Four independent gates — code (AST, before anything runs), data, runtime holdout, statistics — with `cannot_determine` as a first-class verdict instead of a fake opinion.

**[`portfolio-track-record`](https://github.com/chris-dad/portfolio-track-record)** — a fingerprinted monthly record: content hashes, a correction log, no quiet edits.
*The pain it kills:* published numbers get silently revised, and nobody can prove what the page said last month. Here every revision is a new hash; the superseded version stays on the record.

## Background

MSc Financial Economics. In crypto since 2014 — long enough to have run mining rigs, and long enough to watch "obviously correct" models die in public.

## What I am looking for

Model validation and research governance roles — places where the job is to disbelieve a model on schedule and write down why. Also open to quant dev / crypto research where the same reflex is useful.

## Contact

Open an issue on any repository here — it reaches me directly, and it is the fastest channel.
Email available on request.

---

*None of this is a third-party audit. The code was reviewed against a written adversarial brief by a second agent on the same machine, under the same owner — a review, not certification. What survives is visible rather than asserted: fixes sit in the commit history, and the known limits of the detectors are documented in `docs/LINT-SPEC.md` §4 instead of being left for you to find.*
