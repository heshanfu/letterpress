# letterpress

A simple theme focused on letters and words

# Roadmap to 1.0

- [ ] add [Prism.js](http://prismjs.com/) to include source code highlighting
- [ ] Improve blog title representation for SEO in `<title>` tags
- [x] Make navigation adaptive based on Ghost navigation helper

# Ghost Compatibility

This theme is tested and compatible with [Ghost](https://github.com/TryGhost/Ghost) 1.21.7

The theme is based on the excellent [Casper theme](https://github.com/TryGhost/Casper) 1.3.4.

# Ideas

## Improve blog title representation for SEO in `<title>` tags

### Problem

Current representation is `{{@blog.title}}` for the home page and `{{title}}` for any page. This is by making use of the `{{meta_title}}` helper in Ghost.

Preferrable would be to have it as `{{@blog.title}}` for the home page and `{{title}} - {{@blog.title}}` for any blog entries.

### Solution

In Ghost, the `default.hbs` contains a template for all pages. This has the following header:

    <title>{{meta_title}}</title>

Now to change that for all pages, we create a new template that is not inserted into `default.hbs` by default. So `page.hbs` is identical to `default.hbs`. Then we change the title tag to

    <title>{{meta_title}} - {{@blog.title}}</title>

This way all **posts** still only have the title of the post as the title of the page, but all static pages are shown as `page title - blog title`.
