---
name: injective-core-detect-changes
description: "Detect breaking changes in in Injective core between two tagged releases. For use in developer documentation and release notes."
license: MIT
metadata:
  author: bguiz
  version: "0.0.0"
---

# Detect Breaking Changes for Injective Core, Skill Guide

Goal: identify any changes upon a new release of Injective core.

## When to apply

- "Are there any breaking changes in the latest release of injectived or peggo?"
- "For Injective Mainnet validators upgrading to vX.Y.Z, do we need extra requirements?"

## Activities

Perform the following steps in sequence.

## 1 - Inputs

Ask the user:
- `PREV_TAG` what is the previous version, e.g. `v1.19.0`
- `NEXT_TAG` what is the previous version, e.g. `v1.20.0`

If the user inputs tags without the `v` prefix, e.g. `1.19.0`, correct it automatically

## 2 - Run detect breaking changes

Invoke the `devrel-detect-breaking-changes` agent skill.

```text
/devrel-detect-breaking-changes 
REPO: git@github.com:InjectiveFoundation/injective-core.git
PREV_TAG: ${PREV_TAG}
NEXT_TAG: ${PREV_TAG}

PERSONAS: DevOps team running Injective mainnet validator nodes, software engineers running Injective testnet validator nodes, security team

REQS: Hint - when the following files/ globs have been changed, they are more likely to result in breaking changes:
  - `go.mod`
  - `injectived.sh`
  - `scripts/local-genesis/initial_oracle_genesis.json`
  - `client/docs/swagger-ui/swagger.yaml`
  - `cmd/injectived/root.go`
  - `proto/**/*.proto`
  - `injective-chain/app/upgrades/**/upgrade.go`
  - `injective-chain/app/app.go`
  - `injective-chain/app/**/` (when new subdirectory has been added)

```

## Related skills

- `devrel-detect-breaking-changes`

If this skill is not available, run the following command to install it:

```shell
npx skills add bguiz/devrel-agent-skills --skill devrel-detect-breaking-changes 
```

## Prerequisites

Nil
