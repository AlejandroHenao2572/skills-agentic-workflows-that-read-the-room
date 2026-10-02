---
name: update-github-info
engine: copilot
model: gpt-4.1
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
2. Use the GitHub repository API tools to read repository guidance or reference files when needed. Do not use terminal, CLI, or sandboxed commands for that repository guidance.
3. Review `site/content/github-info.md`.
4. Update `site/content/github-info.md` with one concise, practical item about agentic workflow automation and safe pull requests. Cite these official references inline: `https://github.github.com/gh-aw/`, `https://github.blog/latest/`, and `https://github.blog/changelog/`.
5. Always make this small source-backed editorial update; do not use `noop` merely because external fetching is unavailable. The source URLs above are the citation context for the update.
6. Use the edit tool to update only `site/content/github-info.md`.
7. Use the `create-pull-request` safe output to open a draft pull request for Mona. The pull request body must explain the change and include the cited source URLs.
8. Do not write directly to the default branch.