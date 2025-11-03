# Content

After creating models with respect to your requirements, you can start creating contents for your models and display them in your website in various places for the visitors.
Creating a content and publishing is a straightforward task for a user.
During content creation for a model, you can specify name and values for each model's fields.

When a field has `localized` property, you can provide a value for each locale existing in your Yelken instance.
If field has `required` property, you have to specify a value for the field.
With `multiple` property, you can provide more than one value for the field and these values are accessible in your templates as a list of values instead of a single value.

A content can be in one of the predefined stages: `draft` and `published`.
Once you have created your content, it is automatically marked as `draft` meaning that it will not be available in your templates.
Hence it is not visible in your website.
When you feel that content is ready for publishing, you can mark it as `published`.
In the future, these stages can be extended with new ones.
Moreover, Yelken may allow users to define their own stages according to their needs.
