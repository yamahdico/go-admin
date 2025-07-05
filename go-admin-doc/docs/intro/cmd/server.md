
---

# Server

## Video Tutorial

[【go-admin-pro】How to elegantly add APIs (& applicable to go-admin)](https://www.bilibili.com/video/BV1pN4y157wp?spm_id_from=333.999.0.0)

## Starting the Service

`go-admin` provides the `server` command to start the API project; it is used when launching the program.

First, you need to compile the program by running the following command in the project root directory:

```sh
go build
```

Then run the command `go-admin server` to start the project.

## Configuration File

A common question is how to load the project's configuration file.

By default, `go-admin server` loads the `config/settings.yml` file.

However, the author considered different scenarios, so they provided an option to specify the config file via the `-c` parameter, allowing you to modify or specify the config file you need.

For example:

```sh
$ go-admin server -c config/setting.xxxx.yml
# Note: config/setting.xxxx.yml can be changed to your local environment config file path.
```

**Reminder:** Since the above commands use the binary named `go-admin` by default, if you compile the project with `go build`, the binary might have a different name depending on your system.

For example, if your binary is named `sss-admin.exe`, you should use:

```sh
$ sss-admin.exe server
```

Adjust the command according to your local environment and binary name.

## Automatic API Registration

To make it easier to add APIs, `go-admin` provides the `-a` parameter:

```sh
# When starting, the system automatically checks if all APIs in the router are recorded in the sys_api table.
# Missing APIs will be automatically added.
# The default value of -a is false, so it can be omitted.
$ go-admin server -a true
```

## Reminder

The above describes starting the project via the compiled binary.

During development, you can also start the project directly using:

```sh
$ go run main.go server
```

---

Let me know if you want a more concise summary or help with usage examples!
