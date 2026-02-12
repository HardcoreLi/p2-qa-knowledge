---
title: "客户端环境异常定位与解决办法"
aliases:
  - "进不去"
  - "客户端问题"
  - "登录失败"
  - "闪退"
  - "卡登录"
  - "黑屏"
  - "internal error"
  - "ErrCodePfCharacterListFailed"
tags:
  - "环境"
  - "问题排查"
  - "客户端"
updated: "2026-02-12"
source: "https://wiki.tap4fun.com/pages/viewpage.action?pageId=192676912"
---

# 客户端环境异常定位与解决办法

## 简答
> 客户端无法进入游戏时，根据具体错误提示进行排查。常见错误包括 internal error、ErrCodePfCharacterListFailed 等。

---

## 一、Loading 界面提示：internal error

### 现象
进游戏 loading 界面提示 "internal error"

### 原因
TGS 内未配对应版本的 entrance，gold、beta、dev 三个环境需分别配置生效

### 解决方案
1. 登录 TGS 后台
2. 检查对应版本的 entrance 配置是否存在
3. 确认 gold、beta、dev 三个环境都已配置

---

## 二、Loading 界面提示：ErrCodePfCharacterListFailed

### 现象
进游戏 loading 界面提示 "ErrCodePfCharacterListFailed"

### 原因
本地 DLC 配置错误，可能是：
- 导出的 json 文件内容错误
- CDN 地址对不上

### 解决方案
1. 检查本地 DLC 配置
2. 确认导出的 json 文件内容正确
3. 确认 CDN 地址正确
4. 参考：[线上与测试环境DLC操作流程教学](https://wiki.tap4fun.com/pages/viewpage.action?pageId=135241609)

---

## 三、游戏内点击活动入口无响应

### 根本原因
未拉取到 fastfollow 内容

### 可能原因及解决方案

**原因1：打包时未勾选 CDN**
- 现在打包工程都是默认勾选，基本不会出问题
- 若确实未勾选，解决方案：
  - 方案A：在 TGS 对应包版本的 entrance 配置中添加一项配置：
    - 类型：fastfollow
    - 版本号：与 ondemand 一致
    - 更新方式：按需下载
  - 方案B：重新出一个勾选了 CDN 的包

**原因2：包内读取 fastfollow 资源异常**
- 若该包构建时勾选了 CDN 且上传成功
- 可能是包内读取 fastfollow 资源异常
- 需要找客户端同学排查

---

## 四、当前版本功能测试包，但游戏内功能完全异常（或新活动开不出来）

### 可能原因
若包的版本号与线上已有包版本号一致，则可能是拉到线上 DLC 内容导致（未配置本地 DLC，均会自动生效 TGS 上配置的 DLC 内容）

### 处理方案

**方案1：升版本号（推荐）**
- 该功能分支升版本号到当前版本
- beta 环境单独配一条 entrance（只配 ondemand、dynamic）
- 例如：线上版本为 65，当前版本为 66，则该功能分支可升版本号至 66 版本，测试环境的 TGS 内配置 0.66.0 的 entrance

**方案2：关闭 hotfix/patch**
- beta 环境该包对应的已有版本 entrance 关闭更新 hotfix、patch
- ⚠️ 缺点：如果有正式 DLC 验证，测试内部验证过程中又会打开，存在反复出现问题的情况

**方案3：配置本地 DLC**
- 给对方设备内配置一个本地 DLC
- 可按照方案1的方式来配置

---

## 通用排查流程

### 1. 检查网络
- 确认网络连接正常
- 测试环境需要连接 VPN
- 检查是否被防火墙拦截

### 2. 检查版本匹配
- 客户端版本与服务器版本是否匹配
- 检查 TGS entrance 配置
- 确认是否需要更新客户端

### 3. 检查服务器状态
- 登录 Kadmin 查看服务器是否运行
- 检查服务器日志是否有报错
- 确认服务器是否在维护

### 4. 检查资源完整性
- 清除本地缓存重新下载
- 检查 DLC 资源是否下载完成
- 确认 CDN 资源是否正常

### 5. 检查账号状态
- 确认账号是否被封禁
- 检查登录方式是否正确
- 尝试其他账号登录

---

## 日志获取

### 安卓
- 路径：`/sdcard/Android/data/包名/files/logs/`
- 使用 adb pull 导出

### iOS
- 通过 Xcode 导出
- 或使用第三方工具

---

## 白名单限制方法

服务器访问限制有两种常用方式：

| 方式 | 说明 | 适用场景 |
|------|------|----------|
| **UDID 白名单** | 使用手机唯一识别码（UDID），加入白名单清单，特定设备可进 | 审核服安卓设备、特定测试设备 |
| **网关限制** | 通过网络环境限制，如内网可进 | 测试环境、内部服务器 |

### 常见白名单场景
- **审核服**：iOS 设备无需白名单，安卓设备需要白名单
- **测试服**：通常需要连接 VPN 或在内网环境
- **特殊功能测试**：部分功能需要特定设备白名单

### 添加白名单
- 联系运营发送 **user ID** 添加白名单
- 如服务器列表中看不到审核服，说明白名单被移除，需重新添加

---

## 常见坑点
- **测试环境必须连 VPN**：否则无法访问测试服务器
- **缓存问题**：很多问题清缓存可以解决
- **版本号看仔细**：entrance 配置的版本号要精确匹配
- **DLC 配置**：未配置本地 DLC 会自动拉取线上配置
- **白名单被移除**：老号登录报错可能是设备白名单被移除

## 相关链接
- [Wiki 原文](https://wiki.tap4fun.com/pages/viewpage.action?pageId=192676912)
- [线上与测试环境DLC操作流程教学](https://wiki.tap4fun.com/pages/viewpage.action?pageId=135241609)
