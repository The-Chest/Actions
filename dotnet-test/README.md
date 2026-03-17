# Dotnet Test Action

Runs `.NET` tests with optional code coverage collection.

## Inputs

| Name | Required | Default | Description |
| --- | --- | --- | --- |
| `project-path` | Yes | `./` | Project or solution path to test. |
| `configuration` | No | `Debug` | Build configuration for `dotnet test`. |
| `coverage` | No | `false` | Collect XPlat code coverage when `true`. |
| `coverage-output` | No | `TestResults/` | Coverage results directory when enabled. |
| `continue-on-error` | No | `true` | Whether test step failures should fail the workflow step. |

## Outputs

| Name | Description |
| --- | --- |
| `coverage-result` | Status text output from the coverage flow. |

## What this action does

- If `coverage` is `true`, runs:
  - `dotnet test --collect:"XPlat Code Coverage;Format=opencover" ...`
- Otherwise runs:
  - `dotnet test --configuration ...`

Then it writes a simple output string to `$GITHUB_OUTPUT`.

## Example

```yaml
- name: Test
  uses: ./dotnet-test
  with:
    project: ./MySolution.sln
    configuration: Release
    coverage: 'true'
    coverage-output: TestResults/
    continue-on-error: 'false'
```
