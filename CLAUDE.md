# wispr-flow-linux worker - Development Notes

This repo is the Cloudflare Worker at `pkg.wispr-flow-linux.dev`: it passes APT
and DNF metadata through from the main repo's `gh-pages` branch and
302-redirects `.deb` and `.rpm` requests to that repo's GitHub Release assets.

```bash
wrangler dev      # local; try a .deb, an .rpm and a dists/ path
```

## Required reading

- [`README.md`](README.md) for the request-to-release mapping.
- The main repo's
  [`docs/learnings/apt-worker-architecture.md`](https://github.com/wispr-flow-linux/wispr-flow-linux/blob/main/docs/learnings/apt-worker-architecture.md),
  [`RELEASING.md`](https://github.com/wispr-flow-linux/wispr-flow-linux/blob/main/RELEASING.md)
  (the tag scheme the Worker reverses) and
  [`MAINTAINING.md`](https://github.com/wispr-flow-linux/wispr-flow-linux/blob/main/MAINTAINING.md).

## Rules that bite

- **A merge to `main` is a production deploy** (`deploy-worker.yml`), and
  every APT/DNF user goes through this Worker. Nothing merges without the
  maintainer's yes.
- The filename regexes in `src/worker.js` must stay in step with the package
  names the main repo's makers produce (`scripts/packaging/`) and the
  `v<repoVer>+wispr<wisprVer>` tag scheme. A change to either side changes
  both.
- Fetch metadata from `raw.githubusercontent.com`, not the github.io Pages
  URL; the Pages custom-domain redirect loops back through the Worker.
- The Worker only redirects binaries; it must never proxy package bytes.
- The daily `apt-repo-heartbeat` in the main repo is the end-to-end check.
  A red heartbeat after a deploy here is this repo's problem first.

## Issues, PRs, and commits

Same conventions as the main repo: short and plain, evidence in the commit
body. AI-assisted PRs end with a
`Co-Authored-By: Claude <model> <noreply@anthropic.com>` trailer; commits
carry `Co-Authored-By: Claude <claude@anthropic.com>`.
