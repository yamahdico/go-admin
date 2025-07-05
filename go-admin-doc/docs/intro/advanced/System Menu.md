---

```yaml
nav: Development
group:
  title: Code Generation
  order: 4
title: Bind Menu to API
order: 4
toc: content
```

---

## Configure System Menu to Bind with API

1. First, you need to automatically register the newly added APIs in the API Management section.

You can do this directly by running the following command:

```sh
$ go run main.go server -c config/settings.dev.yml -a false
```

In the `server` command, we have added a new `-a` parameter. By default, it is set to `false`. When set to `true`, the system will scan and create all available APIs in the current application.

2. Go to **API Management** and edit the newly registered API information.
