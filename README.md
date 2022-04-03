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
