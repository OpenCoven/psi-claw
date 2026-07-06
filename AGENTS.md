# AGENTS.md — psi-claw

Guidance for **AI agents** (Codex, Claude Code, and any familiar) opening pull
requests against this repo. See [`CLAUDE.md`](CLAUDE.md) for Claude-specific
notes; both share this file as the source of truth.

> `psi-claw` is a desktop agentic model workspace for PsiClaw (Next.js/TypeScript).

## Branch & PR workflow

- **Never push to `main`.** Every change lands via a PR with green CI. Branch
  from current `origin/main`.
- **Fresh branch per task**; use a worktree if multiple sessions may touch this
  repo:
  ```sh
  git fetch origin main
  git worktree add -b <branch> /tmp/psiclaw-<branch> origin/main
  ```
- Keep the diff scoped to one concern; conventional-commit subjects (`feat:`,
  `fix:`, `docs:`, `chore:`, `refactor:`).
- After merge: delete the remote branch, remove your local worktree/branch.

## Local checks before opening the PR

```sh
pnpm lint          # eslint
pnpm build         # next build must succeed
```

Fix lint/build failures; don't disable rules to get green.

## Attribution — credit contributors correctly

When you re-land or build on someone else's work (a fork PR, an issue author's
proposal, a co-author), **credit the human contributor with a working
GitHub-linked trailer** so they appear in the contributors graph and on their
profile:

```
Co-authored-by: Full Name <ID+username@users.noreply.github.com>
```

- Use the **numeric-id no-reply form**. Get the id with `gh api users/<login> --jq .id`.
- **Never** use a machine or `.local` email (e.g. `name@Someones-Mac.local`) in
  a co-author trailer — it links to no account and gives **zero** credit.
- When a squash-merge folds a contributor's PR into an internal branch, preserve
  their `Co-authored-by:` line in the squash commit message.
- Credit **people**, not AI tools.

## Secrets & safety

- Never commit secrets, tokens, or private emails. Use `*.noreply.github.com`
  for attribution.
- Don't disable CI gates or branch protection to land a change; surface the
  blocker instead.

---

<!-- BEGIN:nextjs-agent-rules -->
# This is NOT the Next.js you know

This version has breaking changes — APIs, conventions, and file structure may all differ from your training data. Read the relevant guide in `node_modules/next/dist/docs/` before writing any code. Heed deprecation notices.
<!-- END:nextjs-agent-rules -->
