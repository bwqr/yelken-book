# Administration

Multiple users can actively use Yelken within the boundaries of permissions they have.

## Permission
In Yelken, permissions indicate the capabilities of entity it is assigned to, which can be either a user or a role.
They are predefined inside the Yelken and their capabilities cannot be customized.
Currently defined permissions are:

* `Admin`: gives ability of performing administration related operations.
* `CMS Read`: gives ability of fetching models, contents and assets resources.
* `Asset Write`: gives ability of uploading and deleting an asset.
* `Content Write`: gives ability of creating, modifying and deleting a content.
* `Model Write`: gives ability of creating, modifying and deleting a model.
* `Appearance Read`: gives ability of fetching pages, templates and themes.
* `Page Write`: gives ability of creating, modifying and deleting a page.
* `Template Write`: gives ability of creating, modifying and deleting a template.
* `Theme Write`: gives ability of installing, activating and deleting a template.

## Role
Simply, a role is a group of permissions. You can create a role with a name and reference key.
Reference key needs to be unique across all roles.
Afterwards, you can assign permissions to this role.
Once you configure the role, you can assign the role to any user to let them have permissions.

## User

Yelken allows teams to manage a Yelken instance cooperatively by creating a user account for each team member.
Moreover, by assigning permissions, you can enable a user to perform operations within the limitation of the permissions.

A user can have explicit permissions directly assigned to its account or implicit permissions inherited from its role.
When Yelken checks whether a user has a permission, it first looks user's explicit permissions.
If the permission does not exist in explicit permissions, Yelken looks permissions of user's role if user has a role.
Depending on those checks, Yelken authorizes user to perform action.

To create a user, you can specify name, email and password.
Once you have created a user account, you can login with the new account by using its email and password.

## Settings

Currently, settings only allows you to specify a few site options, such as title, description and keywords.
Once you set these values, you can acces them in the templates like `request.options['site.title']`.
