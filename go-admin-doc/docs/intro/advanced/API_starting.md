
---

## Starting the API

Let's confirm that your go-admin project is configured successfully. Please run the following command:

```bash
go run main.go server -c=config/settings.dev.yml
```

If you see the output as in the image below, congratulations! You have successfully started the server!

<img src="https://doc-image.zhangwj.com/img/serversuccessv1.1.0.png" alt="Server started successfully" width="400px" />

Now the server is running. Open your browser and go to [http://127.0.0.1:8000/](http://127.0.0.1:8000/). You will see the `go-admin` documentation, indicating the server is up and running.

You need to open the configuration file `config/settings.yml`

```yaml
application:
    port: 8000
```

If you want to modify the IP address the server listens on, set it before the port. For example, to listen on all public IPs (useful when running in Vagrant or sharing your project on the network), use:

```yaml
application:
    port: 8080
```

After modifying the config file, you need to restart the server.
https://github.com/go-admin-team/go-admin/issues/new