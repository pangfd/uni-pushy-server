# 简介（Introduction）- uni-pushy-server

`uni-pushy` uni-app 热更新管理平台。

这是 `uni-pushy` 的后端仓库。Github：[uni-pushy-server](https://github.com/SunSeekerX/uni-pushy-server)

基于 `nestjs` +`typeorm`+`redis`+`mysql`+`jsonwebtoken`+`class-validator`+`restful`。

**配套客户端**：**[ uni-pushy-client](https://github.com/SunSeekerX/uni-pushy-client)**

**配套前端**：**[uni-pushy-admin](https://github.com/SunSeekerX/uni-pushy-admin)**

**预览地址**：**[https://uni-pushy.yoouu.cn/](https://uni-pushy.yoouu.cn/)**

> 自行注册账号使用即可体验，对后台配置不熟悉的可以先使用我部署的服务做为测试。
>
> 只需要简单的配置下客户端就行。

**预览文档**：[https://api.uni-pushy.yoouu.cn/docs/](https://api.uni-pushy.yoouu.cn/docs/)

> **uni-app App 整包升级检测：** https://ask.dcloud.net.cn/article/34972
>
> **uni-app App 资源热更新：** https://ask.dcloud.net.cn/article/35667

# ❗ 注意（Notice）

目前应用仍然处于开发阶段，不排除出现重大 **Bug** ，以及 **Api** 升级改造不兼容的可能性。

> 已在公司项目内部使用半年，无明显 bug。

# 快速上手（Getting Started）

克隆仓库（Clone this repo）

```bash
git clone https://github.com/SunSeekerX/uni-pushy-server.git
```

进入项目目录

```bash
cd uni-pushy-server/
```

安装依赖 （Install dependencies），项目根目录下执行

```bash
npm i
# or
yarn
```

> 国内网络安装过慢可以安装 `tbify`， 使用说明：[tbify](https://sunseekerx.yoouu.cn/front-end/npm/#📂-tbify)

## 开发（Dev）

配置环境变量（Set env）,根目录下执行

```bash
mv .env.example .env.development
```

打开 `.env.development`，填写环境变量

```shell
# 服务配置（Server）
# 端口 示例：8081
SERVER_PORT=
# 是否打开文档 示例：true
PRO_DOC=

# OSS 配置（OSS config）
# OSS 地域 示例：oss-cn-hangzhou
OSS_REGION=
# OSS 存储桶名 示例：uni-pushy
OSS_BUCKET=
# OSS 访问域名 示例：https://uni-pushy.oss-cn-hangzhou.aliyuncs.com
OSS_BASE_URL=
# 阿里云 RAM 访问控制配置，用来生成临时账号上传资源到 OSS，需要能访问 OSS 存储桶 示例：acs:ram::1501092948xxxxxx:role/webossuploadrole
ALIYUN_RAM_ARN=
ALIYUN_RAM_ACCESSKEYID=
ALIYUN_RAM_ACCESSKEYSECRET=
# 临时账号有效期（最低15min， 最大60min），单位：min 示例：15
ALIYUN_RAM_TEMPORARY_EXPIRE=

# 数据库配置（DATABASE Config）
DB_HOST=
DB_PORT=
DB_USER=
DB_PASSWORD=
DB_DATABASE=

# Redis 配置（Redis config）
REDIS_HOST=
REDIS_PORT=
REDIS_DB=
REDIS_PASSWORD=
REDIS_PREFIX=

# Token 生成密钥（Token Secret）示例：secret-key
TOKEN_SECRET=

# Api 签名配置（Api sign config）
# Api 签名 RSA 私钥（需要和 Admin 配对）示例：-----BEGIN PRIVATE KEY-----MIICdgIBADANBgkqhkiG9w0BAQEFAASCAmAwggJcAgEAAoGBALvlTV1G0b/q40bYbz/z2cV3tS10oxFiGkr7abO7HF0qp7NXrZMTxj/098sVF32IhOqliQOP9c4arcEFgpHr7mhek5j0xKR7u11DXY6bFKfhOVXdhl9e5s3mc5mhaPgD168txm6a0k+6TyQjHP2pKbzJis54tshfmR3Ley2XfGs3AgMBAAECgYAV6OUejVWEBYW/Cxnd4TdxmUXdKQ6ixke+mpZ2yMjD7GdluEGbNuEVMCF84ta8YqDtI6RYb/7/q4i7S0MwdMx1147YyCS9keZBliNsgnK3drDXAFlVYd1y5YLXrbDMgOiK5W6oIRCQ8455SiuhLd/60lGskeHis+hEhl3WLJ7CYQJBAPltCRSPrXeE5apbRLZq0zXcyUjmEakxe97bpzsjIE9XKwvCU8rISLA0s3HmUuEgqWXqwLvr8snM03WBduPrgQkCQQDA2RnKt2uBPLcZRs5aVo4SusJF9YjDFH/TAjutedOgxP6sYdmQ1iudyVgVE7dCeCKnnJti7rnJsGeXwWrG9to/AkB3+vgkONzjojzrzo1mBkrlHPiCJZGXRqNkV1rBOqtfHvoo5OhzohY9FIzBHF7/xjtWOC9P9jbK1cleO9GZ334pAkA3TkvKSj4Hi00Lb7YATHBkSLEsdRUqtTdPYYWR461gnv5Wm51Un0dU8ghTyxq0clWl8hDSF5qqj++1ot+nfeXrAkEAnMVbHK89dFYQ2yzEMIwF3R+VF0OY/v2ZtL72OOCRexnQ2ISPJokILYg52AH9Esbp8PKVXS5tQ9sQ/nyBsbr1wA==-----END PRIVATE KEY-----
API_SIGN_RSA_PRIVATE_KEY=
# 请求超时时间，单位：秒 示例：15
API_SIGN_TIME_OUT=

# 时区（Time zone）示例：Asia/Shanghai
TZ=
```

**启动**

```bash
npm run serve
# or
yarn serve
```

## 部署（Deploy）

本项目为 nodejs 项目，需要你对 nodejs 项目部署有一定的了解。

### ~~[docker 部署](#docker 部署)~~

> 暂不完善，请使用 `pm2` 部署。

配置环境变量（Set env），根目录下执行

```bash
mv .env.example .env
```

打开 `.env`，填写环境变量，环境变量同开发。

**打包**

```bash
npm run build
```

打包完成生成的静态文件位于 `dist` 目录下，为 `nestjs` 项目。部署时需要带上 `.env` 环境变量文件，以及 `package.json` 依赖说明文件。同时依赖于 `nodejs`。

> 如果只是部署的话安装依赖可以只下载运行时依赖，使用如下命令
>
> ```bash
> npm i --production
> ```

**启动**

```bash
node dist/main
```

### Pm2 部署

[pm2 官网](https://pm2.keymetrics.io/docs/usage/quick-start/)

**全局安装 pm2**

```bash
npm install pm2@latest -g
# or
yarn global add pm2
```

**编译项目**

```bash
npm run build
# or
yarn build
```

**启动项目**

```bash
pm2 start ecosystem.config.js --env production
```

## uni-app 接入（Uni-app deploy）

> 请查看 **[ uni-pushy-client](https://github.com/SunSeekerX/uni-pushy-client)** 说明。

**下面的内容已废弃！！！下面的内容已废弃！！！下面的内容已废弃！！！**

`uni-app` 插件来源：[https://ext.dcloud.net.cn/plugin?id=1643](https://ext.dcloud.net.cn/plugin?id=1643)

改造后的版本位于仓库 `uni-pushy-server/assets/utils/pushy/index.js`

**使用**

在 `app.vue` 中引入，在 `onLaunch` 生命周期接入，初始化成功就能检查更新了。

```vue
<!--
 * @name: 
 * @author: SunSeekerX
 * @Date: 2020-07-20 16:04:27
 * @LastEditors: SunSeekerX
 * @LastEditTime: 2020-07-20 16:51:18
-->

<script>
// #ifdef APP-PLUS
import Pushy from '@/utils/pushy/pushy'
// #endif

export default {
  onLaunch: function () {
    console.log('App Launch')

    // #ifdef APP-PLUS
    const pushy = new Pushy({
      // 项目id
      projectId: '40bb2d3a-f815-4090-91f6-556b1806d52a',
      // 更新地址
      updateUrl: 'http://10.0.0.3:8081',
    })
    pushy.init()
    // #endif
  },

  onShow: function () {
    console.log('App Show')
  },

  onHide: function () {
    console.log('App Hide')
  },
}
</script>
```

初始化参数

|    key    |   说明   |  类型   | 默认 | 必须 |
| :-------: | :------: | :-----: | :--: | :--: |
| projectId | 项目 id  | String  |  ''  | Yes  |
| updateUrl | 更新地址 | String  |  ''  | Yes  |
|  update   | 是否启用 | Boolean | true |  No  |

# 入门篇（Basics）

## 环境准备（Prerequisite）

## 安装（Installation）

## 设置（Configuration）

> [必备] [文件] 软件的设置

# 进阶篇（Advanced)

> [可选] [目录] 又称”开发篇“，提供中高级的开发教程

## ~~docker 部署~~

### ~~自行打包镜像~~

```bash
docker build -t uni-pushy:0.0.1-SNAPSHOT .
```

### ~~Docker hub 镜像~~

`Docker hub` 镜像地址：[https://hub.docker.com/r/1647800606/uni-pushy/tags](https://hub.docker.com/r/1647800606/uni-pushy/tags)

**拉取镜像**

```bash
docker pull 1647800606/uni-pushy:latest
```

**启动镜像**

启动时需要映射外部环境变量文件至容器内部 `/app` 路径下，参考启动命令

```bash
docker run -d -p 8080:3000 -v /w/env/.env:/app/.env --name uni-pushy  1647800606/uni-pushy
```

# **API**（Reference）

> [可选] [目录|文件] 软件 API 的逐一介绍

# TODO

- 检查更新结果缓存
- 接口限流
- 文章：`Nodejs` `rsa` 加密的使用

# 更新日志（Changelog）

## 0.0.1 - 2021-02-12

### 功能（Features）

- 【重要】增加获取最新原生资源的版本号接口

## 0.0.1 - 2021-02-12

### Bug 修复 （Bug Fixes）

- 修复资源列表分页条数不正确

## 0.0.1 - 2020-11-01

### 功能（Features）

- 增加 refresh token 刷新 token 机制，提升体验
- id 去除 “-”

## 0.0.1 - 2020-08-25

- 修复不存在资源依赖无法删除原生资源的 bug

## 0.0.1 - 2020-08-24

- 【重要】移出上传文件到后端接口
- 【重要】增加 `Aliyun STS` 接口，用来生成临时访问的 `AccesId` 给前端直接上传文件到 `OSS`

## 0.0.1 - 2020-08-19

- 增加资源排序

## 0.0.1 - 2020-08-18

- 【重要】增加 `Api sign` 接口加密

## 0.0.1 - 2020-08-15

### 功能（Features）

- 【重要】修改检查更新为查询资源方式，具体是否更新放在用户端进行判断
- 增加资源更新日志

## 0.0.1 - 2020-08-10

### Bug 修复 （Bug Fixes）

- 【重要】修复项目无资源检查更新出错

### 功能（Features）

- 【重要】检查更新新增原生资源校验

- 【重要】项目：新增 `appid` 唯一属性，原来为 `name（项目名）` 为唯一属性

- 【重要】资源：增加了 `wgt` 资源原生版本依赖
- 【重要】资源：确定 `versionCode` 为更新唯一指标
- 【重要】资源：去除 `isFullUpdated` 字段，默认 `wgt` 资源为部分更新，`android`，`ios` 为整包更新
- 【重要】去除数据库`外键约束`， 改为应用层实现外键约束。（提高性能和扩展性）

- 【重要】增加登录注册 `md5` 加密

- 【重要】取消使用 `helmet` 模块，等待后期测试通过再加入
- 代码逻辑优化

# FAQ

## 这是什么？

一个 uni－app 热更新的管理后台。

## 有什么用？

可以用来管理 `uni-app` 热更新的资源和版本。

## 什么是热更新？

装在手机上的 app，不让用户知道就可以增加删除某些功能。快速修复 bug，快速更新功能。

## 有哪些技术用到了热更新？

`React native` ，`flutter `，`uni-app`

## 为什么要做这个？

网上又没有，不只能自己做。

## 后端用的是什么语言框架？

[NestJs](https://nestjs.com/)

## 为什么用 Nestjs ？

其他的我也不会。

## 为什么要用 antd-vue？

至少它一直在更新，你来维护 `element-ui` 吗？

## 为什么有个数据字典模块？

想做一套完整的后台解决方案。

## TS 怎么样？

有一次写 `vue` 尝试了下 `ts`，感觉像 "si" 一样。写 `ts` 还要多些那么多代码，为什么还要确定数据类型，有什么 `interface` ，`type`。

无意中看到了 `nestjs `，写多了 `ts ` 感觉 `js` 像 "si" 一样。

## Nestjs 好用吗？

`Node` 后端要是火起来，`nestjs` 应该是碾压 `express`，`koa2`，`egg.js`。。。

## 为什么要用你写的？

你不想看看我是怎么实现的吗？

## 会持续更新吗？

不会

## 确实学到了一些东西怎么感谢你？

啊这~，你给我点一个 ⭐ 嘛～

## 有问题可以问你吗？

你要是知道你的问题是什么，可以来问我。

## 怎么联系你。

能找到这个项目找不到我的联系方式？
