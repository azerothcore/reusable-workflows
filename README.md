# ![logo](https://raw.githubusercontent.com/azerothcore/azerothcore.github.io/master/images/logo-github.png) AzerothCore
## reusable-workflows
Reusable workflows to be use with AzerothCore

## how to use
Here is an example to use with AzerothCore Modules
```yaml
name: core-build
on:
  push:
    branches:
      - 'master'
  pull_request:

jobs:
  build:
    uses: azerothcore/reusable-workflows/.github/workflows/core_build_modules.yml@main
    with:
      module_repo: ${{ github.event.repository.name }}
```

If the module isn't at the root of the repo, pass the folder that holds it:
```yaml
    with:
      module_repo: ${{ github.event.repository.name }}
      module_path: server-side/mod-my-module
```

If the module needs its own client data to start (custom maps, DBC rows, ...), pass an archive (`.zip`, `.tar.gz`,
`.tgz`) holding `dbc/` and optionally `maps/`, `vmaps/`, `mmaps/`. It is copied over the stock data before the
worldserver dry run. Use a path relative to the repo root (not to `module_path`):
```yaml
    with:
      module_repo: ${{ github.event.repository.name }}
      module_data: client-data.zip
```
or a URL:
```yaml
    with:
      module_repo: ${{ github.event.repository.name }}
      module_data: https://example.com/my-module/client-data.zip
```
