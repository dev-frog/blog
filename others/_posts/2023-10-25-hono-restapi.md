---
layout: post
title: Hono REST API
description: >

---

## Introduction

```bash
yarn create hono


? Target directory server
? Which template do you want to use? nodejs
? Do you want to install project dependencies? yes
? Which package manager do you want to use? yarn


```

## Setup eslint config [https://github.com/antfu/eslint-config]

```bash
pnpm dlx @antfu/eslint-config@latest
```

## Customize eslint rules

```mjs
import antfu from "@antfu/eslint-config";

export default antfu({
  type: "app",
  typescript: true,
  formatters: true,
  stylistic: {
    indent: 2,
    semi: true,
    quotes: "double",
  },
  ignores: ["**/migrations/*"],
}, {
  rules: {
    "no-console": ["warn"],
    "antfu/no-top-level-await": ["off"],
    "node/prefer-global/process": ["off"],
    "node/no-process-env": ["error"],
    "perfectionist/sort-imports": ["error", {
      internalPattern: ["@/**"],
    }],
    "unicorn/filename-case": ["error", {
      case: "kebabCase",
      ignore: ["README.md"],
    }],
  },
});

```
