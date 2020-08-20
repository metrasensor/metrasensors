# PostgreSQL Sensor

## Installing and running the PostgreSQL Sensor

This package is available for Docker:

```bash
# Start an example database
docker run --net=host -it --rm -e POSTGRES_PASSWORD=password postgres
# Connect to it
docker run --net=host -e DATA_SOURCE_NAME="postgresql://postgres:password@localhost:5432/postgres?sslmode=disable" wrouesnel/postgres_exporter
```

## Environment Variables for PostgreSQL Server Exporter

The following environment variables configure the exporter:

DATA_SOURCE_NAME the default legacy format. Accepts URI form and key=value form arguments. The URI may contain the username and password to connect with.

DATA_SOURCE_URI an alternative to which exclusively accepts the hostname without a username and password component. For example, or .DATA_SOURCE_NAMEmy_pg_hostnamemy_pg_hostname?sslmode=disable

DATA_SOURCE_URI_FILE The same as above but reads the URI from a file.

DATA_SOURCE_USER When using , this environment variable is used to specify the username.DATA_SOURCE_URI

DATA_SOURCE_USER_FILE The same, but reads the username from a file.

DATA_SOURCE_PASS When using , this environment variable is used to specify the password to connect with.DATA_SOURCE_URI

DATA_SOURCE_PASS_FILE The same as above but reads the password from a file.

PG_EXPORTER_WEB_LISTEN_ADDRESS Address to listen on for web interface and telemetry. Default is .:9187

PG_EXPORTER_WEB_TELEMETRY_PATH Path under which to expose metrics. Default is ./metrics

PG_EXPORTER_DISABLE_DEFAULT_METRICS Use only metrics supplied from . Value can be or . Default is .queries.yamltruefalsefalse

PG_EXPORTER_DISABLE_SETTINGS_METRICS Use the flag if you don't want to scrape . Value can be or . Defauls is .pg_settingstruefalsefalse

PG_EXPORTER_AUTO_DISCOVER_DATABASES Whether to discover the databases on a server dynamically. Value can be or . Defauls is .truefalsefalse

PG_EXPORTER_EXTEND_QUERY_PATH Path to a YAML file containing custom queries to run. Check out queries.yaml for examples of the format.

PG_EXPORTER_CONSTANT_LABELS Labels to set in all metrics. A list of pairs, separated by commas.label=value

PG_EXPORTER_EXCLUDE_DATABASES A comma-separated list of databases to remove when autoDiscoverDatabases is enabled. Default is empty string.

*[More information about PostgreSQL Server Exporter](https://github.com/wrouesnel/postgres_exporter)
