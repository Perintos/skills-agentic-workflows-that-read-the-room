---
name: update-github-info
description: Draft GitHub Info site updates for Mona from official GitHub sources.
on:
  workflow_dispatch:
  schedule: daily
permissions:
  copilot-requests: write
  contents: read
  issues: read
  pull-requests: read
strict: true
tools:
  github:
    toolsets: [default]
  edit:
  web-fetch:
safe-outputs:
  steer: true
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
    fallback-as-issue: false
  noop:
network:
  allowed:
    - github
---

# Update Mona's GitHub Info website

Read `notes/mona-notes.md` before making changes.

Use GitHub repository API tools to read repository files instead of terminal, CLI, or sandboxed commands.

Use these sources:
- `notes/mona-notes.md`
- GitHub Blog: https://github.blog/latest/
- GitHub Changelog: https://github.blog/changelog/

Update `site/content/github-info.md` with concise, practical updates that help developers learn GitHub faster.

When content comes from the GitHub Blog or GitHub Changelog, include source links and dates in the updated page.

If no relevant update is needed, use `noop`.

Open a pull request for Mona to review.
Do not write directly to `main`; rely on `safe-outputs` with `create-pull-request`.
