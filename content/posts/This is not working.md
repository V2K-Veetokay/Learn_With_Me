---
date: 2025-12-29
linktitle: This is not working
menu:
  main:
    parent: tutorials
prev: /tutorials/Hugo
title: Hugo
weight: 10
---

## Hugo notes


```
{{<button href="/docs/example">}}Explore{{</button>}}
```


```
---
bookHidden: true
---

# This page is hidden in menu
```
### snippets for blogs

```
---
date: 2025-12-29
linktitle: This is not working
menu:
  main:
    parent: tutorials
prev: /tutorials/Hugo
title: Hugo
weight: 10
---
```

or

```
+++
title = "Getting Started with Hugo"
description = ""
tags = [
    "go",
    "golang",
    "hugo",
    "development",
]
date = "2014-04-02"
categories = [
    "Development",
    "golang",
]
menu = "main"
+++
```

or

```
---
author: "Michael Henderson"
date: 2014-09-28
linktitle: Creating a New Theme
menu:
  main:
    parent: tutorials
next: /tutorials/github-pages-blog
prev: /tutorials/automated-deployments
title: Creating a New Theme
weight: 10
---
```