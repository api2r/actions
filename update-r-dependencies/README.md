# `update-r-dependencies`: Update R package dependencies

Updates missing or outdated R package dependencies using [pak](https://pak.r-lib.org/). Calls `pak::pak()` directly so it checks `.libPaths()` and only installs or updates packages that are genuinely missing or outdated, rather than reinstalling everything from a lockfile.

## Usage

```yaml
- uses: api2r/actions/update-r-dependencies@v1
  with:
    token: ${{ secrets.GITHUB_TOKEN }}
```

## Inputs

| Input | Description | Default |
|---|---|---|
| `token` | GitHub token | `${{ github.token }}` |
| `needs` | `Config/Needs` tag(s), used to expand additional dependency fields | `""` |
| `extra-packages` | Extra packages to install, in addition to package dependencies | `""` |

## Examples

Basic usage inside a pre-warmed container:

```yaml
steps:
  - uses: actions/checkout@v6
  - uses: api2r/actions/update-r-dependencies@v1
```

With extra packages and additional needs:

```yaml
steps:
  - uses: actions/checkout@v6
  - uses: api2r/actions/update-r-dependencies@v1
    with:
      extra-packages: any::rmarkdown any::knitr
      needs: website
```
