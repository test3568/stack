### Init

```shell
git submodule update --init --recursive --remote
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

### Test Data

POLYGON_1
```text
[76.8007387, 139.9218750]
[76.3933117, 250.8398438]
[70.2594520, 250.6640625]
[70.9596972, 142.9101563]
[60.1524422, 144.1406250]
[59.8006343, 250.8398438]
[47.2792290, 250.6640625]
[47.2792290, 127.0898438]
[53.3308730, 127.4414063]
[53.4357192, 245.3906250]
[56.6562265, 245.0390625]
[56.9449742, 128.1445313]
[73.2773532, 127.9687500]
[72.2890672, 243.9843750]
[74.9137082, 243.4570313]
[75.3200252, 128.4960938]
[76.9206135, 128.1445313]
[76.8007387, 139.2187500]
```

POLYGON_2
```text
[68.7841438, 169.2773438]
[68.2042122, 206.3671875]
[61.6063964, 206.0156250]
[61.9389504, 169.2773438]
[68.6565550, 169.2773438]
```

INTERSECTION
```text
[66.7225413, -180.3515625]
[73.8737165, -176.9238281]
[73.7265947, -172.7929688]
[66.2668563, -174.8144531]
[66.0893643, -169.1015625]
[73.5034606, -167.4316406]
[74.2119825, -160.4003906]
[65.8387757, -162.9492188]
[57.5158229, -172.6171875]
[66.6877839, -180.3515625]
```

### Known bugs

- Intersections are drawn with deviations (turf.js)

### Video

https://github.com/user-attachments/assets/3b63432b-c88c-48ea-b662-32d1e1b42686
