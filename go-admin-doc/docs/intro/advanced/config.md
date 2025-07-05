
---

## Creating Configuration Files for Different Environments

The default configuration file of go-admin is located in the `config` folder as `settings.yml`.

Users can create different configuration files for different environments:

```sh
# Create configuration file for development environment
settings.dev.yml

# Create configuration file for production environment
settings.prod.yml

# Create configuration file for testing environment
settings.test.yml
```

## Adding Custom Configuration Items

Under the `settings` node, add `extend`, and then create the custom configuration items you need under it.

```yml
settings:
  extend: # Description for extension items
    demo:
      name: data
```

Then, open the file `config/extend.go`

Add the following code:

```go
type Extend struct {
	Demo Demo   // Configure the structure corresponding to the config file here
}

type Demo struct {
	name string
}
```

That’s it.

## Reading Custom Configuration Items

Add the import in the file where you want to use the config:

```go
import (
    extConfig "go-admin/config"
)
```

Then use the following code directly in your usage place:

```go
    fmt.Println("extConfig.ExtConfig.Demo.Name", extConfig.ExtConfig.Demo.Name)
```

---

