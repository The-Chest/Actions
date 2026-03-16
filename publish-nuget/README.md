# Publish NuGet Package Action

Packs and publishes a .NET NuGet package to `nuget.org`.

## Inputs

| Name | Required | Description |
| --- | --- | --- |
| `package-path` | Yes | Path used for both `dotnet pack` target and `dotnet nuget push` package path. |
| `package-name` | Yes | Package name metadata input (currently not used by command steps). |
| `package-version` | Yes | Version passed to `dotnet pack` (`/p:Version=...`). |
| `nuget-api-key` | Yes | API key used for `dotnet nuget push`. |

## Outputs

| Name | Description |
| --- | --- |
| `package-artifact` | Package path written after publish completes. |

## What this action does

1. Runs `dotnet pack` in Release mode with the provided version.
2. Runs `dotnet nuget push` to `https://api.nuget.org/v3/index.json`.
3. Exposes the package path as an output.

## Example

```yaml
- name: Publish package
  uses: ./publish-nuget
  with:
    package-path: ./src/MyLibrary/MyLibrary.csproj
    package-name: MyLibrary
    package-version: 1.2.3
    nuget-api-key: ${{ secrets.NUGET_API_KEY }}
```
