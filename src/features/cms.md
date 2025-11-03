# Content Management System

**Content Management System (CMS)** feature of Yelken tries to allow you organize contents of your website without requiring much effort.
It comes with localization enabled by default and you can translate your contents to multiple locales.
To make organization easy, Yelken allows you to define models of your contents which describe the structures.
To illustrate that, consider a model called `post` with `title` and `content` as its fields.

After having your models defined, you can create new contents for a corresponding one.
Once a content is created, you can control whether it should be visible to visitors or not by moving its stage to `published` or `draft`.
In addition to creating content, you can also upload assets, such as image and video files, to use them in various part of Yelken like contents or directly in templates.

To speak about required permission for CMS feature, a user needs to have `CMS Read` permission to at least be able to access pages under `CMS` section of main menu in the App.
In order to make any changes on models, contents or assets, a user needs to have corresponding `Model Write`, `Content Write` or `Asset Write` permissions.
