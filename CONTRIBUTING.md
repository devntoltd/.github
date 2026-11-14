# Contributing

This is the default contributing guide of every repository of the organization that has none of its own. Thank you for helping.

## Before you start

- Read the repository's README, and its own `CONTRIBUTING.md` if it has one: they say what the repository does, how to set it up and how to run its checks, and they take precedence over this guide. Where a repository documents no local checks, its checks run on the pull request.
- Search the existing issues. For anything larger than a small fix, open an issue first and agree on the approach there, so the work is not wasted.
- A security problem is never an issue or a pull request: follow the [security policy](https://github.com/devntoltd/.github/blob/main/SECURITY.md).

## Making a change

- Work on a branch (from a fork, if you cannot push to the repository) and open a pull request against the default branch; nothing is committed to it directly.
- Keep a pull request to one change, and link the issue it closes.
- New or changed behavior comes with a test that failed before the change.
- Update the documentation in the same pull request when the change affects what it describes.
- Every check of the pull request must pass, and a maintainer reviews and approves it before the merge.
- Everything committed is in English: code, comments, documentation, commit messages.

## Secrets

Never commit a secret: a password, token, key or connection string. A secret that reached a commit is revoked and rotated first, even if the commit was never pushed: removing it from the history does not make it safe again.

## Conduct

Everyone taking part follows the [Code of Conduct](https://github.com/devntoltd/.github/blob/main/CODE_OF_CONDUCT.md).

## Questions

See [Support](https://github.com/devntoltd/.github/blob/main/SUPPORT.md).
