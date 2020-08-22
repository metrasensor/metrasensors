# PostgreSQL Sensor

The PostgreSQL Sensor exposes a wide variety of PostgresQL metrics.

## Installing and running the PostgreSQL Sensor

To start with, you need to run Promethius PostgreSQL Exporter and connect to the current database:

```bash
docker run -d wrouesnel/postgres_exporter \
    --name postgresql-exporter \
    --env DATA_SOURCE_NAME="postgresql://postgres:password@localhost:5432/postgres?sslmode=disable"
```

Then you run the PostgreSQL Sensor:

```bash
docker run -d metrasensor/postgresql-sensor:latest \
    --name postgresql-sensor \
    --env PROJECT_UUID="<your_project_uuid>" \
    --env SENSOR_NAME="<your_sensor_name>" \
    --env PROMETHEUS_HOST="http://<prometheus_host>:9100/metrics"
```

## Environment Variables for PostgreSQL Server Exporter

| Name | Description |  
|------|-------------|
| DATA_SOURCE_NAME |  The default legacy format. Accepts `URI` form and `key=value` form arguments. The `URI` may contain the username and password to connect with. |
| DATA_SOURCE_URI | An alternative to `DATA_SOURCE_NAME` which exclusively accepts the hostname without a username and password component. For example, `my_pg_hostname` or `my_pg_hostname?sslmode=disable`. | 
| DATA_SOURCE_URI_FILE | The same as above but reads the URI from a file. |
| DATA_SOURCE_USER | When using , this environment variable is used to specify the `username.DATA_SOURCE_URI` |
| DATA_SOURCE_USER_FILE | The same, but reads the username from a file. |
| DATA_SOURCE_PASS | When using , this environment variable is used to specify the password to connect `with.DATA_SOURCE_URI` |
| DATA_SOURCE_PASS_FILE | The same as above but reads the password from a file. |
| PG_EXPORTER_WEB_LISTEN_ADDRESS | Address to listen on for web interface and telemetry. Default is `.:9187` |
| PG_EXPORTER_WEB_TELEMETRY_PATH | Path under which to expose metrics. Default is `./metrics` |
| PG_EXPORTER_DISABLE_DEFAULT_METRICS | Use only metrics supplied from . Value can be or . Default is `.queries.yamltruefalsefalse` |
| PG_EXPORTER_DISABLE_SETTINGS_METRICS | Use the flag if you don't want to scrape . Value can be or . Defauls is `.pg_settingstruefalsefalse` |
| PG_EXPORTER_AUTO_DISCOVER_DATABASES | Whether to discover the databases on a server dynamically. Value can be or . Defauls is `.truefalsefalse` |
| PG_EXPORTER_EXTEND_QUERY_PATH | Path to a YAML file containing custom queries to run. Check out `queries.yaml` for examples of the format. |
| PG_EXPORTER_CONSTANT_LABELS | Labels to set in all metrics. A list of pairs, separated by `commas.label=value` |
| PG_EXPORTER_EXCLUDE_DATABASES | A comma-separated list of databases to remove when `autoDiscoverDatabases` is enabled. Default is empty `string`. |

*[More information about PostgreSQL Server Exporter](https://github.com/wrouesnel/postgres_exporter)
