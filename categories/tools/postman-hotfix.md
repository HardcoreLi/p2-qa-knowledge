---
title: "Postman 常用热更操作"
aliases:
  - "postman"
  - "热更"
  - "热更配置"
  - "hotcfg"
  - "schema"
  - "schema id"
tags:
  - "工具"
  - "热更"
  - "配置"
updated: "2026-02-12"
source: "https://wiki.tap4fun.com/pages/viewpage.action?pageId=208827522"
---

# Postman 常用热更操作

## 简答
> Postman 用于热更配置表和修改服务器 schema id。热更配置表需要 Authorization 认证，热更 schema 不需要。

---

## 一、环境准备

1. 从 Postman 官网下载 PC 版并安装
   - 官网地址：https://www.postman.com/
2. 打开 Postman，使用公司邮箱账号登录

---

## 二、热更配置表

### 请求配置

| 项目 | 值 |
|------|-----|
| 请求方式 | POST |
| 请求地址 | http://p2-beta-office-4c1f24329c853d02.elb.us-west-2.amazonaws.com:10014/fix/normal |

### Headers 配置

| KEY | VALUE |
|-----|-------|
| Authorization | eyJ1c2VybmFtZSI6InFhIiwicGVybWlzc2lvbiI6ImFkbWluIiwiZW52aXJvbm1lbnQiOiJiZXRhIiwiY3JlYXRlZF9hdCI6IjIwMjUtMDUtMDlUMDc6NTM6MzkuNDcyMzI5ODE5WiIsImV4cGlyZXNfYXQiOiIyMTI1LTA0LTE1VDA3OjUzOjM5LjQ3MjMyOTgxOVoiLCJyYW5kb21fbm9uY2UiOiJhNDMxZTE3ZDIxOGFlNDY3ODI5Zjk4OGVhNzM3MzcyMiIsInRlbXBfdG9rZW4iOnRydWV9.Xkr3RxTQt9eOMTh1u9aaFTyeNH3XUVilh1W_O0KkQlA= |

### Body 配置

选择 **raw** 格式，填写：

```json
{
  "cmd": "hotcfg",
  "args": ["activity_config"],
  "server_ids": [2902]
}
```

**参数说明**：
- `args`：填写需要热更的配置表名称
- `server_ids`：填写需要热更的服务器 ID

### 执行
点击 **Send** 按钮，等待几秒后返回 `success` 消息即热更成功。

---

## 三、热更服务器 Schema ID

### 请求配置

| 项目 | 值 |
|------|-----|
| 请求方式 | POST |
| 请求地址 | http://p2-beta-office-4c1f24329c853d02.elb.us-west-2.amazonaws.com:10014/ark/server/iapschema |

⚠️ **注意**：不需要填写 Headers 里面的内容

### Body 配置

选择 **raw** 格式，填写：

```json
{
  "server_id": 6002,
  "schema_id": 5,
  "group_id": 3
}
```

**参数说明**：
- `server_id`：填写需要修改 schema id 的服务器
- `schema_id`：填写想要的 schema id（1-6）
- `group_id`：固定填 3

### 执行
点击 **Send** 按钮，等待返回成功消息。

---

## 常见坑点

- **热更配置表忘记填 Authorization**：会返回认证失败
- **热更 schema 填了 Authorization**：不影响，但没必要
- **配置表名称填错**：注意确认正确的配置表名
- **服务器 ID 填错**：确认要热更的目标服务器

---

## 相关链接
- [Postman 官网](https://www.postman.com/)
- [热更相关文档](https://docs.google.com/spreadsheets/d/1ztVd37IO8vFNlGu6NZ0P2O54SJ6X29-7KaInqyEGcGM/edit?gid=62432677#gid=62432677)
- [Wiki 原文](https://wiki.tap4fun.com/pages/viewpage.action?pageId=208827522)
