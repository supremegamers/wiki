---
label: Developer GUide
order: -200
---

## Creating a new bigdroid project

If you want to create a new bigdroid project you can run the following:

```bash
bigdroid new --image="local-path-or-web-url (optional)" codename
```

## Working with hooks development

All hooks must and will reside under `~/.bigdroid/registry`.

If you want to create a new hook then use [this template repository](https://github.com/bigdroid-hooks/template)

As most standard bigdroid projects witll pinpoint hooks to a specific commit and branch in their `Bigdroid.meta`, so during hooks development related with such a project will conflict with your local changes. In order to ease your work and so that you don't have to constantly keep updating `Bigdroid.meta` for bumping a hook's commit hash you can use the `--dev` flag during build. More specifically this:

```bash
bigdroid build --release --dev --hooks-only
```

Once you are done with a particular hook, you can just grab the commit hash you want to use and put in your `Bigdroid.meta`

For example:

```bash
git rev-parse --short HEAD
```

This will give you the HEAD short commit hash for the hook repo.
