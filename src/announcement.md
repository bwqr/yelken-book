# Yelken
Welcome to announcement of **Yelken**, a project that describes itself as a *Secure by Design, Extendable and Speedy Next Generation Content Management System (CMS)*.
Yelken is a traditional CMS where you can both manage your contents (backend) and present them to your users (frontend).

Literary, Yelken is a Turkish noun that means **sail** in English.
It is free for everyone to use and its source code is available on [Github repository](https://github.com/bwqr/yelken).
Under the hood, Yelken utilizes [Rust](https://www.rust-lang.org/) programming language and libraries developed around it to achieve its goals.
Project is still under heavy development and may contain bugs or missing some features but it is ready to be tested and experimented.
You can check [examples](https://github.com/bwqr/yelken/tree/main/examples) folder in the repository to see Yelken in action.

While there are many CMS projects out there, such as traditional ones like Wordpress and Drupal or headless ones, Yelken has many ambitious goals to make itself distinct from others.
This distinction can be observable in its description where each of its word has a strong meaning in the Yelken and also defines its identity.

To begin with *Secure by Design*, Yelken's top most priority is to keep itself from being infected by malicious user input or by a malicious plugin. 
No matter what input is given to Yelken, it must continue sustaining its functionalities and not affect other users in an unintentional way, such as causing cross site scripting (XSS) and a bunch of other possible attacks.
A plugin also must not alter behavior of system permanently. If a plugin causes any undesired effect on the system, admins must be able to disable the plugin and make the system return back to its original behavior.

Another important aspect of Yelken is its *Extendable* architecture with plugins.
Yelken utilizes [WebAssembly System Interface (WASI) Preview 2](https://github.com/WebAssembly/WASI/blob/main/wasip2/README.md) and defines a set of interfaces for plugins to interact with Yelken.
WebAssembly enables developers use their favorite programming languages that support WebAssembly, such as low level languages C, C++ and Rust or high level languages Javascript and Python, and develop plugins for Yelken.
The diversity of supported programming languages should bring developers with different backgrounds into Yelken plugin development.
Capabilities of plugins are still under investigation but the plugin architecture is solidified in Yelken.

Lastly, besides security and extendability, Yelken is aiming to be a *Speedy* CMS by requiring very low compute resources (CPU and memory mainly) and serving many requests concurrently and very fast.
Thanks to software stack Yelken uses, it is easy to host many Yelken instances on a compute device with very low resources.

In addition to ambitious goals, Yelken tries to be user friendly from out of box with sane defaults and easy to deploy to any hosting solutions.
However, it also gives you enough power to customize it according to your liking or revert back to its original behavior thanks to its layered approach.

After talking about goals of Yelken, we can now discuss its features expected from a CMS.

## Features
Aside from three main goals, Yelken has a bunch of features built into itself to provide a greater out of box experience and reduce the number of required plugins installed.
These features are, advanced permission system, builtin localization (l10n) support, themes and a powerful templating system, structured content management, and dynamic pages to decide what to render at which url path.

And these are not all the features Yelken has implemented now.
There are also features, such as form handling, observability and asset management, that are planned to be added into Yelken in the near feature.

### Localization
L10n support in Yelken sits at its core and has a strong relation with other features.
A Yelken instance can have one or more locales defined  to provide localized url paths, texts in templates, and contents.

In order to enable themes translate static texts found in their templates, Yelken uses [Fluent](https://projectfluent.org/) localization system.
Themes can provide default translations for the static texts in their templates by providing necessary fluent files.
Users can also override these translations either globally or scoped to per theme.

Url paths of displayed pages can also be localized. As an example, you might have a page at `/article/{id}` displaying an article identified with `id` path parameter in English.
You can also have corresponding Turkish page at path `/makale/{id}` displaying same article in Turkish.
Behind the scenes, these two pages are linked with same `name` which enables localizing the link inside anchor tag.

Finally, to enable localization in contents, each field of a model can be marked as localizable, allowing admins to create different values for each locale while creating or updating a content's field.
If a field is not marked as localizable, its single value can be used regardless of resolved locale.

### Theme & Template
Yelken enables users to customize the look of their website by installing a theme.
There can be many different theme installed on the Yelken but only one can be active at a time.
Technically, a theme consists of templates, contents and pages in order to render an html document for a given url path.

Speaking of templates, Yelken uses a template engine based on [Jinja2](https://jinja.palletsprojects.com/en/stable/) to render a page and display it to users.
Inside templates, Yelken exposes various variables and functions to let theme developers or users access various information about request, such as locale and path params, and load contents to display them.

In terms of customizing a theme, users can easily customize active theme by modifying parts of its templates.
As it was the case for overriding the translations, templates can be overriden either globally or scoped to per theme.

### Content Management
Yelken's Content management is anticipated to be the most frequently used feature of project.
It also hosts many sub-features to make using the Yelken a breeze. In Content feature, there are multiple components that help manage a content easily

* Models

  They define the shape of a content. Models are composed of many individual fields to form a shape.

* Fields

  They define the type of input that will be received from admin during content creation. The most basic field is text that can be used to receive any kind of value from admin. A special kind of field is enums where possible values are already specified. A field can have its own validation or parsing rules (e.g. path field can store its values syntactically as string while it semantically means a url segment and can contain only valid url segments). There can be many different fields built into Yelken or provided by admin or even by plugins.

* Contents

  Once admins set up their desired models and fields, they can start creating content for a given model by providing values for each field of model.

To ease the management of content, there are a few content specific features

* Stages

  A content can be in one of the stages to differentiate draft and published ones. As it can be guessed, published and draft can be provided as default stages. Admins may add custom stages as well.

* Scheduling

  A content can be scheduled to transition from one stage to another one. This enables publishing a content at a specified time without manually publishing it.

* Default fields

  Contents need to have a set of fields by default, such as its publisher, its first creation time, latest update time, stage transition time, etc.

### Page
A page is composed of a url path and template to define which template will be rendered when a user request a url path.
As an example, we can define a page with `/article/{id}` as its url path and `article.html` as its template.
When user request `/article/hello-world` url path, Yelken will find the `article.html` template and render it.

## Current Status
At the moment, most of the aforementioned features are implemented in Yelken.
However, there is a very big piece missing in the puzzle.
Yelken lacks a User Interface (UI), or an admin panel.
All the infrastructure of this admin panel does exist, but necessary pages and components to interact with features are not implemented yet.
Only possible way to interact with Yelken is using its REST API.

Since features are  still in heavy development, developing a UI and adapting it to changes does not make sense.
Once features are stabilized, I can start developing the admin panel.

## Future of Yelken
Yelken has many compelling features and has most of them implemented.
From now on, stabilizing these features and fine tuning them according to user's needs will be the next step.
In the mean time, missing parts of features will also be implemented, such as admin panel and stable plugin interface.

Afterwards, the planned features can start being added into Yelken. In this case, form handling has a high priority since admins need to receive inputs from their users.
Secondly, a Yelken instance needs to be observable and provide many metrics to inform traffic and performance of the website.
For this purpose, Yelken plans exposing many different metrics and displaying them in the admin panel.

### Plugins
Plugin feature is important for Yelken in terms of enabling its extendability.
How plugins should be written, distributed and installed into Yelken is settled down, however, what capabilities they need is still under investigation.
As an example, should plugins hook into flow of a request, such as middlewares, or should they be only callable from templates by themes or users?
As a third option, a plugin can do both :).

In addition to capabilities, the plugin needs to have a permission system where they explicitly specify what they can do in order to inform admin about their possible effect on the Yelken.
This will also let us configure WebAssembly runtime to enable only required WASI parts, such as networking and filesystem access.

### SaaS Product
As a way to sustain development of Yelken and create a revenue source, ultimate goal is to provide Yelken as a Software as a Service (SaaS) product to people.
With this way, anyone can easily use Yelken for their website and not think about the underlying infrastructure.
SaaS will automatically create necessary resources for Yelken to function and hide the management part from its users.
This includes managing databases, collecting metrics from Yelken instances, enabling seemless user login, etc.

At the moment, I am not planning adding any feature that will be feature gated behind a paid version, such as enterprise version.
All the features you can get in SaaS version will be available to you too. Only requirement is that you need to manage all the required resources by yourself.
For example, if you need to utilize observability feature of Yelken, you may need to setup a time series database to collect metrics periodically.

To achieve providing Yelken as SaaS product, Yelken employs a license that only restricts its usage when another company wants to provide Yelken as SaaS product. Next section talks about this license.

## License
Yelken is currently licensed with Business Source License 1.1.
This license is not meant to prevent any **individual** benefitting the Yelken.
Individuals are able to use and deploy Yelken to production.
Even companies can utilize Yelken to manage their websites.
The main motivation behind choosing this license is to prevent a company providing Yelken as a SaaS product without acquiring an explicit license.

Yelken is not the first project utilizing this license or will not be the last one.
As an example usage, you can checkout [surrealdb licensing](https://github.com/surrealdb/license).
If you have any concern about the license, you can open an issue or discussion on the Yelken repository or even join into the Discord server and we can discuss.

## Learn more
If this announcement makes you excited about Yelken or you want to have a more detailed view of Yelken, you can start reading [Yelken's book](https://bwqr.github.io/yelken-book/).
Additionally, here are a few links to check more about Yelken:

* Repository: [https://github.com/bwqr/yelken](https://github.com/bwqr/yelken)
* Book: [https://bwqr.github.io/yelken-book](https://bwqr.github.io/yelken-book)
* Examples: [https://github.com/bwqr/yelken/tree/main/examples](https://github.com/bwqr/yelken/tree/main/examples)
* Discord server: [https://discord.gg/D4bfHr8neh](https://discord.gg/D4bfHr8neh)
