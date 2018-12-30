# Nutshell web (Jekyll)

![nutshell](https://murfinsandburglars.files.wordpress.com/2012/12/nutshell1.jpg?)

Here's the back-end of my personal blog where I note how to custom this thing :D

# Prose

Prose.io is a content editor for GitHub designed for managing websites

# Daktilo

Daktilo is a [Jekyll](jekyllrb.com) theme with a minimal design inspired from typewriters.

## Local

Execute `jekyll serve --watch` and head to [localhost:4000](http://127.0.0.1:4000) to see the result.

## Using categories
Categories are little bit tricky. Please make sure to do the following for each category:

- Create a file within `categories` folder with the name of your category
For example let's say that we have a category called `An Awesome Category` you will need to add an `an-awesome-category.html` file with this content:

``` html
---
layout: category
category: an-awesome-category
permalink: /categories/an-awesome-category/
---

```

- Create an entry inside `_data/categories.yml`

``` html
- slug: an-awesome-category
  name: An Awesome Category
```

- Then you will see it in the footer in the `Explore` section.
