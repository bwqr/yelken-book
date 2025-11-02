# Namespace

Inside the Yelken, namespaces separate group of resources from each other to create an isolation.
This enables two different themes have resources that are named as same, such as models.

When you install a theme, Yelken creates a new namespace with theme's id.
It also places any resources created by the theme during installation into this namespace.
While rendering a page when a visitor visits the website, Yelken uses resources only in current active theme's namespace.
When you mark another theme as active, the new one's namespace will be used for searching the resources.

To allow themes share resources between each other, there is also a `global` namespace.
Any resources created in `global` namespace can be used regardless of current active theme.
`global` namespace is especially helpful for users to use a resource across all themes.
