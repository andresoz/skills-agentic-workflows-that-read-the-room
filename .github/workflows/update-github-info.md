---
name: update-github-info
description: Keep Mona's GitHub Info page current with practical, source-backed updates.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
strict: true
network:
  allowed:
    - github.blog
    - github.com
tools:
  edit:
  web-fetch:
  github:
    toolsets: [repos]
safe-outputs:
  create-pull-request:
    max: 1
    allowed-files:
      - site/content/github-info.md
    title-prefix: "[mona] "
    reviewers:
      - mona
  noop:
---

# Update GitHub Info

Keep Mona's GitHub Info page current with concise, practical guidance for developers.

## Task

1. Read `notes/mona-notes.md` and `site/content/github-info.md` before making changes.
2. Use the GitHub repository API tools to read repository guidance or reference files when needed. Do not use terminal, CLI, or sandboxed shell commands for those reads.
3. Fetch and review both official sources:
   - https://github.blog/latest/
   - https://github.blog/changelog/
4. Identify useful, recent updates that fit Mona's editorial angle. Keep summaries short and practical, and cite the source URL for every update.
5. Edit only `site/content/github-info.md`. Preserve its existing structure and avoid duplicating information already present.
6. When the page needs a source-backed update, use the configured `create-pull-request` safe output to open one pull request targeting `main` for Mona to review. Include a concise summary and the source links in the pull request body.
7. If no source-backed update is appropriate, or if the sources cannot be fetched, use `noop` with a short reason and make no edits.

Do not write directly to `main`, modify any other file, or use direct GitHub write APIs.