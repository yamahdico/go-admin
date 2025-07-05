---

```yaml
nav: Development
group:
  title: Frontend Basics
  order: 0
title: Starting the Service
order: 3
toc: content
```

---

## Starting the Frontend

To start the `go-admin-ui` project, please run the following commands:

```bash
# First, check the Node.js version. It must be 16.15.0
node -v
# If not, install Node.js version 16.15.0

# Install dependencies
# If installation is slow, consider using the Taobao (npmmirror) registry
# If you encounter errors with packages:
# Delete yarn.lock or package-lock.json and the node_modules folder
# Then reinstall the dependencies
npm install
# If there are still errors, try:
yarn install

# Start the project
npm run dev
```

Once the program is running, open your browser and visit [http://localhost:9527/](http://localhost:9527/).
You should see the `go-admin` login page.
