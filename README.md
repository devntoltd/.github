# .github

Organization-wide files of devntoltd.

| File | What |
| --- | --- |
| `.github/workflows/org-checks.yml` | The organization checks (workflow lint, secret scan) that the organization ruleset requires on every pull request of every repository |
| `SECURITY.md` | The default security policy |
| `CONTRIBUTING.md` | The default contributing guide |
| `CODE_OF_CONDUCT.md` | The default code of conduct (Contributor Covenant 2.1) |
| `SUPPORT.md` | The default support page: where to ask what |
| `.github/ISSUE_TEMPLATE/` | The default issue forms (bug report, feature request) and the contact links of the "New issue" chooser |
| `.github/PULL_REQUEST_TEMPLATE.md` | The default pull request template |
| `profile/README.md` | The organization profile shown on <https://github.com/devntoltd> |

## How the defaults work

GitHub shows a default file in every repository of the organization that has no file of its own of the same kind. It replaces the whole file, never merges: a repository with its own `.github/ISSUE_TEMPLATE/` shows none of the organization's forms. Links in these files are absolute, since the same file is shown in every repository. The forms use only the labels `bug` and `enhancement`, which every new repository has.

This repository is public, as GitHub requires for the defaults: nothing internal goes here.
