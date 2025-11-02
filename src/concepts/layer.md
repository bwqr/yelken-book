# Layer

To keep most of the resources provided by themes and plugins as immutable, Yelken allows overriding them without directly modifying them.
This is accomplished by searching a given resource through each source in a fixed order where a source represents one layer.
Hence, a source with a higher order can override a source located at lower order.

Currently, there are 3 different sources in Yelken: theme, user created resources in global namespace and user created resources in a theme's namespace.
As an example, when Yelken starts loading a template file called `index.html`, it first looks resources created by user that are in active theme's namespace.
If it does not exist, it checks whether user has created this resource in global namespace.
As a last resort, it checks whether the resource exists in the theme's templates.
When non of the sources has the requested resource, it is considered as not exists.

While template resource has this behaviour, some kind of resources may not share exact semantics in terms of searching, such as pages.
This is left as future work to bring them to the same level as templates.
You can find the exact semantics for each resource kind in their own documentation page.
