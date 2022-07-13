---
layout: post
title: NPM Modules Managing
description: >
    A complete package manager can do a lot more that install modules. npm has over 20 commands relating to dependency management available.
---

# NPM Modules Managing

Using `npm` to manage your dependencies is a great way to manage your project dependencies.

- List modules in your project.
- Update modules to a more recent version
- Uninstall modules.
- Perform a securtiy audit on your modules to find and fix security flaws.

## Listing Modules

```bash
npm ls
```

`npm ls` will show the entire dependencies tree of your project. If you want a high-level view of your dependencies what's instlled.

```bash
npm ls --depth 0
```

## Update Modules

It is a good practice to keep your `npm` modules up to date. This will improve the stability and security of your project.

```bash
npm outdated
```

This command list the `package` that's installed and the `current` version. The `Wanted` column shows which version satisfies your version requirements in `package.json`. The `Latest` column shows the latest version of the module. The `Location` column states where in the dependency tree the package is located.

> If you wanted yo update all modules at once, then you would enter:

```bash
npm up
```

> If you wanted to update a single module, then you would enter:

```bash
npm up <module>
```

## Uninstalling Modules

The `npm uninstall` command  can remove modules from your project.

```bash
npm un <module>
```

## Auditing Modules

`npm` provide an `audit` command to highlight potential security risks in your dependencies.

```bash
npm audit
```

You can see the path of the vulnerability, and sometime npm offers ways to fixed this issue.

```bash
npm audit fix
```

Although a version of a module may have a security vulnerability,if you update it to a version with a different API then it could break code higher up in the dependency tree.

```bash
npm audit fix --force
```

## Deprecate

This command will deprecate the `npm` registry for a package, providing a deprecation warning to all who attempt to install it.

```bash
npm deprecate <package>
```

## Doctor

Checks our environment so that our `npm` installation has what it needs to manage our javascript packages.

```bash
npm doctor
```
