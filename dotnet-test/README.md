# Dotnet Test Action

Tests a .NET project or solution with optional code coverage collection.

## Inputs

| Name | Required | Default | Description |
| --- | --- | --- | --- |
| `project-path` | No | _None_ | Path to the .NET project or solution to test. If omitted, `dotnet test` runs in the current directory. |
| `configuration` | No | `Debug` | Build configuration passed to `dotnet test` (for example `Debug` or `Release`). |
| `coverage` | No | `false` | Set to `true` to run tests with XPlat Code Coverage in OpenCover format. |
| `coverage-output` | No | `TestResults/` | Results directory used when coverage is enabled. |
| `continue-on-error` | No | `true` | Whether the test step should continue when tests fail. |

## Outputs

| Name | Description |
| --- | --- |
| `coverage-result` | Output emitted by the coverage step when `coverage` is `true`. |

## Behavior

- When `coverage: 'true'`, the action runs `dotnet test` with:
  - `--collect:"XPlat Code Coverage;Format=opencover"`
  - `--results-directory` set from `coverage-output`
  - `--configuration` set from `configuration`
- When `coverage` is not `true`, the action runs `dotnet test` with `--configuration` only.

## Example

```yaml
- name: Test
  uses: ./dotnet-test
  with:
    project-path: ./MySolution.sln
    configuration: Release
    coverage: 'true'
    coverage-output: TestResults/
    continue-on-error: 'false'
```
