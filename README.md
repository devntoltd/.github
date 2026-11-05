# .github

Organization-wide files of devntoltd.

- `.github/workflows/org-checks.yml`: the organization checks (workflow lint, secret scan) that the organization ruleset requires on every pull request of every repository. It is a copy of [`00-github/org-checks.yml`](https://github.com/devntoltd/cenytu-bootstrap/blob/main/00-github/org-checks.yml): change it there first, copy it here by a pull request, then put the merge commit in `00-github/github.json` and run `00-github`.
- `SECURITY.md`: the default security policy of every repository of the organization.
