# Daily automation

## Automated daily updates

`.github/workflows/daily-update.yml` runs once each day at `03:17 UTC` (the
cron schedule is evaluated in UTC). It creates a random total of **2 to 5**
automated repository-maintenance commits in one workflow run. Each commit adds
one timestamped Markdown line to `daily-log.md`, then all of those commits are
pushed together to the default branch. Scheduled workflows run from the
default branch. GitHub Actions scheduling can be delayed, so a scheduled run
may not start at exactly 03:17.

To test it, open the repository's **Actions** tab, select **Daily automated
update**, choose **Run workflow**, and click **Run workflow**. After it
finishes, inspect the workflow log and the default branch history: each run
will have 2–5 separate commits named `chore: daily automated update N/T`, and
`daily-log.md` will have one corresponding timestamped line per commit.

Before enabling the workflow, edit the two `git config` lines in
`.github/workflows/daily-update.yml`: replace `Axinion` with
`YOUR_GITHUB_USERNAME` if needed, and replace `mihirpaddy@gmail.com` with
`YOUR_GITHUB_NOREPLY_EMAIL`. The email must be verified on that GitHub account;
the preferred value is the GitHub-provided noreply address shown under
**GitHub Settings → Emails**. Also enable **Read and write permissions** at
**Repository Settings → Actions → General → Workflow permissions** so the
automatically provided `GITHUB_TOKEN` can push. These are automated repository
maintenance commits, not manual coding contributions.
