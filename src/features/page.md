# Page

A page resource helps Yelken understand which template should be rendered at which url path.
When a visitor visits the url that matches a page entry, Yelken will render its corresponding template and display the result to visitor.
For example, we can define a page with `/article/{id}` as its URL path and `article.html` as its template.
When the user requests `/article/hello-world` URL path, Yelken will find the `article.html` template and render it.

During page creation, you can specify name, key, optionally a description, path, namespace, template and whether this page is localized or not.
Currently, key of a page needs to be unique across all pages in both theme's namespace and global namespace, unless it is localized.
A localized page can have an entry for each locale in the Yelken.
This way, you can have a page that has different paths for each locale.
Additionally, it allows you to retrieve the path of a page for a specific locale by using its key.
As an examle, consider two page entries:
```
     key   |    path    |  locale
|-----------------------------------|
| articles | /articles  | en        |
|-----------------------------------|
| articles | /makaleler | tr        |
|-----------------------------------|
```
Inside your templates, you can retrieve corresponding entry for visitor's locale by simply calling `get_url(page="articles")` function.

There is one important note to keep in mind.
The path you have specified does not directly map to URL path of web page if it is a localized page. 
For localized pages, Yelken prepends the locale identifier to path if it is not the default locale. 
Actual paths of two entries shown above actually become `/articles` and `/tr/makaleler` when `en` is the default locale.

For template part, if you are creating a page in global namespace, you can only choose templates located in global namespace.
However, if you are creating a page in a theme's namespace, you can both choose templates located in global namespace and theme's namespace.

Contrary to [layer concept](../concepts/layer.md) of Yelken, you can directly modify a theme's page entry or override it by creating a page with same key and locale in global namespace.
However, there is a way to restore the original pages of a theme, though it is not implemented in Yelken.
Current design of page does not fit very well to layer concept but it will be improved in the future.
