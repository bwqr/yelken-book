# Template

Template is a resource that contains text and lets you describe how a page should be rendered.
Yelken uses a template engine called [minijinja](https://docs.rs/minijinja/latest/minijinja/) which is based on [Jinja2's](https://jinja.palletsprojects.com/en/stable/templates/) template syntax.
Since Yelken displays your website inside a browser, the final goal of template is to generate a HTML document by using Jinja2's syntax.

Inside the templates, Yelken exposes various variables and functions to let you access information about request, such as locale and path params, and load contents to display them.
You can read [Template API](../template-api.md) page to learn about those variables and functions.
You can also check [Examples](../examples/README.md) to understand how to use them effectively.

During template creation, you can specify path of template and its namespace.
The path needs to be a unix file path which uses `/` as separator.
Additionally, the path also must be at least 3 characters and end with `.html`.
Once a template resource is created, you can edit its content as you wish and use it both inside other templates or in a page entry by using its path.

A template resource can be provided by either a theme or a user.
Thanks to [layer concept](../concepts/layer.md), Yelken allows you to override a theme's template by creating a template with same path either in global namespace or in theme's namespace.
This also allows you to extend a theme by creating your own templates and using them in various places.

## Special Templates

When there is a problem during rendering a web page, such as not found page, Yelken renders a template that has special path.
An example is when no matching page entry is found for a path.
In this case, Yelken tries to render `__404__.html` template if it exists.
You can create your own template with `__404__.html` path to customize the rendered page when Yelken responds the requests with `404` HTTP error code.
Currently, Yelken does not have any other special templates but may be added in the future like customizing pages for `50x` error code.
