# Docker Compose

With the help of a docker compose file, it is easy to setup database, perform migrations and initialize it with default values.
This enables providing an out of box experience for Yelken.
Following docker compose file shows an example deployment configuration for version `0.1.0-alpha3`.

This config mounts postgresql's storage into `db` directory. It also mounts Yelken's storage into `storage` directory.
Please note that some of the configurations need to be adjusted for yourself, namely `POSTGRES_PASSWORD`, `YELKEN_DATABASE_URL` and `YELKEN_SECRET_KEY`.

When you first bring services up with `docker-compose up -d`, `yelken_migrate` service can fail since postgresql may not have its initialization completed yet.
After a few seconds, you can run the same command again.

Once every service runs successfully, you can create an admin user with following command.
Please update placeholders: `<name>`, `<email>` and `<password>`.
```sh
docker-compose run --rm yelken sh -c 'echo { "name": "<name>", "email": "<email>", "password" : "<password>" } | ./yelken setup --admin'
```

```yaml
services:
  postgres:
    image: postgres:18
    restart: always
    environment:
      POSTGRES_PASSWORD: <replace-with-a-strong-password>
      POSTGRES_USER: yelken
      POSTGRES_DB: yelken
    networks:
      - app-network
    volumes:
      - ./db:/var/lib/postgresql:z
  yelken_migrate:
    image: bwqr/yelken:0.1.0-alpha3
    command: ["./yelken", "migrate"]
    depends_on:
      postgres:
        condition: service_started
    environment:
      RUST_LOG: info
      YELKEN_DATABASE_URL: postgres://yelken:<postgres-password>@postgres/yelken
      YELKEN_SECRET_KEY: <secret-key-with-32-characters-long>
    networks:
      - app-network
  yelken_setup:
    image: bwqr/yelken:0.1.0-alpha3
    command: ["./yelken", "setup", "--defaults", "--theme"]
    depends_on:
      yelken_migrate:
        condition: service_completed_successfully
    environment:
      RUST_LOG: info
      YELKEN_DATABASE_URL: postgres://yelken:<postgres-password>@postgres/yelken
      YELKEN_SECRET_KEY: <secret-key-with-32-characters-long>
      YELKEN_STORAGE_DIR: /storage
    networks:
      - app-network
    volumes:
      - ./storage:/storage:z
  yelken:
    image: bwqr/yelken:0.1.0-alpha3
    restart: always
    depends_on:
      yelken_setup:
        condition: service_completed_successfully
    environment:
      RUST_LOG: info
      YELKEN_ENV: prod
      YELKEN_BIND_ADDRESS: 0.0.0.0:8080
      YELKEN_DATABASE_URL: postgres://yelken:<postgres-password>@postgres/yelken
      YELKEN_SECRET_KEY: <secret-key-with-32-characters-long>
      YELKEN_SITE_URL: http://127.0.0.1:8080
      YELKEN_APP_URL: http://127.0.0.1:8080
      YELKEN_CORS_ORIGINS: http://127.0.0.1:8080
      YELKEN_UPLOAD_SIZE_LIMITS: "8192"
      YELKEN_RELOAD_TEMPLATES: no
      YELKEN_STORAGE_DIR: /storage
      YELKEN_TMP_DIR: /tmp
    ports:
      - '8080:8080'
    networks:
      - app-network
    volumes:
      - ./storage:/storage:z
networks:
  app-network:
    driver: bridge
```
