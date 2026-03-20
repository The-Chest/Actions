# Upload Release Artifacts Action

Uploads a file as a GitHub Release asset for a given release tag.

## Inputs

| Name | Required | Description |
| --- | --- | --- |
| `github-token` | Yes | Token used to authenticate release upload. |
| `path` | Yes | File path to upload. |
| `name` | Yes | Asset name shown in the release. |
| `version` | Yes | Release tag (for example, `v1.0.0`). |

## Outputs

| Name | Description |
| --- | --- |
| `artifact-url` | URL returned by the upload-release-asset action. |

## What this action does

Uses `actions/upload-release-asset@v1` with:
- `upload_url`
- `asset_path`
- `asset_name`
- `asset_content_type: application/octet-stream`

## Example

```yaml
- name: Upload release zip
  uses: ./upload-release-artifacts
  with:
    github-token: ${{ secrets.GITHUB_TOKEN }}
    path: ./dist/my-app.zip
    name: my-app-v1.0.0.zip
    version: v1.0.0
```
