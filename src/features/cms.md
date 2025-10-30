# Content Management System

**Content Management System (CMS)** feature of Yelken tries to allow you organize contents of your website without requiring much effort.
It comes with localization enabled by default and you can translate your website to multiple different locales.
Additionally, you can define models of your contents to describe their structures.
Once you have your models defined, you can create new contents for a corresponding model.
You can also upload assets, such as image and video files, to use them in the contents.

As a result of Yelken's permission system, a user needs to have `CMS Read` permission to at least be able to access pages under `CMS` section of main menu in the App.
In order to make any changes on models, contents or assets, a user needs to have corresponding `Model Write`, `Content Write` or `Asset Write` permission.

## Locale
Yelken allows you to create multiple locales representing different languages and regions of your visitors.
To manage the locales of your website, you can navigate to `Locales` page located under `Administration` section of the main menu in App.
While **Locales** page is located under `Administration`, it can be considered as part of CMS feature.
This is done to differentiate that managing locales require a different permission than managing the contents.
In order to make any changes on locales, the user needs to have `Admin` permission.

In Yelken, locales are represented with their locale identifier, such as `en` for English.
There must exist at least one locale and exactly one of them must be default locale.
By default, Yelken comes with `English (en)` locale.
When a visitor visits your website, Yelken tries to find the best matching locale for the visitor's locale.
If there is no matching locale, the default one is used for rendering the website.

In terms of managing locales in the App, you can delete a non-default locale, set another locale as default one, create a new one or edit an existing one.

## Model and Field
With the help of models, you can define the structure of contents. Models are composed of many individual fields to form a structure.

A field defines the type of input that will be received during content creation.
The most basic field is text, which can be used to receive any kind of value.
Yelken currently has 4 different builtin fields: `Text`, `Multiline`, `Number` and `Asset`.
<!-- A special type of field is enums, where possible values are already specified. -->
A field can have its own validation or parsing rules (e.g. `Path` field, that is planned to be added to Yelken, can store its values syntactically as a string while it semantically means a URL segment and can contain only valid URL segments).

## Content

TODO

## Asset

TODO
