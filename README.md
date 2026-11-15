# Coder-Shell

Container image for the OpenCode shell used by the Coder bot.

## Commit identity guard

Native config-based hooks require Git 2.54 or newer, so the image installs Git
2.56.1 from the `git-core` PPA.

When `GIT_USER_NAME` and/or `GIT_USER_EMAIL` are set, the image installs a
global native Git hook (`hook.verify-commit-identity`) for the `pre-commit`
event. It rejects commits whose effective author or committer name/email does
not match the set values. Each variable is enforced independently, so an unset
variable is not checked. Repository-local hooks still run alongside the global
hook, and `core.hooksPath` is not modified.

The guard does not apply to `git commit --no-verify`, to `--author` overrides,
or to commits created by commands that do not run the `pre-commit` hook (for
example `cherry-pick`, `rebase`, and `commit-tree`).
