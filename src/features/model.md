# Model

With the help of models, you can define the structure of contents. Models are composed of many individual fields to form a structure.

A field defines the type of input that will be received during content creation.
The most basic field is text, which can be used to receive any kind of value.
Yelken currently has 4 different builtin fields: `Text`, `Multiline`, `Number` and `Asset`.
<!-- A special type of field is enums, where possible values are already specified. -->
A field can have its own validation or parsing rules (e.g. `Path` field, that is planned to be added to Yelken, can store its values syntactically as a string while it semantically means a URL segment and can contain only valid URL segments).
