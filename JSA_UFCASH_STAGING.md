# J$A UFCash staging worker · 19 November 2026

**This is an isolated TEMPORARY branch for J$A MMA research.** The repository's default branch and video application are unchanged. Migrate this worker to its own public `jsa-ufcash-public-worker` repository when the owner creates that repository.

## Research-only, no paid services

- **Compute:** Standard GitHub-hosted `ubuntu-24.04` runner in a **public** repository. No self-hosted infrastructure, paid runners, subscriptions, payment accounts or API credits.
- **Source:** Official UFC Qatar event page via the existing read-only J$A endpoint: https://jsa-ai-trading-hq.vercel.app/api/ufc-reference-odds.
- **Event:** 2026-11-21, 7 publicly listed featured matchups; no invented bouts or bookmaker lines.
- **UFCash:** https://github.com/SolvAI/ufcash pinned to `c6b1e8233b172fde6e2dabb8757d351c1a4a5ede`; no GitHub secrets are passed to the model.
- **Odds:** UFC.com display references, *not* authenticated executable bookmaker prices or UFCash's actual opening lines.
- **Output:** `results/upcoming_predictions.csv`, checksum manifest, and public market snapshot as a one-day GitHub Actions artifact. No personal bankroll data or betting action.

### Running the worker

The first push of `.github/workflows/jsa-ufcash.yml` triggers the public branch's **push** workflow. Later use Actions → JSA UFCash public research staging → Run workflow (manual dispatch may require the workflow to be present on the default branch, so the push event is the supported activation mechanism in this temporary branch).

**No betting execution, account credentials, real-money transfers or profit guarantees.** UFCash models use external datasets whose licensing and freshness are independent from UFCash's MIT code. Because its trained model is loaded via `joblib`, the worker runs only in an ephemeral isolated GitHub runner with no elevated permissions.

If the UFC official page is blocked, the model or sources change, or Python dependencies cannot be installed, the workflow FAILS rather than publishing fabricated predictions.

Original source belongs to SolvAI and its respective data licensors. This J$A wrapper does not claim authorship of the model.
