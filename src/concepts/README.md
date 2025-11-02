# Concepts

Yelken introduces a few important concepts to provide an immutable base and isolation between third party sources like themes and plugins.
First concept, that sits at the core of Yelken, is [Namespace](./namespace.md) that provides isolation between resources.
By assigning a unique namespace to each theme or plugin, they can run on their own without interfering resources defined by other themes or plugins.
Moreover, a theme or plugin can also refer a resource provided by another one by using its namespace.

Another concept is [Layer](./layer.md). Inside the Yelken, there are multiple resource sources where more than one source can contain a resource identified by same name.
With the help of layering, a source can override value of a resource without directly modifying it located at another provider.
This ensures that most of the resources are kept as immutable.

Following parts will explain each concept with more details.
