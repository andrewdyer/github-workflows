![GitHub Workflows](https:/raw.githubusercontent.com/andrewdyer/andrewdyer/refs/heads/main/assets/images/covers/github-workflows.png)

# GitHub Workflows

A collection of GitHub Actions and workflows to automate and streamline development processes.

## License

Licensed under the [MIT license](https:/opensource.org/licenses/MIT) and is free for private or commercial projects.

## Introduction

This repository contains a collection of GitHub Actions and workflows designed to streamline the development process for Node.js and TypeScript projects.

## Usage

### Actions

Reusable actions to be used in workflows.

#### **Prepare Node**

This action sets up a Node.js environment and installs dependencies for TypeScript projects. It supports `npm`, `yarn`, and `pnpm` as package managers.

```yml
jobs:
  build:
    steps:
      - name: Prepare Environment
        uses: andrewdyer/github-workflows/actions/prepare-node@main
        with:
          package-manager: yarn
```

### Workflows

Reusable workflows for different technologies.

#### **Node Build**

A workflow to build Node.js projects, including steps for checking out the repository, preparing the environment, and running the build script.

```yml
name: Build

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  build:
    uses: andrewdyer/github-workflows/.github/workflows/build.yml@main
```

#### **Node Test**

A workflow to test Node.js projects, including steps for checking out the repository, preparing the environment, and running the test script.

```yml
name: Test

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  test:
    uses: andrewdyer/github-workflows/.github/workflows/test.yml@main
```

#### **Node Type-check**

A workflow to run type-checking for Node.js projects, including steps for checking out the repository, preparing the environment, and running the type-check script.

```yml
name: Type-check

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  typecheck:
    uses: andrewdyer/github-workflows/.github/workflows/type-check.yml@main
```
