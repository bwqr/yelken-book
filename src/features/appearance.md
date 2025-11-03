# Appearance

**Appearance** feature lets you decide which pages your website has in addition to allowing you to design the look of each page, though it currently requires some programming knowledge.
This is accomplished by combining the power of **template** and **page** features.

Yelken uses a template engine called [minijinja](https://docs.rs/minijinja/latest/minijinja/) which is based on [Jinja2's](https://jinja.palletsprojects.com/en/stable/) template syntax.
Yelken renders a given template to produce an HTML output and send it back to the visitor.
Yelken exposes various variables and functions to templates to let you access information about request, such as locale and path params, and load contents to display them.

A **page** entry links a url in your website to a template.
When a visitor visits the url that matches a page entry, Yelken will render its corresponding template and display the result to visitor.
For example, we can define a page with `/article/{id}` as its URL path and `article.html` as its template.
When the user requests `/article/hello-world` URL path, Yelken will find the `article.html` template and render it.

Lastly, themes are just collection of pages and templates to give you a starting point.
They also contain their own models and contents to let you have a great out of box experience once you install a new theme.

In order for users to at least access pages under `Appearance` section of main menu in the App, they need to have `Appearance Read` permission.
In order to install a new theme or make any changes on pages and templates, a user needs to have corresponding `Theme Write`, `Page Write` or `Template Write` permissions.
