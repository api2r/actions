# actions

Composite GitHub Actions for R-based repositories.

## Available actions

### `install`: Install R and dependencies

Sets up pandoc, R, and package dependencies with sensible defaults, and adds support for pre-warmed container environments. See [`install/README.md`](install/README.md) for full details.

### `update-r-dependencies`: Update R package dependencies (container)

Updates missing or outdated R package dependencies inside a pre-warmed container using pak. See [`update-r-dependencies/README.md`](update-r-dependencies/README.md) for full details.