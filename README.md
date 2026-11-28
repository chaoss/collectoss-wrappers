# collectoss-wrappers

[![Python wrapper tests](https://github.com/chaoss/collectoss-wrappers/actions/workflows/unittests.yml/badge.svg)](https://github.com/chaoss/collectoss-wrappers/actions/workflows/unittests.yml)

Python wrappers for the binaries that [CollectOSS](https://github.com/chaoss/CollectOSS) runs during data collection.

## What is this project?

Some of the tools CollectOSS runs during collection are Go binaries, like `scc` and `scorecard`, and CollectOSS calls them through `subprocess`. Each wrapper in this repository packages one of those binaries as a Python library, so it can be called from CollectOSS, a notebook or a script without shelling out by hand.

| wrapper | wraps | status |
|---|---|---|
| [`disclosure`](disclosure/) | [chaoss/disclosure](https://github.com/chaoss/disclosure), which gathers signals of disclosed AI contributions | proof of concept, not on PyPI yet |

`disclosure` is the first one, and wrappers for `scc` and `scorecard` may come later. It started as a proof of concept in [chaoss/disclosure#98](https://github.com/chaoss/disclosure/pull/98), and its integration into CollectOSS is tracked in [chaoss/CollectOSS#451](https://github.com/chaoss/CollectOSS/issues/451).

## Supported systems

The `disclosure` wrapper runs the prebuilt `disclosure` release for the platform it is on. It needs Python 3.9 or newer.

| platform | release binary | tested in CI |
|---|---|---|
| Linux amd64 | yes | yes, on Python 3.9, 3.11 and 3.14 |
| macOS arm64 | yes | yes, on Python 3.14 |
| Linux arm64, macOS amd64 | yes | no |
| Windows amd64, arm64 | yes | no, the Windows job is off for now |

The first call downloads the release archive from GitHub and verifies it against the release checksums, so it needs network access once per `disclosure` version. See [disclosure/README.md](disclosure/README.md) for how the download and the cache work.

## Contributing

Contributions are welcome. [CONTRIBUTING.md](CONTRIBUTING.md) covers how to get started, how to run the tests, and what we expect in a pull request.

Check out the [CHAOSS Getting Started guide](https://chaoss.community/kb-getting-started/) to join Slack. Questions about this repository go to **#wg-collectoss-8knot**, and the CHAOSS Software meetings are on the [CHAOSS Calendar](https://chaoss.community/chaoss-calendar/).

To run the tests of the `disclosure` wrapper:

```bash
cd disclosure
uv run --dev pytest
```

## Governance and Maintainers

This repository is part of the CollectOSS project, which is part of [CHAOSS](https://chaoss.community), a Linux Foundation® project. It follows the [CollectOSS governance](https://github.com/chaoss/CollectOSS/blob/main/GOVERNANCE.md), and the [CollectOSS maintainers](https://github.com/chaoss/CollectOSS/blob/main/MAINTAINERS.md) have merge rights here, as in every CollectOSS repository.

## Licensing

Each wrapper carries its own license. The `disclosure` wrapper is licensed under GPL-3.0, the same license as `disclosure` itself. See [disclosure/LICENSE](disclosure/LICENSE).
