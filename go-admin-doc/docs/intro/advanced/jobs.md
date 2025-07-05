
---

```yaml
group:
  title: Advanced Usage
  order: 10
title: Scheduled Tasks
order: 300
toc: content
```

## Scheduled Tasks

The system currently supports two types of scheduled tasks: function type and interface type, to support diverse business needs.

### HttpJob Interface Type

The interface type is quite simple; you just configure the interface URL and the invocation cycle in the system.

### ExecJob Function Type

The function type requires implementing the business logic in code. In this case, you need to use the function type.

The system provides an example:

In the `jobs` directory, you can find a file called `examples.go`, which contains a sample implementation.

Let’s explain the example code:

**Step 1:** Create a struct that implements the `JobCore` interface; for example, `ExamplesOne` implements the `Exec` method:

```go
type ExamplesOne struct {
}

func (t ExamplesOne) Exec(arg interface{}) error {
	str := "JobCore ExamplesOne exec success"
	// TODO: Note that Examples passes a string parameter, so arg.(string) is used here; convert according to your parameter type.
	switch arg.(type) {
	case string:
		if arg.(string) != "" {
			logger.Info(str, arg.(string))
		} else {
			logger.Warn(str, "arg is nil")
		}
		break
	}
	return nil
}
```

**Step 2:** Register this struct in `InitJob`; for example, register `ExamplesOne` by using the struct name as the key and the struct itself as the value. After restarting the project, you can configure and use it in the system:

```go
func InitJob() {
	jobList = map[string]JobsExec{
		"ExamplesOne": ExamplesOne{},
		// ...
	}
}
```

---
