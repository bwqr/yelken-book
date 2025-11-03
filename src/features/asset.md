# Asset

Thanks to Asset, Yelken allows you to store any kind of file in its storage by uploading them.
When you upload an asset to Yelken, you can use it in various places such as contents whose model has a field with `asset` type or directly referencing it in your templates.

Unfortunately, there is no easy way to reference an asset directly in your content's `text` fields.
For the moment, you can embed the exact url of your asset in your contents, which can be obtained in the asset's details.
This is a feature that will be implemented in the future though.

Another limitation about assets is that there is a limit in the upload size.
By default, upload size is limited to 2 megabytes (MB).
This can be configured with `YELKEN_UPLOAD_SIZE_LIMIT` environment variable.
You can checkout [Configuration](/getting-started/running-yelken.html#configuration) section for more information about this config.
