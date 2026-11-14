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

## Changing this repository

`CONTRIBUTING.md` here is the default of every repository; what applies to this one only is in this section. A change goes through a pull request; `.github/workflows/ci.yml` checks the files on every pull request, and the organization checks (workflow lint, secret scan) run as everywhere.

Setup, once per clone:

```powershell
winget install EditorConfig-Checker.EditorConfig-Checker lycheeverse.lychee Betterleaks.Betterleaks
git config --local core.hooksPath .githooks   # the pre-commit hook scans the staged changes for secrets
```

Markdown lint needs Node.js, the issue forms check Python with pipx. VS Code offers the recommended extensions (`.vscode/extensions.json`) when the folder is opened; the YAML extension checks the issue forms while typing.

The checks, as CI runs them; in VS Code **Terminal → Run Task…** has each, and **Ctrl+Shift+B** runs *All checks*:

```powershell
editorconfig-checker                      # every file against .editorconfig; must print nothing
npx markdownlint-cli2@0.23.3              # must report 0 issues (config: .markdownlint-cli2.jsonc)
lychee --offline --include-fragments --remap "https://github\.com/devntoltd/\.github/blob/main/(.*) $(([uri]$PWD.Path).AbsoluteUri)/`$1" './**/*.md' './.github/**/*.md'   # links to files of this repository and their anchors
pipx run check-jsonschema==0.39.0 --builtin-schema vendor.github-issue-forms .github/ISSUE_TEMPLATE/bug-report.yml .github/ISSUE_TEMPLATE/feature-request.yml
pipx run check-jsonschema==0.39.0 --builtin-schema vendor.github-issue-config .github/ISSUE_TEMPLATE/config.yml
betterleaks git --redact --verbose .      # secrets in the full git history
```

A link in these files is absolute, since every repository shows it; the links check reads a link to a file of this repository (`https://github.com/devntoltd/.github/blob/main/...`) from the working tree, so a new file or anchor is checked before the merge. Other external links are not checked. The versions are those of `ci.yml`; Dependabot updates only the actions, so a tool version is raised by hand in `ci.yml`, `.vscode/tasks.json` and here together.
