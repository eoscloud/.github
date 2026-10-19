# .github

Organization defaults for github.com/eoscloud: community health files, issue
forms, the pull request template, the organization profile and the shared
Renovate preset.

## Renovate

Repositories use the Mend Renovate GitHub App with this preset in their
`renovate.json`:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["github>eoscloud/.github:renovate-config"]
}
```

`github>eoscloud/.github:renovate-automerge` additionally merges minor, patch,
pin and digest updates once the required checks pass.

What `renovate-config` does:

- `config:recommended` with a dependency dashboard.
- Conventional commit messages, which the pull request title check requires:
  `chore(deps): ...` for all updates (dependency updates are maintenance and
  do not trigger a release), `fix(deps): ...` for security updates (they lead
  to a patch release).
- A `Signed-off-by` line in every commit, which the DCO check requires.
- `go mod tidy` after Go module updates.
- GitHub Actions stay pinned to commit SHAs with the version as a comment
  (`helpers:pinGitHubActionDigestsToSemver`).
