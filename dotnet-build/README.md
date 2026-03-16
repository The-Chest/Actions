# Dotnet Build Action

Builds a .NET project using `dotnet restore` and `dotnet build`, with optional artifact upload.

## Inputs

| Name | Required | Default | Description |
| --- | --- | --- | --- |
| `dotnet-version` | Yes | `6.0.x` | .NET SDK version passed to `actions/setup-dotnet`. |
| `project-path` | Yes | `./` | Project or solution path to build. |
| `create-build-artifact` | No | `false` | Upload a build artifact when set to `true`. |
| `artifact-name` | No | `build-artifact` | Artifact name used by `actions/upload-artifact`. |
| `artifact-folder` | No | `bin/Release` | Folder path uploaded as artifact content. |
| `artifact-retention-days` | No | `14` | Retention in days for uploaded artifact. |

## Outputs

| Name | Description |
| --- | --- |
| `build-artifact` | Artifact folder path (set only when `create-build-artifact` is `true`). |

## What this action does

1. Sets up the requested .NET SDK.
2. Runs `dotnet restore`.
3. Runs `dotnet build --no-restore --configuration Release`.
4. Optionally uploads the build output folder as an artifact.

## Example

```yaml
- name: Build
  uses: ./dotnet-build
  with:
    dotnet-version: 8.0.x
    create-build-artifact: 'true'
    artifact-name: app-build
    artifact-folder: src/MyApp/bin/Release
    artifact-retention-days: '7'
```
