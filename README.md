# ark-marketplace

The Ark Project's Claude Code plugin marketplace. One file,
`.claude-plugin/marketplace.json`, listing each Ark plugin at a pinned
release in its own repository. Nothing is vendored or built here.

## Install

```
claude plugin marketplace add jbarnes7952/ark-marketplace
claude plugin install cars@ark-project
claude plugin install commlink@ark-project
```

Plugins installed this way are copied into `~/.claude/plugins/cache` at the
pinned commit and move only on `claude plugin update <name>@ark-project`
after this catalog's pin changes. A maintainer working on a component repo
should keep installing from that repo's own directory marketplace, which
runs in place from the checkout.

## Pins

Each entry carries `version`, `ref` (the release tag) and the full commit `sha`; the sha is what is
checked out. The pins mirror `fleet.json` in the `ark` contracts repo, and
ark's test suite checks that they agree.

| Plugin | Repo | Version | Commit |
|---|---|---|---|
| cars | jbarnes7952/cars | 1.18.2 | c49ed7c |
| commlink | jbarnes7952/commlink | 0.4.3 | 68246c2 |

## Releasing a pin

1. The component maintainer merges and (where the repo tags) tags the release.
2. Edit the entry's `version`, `ref` and `sha` here on a `chore/<plugin>-<version>` branch, squash-merge.
3. Repin `fleet.json` in ark in the same pass.

## Validate

```
claude plugin validate .
```
