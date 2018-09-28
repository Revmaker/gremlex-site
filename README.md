# Gremlex Site

This is use to create the site for [Gremlex](https://gremlex.carlabs.ai).

## Requirements

The site is built using [Hugo](https://gohugo.io/) with the theme [Learn](https://github.com/matcornic/hugo-theme-learn)

## Basic How Tos for the lazy

### Running the site locally
```bash
$ hugo serve
```

### Creating a new Chapter
Chapters are the primary side bar sections

```bash
$ hugo new --kind chapter <chapter name>/_index.md
```

#### Example
```bash
$ hugo new --kind chapter documentation/_index.md
```

### Creating a new page within a chapter
```bash
$ hugo new <chapter name>/<section name>.md
```

#### Example
```bash
$ hugo new documentation/graph.md
```

## How to generate static site
```bash
$ hugo
```

This will generate a public folder that can be deployed