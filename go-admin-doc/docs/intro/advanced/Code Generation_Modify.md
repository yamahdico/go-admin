---

```yaml
nav: Development
group:
  title: Code Generation
  order: 4
title: Modify Configuration
order: 1
toc: content
```

---

## Modify Configuration

Now, open the file `config/settings.yml`. This file contains configuration information for the `go-admin` project.

```yaml
  database:
    # Database type: mysql, sqlite3, postgres
    driver: mysql
    # Database connection string. Default options for MySQL: charset=utf8&parseTime=True&loc=Local&timeout=1000ms
    source: user:password@tcp(127.0.0.1:3306)/dbname?charset=utf8&parseTime=True&loc=Local&timeout=1000ms
  gen:
    # Database name used for code generation
    dbname: dbname
    # Path where the frontend code will be generated. Must point to the src folder, relative path
    frontpath: ../go-admin-ui/src
```

Update the database configuration and code generation settings:

1. `gen > dbname`: This setting allows you to fetch all tables under the specified database for code generation.
2. `gen > frontpath`: Specifies where the frontend code should be placed. It must point to the `src` folder.
   **Note:** `go-admin` and `go-admin-ui` must be placed in the same directory level.

We will now create the database table manually using an SQL script.
[See the table structure definition here](/guide/db.html)

```sql
CREATE TABLE `article` (
  `id` int(11) unsigned NOT NULL AUTO_INCREMENT COMMENT 'ID',
  `title` varchar(128) DEFAULT NULL COMMENT 'Title',
  `author` varchar(128) DEFAULT NULL COMMENT 'Author',
  `content` varchar(255) DEFAULT NULL COMMENT 'Content',
  `status` int(1) DEFAULT NULL COMMENT 'Status',
  `publish_at` timestamp NULL DEFAULT NULL COMMENT 'Publish Time',
  `created_at` timestamp NULL DEFAULT NULL,
  `updated_at` timestamp NULL DEFAULT NULL,
  `deleted_at` timestamp NULL DEFAULT NULL,
  `create_by` int(11) unsigned DEFAULT NULL,
  `update_by` int(11) unsigned DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `idx_article_deleted_at` (`deleted_at`) USING BTREE
) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8mb4 COMMENT='Article';
```

Once the database table is created, start the project with:

```bash
go run main.go server -c config/settings.dev.yml
```
