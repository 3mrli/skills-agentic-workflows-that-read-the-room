---
name: update-github-info
description: Keep the GitHub information page current from official GitHub sources.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
  pull-requests: read
engine: copilot
tools:
  edit:
  web-fetch:
  github:
    toolsets: [repos]
network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    reviewers: [mona]
    draft: true
    max: 1
---

# Update GitHub Information

Read `notes/mona-notes.md` for repository and editorial guidance.

Use `web-fetch` to read these official public sources:

- https://github.blog/latest/
- https://github.blog/changelog/
- https://awesome-copilot.github.com/workflows/

Use GitHub repository API tools for repository guidance and reference files. Do not use terminal, CLI, or sandboxed commands for GitHub API reads.

Update `site/content/github-info.md` with accurate, concise information based on the sources and repository guidance. Preserve the existing structure and writing style, and make no unrelated changes.

When the content needs updating, use the edit tool and then use the `create-pull-request` safe output to open one draft pull request for Mona to review. Include a concise summary of the changes and the official sources consulted in the pull request body. Do not write directly to the default branch. If no update is needed, do not open a pull request.