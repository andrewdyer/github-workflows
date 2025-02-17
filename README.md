![GitHub Workflows](https://raw.githubusercontent.com/andrewdyer/andrewdyer/refs/heads/main/assets/images/covers/github-workflows.png)

# GitHub Workflows

A collection of GitHub Actions and workflows to automate and streamline development processes.

## License

Licensed under the [MIT license](https:/opensource.org/licenses/MIT) and is free for private or commercial projects.

## Introduction

This repository contains a collection of GitHub Actions and workflows designed to streamline the development process for Node.js and TypeScript projects.

## Usage

### Actions

Reusable actions to be used in workflows.

#### **Cache Dependencies**

This action caches dependencies for `npm`, `yarn`, and `pnpm` package managers to speed up workflow execution.

```yml
jobs:
  build:
    steps:
      - name: Cache Dependencies
        uses: andrewdyer/github-workflows/.github/actions/cache-dependencies@main
        with:
          package-manager: yarn
```

| Input           | Description                              | Type   | Required | Default |
| --------------- | ---------------------------------------- | ------ | -------- | ------- |
| package-manager | Package manager to use (npm, yarn, pnpm) | string | true     |         |

#### **Prepare Node**

This action sets up a Node.js environment and installs dependencies for TypeScript projects. It supports `npm`, `yarn`, and `pnpm` as package managers.

```yml
jobs:
  build:
    steps:
      - name: Prepare Environment
        uses: andrewdyer/github-workflows/.github/actions/prepare-node@main
        with:
          node-version: 16
          package-manager: yarn
          registry-url: https://npm.pkg.github.com/
```

| Input           | Description                              | Type   | Required | Default                     |
| --------------- | ---------------------------------------- | ------ | -------- | --------------------------- |
| node-version    | Node.js version to use                   | string | false    | 20                          |
| package-manager | Package manager to use (npm, yarn, pnpm) | string | false    | npm                         |
| registry-url    | Custom registry URL for dependencies     | string | false    | https://registry.npmjs.org/ |

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
