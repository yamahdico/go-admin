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
# First, check your node version to ensure it is 16.15.0
node -v
# If not, you need to install node version 16.15.0

# Install dependencies. Note: if installation is slow, you can configure a Taobao mirror
# If installation packages fail,
# delete yarn.lock or package-lock.json and node_modules folder,
# then reinstall.
npm install
# If errors occur or alternatively, you can use
yarn install

# Start the project
npm run dev
```

After the program starts, open your browser and visit [http://localhost:9527/](http://localhost:9527/). You should see the `go-admin` login page.
