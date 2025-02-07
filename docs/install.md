---
id: install
title: 二次开发
---

> 此安装文档适合具有一定编程能力基础的人员进行二次开发时的环境搭建，如果你是在生产环境部署，推荐 [Docker安装](/docs/install-docker)，
> 如有必要你也可以考虑 [手动部署](/docs/deploy-product/)。

## 依赖环境

- Python 3.6及以上
- Nodejs 12.14 LTS
- Redis 3.x及以上
- 现代浏览器

## 安装步骤
以下安装步骤假设项目安装在一台 `macOS` 系统的 `/data/spug` 目录下。

### 1. Clone项目代码

```shell script
$ git clone https://github.com/openspug/spug /data/spug
```

### 2. 创建运行环境
```shell script
$ cd /data/spug/spug_api
$ python3 -m venv venv
$ source venv/bin/activate
$ pip install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple/
```

### 3. 初始化数据库
默认使用的 `Sqlite` 数据库。
```shell script
$ python manage.py updatedb
````
### 4. 创建默认管理员账户
```shell script
$ python manage.py user add -u admin -p spug.dev -s -n 管理员

# -u 用户名
# -p 密码
# -s 超级管理员
# -n 用户昵称
```

### 5. 启动 api 开发环境服务
```shell script
$ python manage.py runserver
```

### 6. 安装前端依赖
可以把 `npm` 用 `yarn` 或 `cnpm` 代替。
```shell script
$ cd /data/spug/spug_web
$ npm install --registry=https://registry.npm.taobao.org
```

### 7. 启动前端
```shell script
$ npm start
```

### 8. 访问测试
正常情况下 `npm start` 会自动在浏览器中打开项目，如果未打开可以在浏览器中输入 `http://localhost:3000` 访问。  
如果你按照上边的文档执行的话，在第 4 步创建了默认的管理员账户：  
```
用户名：admin  
密码：spug.dev
```

### 9. 其他可选服务
通过以上步骤已经可以正常访问 `Spug` 了，但一些功能依赖额外的服务，请参考以下文档
- [批量执行的任务卡住无法看到执行输出](/docs/install-error#%E6%89%B9%E9%87%8F%E6%89%A7%E8%A1%8C%E7%9A%84%E4%BB%BB%E5%8A%A1%E5%8D%A1%E4%BD%8F%E6%97%A0%E6%B3%95%E7%9C%8B%E5%88%B0%E6%89%A7%E8%A1%8C%E8%BE%93%E5%87%BA)
- [任务计划模块添加的任务不会执行](/docs/install-error#%E4%BB%BB%E5%8A%A1%E8%AE%A1%E5%88%92%E6%A8%A1%E5%9D%97%E6%B7%BB%E5%8A%A0%E7%9A%84%E4%BB%BB%E5%8A%A1%E4%B8%8D%E4%BC%9A%E6%89%A7%E8%A1%8C)
- [监控中心模块添加的监控任务不会执行](/docs/install-error#%E7%9B%91%E6%8E%A7%E4%B8%AD%E5%BF%83%E6%A8%A1%E5%9D%97%E6%B7%BB%E5%8A%A0%E7%9A%84%E7%9B%91%E6%8E%A7%E4%BB%BB%E5%8A%A1%E4%B8%8D%E4%BC%9A%E6%89%A7%E8%A1%8C)
## 常见安装问题
请参考 [安装问题](/docs/install-error)
