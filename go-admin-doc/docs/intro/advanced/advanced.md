````markdown
---
nav:
  title: Development
  order: 2
group:
  title: Advanced
  order: 4
title: actions
toc: content
---

## Actions Mode

:::warning
Note  
The `go-admin` service supports two handling modes:
:::

- For complex business logic, you can use the **"Standard Mode"**.

# Generate Code and Configure Role Permissions via Developer Tools

## Step 1: Generate Code with Developer Tools

1. First, insert a structured SQL table definition:

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
````

2. In the field info panel, select the operations you want to enable—for example, check the box if you want to allow querying.

3. After selecting the desired options, click "Generate Code" to automatically generate both the Go and Vue files. To make the menu visible, also click "Generate Config".

## Step 2: Rebuild and Run Frontend & Backend

```shell
go build .

npm run dev
```

## Step 3: Insert API Definitions into the Database

After building, the menu will appear, but roles still cannot access it. You must define API endpoints and write them to the database:

```shell
./go-admin server -c config/settings.yml -a true
```

The `-a` flag instructs the system to check for APIs and insert any that do not yet exist into the database.

## Step 4: Assign API Permissions

Once APIs are inserted, go to **API Management** → locate the relevant API → assign a title and type:

* `BUS` = business type
* `SYS` = system type

## Step 5: Assign Menu Permissions

Navigate to **Menu Management** → locate the related menu item → click "Edit" → configure permissions:

* Assign "Query API" to the list menu
* Assign "Edit API" to the edit menu
* Assign "Delete API" to the delete button menu

## Step 6: Create and Assign Roles

1. Go to **Role Management**, create a role and assign access to the new page.
2. Create a user and assign them to the role.
3. Now the user has access to the generated menu and related role-based permissions.

```
