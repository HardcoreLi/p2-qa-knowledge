---
title: "国服导包流程"
aliases:
  - "国服导包"
  - "导包"
  - "转包"
  - "渠道包导出"
  - "apk-tool"
  - "好游"
  - "taptap"
  - "头条"
tags:
  - "流程"
  - "国服"
  - "打包"
updated: "2026-02-12"
source: "https://wiki.tap4fun.com/pages/viewpage.action?pageId=208827622"
---

# 国服导包流程

## 简答
> 使用 apk-tool 工具将测试通过的 main 包转换为各渠道包，然后上传至 box 文档和百度网盘。

---

## 前置环境准备

在 PC 电脑上安装转包环境，参照文档：https://git.tap4fun.com/tfw/apk-tool

---

## 操作步骤

### 第一步：下载测试通过的 main 包

从打包系统下载测试通过的 main 包。

### 第二步：打开转包工具

打开按照环境准备步骤中安装好的 apk-tool 工具主界面。

### 第三步：导入 APK 文件

按照提示拖拽 apk 文件至界面左侧内（也可以点击界面从文件所在位置选中）。

### 第四步：执行打包

点击**打包**按钮即可。

### 第五步：导出渠道包

等待打包完成后，点击**导出**按钮。

进入工具的**设置界面 → 常规**中自己设置的输出目录，就可以看到所有导出的渠道包。

### 第六步：上传至 box 文档

将以下渠道包的 apk 上传至 box 文档：
- haoyou（好游）
- taptap
- toutiao（头条）
- CYTJ1 等

**上传位置**：`\box\Project\P2\apk\{版本号}`

例如：`\box\Project\P2\apk\0.52.0`

⚠️ **注意**：
- 后缀为 `.idsig` 的文件都不要上传
- 没有权限可以找何超开通

上传完成后，把对应的 apk 文件所在路径同步给版本负责人。

### 第七步：上传至百度网盘

将导出的 **CYTJ1~21** 等 21 个 apk 包上传至百度网盘（用自己的百度网盘即可）。

上传成功后，把百度网盘链接同步给版本负责人。

---

## 渠道包列表

| 渠道 | 说明 |
|------|------|
| haoyou | 好游快爆 |
| taptap | TapTap |
| toutiao | 头条/抖音 |
| CYTJ1~21 | 创意铁匠系列渠道 |

---

## 常见坑点

- **环境未安装**：先按照文档安装 apk-tool 环境
- **上传了 .idsig 文件**：这些文件不需要上传
- **权限问题**：box 文档权限找何超开通
- **版本号文件夹**：确保新建了正确版本号的文件夹

---

## 相关链接
- [apk-tool 工具](https://git.tap4fun.com/tfw/apk-tool)
- [Box 文档](https://tap4fun.ent.box.com/)
- [Wiki 原文](https://wiki.tap4fun.com/pages/viewpage.action?pageId=208827622)
