---
title: "线上与测试环境 DLC 操作流程"
aliases:
  - "dlc"
  - "dlc测试"
  - "热更测试"
  - "资源更新"
  - "dlc构建"
  - "本地entrance"
  - "EntranceViewer"
tags:
  - "流程"
  - "测试"
  - "DLC"
updated: "2026-02-12"
source: "https://wiki.tap4fun.com/pages/viewpage.action?pageId=135241609"
---

# 线上与测试环境 DLC 操作流程

## 简答
> 从60版本开始，版本功能更新方式由发整包变为 DLC 热更。线上环境通过 TGS 配置，测试环境通过本地 Entrance.json 文件配置。

---

## 前言

从60版本开始，版本功能更新方式由发整包变为 DLC 热更，导致线上与当前功能版本内容存在不兼容情况。若共用 entrance 配置，会出现无法进入游戏或游戏内修改内容异常等问题。

---

## 一、DLC 构建

### 打包机信息

| 环境 | 打包机地址 | 账户名 | 密码 | 安卓工程 | iOS工程 | 构建分支 |
|------|-----------|--------|------|----------|---------|----------|
| **Gold** | http://172.20.110.28:8080/ | p2admin | p2admin123123 | p2-android-asset-bundle | p2-ios-asset-bundle | hotfix/hotfix_av_high/hotfix_unified |
| | http://172.20.110.10:8080/ | 同上 | 同上 | 同上 | 同上 | hotfix_unified |
| **GoldCN** | http://172.20.110.8:8080/ | 同上 | 同上 | p2-android-asset-bundle | p2-ios-asset-bundle | hotfix_cn/hotfix_cn_av_high/hotfix_cn_unified |
| **Beta** | http://172.20.110.14:8080/ | 同上 | 同上 | 同上 | 同上 | 功能测试分支 |

### 注意事项
1. **国服、国际服打包机不可混用**
2. **10打包机**用于打正式包（分支为 hotfix_unified），也可用于打 hotfix_unified 分支的 dlc，但最好不要打其他分支的 dlc
3. **Beta 打包机**只可构建测试环境的功能 dlc，不可构建线上 dlc（构建成功后不会上传到线上 CDN 库）

---

## 二、DLC 上传同步与配置

### a. 线上国际服

1. **构建成功与上传**：构建成功后在 develop 群内通知，上传成功后在 CDN 群内通知
2. **配置**：进入 TGS 内更新对应客户端版本的相关 entrance 配置
3. **验证**：
   - 对应版本线上包进入游戏内
   - 打开 fps 栏
   - entrance 项后方**不显示** local 的文本提示
   - 展开 entrance 项，可查看 TGS 上配置的 dynamic、ondemand、hotfix、patch 等内容版本号
   - 游戏内验证修改内容

### b. 线上国服

步骤与线上国际服一致

### c. 测试环境

1. **构建成功与上传**：构建成功与上传成功的消息均在 develop 群内通知，**不会**在 CDN 群内通知（仅上传本地，不会上传到线上环境）

2. **手动修改本地 json 文件及配置**：

#### 方法一：手动修改 JSON 文件

（1）打开本地 entrance 的 json 文件（可在测试群文件夹内下载）

**需要修改的字段**：

| 字段 | 说明 |
|------|------|
| **client_version** | 填写自己对应测试功能的客户端包版本号 |
| **bundle_id** | 根据渠道填写（见下表） |
| **bundle_source** | 配置 dynamic、ondemand、hotfix、patch 等 |

**Bundle ID 对照表**：

| 渠道 | Bundle ID |
|------|-----------|
| 国际服安卓 | com.tap4fun.ape.gplay |
| 国际服 iOS | com.tap4fun.ape.appstore |
| 国服安卓 | com.tap4fun.ape.cn.main |
| 国服 iOS | com.tap4fun.ape.appstore.cn |
| 国服渠道包 | com.tap4fun.ape.cn.dummy |

**bundle_source 参数说明**：
- **name**：配置项昵称
- **version**：版本号（根据打出来的 dlc 版本号修改，若无相关修改可复用线上版本号）
- **update_type**：更新方式
  - 0 = 关闭更新
  - 1 = 按需下载
  - 2 = 启动时更新
  - 3 = 游戏内更新

（2）保存文件
- 文件名必须为：`Entrance.json`（不能有任何后缀）
- 不建议手动修改，容易有格式、标点符号不对等问题

**小贴士**：因客户端版本号、渠道等测试需求不同会对应不同的 json 内容，建议在本地建一个 entrance 文件夹，分别再建文件夹命名不同版本号、渠道、功能等，每个文件夹里放入对应需求的 json 文件。

（3）导入到设备

**安卓设备**：
- 手机连线到电脑
- 打开路径：`此电脑\{设备名}\内部存储\Android\data\com.tap4fun.ape.gplay\files`
- 把 json 文件放入该文件夹内

**iOS 设备**：
- 电脑端下载爱思助手
- 连线后进入爱思助手内
- 打开应用游戏找到对应 app
- 点击浏览打开文件
- 把 json 文件放入 Documents 文件夹内

#### 方法二：使用 EntranceViewer 工具（推荐）

（1）测试群内下载 EntranceViewer 文件压缩包，解压到本地

（2）双击 EntranceViewer.exe，打开工具弹窗

（3）拖动本地修改了渠道的 json 文件至弹窗上方空白格内

（4）可直接修改版本号、更新方式等，也可删除不用的 entrance 项或新增 bundle 源

（5）修改完成后，点击右下角导出按钮，保存 json 文件到本地

（6）json 文件配置到安卓、iOS 的步骤与手动方法一致

#### EntranceViewer 导入 TGS 配置

1. 点击工具弹窗内 **TGS 导入**按钮
2. 根据当前设备上包渠道修改 bundle id、版本号等
3. 环境可选择：
   - **gold**：线上当前对应渠道、对应版本号的配置
   - **beta**：beta 环境当前对应渠道、对应版本号的配置
4. 点击导入按钮即可立即导入相应的 entrance 配置内容
5. 再根据自己测试需求做对应修改

### 验证

1. 进入游戏内
2. 打开 fps 栏
3. entrance 项后方正确显示 **local** 的文本提示
4. 展开 entrance 项，可查看设备本地配置的 dynamic、ondemand、hotfix、patch 等内容版本号
5. 游戏内验证修改内容

---

## 常见坑点

- **JSON 文件名错误**：必须是 `Entrance.json`，不能有后缀
- **JSON 格式错误**：手动修改容易出错，建议使用 EntranceViewer 工具
- **Beta 打包机打的 DLC 无法用于线上**：只会上传到本地，不会上传到线上 CDN
- **国服国际服打包机混用**：会导致问题
- **忘记检查 fps 栏的 local 标识**：无法确认是否使用了本地配置

---

## 相关链接
- [TGS 后台](https://console.tap4hub.com/login)
- [Wiki 原文](https://wiki.tap4fun.com/pages/viewpage.action?pageId=135241609)
