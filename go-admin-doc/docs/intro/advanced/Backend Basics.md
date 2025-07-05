---

```yaml
nav: Development
group:
  title: Backend Basics
  order: 0
title: Directory Structure
order: 1
toc: content
```

---

First, let's introduce the directory structure of go-admin:

```bash
.
├── Dockerfile
├── LICENSE.md 
├── Makefile 
├── README.en.md 
├── README.md 
├── _config.yml 
├── app               # Application folder
│   ├── admin         # admin application
│   │   ├── apis      # APIs
│   │   ├── models    # Models
│   │   ├── router    # Routes
│   │   └── service   # Business logic
│   └── jobs          # Automated jobs
│       ├── apis      # APIs
│       ├── models    # Models
│       ├── router    # Routes
│       └── service   # Business logic
├── cmd               # Commands
├── common            # Common utilities
├── config            # System configuration
├── docs              # Documentation
├── go.mod
├── go.sum 
├── logger            # Logging package
├── main.go           # Main entry point
├── package-lock.json
├── static            # Static files
├── temp              # Temporary files
├── template          # Template files
├── test              # Tests
└── tools             # Tools
```

The purpose of these directories and files:

* The top-level `go-admin` is the project root directory.
* `app`: Application folder

  * `admin`: admin application

    * `apis`: APIs
    * `models`: Data access layer
    * `router`: Routes and middleware
    * `middleware`: Middleware
* `config`: Configuration files and classes
* `docs`: API documentation
* `static`: Uploaded static files
* `temp`: Temporary log files
* `template`: Template files
* `test`: Tests
* `tools`: Tools
* `main.go`: The main entry point
