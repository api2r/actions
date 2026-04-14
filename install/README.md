# `install`: Install R and dependencies

Sets up pandoc, R, and package dependencies. Wraps the `setup-pandoc`, `setup-r`, and `setup-r-dependencies` actions from [r-lib/actions](https://github.com/r-lib/actions) with sensible defaults, and adds support for pre-warmed container environments.

## Usage

```yaml
- uses: api2r/actions/install@v1
  with:
    token: ${{ secrets.GITHUB_TOKEN }}
```

## Inputs

| Input | Description | Default |
|---|---|---|
| `token` | GitHub token | `${{ github.token }}` |
| `r-version` | R version, passed to `r-lib/actions/setup-r@v2` | `release` |
| `http-user-agent` | HTTP user agent, passed to `r-lib/actions/setup-r@v2` | `""` |
| `needs` | `Config/Needs` tag(s), passed to `r-lib/actions/setup-r-dependencies@v2` | `""` |
| `extra-packages` | Extra packages, passed to `r-lib/actions/setup-r-dependencies@v2` | `""` |
| `optional-packages` | Optional extra packages; installed individually, warn (not error) on failure | `""` |
| `cache-version` | Cache version for `r-lib/actions/setup-r-dependencies@v2` | `"1"` |
| `use-container` | Set to `'true'` when running inside a pre-warmed container (skips R and pandoc setup) | `"false"` |

## Examples

Standard workflow (installs R, pandoc, and all package dependencies with caching):

```yaml
steps:
  - uses: actions/checkout@v6
  - uses: api2r/actions/install@v1
```

With extra packages and a specific R version:

```yaml
steps:
  - uses: actions/checkout@v6
  - uses: api2r/actions/install@v1
    with:
      r-version: "4.3"
      extra-packages: any::rmarkdown any::knitr
      needs: website
```

Inside a pre-warmed container (skips R/pandoc installation, updates only missing or outdated packages):

```yaml
steps:
  - uses: actions/checkout@v6
  - uses: api2r/actions/install@v1
    with:
      use-container: "true"
```
