
---

## Configuration File Explanation

In development mode, the configuration file is `.env.development`, and in production mode, the configuration file is `.env.production`. Both configuration files have the same set of options, only the values differ.

### Configuration Options Explanation

```bash
# just a flag
ENV = 'development'

# base API
VUE_APP_BASE_API = 'http://localhost:8000'
```

`ENV` is the environment variable. If your environment is development, this value should be `development`. If it's production, then it should be `production`.

`VUE_APP_BASE_API` is the backend service address. If your backend service is not running on the local machine, you need to modify this option.

### Modifying the Development Environment Configuration File

If your backend service runs on the local machine, modify the configuration file like this:

```bash
# just a flag
ENV = 'development'

# base API
VUE_APP_BASE_API = 'http://localhost:8000'  # Modify this option
```

If your backend service runs on another machine, modify the configuration file like this:

```bash
# just a flag
ENV = 'development'

# base API
VUE_APP_BASE_API = 'http://<IP-of-the-running-machine>:8000'  # Replace <IP-of-the-running-machine> with the actual IP address
```

Make sure that the port on the running machine is open.

### Modifying the Production Environment Configuration File

When deploying the application, modify the configuration file as follows:

```bash
# just a flag
ENV = 'production'

# base API
VUE_APP_BASE_API = 'http://<IP-or-domain>:8000'  # Replace <IP-or-domain> with your server IP or domain
```

In production, the address should be changed to the domain name or the server IP. If it's a domain name, make sure it resolves to the server IP.

Also, ensure the port on the running machine is open.

### Common Issues

If the frontend captcha doesn't load or the API reports errors, check the configuration file corresponding to your environment:

* For development, check and modify `VUE_APP_BASE_API` in `.env.development`.
* For production, check and modify `VUE_APP_BASE_API` in `.env.production`.