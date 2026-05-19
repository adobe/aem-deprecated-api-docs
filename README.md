# AEM API Deprecation Documentation

This repository documents how developers can handle AEM API deprecations over time.

The content is organized so that:

- each deprecation **wave** has its own page
- each **deprecated API topic** has its own page
- each affected **bundle** has one canonical remediation guide

This avoids duplicating the same bundle update instructions across multiple waves.

## How To Use This Repository

Choose the path that matches what you know already:

1. If you know the rollout or release window, start with a page in `docs/waves/`.
2. If tooling has already identified an affected bundle, go directly to `docs/3rd-party-dependencies/index.md` to see if there is special guidance available for it.

If you are new to AEM Maven project structure, read [Getting Started](docs/getting-started.md) first.

## Current Waves

- [`2026-June-11`](docs/waves/2026-June-11.md)


## Guidelines

- [3rd Party Dependencies](docs/3rd-party-dependencies/index.md)

## Authoring Rules

- Add a new page under `docs/waves/` for each new deprecation wave.
- Add or update a page under `docs/apis/` when a deprecation topic changes.
- Add or update a page under `docs/bundles/` only when bundle remediation guidance changes.
- Keep the full implementation guidance in the bundle guide and link to it from wave and API pages.
- Keep generic AEM Project Archetype and Maven background in [`docs/getting-started.md`](docs/getting-started.md).
