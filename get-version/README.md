# Get Version Action

Extracts a version string from the current Git reference.

## Inputs

| Name | Required | Default | Description |
| --- | --- | --- | --- |
| `version-source` | No | `tag` | Source of version: `tag` or `branch`. |

## Outputs

| Name | Description |
| --- | --- |
| `version` | Parsed version string from the selected ref source. |

## Behavior

- `version-source: tag`
  - Reads `GITHUB_REF` like `refs/tags/v1.2.3`
  - Removes `refs/tags/` and a leading `v`
  - Output becomes `1.2.3`
- `version-source: branch`
  - Reads `GITHUB_REF` like `refs/heads/release/v1.2.3`
  - Removes `refs/heads/release/v`
  - Output becomes `1.2.3`

## Example

```yaml
- name: Get package version
  id: version
  uses: ./get-version
  with:
    version-source: tag

- name: Show version
  run: echo "Version is ${{ steps.version.outputs.version }}"
```
