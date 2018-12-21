# fckoa

## 项目介绍
```
git clone git@gitee.com:fckoa/fckoa.git 
```
先克隆项目到本地

先阅读 https://help.aliyun.com/product/50980.html 对阿里云函数计算有基本的概念

复制 fckoa/config/pg.coffee.example 到 fckoa/config/pg.coffee , 修改为自己阿里云postgresql的外网访问

```
cd config
cp pg.coffee.example pg.coffee
```

复制 config/fc.coffee.example 到 config/fc.coffee , 修改为自己的阿里云函数密钥 ， 机房请选择和postgresql同一个机房

复制 config/dev.coffee.example 到 config/dev.coffee 

为了方便数据库的使用，在 fckoa/db/pg.coffee 中自定义了一些助手函数，请查阅源码

运行 ./dev.sh 进入开发调试环境，可以在本机访问

进入 url 目录

```
git clone https://gitee.com/fckoa/demo.git
```

然后参考 url/demo 编写代码。

url 映射规则如下

demo/index.coffee 中的url，默认会加上 /demo/ 的前缀。

demo/test.coffee 中的url，默认会加上 /demo/test/ 的前缀

启动开发服务器并克隆demo后， 可以访问 

* http://127.0.0.1:9999/demo/
* http://127.0.0.1:9999/demo/test/ 
* http://127.0.0.1:9999/demo/query?a=1&b=2

等路径并对照源代码看看，注意结尾的 / 不能被省略 

想创建一个新的工程，可以参考demo，先新建一个Git项目，目录clone到url下。


运行 ./dist.sh 部署更新

首次部署后，请创建HTTP触发器。

![](https://p.gu321.com/20181206013143.png)

## 常见问题

如果在VUE文件中写了CSS文件，但是页面没反应，重启开发服务器即可

## 备份

### 数据库备份

fckoa/sh/backup/pg 目录下，先运行make.coffee,生成config.sh配置文件，然后运行各个备份脚本
