# Template API
> Note: Template API is currently unstable and may change without any notice.

As templates are rendered with [minijinja](https://docs.rs/minijinja/latest/minijinja/) library, the builtin [filters](https://docs.rs/minijinja/latest/minijinja/filters/index.html#functions) and [tests](https://docs.rs/minijinja/latest/minijinja/tests/index.html#functions) defined in minijinja is also available to you in templates.
You can use them to perform various operations.

In addition to these filters and tests, Yelken also exposes various variables and functions to let you access information about request, such as locale and path params, and load contents to display them.
Starting with [global](#global) context, following shows variables and functions exposed by Yelken and their types side by side.

### Global
* `request`: [Request](#request)
* `response`: [Response](#response)
* `l10n`: [L10n](#l10n)
* `localize`: Fn(key: string, **kwargs) -> string
* `asset_url`: Fn(path: string, kind: string) -> string
* `get_url`: Fn(page: string, path: string, params: string, localize: bool) -> string
* `get_content`: Fn(model: string, field: string, value: string) -> Option<Map<string, string>>
* `get_contents`: Fn(model: string, fields: List<string>, limit: integer, offset: integer) -> List<Map<string, string>>
* `paginate`: Fn(model: string, fields: List<string>, per_page: integer, page: integer) -> [Pagination](#pagination)

### Request
* `locale`: [Locale](#locale)
* `options`: Map<string, string>
* `params`: Map<string, string>
* `search_params`: Map<string, string>

### Response
* `set_status`: Fn(integer) -> None

  Function that accepts one integer argument as http status code and returns None

### L10n
* `locales`: List<[Locale](#locale)>
* `default`: [Locale](#locale)

### Locale
* `key`: string
* `name`: string

### Pagination
* `per_page`: integer
* `current_page`: integer
* `total_pages`: integer
* `total_items`: integer
* `items`: List<Map<string, string>>
