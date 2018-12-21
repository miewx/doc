# 导读

## 配置开发环境

先注册GITEE的账户 

{% embed url="https://gitee.com/" %}

然后[配置SSH公钥](https://gitee.com/profile/sshkeys) ，然后运行如下命令（[点此浏览脚本源码](https://t.cn/E4MVVWI)）

```text
bash <(curl -sL https://t.cn/E4MVVWI)
```

该脚本会克隆前端框架h5，后端框架fckoa，登录模块auth已经他们对应

如果需要修改后端框架配置文件，可以fork以下项目。**记得修改为私密项目**

{% embed url="https://gitee.com/fckoa/config" %}

配置文件中 fc.coffee 是 [阿里云函数计算](https://help.aliyun.com/product/50980.html%20)的配置文件，工程可以部署到阿里函数计算。

如果只是开发，可以忽略fc.coffee （不用修改）。

### 克隆演示工程

进入 url 目录

```text
git clone https://gitee.com/fckoa/demo.git
```

然后参考 url/demo 编写代码。

url 映射规则如下

demo/index.coffee 中的url，默认会加上 /demo/ 的前缀。

demo/test.coffee 中的url，默认会加上 /demo/test/ 的前缀

启动开发服务器并克隆demo后， 可以访问

* [http://127.0.0.1:9999/demo/](http://127.0.0.1:9999/demo/)
* [http://127.0.0.1:9999/demo/test/](http://127.0.0.1:9999/demo/test/) 
* [http://127.0.0.1:9999/demo/query?a=1&b=2](http://127.0.0.1:9999/demo/query?a=1&b=2)

等路径并对照源代码看看，注意结尾的 / 不能被省略

### 数据库访问

为了方便数据库的使用，在 fckoa/fckoa/db/pg.coffee 中自定义了一些助手函数，请查阅源码

运行 ./dev.sh 进入开发调试环境，可以在本机访问

### 常见问题

1. 如果在VUE文件中写了CSS文件，但是页面没反应，重启前端开发服务器即可
2. 后端route不能写空的规则 ，可以写`"/": (ctx)-> ……`访问的时候结尾也必须加上 /

### 线上部署

运行 ./dist.sh 部署到阿里云函数

首次部署后，请创建HTTP触发器。

![](https://p.gu321.com/20181206013143.png)

### 备份

### 数据库备份

fckoa/sh/backup/pg 目录下，先运行make.coffee,生成config.sh配置文件，然后运行各个备份脚本

