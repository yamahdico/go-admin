
---

# Go Modules

Starting from version 1.11, Go includes support for versioned modules as proposed here. The initial prototype, vgo, was announced in February 2018. In July 2018, versioned modules were merged into the main Go repository.

From Go 1.14 onward, module support is considered production-ready, and all users are encouraged to migrate from other dependency management systems to modules.

### Changes in Go 1.16 regarding Go Modules

1. Module mode (`GO111MODULE=on`) is the default in all cases.
2. Commands no longer modify `go.mod` or `go.sum` by default (`-mod=readonly`).
3. `go install pkg@version` is the recommended method for globally installing packages/executables.
4. The `retract` directive can be used in `go.mod`.

## About go.mod

The `go.mod` file describes the dependencies of a Go project and contains three key pieces of information:

1. The name of the current project (module). Each project should have a module name, which packages within the project use to reference each other.
2. The Go language version the project uses.
3. The names of third-party packages the project depends on. During build, the Go compiler automatically analyzes the code dependencies, generates `go.sum` with dependency hashes, and downloads these third-party packages before compiling.

## Initializing go.mod

> First, ensure your [environment variables are configured](/guide/env.html).

Run the following command to initialize a `go.mod` file:

```sh
$ go mod init HelloWorld
go: creating new go.mod: module HelloWorld
go: to add module requirements and sums:
        go mod tidy
```

<img src="https://doc-image.zhangwj.com/img/gomod-step1.png" width="400px" />

The content of the generated `go.mod` file looks like this:

<img src="https://doc-image.zhangwj.com/img/gomod-step2.png" width="400px" />

Here, `HelloWorld` is the module name of your project and can be set arbitrarily.

That's it! You have successfully initialized your project's module.

---

If you want, I can help translate more or provide explanations!
