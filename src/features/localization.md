# Localization
Yelken allows you to create multiple locales representing different languages and regions of your visitors.
To manage the locales of your website, you can navigate to `Locales` page located under `Administration` section of the main menu in App.
In order to make any changes on locales, a user needs to have `Admin` permission.

In Yelken, locales are represented with their locale identifier, such as `en` for English.
There must exist at least one locale and exactly one of them must be default locale.
By default, Yelken comes with `English (en)` locale.
When a visitor visits your website, Yelken tries to find the best matching one for the visitor's locale.
If there is no matching locale, the default one is used for rendering the website.

Under the hood, Yelken utilizes [Fluent](https://projectfluent.org/) to handle localization.
Each source can define a localization resource for a locale in fluent localization file format which is basically a collection of key-value pair of translation units that also support more advanced usecases like plural form of words.

In terms of managing locales in the App, you can delete a non-default locale, set another locale as default one, create a new one or edit an existing one.
Besides that, when you go into details of a locale, you can see links for translations defined in different sources: `global` namespace, each theme's own translations, and user created translations for each theme.

When you want to have a translation unit for a locale available for use regardless of the active theme, you can define it in `global` namespace for the locale.
Otherwise, you can keep this translation unit scoped to a theme and only use it when that theme become active.

Contrary to [layer concept](../concepts/layer.md), localization resources have a slightly different layering approach.
All the translation units defined in different sources are merged into a single one.
If two sources have a translation unit identified with same key, the one whose source has higher order will be used.
Let's consider that we have a translation unit `hello = Hello` for `en` locale defined in theme's localization resource.
To override this translation with `hello = Hello!`, we can define it in `global` namespace.
Moreover, to override the translation in `global` namespace with `hello = Hello Everybody!`, we can define it in the theme's namespace which has higher order than both theme's original translations and `global` namespace's translations.
