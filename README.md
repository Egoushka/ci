# ci

Reusable GitHub Actions workflows for the repos of Egoushka: `dotnet`, `node`, `go`, `python`, `rust`
(`.github/workflows/<stack>.yml`, `on: workflow_call`).

A repo does not copy them. Its `stack` in the workspace manifest (`repos.toml`) selects one, and `ws repos apply`
renders a thin caller (`.github/workflows/ci.yml`). A pull request from the owner is gated by the `fast-tier` status;
these jobs run on fork and bot PRs, on `workflow_dispatch` (the merge train) and on the nightly run.

Call one by hand:

```yaml
jobs:
  ci:
    uses: Egoushka/ci/.github/workflows/node.yml@v1
    with: { node-version: "22" }
```

Check: `gh workflow list -R <repo>` shows `ci`; the caller's run starts the `<stack>` job of this repo.

MIT, see `LICENSE`.
