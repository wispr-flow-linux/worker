# Contributing

This repo holds the Cloudflare Worker in front of pkg.wispr-flow-linux.dev for the unofficial
[Wispr Flow for Linux](https://github.com/wispr-flow-linux/wispr-flow-linux)
port. The main repo's
[CONTRIBUTING.md](https://github.com/wispr-flow-linux/wispr-flow-linux/blob/main/CONTRIBUTING.md)
applies here: what we accept, the pull request policy, maintainer edits, and
AI attribution.

- **Using Wispr Flow on Linux and something broke?** File it in the
  [main repo](https://github.com/wispr-flow-linux/wispr-flow-linux/issues/new/choose)
  with your `wispr-flow --doctor` output, even if the fix lands here.
- **Have a fix for this repo?** Open a PR against `main` and link the
  main-repo issue (`Refs wispr-flow-linux/wispr-flow-linux#123`).
- **Security concern?** Follow the main repo's
  [SECURITY.md](https://github.com/wispr-flow-linux/wispr-flow-linux/blob/main/SECURITY.md).

There is no CI on PRs here, and a merge to `main` deploys to production. Say
in the PR which request paths you checked (a `.deb`, an `.rpm` and a metadata
path) and how, for example with `wrangler dev`.

How this repo fits with the other three, and how it releases, is in
[MAINTAINING.md](https://github.com/wispr-flow-linux/wispr-flow-linux/blob/main/MAINTAINING.md).
