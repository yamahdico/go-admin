
---

# Environment Variables

## How to configure on Windows

Right-click **My Computer**, select **Properties**;

<img src="https://doc-image.zhangwj.com/img/wodediannaoshuxing.png" width="400px" />

Click **Advanced system settings**;

<img src="https://doc-image.zhangwj.com/img/xitongshuxing.png" width="400px" />

Click **Environment Variables**;

<img src="https://doc-image.zhangwj.com/img/huanjingbianliang1.png" width="400px" />

Click **New**;
Fill in the variable name as `GO111MODULE`, variable value as `on`;

<img src="https://doc-image.zhangwj.com/img/huanjingbianliang2.png" width="400px" />

Click **OK**;
Click **New** again;
Fill in the variable name as `GOPROXY`, variable value as `https://goproxy.cn`;

<img src="https://doc-image.zhangwj.com/img/huanjingbianliang3.png" width="400px" />

Click **OK**;

<img src="https://doc-image.zhangwj.com/img/huanjingbianliang4.png" width="400px" />

Click **OK**;

Reopen `CMD` to take effect immediately.

## How to configure on macOS

```bash
$ go env -w GOPROXY=https://goproxy.cn,direct
$ go env -w GO111MODULE=on
```

## How to configure on Linux

```bash
$ go env -w GOPROXY=https://goproxy.cn,direct
$ go env -w GO111MODULE=on
```

---

If you want, I can help with more translations or explanations!
