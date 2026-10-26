# OrderKit - CS_VNETFX45_SDKMSBUILD_PAKET_MONO

One branch of the C# tool-evaluation corpus. Test **data**, not a product: tool
execution is not part of the build, and evaluation happens later.

## Branch

`CS_VNETFX45_SDKMSBUILD_PAKET_MONO`

## Cell

| Axis | Value |
|---|---|
| Bundler | SDK-style MSBuild |
| Package manager | Paket |
| Architecture | Monolith |

Projects:

- `OrderKit` (`src/OrderKit`)

## Target framework

`net45` - .NET Framework 4.5

The oldest TFM named anywhere in the source metric sheet. Out of support since 12 January 2016; retained deliberately as the corpus floor.

## Language version

C# 5, taken as the default of the target framework. `LangVersion` is deliberately
never written to any project file, which is what keeps the family axis one number
instead of two.

The domain layer is written to that language subset exactly, and the lock is
verified by execution rather than asserted:

```
csc -langversion:5   ->  clean
csc -langversion:4   ->  error CS8025: Feature 'async function' is not available
```

## Build

```bash
./build.sh
```

Restore will not succeed on a host where NuGet is unreachable; see `dataset.json`
`blockedHosts`.

## Test

```bash
./build.sh          # the test step is wired into the build
```

19 tests are declared. They are **not** executed in this corpus's build, because no
test framework can be restored.

## Tool data folders

This repo carries only `Tool Triggering (Tool Github Test data)` from testable-platform/csharp-corpus's original per-branch task-data folders.

| Folder | What it holds |
|---|---|
| `Tool Triggering (Tool Github Test data)` | Each tool's own upstream test suite, copied byte-for-byte from the tool's repository. `SOURCE.md` records the repo, commit and licence. |

`Tool Triggering (Tool Github Test data)` is upstream code kept exactly as upstream ships it, manifests included.

