# Publishing a legacy (v2 line) security release — k8s library

This Go library belongs to the legacy KubeMQ v2 line: security and critical fixes only.
End of life is 12 months after KubeMQ next v1.0.0 general availability (18 September 2027).

This repository publishes **one artifact: a semantic-version git tag**. There is no
container image, no chart and no moving tag.

## Steps

1. Bump `VERSION:` in `Taskfile.yml` (patch bump, e.g. `v1.12.1` -> `v1.12.2`).
   Note: the `VERSION:` value in `Taskfile.yml` may lag the latest git tag; check
   `git tag --sort=creatordate | tail` first.
2. Run `task test`.
3. Run `task release` (runs `commit-modifed`, then `tag`:
   `git tag -a {{.VERSION}} -m {{.VERSION}}` and `git push origin master --tags`).
4. Push with the `kubemq` GitHub account.

## Rules

- Semantic-version tags only (for example `v1.12.2`). Never create or move a tag named
  `next` or `latest`.
- No other artifacts are published from this repository.
