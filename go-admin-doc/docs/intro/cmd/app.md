
---

## Video Tutorial

[【go-admin-pro】Subscription Edition app Command (& also applicable to go-admin)](https://www.bilibili.com/video/BV1Wa411o7Zr?spm_id_from=333.999.0.0)

## Creating an app

To keep the project structure and ideas clear and to help you manage your own projects better, `go-admin` introduces the concept of an **app**. After downloading the project, it is recommended not to change the code inside the `admin` app, so you can easily upgrade versions later and just focus on your own business logic. For this, we provide an `app` command.

You can create a new app using the `app` command. Below is an example creating an app named `appname`. In practice, replace `appname` with your business module name.

```sh
$ ./go-admin app -n appname
```

This command creates a new folder under the `app` directory in the `go-admin` project. After that, you can generate business code in this folder. The module will also be automatically registered in the go-admin startup configuration.

---

If you want me to translate more or help with something else, just ask!
