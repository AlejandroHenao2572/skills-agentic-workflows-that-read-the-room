---
name: update-github-info
engine: copilot
model: gpt-5.4
on:
  schedule: daily
  workflow_dispatch:

permissions:
  contents: read
  pull-requests: read

tools:
  github:
    toolsets: [repos]
  edit:
  web-fetch:

network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com

safe-outputs:
  create-pull-request:
    allowed-files:
      - site/content/github-info.md
    draft: true
    max: 1
---

# Update GitHub Info

Keep the GitHub Info website current with concise, practical guidance for developers.

## Instructions

1. Read `notes/mona-notes.md` before making any decisions.
2. Use the web-fetch tool to read `https://github.blog/latest/` and `https://github.blog/changelog/`.
3. Use the web-fetch tool to read `https://awesome-copilot.github.com/workflows/`.
4. Use the GitHub repository API tools to read repository guidance or reference files when needed. Do not use terminal, CLI, or sandboxed commands for that repository guidance.
5. Review `site/content/github-info.md` and identify only useful, current updates supported by the official GitHub Blog, Changelog, or Awesome Copilot workflows sources.
6. Use the edit tool to update only `site/content/github-info.md`. Keep summaries short and practical, preserve the existing editorial angle, and include the source for every new update.
7. When an update is warranted, use the `create-pull-request` safe output to open a draft pull request for Mona to review. Include a concise title and explain the source-backed changes in the pull request body.
8. Do not write directly to the default branch. If no worthwhile update is found, do not create a pull request.