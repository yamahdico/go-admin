
---

```yaml
nav:
  title: Development
  order: 2
group:
  title: Standards
  order: 5
title: Database Standards
toc: content
```

# Database Standards

This section provides rules for database table fields to use when creating tables. By following the rules below for naming fields, setting types, and comments, you ensure consistency.

## Special Fields

| Field       | Field Name  | Field Type | Description                                                                                                                                                  |
| ----------- | ----------- | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| id          | Primary Key | int(11)    | Record ID                                                                                                                                                    |
| create\_by  | Created By  | int(11)    | Records the creator; used for controlling data permissions                                                                                                   |
| update\_by  | Updated By  | int(11)    | Records who last modified the record                                                                                                                         |
| created\_at | Created At  | timestamp  | Records the creation time; no manual maintenance needed                                                                                                      |
| updated\_at | Updated At  | timestamp  | Records the update time; no manual maintenance needed                                                                                                        |
| deleted\_at | Deleted At  | timestamp  | Records deletion time; no manual maintenance needed. If this field exists, a recycle bin feature is generated. The default value of this field must be null. |

## Supported Databases

### MySQL

```yml
driver: mysql
source: user:password@tcp(127.0.0.1:3306)/dbname?charset=utf8&parseTime=True&loc=Local&timeout=1000ms
```

### SQLite3

```yml
driver: sqlite3
source: sqlite3.db
```

### PostgreSQL

```yml
driver: postgres
source: host=myhost port=myport user=gorm dbname=gorm password=mypassword
```

---

