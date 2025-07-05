
---

## Directory Structure

Let's take a look at the directory structure of **go-admin-ui**:

```bash
.
├── README.md
├── dist
├── index.html
├── jsconfig.json
├── mock
├── package.json
├── prettier.config.js
├── public
│   ├── favicon.ico
│   └── login_left_bg.jpg
├── src
│   ├── App.vue
│   ├── api
│   ├── components
│   ├── icons
│   ├── layout
│   ├── main.js
│   ├── router
│   ├── store
│   ├── style
│   ├── utils
│   └── views
├── vite.config.js
├── .env.production
└── .env.development
```

The purpose of these directories and files is as follows:

* The outermost folder **go-admin-ui** is the project root
* **dist**: bundled files after build
* **index.html**: entry HTML file
* **jsconfig.json**: JS configuration file
* **mock**: mock data
* **package.json**: project dependencies
* **prettier.config.js**: code formatting configuration
* **public**: static files

  * **favicon.ico**: website icon
  * **login\_left\_bg.jpg**: login page background image
* **src**: source code

  * **App.vue**: root Vue component
  * **api**: API interfaces
  * **components**: common components
  * **icons**: icons
  * **layout**: layouts
  * **main.js**: entry JavaScript file
  * **router**: routing
  * **store**: Vuex store
  * **style**: styles
  * **utils**: utilities
  * **views**: pages
* **config**: configuration files and classes
* **docs**: API documentation
* **static**: uploaded static files
* **temp**: temporary log files
* **template**: template files
* **vite.config.js**: Vite configuration file
* **.env.production**: production environment config file
* **.env.development**: development environment config file

---

