# Relative Paths in VuePress

## Scenes

The following are all scenes in VuePress that involve referencing another markdown file via `relative path`:

- [From normal page to normal page](./normal.md#from-normal-page-to-normal-page)
- [From normal page to permalink page](./normal.md#from-normal-page-to-permalink-page)
- [From permalink page to normal page](./permalink.md#from-permalink-page-to-normal-page)
- [From permalink page to permalink page](./permalink.md#from-permalink-page-to-permalink-page)

## Notes

1. All above usages are only valid under `>= vuepress@v1.0.0-alpha.39`.

## Background

Since VuePress 1.x supports [permalinks](https://vuepress.vuejs.org/guide/permalinks.html), that is, the original link based on the directory structure can be converted to any link according to the user's permalink config.
 
Let us give a practical example, you have a markdown file named `permalink.md` in your document's source directory, the default route path that you'll get at the dev server or production will be `permalink.html`, once you set the permalink as follows:

```markdown
---
permalink: /foo/bar/
sidebar: auto
---
```

The final route path of `permalink.html` will be `/foo/bar/`, this looks great, but the problem is coming: when you want to write a relative path to link to another page in `permalink.md`, such as:

```markdown
[Go to `(./normal.md)`](./normal.md)
```

In a lower version of VuePress, above markdown file will be transformed into following markup:

```vue
<router-link to="./normal.html"></router-link>
```

It means that the relative path will be resolved by vue-router at runtime, since current `location.pathname` is `/foo/bar/`, the resolved path will be `/foo/bar/normal.html`, which will let you to get a 404.

A workaround of this issue is to use absolute path at your source code:

```markdown
[Go to `(normal.md)`](/normal.md)
```

But in this case, you will lose a feature that programmers like very much in writing documents —— **"Ctrl+Click Go To Definition"**, so the best is to let VuePress help us to transform the relative path to the absolute path conversion directly during the build process.

**Of course, VuePress did it**, for now you're free to use relative paths in VuePress. The motivation of introducing the above background is that you need to know that once you use relative paths, You don't have to care about the path of your production environment. and don't nedd worry about it maybe goes 404, just enjoy your documentation!



