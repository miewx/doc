# 导读

首先注册[ gitee.com](https://gitee.com/) ，[配置访问公钥](https://gitee.com/profile/sshkeys)

然后运行

```text
bash <(curl -sL https://t.cn/E4MVVWI)
```

留意bash的输出，有启动说明。

项目开发人员申请访问私有仓库权限后，可以删除 fckoa/fckoa/config ，克隆私有的配置文件仓库 

```text
cd  ~/urwork/fckoa/fckoa
rm -rf config
git clone https://gitee.com/fckoa/fckoa.shop.config config
```

否则请参考config的示例配置，修改配置文件，然后push到自己的fork中去。

### 示例项目

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

想创建一个新的工程，可以参考demo，先新建一个Git项目，目录clone到url下。

为了方便数据库的使用，在 fckoa/fckoa/db/pg.coffee 中自定义了一些助手函数，请查阅源码

## 常见问题

#### 前端

如果在VUE文件中写了CSS文件，但是页面没反应，重启开发服务器即可

#### 后端

后端的url不能为空字符串，必须写"/"（如下），访问的结尾也必须带上/

```text
"/":(ctx)->……
```

## 备份

### 数据库备份

fckoa/sh/backup/pg 目录下，先运行make.coffee,生成config.sh配置文件，然后运行各个备份脚本

