
---

## Configuration File Explanation

If this is your first time using go-admin, you need some initial setup. In other words, you need to configure a go-admin project instance by setting up the database or you can use the built-in sqlite3 experience database (some features like code generation are not supported). Currently, it is recommended to use a MySQL database.

Go to your project working directory and open `config/settings.yml` to configure:

```yml
settings:
  application:
    # Mode: dev (development), test, prod (production)
    mode: dev
    # Server IP, default is 0.0.0.0
    host: 0.0.0.0
    # Service name
    name: testApp
    # Port number
    port: 8000
    readtimeout: 1
    writertimeout: 2
    # Data permission feature switch
    enabledp: false
  logger:
    # Log storage path
    path: temp/logs
    # Log output: file (to file), default (console), others default to console
    stdout: ''  # If enabled, no logs will be written to file, only to console
    # Log level: trace, debug, info, warn, error, fatal
    level: trace
    # Database logging switch; automatically enabled in dev mode
    enableddb: false
  jwt:
    # Token secret key; change for production environment
    secret: go-admin
    # Token expiration time in seconds
    timeout: 3600
  database:
    # Database type: mysql, sqlite3, postgres
    driver: mysql
    # Database connection string; for mysql default charset=utf8&parseTime=True&loc=Local&timeout=5000ms
    source: user:password@tcp(127.0.0.1:3306)/dbname?charset=utf8&parseTime=True&loc=Local&timeout=5000ms
  gen:
    # Database name for code generation
    dbname: dbname
    # Frontend code path for code generation; must point to src folder, relative path
    frontpath: ../go-admin-ui/src
```

In the configuration, you need to modify the following attributes under `database`:

`user:password@tcp(127.0.0.1:3306)/dbname`

* `dbname`: your database name
* `password`: your database password
* `user`: your database username

Also modify the attributes under `application`:

* `logpath`: path for log files, relative to the program directory
