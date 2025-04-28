# Getting Started

Easy way to spin up a Yelken instance is running the [hello-world](https://github.com/bwqr/yelken/tree/main/examples/hello-world) example.
This example contains a docker-compose file to setup a Postgresql database and Yelken instance with appropriate configuration.
You can also check out other examples to experiment with Yelken.

If you want to build Yelken manually and run locally, proceed to following sections.
When you are asked to run some command, please do it inside the [yelken](https://github.com/bwqr/yelken/tree/main/yelken) directory, unless specified otherwise.

### Prerequisites
Before running Yelken, you need to have a few things installed on your machine.

* Rust

  To compile Yelken, you must have rust toolchain installed and accessible via `PATH` in your system, specifically cargo and rustc.
  You can look at [rustup](https://rustup.rs) to set up the Rust programming language.

* Postgresql

  Yelken uses Postgresql as relational database. In the future, this option can be expanded to other relational databases, such as Mariadb or Mysql.

* Trunk

  Yelken needs to have its application, or Admin Panel, assets built and ready before starting. And these assets are built with trunk. You can install it with this command:
  ```sh
  cargo install --locked trunk
  ```

* Diesel (Optional)

  To manage the database migrations, we need to install `diesel_cli`. If you want to migrate database manually, you can skip this part.
  However, before running the Yelken, you must **ensure that all queries** inside the `migrations/**/up.sql` files are executed.

  To install the `diesel_cli`, you can type the following command and build locally.
  You may need to install necessary postgresql client libraries on your machine (e.g. `libpq`).
  For more information, please visit [diesel documentation](https://diesel.rs/guides/getting-started#installing-diesel-cli).
  ```sh
  cargo install diesel_cli --no-default-features --features postgres
  ```

### Migrations

After having dependencies installed on your machine, you need to set up an empty database and run the following command by replacing placeholders with real values to apply all the migrations Yelken needs:
```sh
diesel migration run --database-url postgres://<username>:<password>@<hostname>/<database>
```
Following command gives a concrete example:
```sh
diesel migration run --database-url postgres://yelken_user:toor@127.0.0.1:5432/yelken
```

### Configuration
Yelken requires some environment variables for its configuration. It is also able to load environment variables from `.env` file which needs to be located where it is run.
You can find required environment variables with example values in `.env.example` file. You can copy this file to `.env` and update variables inside it with corresponding values for your environment, such as `YELKEN_DATABASE_URL`.
Each environment variable is explained below:

* `RUST_LOG`: Log configuration for [env_logger](https://docs.rs/env_logger).
* `YELKEN_ENV`: Determines whether Yelken runs in development or production environment. Possible values are `dev` and `prod`.
* `YELKEN_BIND_ADDRESS`: TCP/IP address Yelken listens on.
* `YELKEN_DATABASE_URL`: Postgresql database connection URL.
* `YELKEN_SECRET_KEY`: Secret key used for cryptographic operations in Yelken. This includes signing Json Web Token (JWT) and hashing passwords.
* `YELKEN_BACKEND_ORIGIN`: The full URL with its domain where Yelken runs on. For production deployments, this corresponds to your website domain.
* `YELKEN_FRONTEND_ORIGIN`: The full URL with its domain where Yelken App runs on. This variable mostly has same value as `YELKEN_BACKEND_ORIGIN`. For local development, you may have app running on different origin though.
* `YELKEN_RELOAD_TEMPLATES`: A boolean variable to decide whether templates and localization files should be reloaded on each request. This is useful for iteratively changing your templates or locales. For production, this should be set to false. Values `on`, `yes` and `true` are treated as true whereas any other value is treated as false.
* `YELKEN_STORAGE_DIR`: Storage directory path that is used by Yelken as persistent storage. Right now, this path corresponds to a directory on filesystem. In the future, this can also point to an object storage such as AWS S3 bucket.
* `YELKEN_TMP_DIR`: Directory to use for temporary operations, such as extracting themes and plugins to analyze them. This is decoupled from storage directory since this should always point to a directory on filesystem for quick accesses.
* `YELKEN_APP_ASSETS_DIR`: Directory to serve app assets, such as Wasm and CSS files. This is also decoupled from storage directory to ensure that Yelken and its app are distributed together since they are tightly coupled with each other.

### Running
Once the configuration of Yelken is completed, you first need to build `app` by running following command inside the `app-client` directory:
```sh
# cd app-client
trunk build --public-url /assets/yelken
```


This will compile the Yelken App and put its assets under `app-client/dist` directory. After that, you can start Yelken by running this simple command inside the `yelken` directory:
```sh
cargo run
```

You can access the Yelken from the address specified in `YELKEN_BIND_ADDRESS`.
If you did not change its default value, it should be accessible from [http://127.0.0.1:3000](http://127.0.0.1:3000) address.
