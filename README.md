# 乡村闲置资源

## 目录

1. [开发流程](#开发流程)
    1. [需求分析](#1-需求分析)
        1. [必要需求](#必要需求)
        2. [重要需求](#重要需求)
        3. [期望需求](#期望需求)
        4. [非功能需求](#非功能需求)
        5. [用户需求调查](#用户需求调查)
    2. [系统分析与设计](#2-系统分析与设计)
        1. [功能模块划分](#功能模块划分)
        2. [页面设计](#页面设计)
            - [首页](#首页)
            - [注册/登录页](#注册登录页)
            - [资源发布页](#资源发布页)
            - [资源列表页](#资源列表页)
            - [资源详情页](#资源详情页)
            - [搜索页](#搜索页)
            - [个人主页](#个人主页)
            - [收藏页](#收藏页)
            - [设置页](#设置页)
            - [浏览历史页](#浏览历史页)
        3. [数据库设计](#数据库设计)
            - [user(用户表, 用户基本信息)](#user用户表-用户基本信息)
            - [resource(资源表, 资源基本信息)](#resource资源表-资源基本信息)
            - [media(媒体表, 资源拓展信息如图片视频等)](#media媒体表-资源拓展信息如图片视频等)
            - [log(日志表, 记录用户操作日志)](#log日志表-记录用户操作日志)
            - [comment(评论表, 记录用户对资源的评价)](#comment评论表-记录用户对资源的评价)
        4. [技术架构设计](#技术架构设计)
            - [整体架构](#整体架构)
            - [系统组件](#系统组件)
            - [交互模式](#交互模式)
            - [安全性](#安全性)
            - [开发和部署工具](#开发和部署工具)
    3. [技术选型](#3-技术选型)
    4. [接口设计](#4-接口设计)
        - [用户相关](#用户相关)
        - [资源相关](#资源相关)
        - [文件相关](#文件相关)
        - [评论相关](#评论相关)
    5. [开发计划](#5-开发计划)
    6. [测试](#6-测试)
    7. [部署上线](#7-部署上线)
    8. [维护迭代](#8-维护迭代)

2. [API示例](#API示例)
    1. [注册登录](#注册登录)
    2. [修改用户信息](#修改用户信息)
    3. [发布资源](#发布资源)
    4. [修改资源信息](#修改资源信息)
    5. [删除资源](#删除资源)
    6. [获取资源列表](#获取资源列表)
    7. [上传文件](#上传文件)
    8. [访问文件](#访问文件)
    9. [删除文件](#删除文件)

## 开发流程

## 1 需求分析

### 必要需求

- [ ] 出租/租赁资源
- [ ] 资源展示
- [ ] 账号系统

### 重要需求

- [ ] 资源审核
- [ ] 反馈评价
- [ ] 客服和帮助中心
- [ ] 地图定位
- [ ] 系统通知

### 期望需求

- [ ] AR/VR展示
- [ ] 社区交流
- [ ] 个性化推荐
- [ ] 资源评估
- [ ] 信用评分

### 非功能需求

- [ ] 日志记录
- [ ] 数据加密

### 用户需求调查

- [ ] TODO

## 2 系统分析与设计

### 功能模块划分

- [ ] 用户模块
- [ ] 资源模块
- [ ] 评价模块
- [ ] 日志模块

### 页面设计

#### 首页

1. 功能
    1. 资源展示
    2. 资源搜索
    3. 资源推荐
2. 页面跳转关系
    1. [搜索页](#搜索页)
    2. 热门/推荐资源[资源详情页](#资源详情页)
    3. [资源发布页](#资源发布页)

#### 注册/登录页

1. 功能
    1. 用户注册
    2. 用户登录
2. 页面跳转关系
    1. [首页](#首页)

#### 资源发布页

1. 功能
    1. 资源发布
    2. 资源编辑

#### 资源列表页

1. 功能
    1. 资源展示
    2. 资源筛选
    3. 资源排序
2. 页面跳转关系
    1. [资源详情页](#资源详情页)
    2. [资源发布页](#资源发布页)

#### 资源详情页

1. 功能
    1. 资源展示
    2. 资源评论
    3. 资源收藏
    4. 联系出租方
2. 页面跳转关系
    1. 资源所属用户[个人主页](#个人主页)

#### 搜索页

1. 功能
    1. 资源搜索
    2. 资源筛选
    3. 资源排序
2. 页面跳转关系
    1. 搜索结果[资源列表页](#资源列表页)

#### 个人主页

1. 功能
    1. 用户信息
    2. 用户资源
    3. 用户收藏
    4. 浏览历史
    5. 用户评价
    6. 用户设置
2. 页面跳转关系
    1. 已发布/编辑中资源[资源详情页](#资源详情页)
    2. [资源发布页](#资源发布页)
    3. [收藏页](#收藏页)
    4. [浏览历史页](#浏览历史页)
    5. [设置页](#设置页)

#### 收藏页

1. 功能
    1. 查看收藏
    2. 取消收藏
2. 页面跳转关系
    1. [资源详情页](#资源详情页)

#### 设置页

1. 功能
    1. 修改用户信息
    2. 其他设置

#### 浏览历史页

1. 功能
    1. 查看浏览历史
    2. 管理浏览历史
2. 页面跳转关系
    1. [资源详情页](#资源详情页)

### 数据库设计

#### user(用户表, 用户基本信息)

 ```sql
 create table user
 (
     id         int auto_increment
         primary key,
     phone      char(11) null,
     name       varchar(255) null,
     avatar     varchar(255) null,
     role       varchar(255) null,
     created_at datetime default CURRENT_TIMESTAMP null,
     updated_at datetime default CURRENT_TIMESTAMP null on update CURRENT_TIMESTAMP
 );
 ```

#### resource(资源表, 资源基本信息)

 ```sql
 create table resource
 (
     id          int auto_increment
         primary key,
     name        varchar(255) null,
     type        varchar(255) null,
     duration    varchar(255) null,
     user_id     int null,
     description text null,
     price       decimal(10, 2) null,
     view        int null,
     created_at  datetime default CURRENT_TIMESTAMP null,
     updated_at  datetime default CURRENT_TIMESTAMP null on update CURRENT_TIMESTAMP,
     constraint resource_pk
         unique (name, user_id),
     constraint resource_ibfk_1
         foreign key (user_id) references user (id)
 );

create index user_id
    on resource (user_id);
 ```

#### media(媒体表, 资源拓展信息如图片视频等)

```sql
create table media
(
    id          int auto_increment
        primary key,
    resource_id int null,
    url         varchar(255) null,
    created_at  datetime default CURRENT_TIMESTAMP null,
    constraint media_ibfk_1
        foreign key (resource_id) references resource (id)
);

create index resource_id
    on media (resource_id);
 ```

#### log(日志表, 记录用户操作日志)

 ```sql
 create table log
 (
     id          int auto_increment
         primary key,
     user_id     int null,
     resource_id int null,
     action      varchar(255) null,
     created_at  datetime default CURRENT_TIMESTAMP null,
     constraint log_ibfk_1
         foreign key (user_id) references user (id),
     constraint log_ibfk_2
         foreign key (resource_id) references resource (id)
 );

create index resource_id
    on log (resource_id);

create index user_id
    on log (user_id);
 ```

#### comment(评论表, 记录用户对资源的评价)

 ```sql
 create table comment
 (
     id          int auto_increment
         primary key,
     user_id     int null,
     resource_id int null,
     content     text null,
     created_at  datetime default CURRENT_TIMESTAMP null,
     constraint comment_ibfk_1
         foreign key (user_id) references user (id),
     constraint comment_ibfk_2
         foreign key (resource_id) references resource (id)
 );

create index resource_id
    on comment (resource_id);

create index user_id
    on comment (user_id);
 ```

### 技术架构设计

#### 整体架构

单体架构+前后端分离

#### 系统组件

- 用户界面层
- 业务逻辑层
- 数据访问层

#### 交互模式

- RESTful API
- json数据交互

#### 安全性

- 数据加密
- 用户认证

## 3 技术选型

### 前端

- uni-app
- Vue.js

### 后端

- Java Spring Boot

### 数据库

- MySQL

### 服务器

- Ubuntu 22.04 LTS Server

### 安全

- HTTPS
- MD5

### 开发和部署工具

- Git
- Docker

## 4 接口设计

### 用户相关

1. 注册/登录[示例](#注册登录)
    - URL: /user/login
    - Method: POST
    - Request:
        - phone: 手机号
        - role: 角色
    - Response:
        - data:
            - id: 用户ID
            - phone: 手机号
            - name: 用户名
            - avatar: 头像(url)
            - role: 角色

2. 更新用户信息[示例](#修改用户信息)
    - URL: /user/update/{id}
    - Method: PUT
    - Request: id必须, 剩余参数可选
        - id: 用户ID
        - phone: 手机号
        - name: 用户名
        - avatar: 头像(通过Media接口上传)
        - role: 角色
    - Response:
        - data: 用户信息
            - id: 用户ID
            - phone: 手机号
            - name: 用户名
            - avatar: 头像(url)
            - role: 角色

### 资源相关

1. 获取资源列表
    - URL: /resource/list
    - Method: GET
    - Request:
        - page: 页码
        - size: 每页数量
    - Response:
        - data: 资源列表
            - item: 资源信息
                - id: 资源ID
                - name: 资源名称
                - type: 资源类型
                - user: 发布者
                - media: 媒体列表
                    - item: 媒体url
                        - url: url
                - description: 描述
                - price: 价格
                - view: 浏览量
                - duration: 租赁时长

2. 发布资源[示例](#发布资源)
    - URL: /resource/publish
    - Method: POST
    - Request:
        - name: 资源名称
        - type: 资源类型
        - userId: 发布者id
        - description: 描述
        - price: 价格
        - view: 浏览量
        - duration: 租赁时长
        - _media: 媒体资源通过Media接口上传_
    - Response:
        - data: 资源信息
            - id: 资源ID
            - name: 资源名称
            - type: 资源类型
            - user: 发布者
            - media: 媒体列表
                - item: 媒体url
                    - url: url
            - description: 描述
            - price: 价格
            - view: 浏览量
            - duration: 租赁时长

3. 修改资源信息[示例](#修改资源信息)
    - URL: /resource/update/{id}
    - Method: PUT
    - Request: id必须, 剩余参数可选
        - id: 资源ID
        - name: 资源名称
        - type: 资源类型
        - description: 描述
        - price: 价格
        - view: 浏览量
        - duration: 租赁时长
        - _media: 媒体资源通过Media接口上传_
    - Response:
        - data: 资源信息
            - id: 资源ID
            - name: 资源名称
            - type: 资源类型
            - user: 发布者
            - media: 媒体列表
                - item: 媒体url
                    - url: url
            - description: 描述
            - price: 价格
            - view: 浏览量
            - duration: 租赁时长

4. 删除资源[示例](#删除资源)
    - URL: /resource/delete/{id}
    - Method: DELETE
    - Request: id必须
        - id: 资源ID

### 文件相关

1. 上传文件[示例](#上传文件)
    - URL: /media/upload
    - Method: POST
    - Request:
        - file: 文件
        - resourceId: 资源ID

2. 访问文件[示例](#访问文件)
    - URL: /media/{prefixPath:.+}/{filename:.+}
    - Method: GET
    - Request:
        - prefixPath: 文件路径(头像为avatar, 资源图片/视频为对应资源id)
        - filename: 文件名

3. 删除文[示例](#删除文件)
    - URL: /media/delete/{prefixPath:.+}/{filename:.+}
    - Method: DELETE
    - Request:
        - prefixPath: 文件路径(头像为avatar, 资源图片/视频为对应资源id)
        - filename: 文件名

### 评论相关

TODO

## 5 开发计划

## 6 测试

## 7 部署上线

## 8 维护迭代

## API示例

### 注册登录

```javascript
const data = {
    phone: "11122223333",
}
fetch("http://kimin.cn:8080/user/login", {
    method: "POST",
    body: JSON.stringify({data})
})
```

### 修改用户信息

```javascript
const data = {
    id: 1,
    name: "张三",
}
fetch("http://kimin.cn:8080/user/update/1", {
    method: "PUT",
    body: JSON.stringify({data})
})
```

### 发布资源

```javascript
const data = {
    name: "资源1",
    type: "类型1",
    userId: 1,
}
fetch("http://kimin.cn:8080/resource/publish", {
    method: "POST",
    body: JSON.stringify({data})
})
```

### 修改资源信息

```javascript
const data = {
    id: 1,
    name: "资源2",
    type: "类型2",
}
fetch("http://kimin.cn:8080/resource/update/1", {
    method: "PUT",
    body: JSON.stringify({data})
})
```

### 删除资源

```javascript
fetch("http://kimin.cn:8080/resource/delete/1", {
    method: "DELETE",
})
```

### 获取资源列表

```javascript
fetch("http://kimin.cn:8080/resource/list", {
    method: "GET",
})
```

### 上传文件

```javascript
const data = {
    file: null, //通过input["file"].files[0]获取
    resourceId: 1,
}
fetch("http://kimin.cn:8080/media/upload", {
    method: "POST",
    body: JSON.stringify({data})
})
```

### 访问文件

```html
<img src="http://kimin.cn:8080/media/avatar/default.png" alt="avatar">
```

### 删除文件

```javascript
fetch("http://kimin.cn:8080/media/delete/1/1.png", {
    method: "DELETE",
})
```
