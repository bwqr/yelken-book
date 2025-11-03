# Theme

Yelken makes it easy for users to customize the look of their website by installing a theme, without requiring them to start from scratch.
Themes contain their own page definitions, templates and also models.
You can install many themes into your Yelken instance, and have only one of them active for your website.

Inside the **Install Theme** page, you can select a theme file and inspect its properties such as its id, version, name and models it contains.
Under the hood, a theme file is actually a zip archive.
Its folder structure is described as below
```sh
.
├── assets
│   └── main.css
├── locales
│   ├── en.ftl
├── templates
│   ├── __404__.html
│   └── index.html
└── Yelken.json
```

Inside the `assets` folder, theme can include any kind of assets it requires, such as `css`, `js` and font files.
URLs for these assets can be fetched inside the templates with `asset_url` function, e.g. `asset_url("main.css", kind="theme")`.
On the other hand, `locales` and `templates` folders contain locale and template resources, respectively.

Lastly, `Yelken.json` file is a JSON file containing information about theme as well as models, contents and pages.
An example file can be given as:
```json
{
  "id": "yelken.default",
  "version": "0.1.0",
  "name": "Yelken Default Theme",
  "models": [
    {
      "name": "Menu",
      "key": "menu",
      "fields": [
        { "name": "Name", "key": "name", "field": "text", "localized": true, "required": true },
        { "name": "Url", "key": "url", "field": "text", "localized": true }
      ]
    }
  ],
  "contents": [
    {
      "name": "Home",
      "model": "menu",
      "values": [
        { "field": "name", "locale": "en", "value": "Home" },
        { "field": "name", "locale": "tr", "value": "Ana Sayfa" },
        { "field": "url", "locale": "en", "value": "/" },
        { "field": "url", "locale": "tr", "value": "/" },
      ]
    }
  ],
  "pages": [
    { "name": "Home", "key": "home", "path": "/", "template": "index.html", "locale": "en" },
    { "name": "Home", "key": "home", "path": "/", "template": "index.html", "locale": "tr" },
    { "name": "Blog", "key": "blog", "path": "/blog", "template": "blog.html" },
  ]
}
```
