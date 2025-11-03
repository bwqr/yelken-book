# Model

With models, Yelken allows you to define the structure of your contents according to your requirements.
It enables you to manage many parts of your website dynamically by utilizing CMS feature.
As an example, you can define a `menu` model where each content in this model is displayed at the top navigation bar in your website.
Moreover, you can also use same contents in your footer to display a similar menu.

During model creation, you can specify name, key, namespace, optionally a description, and at least one field.
Name is used for display purposes in the App and only visible to you.
Key is a unique identifier of the model for the namespace it is created in.
Models can be placed inside of either global namespace or a theme's namespace.
Once you create a model, you can run queries on them and display the results by using its key in the templates.

As a final note, when you want to delete a model from Yelken, you first need to delete all the contents belonging to the model.

## Field
Under the hood, models are composed of many individual fields to form a structure.
Fields define type of value that will be received during content creation.
Besides the type of value, a field belonging to a model also contains a few boolean properties: `required`, `localized` and `multiple`.

The most basic field is `text`, which can be used to receive any kind of value.
Yelken currently has 4 different builtin fields: `text`, `multiline`, `number` and `asset`.
A field can have its own validation or parsing rules (e.g. `path` field, that is planned to be added to Yelken, can store its values syntactically as a string while it semantically means a URL segment and can contain only valid URL segments).
In the future, Yelken may let plugins and themes define their own fields to enable validation on the values.

Similar to model, while adding a field to a model, you can specify name, key, optionally a description, type of field, and properties mentioned above.
In this case, key must be unique across the fields defined for the model.
You can access the values belonging to this field in your templates by using the key.
