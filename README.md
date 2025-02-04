### Init

```shell
git submodule update --init --recursive
```

### Basic setup (local dev)

```shell
docker compose up -d postgis redis rabbitmq kafka db-makemigrations db-migration
```

<span style="color:red">IMPORTANT: </span> Create admin user:
```shell
docker exec -it backend-api bash
python manage.py createsuperuser --username=admin  # password prompt
exit
```

### Full setup

```shell
# Optional pre-build
docker compose build db-makemigrations backend2-kafka

docker compose up -d
```

<span style="color:red">IMPORTANT: </span> Create admin user (follow Basic setup)

#### Urls:
- App: http://127.0.0.1:6661
- Rest api docs (swagger): http://127.0.0.1:6661/app/swagger
- Websocket docs: http://127.0.0.1:6662
- Admin: http://127.0.0.1:6661/app/admin

### Additional Info
Migrations stored in volume. Path in container: `/usr/app/src/polygons/migrations`
