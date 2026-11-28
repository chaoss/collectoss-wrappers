# disclosure (Python wrapper)

A thin Python wrapper around the [CHAOSS `disclosure`](https://github.com/chaoss/disclosure) CLI, so you can run it and get its results from Python.

> **Status: alpha, not on PyPI yet.** Install it from this repository as shown below. Any package on PyPI or TestPyPI that claims to be this wrapper is not ours.

## Install

```sh
pip install "git+https://github.com/chaoss/collectoss-wrappers#subdirectory=disclosure"
```

Or run it without installing, with [uv](https://docs.astral.sh/uv/):

```sh
uvx --from "git+https://github.com/chaoss/collectoss-wrappers#subdirectory=disclosure" disclosure scan --format=json
```

To get the same code every time, pin a commit: `git+https://github.com/chaoss/collectoss-wrappers@<commit>#subdirectory=disclosure`.

## Use it

As a CLI it behaves like the native binary, exit codes included:

```sh
disclosure scan /path/to/repo --format=json
```

From Python, `scan()` and `text()` return the JSON report as a `dict`:

```python
import disclosure

report = disclosure.scan("/path/to/repo", min_confidence="medium")
findings = disclosure.text("I used Claude to write this")
print(disclosure.version())
```

## How it works

On first use, the wrapper downloads the prebuilt `disclosure` release for your platform from GitHub, checks it against the release `checksums.txt`, and caches the binary. Later calls run the cached binary as a separate process: this is not an in-process binding.

If the download does not match its checksum, or the cached file is a symlink, empty or not executable, the wrapper refuses to run it and tells you which file to remove.

| exit code | meaning |
|---|---|
| `0` | no AI detected |
| `1` | AI detected |
| `2` | error, including wrapper errors like a failed download |

From Python, a failed download or a broken cache raises `BinaryResolutionError`, and a failed scan raises `DisclosureError`.

A later version could bundle the binary in platform-specific wheels, so nothing is downloaded at runtime.

## Configuration

| variable | default | what it does |
|---|---|---|
| `DISCLOSURE_VERSION` | `1.0.0` | Version of the `disclosure` release to use. Meant for local testing. |
| `DISCLOSURE_CACHE_DIR` | `$XDG_CACHE_HOME` or `~/.cache` (`%LOCALAPPDATA%` on Windows) | Base directory of the cache. The binary goes in `disclosure-cli/<version>/` inside it. |

## Tests

See [Running the tests](../CONTRIBUTING.md#running-the-tests) in CONTRIBUTING. In short:

```sh
cd disclosure
uv run --dev pytest
```
