![GitHub Workflows](https://raw.githubusercontent.com/andrewdyer/andrewdyer/refs/heads/main/assets/images/covers/github-workflows.png)

# GitHub Workflows

## Introduction

This repository contains a collection of GitHub Actions and workflows designed to streamline the development process for Node.js and TypeScript projects.

## Usage

### Prepare Node

This action sets up a Node.js environment and installs dependencies for TypeScript projects. It supports npm, yarn, and pnpm as package managers.

```yml
jobs:
  build:
    steps:
      - name: Prepare Environment
        uses: andrewdyer/github-workflows/.github/actions/prepare-node@main
        with:
          package-manager: yarn
```
