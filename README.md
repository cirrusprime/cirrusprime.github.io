Notes for myself (first-timer here; don't mind me):

## Default `leap-day` Important Theme Files

### HTML

`/_layouts/default.html` contains HTML giving the layout to be used, um, *by default*...  `/_layouts/home.html` is (presumably) the layout used for the static landing page, if specified; `/_layouts/page.html` is the layout used for pages; and of course `/_layouts/post.html` is the layout used for posts.  I know, who'd have thought, right?

Within these files, there will be `{{ liquid.tags }}`, which are used by Jekyll to input specific content into the given template files in `/_layouts/`.

### CSS

`/assets/css/style.scss` holds only the empty frontmatter and the single line `@import "{{ site.theme }}";`, which is basically a "call" to `/_sass/jekyll-theme-leap-day.scss`, which actually holds the style information.  So custom CSS should go under the `@import` line in `/assets/css/style.scss`, or in a separate file (that gets called in a tailored duplicate `@import` line in the same).

### `_config.yml`

This file contains [Liquid variables](https://jekyllrb.com/docs/variables/) for setting.  Every `blah: value` pair in `_config.yml` can be referenced in other files using `site.blah` syntax.

### Liquid syntax used by Jekyll

[Liquid](https://shopify.github.io/liquid/) is a templating language, which is [used (and expanded) by Jekyll](http://jekyllrb.com/docs/templates/) for inclusion within the main (HTML syntax, generally, I think?) files.

## Adding customised HTML, CSS, and suchlike

Override Jekyll defaults with stuff in:

* `_layouts`
* `_includes`: contains snippets of code to ease the templating process
    * `head.html`: DOCTYPE and starting `html` tag (including `lang` definition within it); then full `head` and starting `body` tag
    * `header.html`: Full `header` tags
    * `footer.html`: Credit-attributing stuffs/quick contact details; full `footer` tag
    * `foot.html`: Ending `body` and ending `html` tags
    * `nav.html`: Links to pages (using liquid tags again)
* `_sass`
* `assets`

## Pages

If you want your [pages to go in a specific directory](http://damonbauer.me/organizing-jekyll-pages/) (`_pages`, for example), you need to add it to the `includes: ["blah"]` hash, to become `includes: ["blah", "_pages"]`.  Additionally, you need a directory per page, within the `_pages` directory, and in each page-specific directory, you need an `index.html` file, with frontmatter that includes `permalink: "/pagename/`.
