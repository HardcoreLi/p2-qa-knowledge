---
title: "AAB 包安装方法"
aliases:
  - "aab"
  - "aab安装"
  - "aab包"
  - "bundletool"
  - "安装aab"
  - "一键安装"
tags:
  - "环境"
  - "安装"
  - "安卓"
updated: "2026-02-12"
source: "https://wiki.tap4fun.com/pages/viewpage.action?pageId=71782874"
---

# AAB 包安装方法

## 简答
> AAB 包有两种安装方式：PC端通过 install.bat 脚本安装，手机端通过无线调试一键安装。

---

## 方式一：PC 端安装（推荐）

### 一、JDK 环境安装

#### 1. 下载安装 JDK
- 下载 jdk-16_windows-x64_bin.exe（Wiki 附件）
- 安装在推荐目录下即可

#### 2. 验证安装
打开 cmd 命令提示符，输入以下命令验证：
```bash
java
javac
java -version
```
如果提示"java不是内部命令"，需要手动配置环境变量。

#### 3. 配置环境变量（如需）

**JAVA_HOME 环境变量：**
- 右击"我的电脑" → 属性 → 高级系统设置 → 环境变量
- 系统变量中点击新建
- 变量名：`JAVA_HOME`
- 变量值：jdk 的安装路径

**CLASSPATH 环境变量：**
- 系统变量中点击新建
- 变量名：`CLASSPATH`
- 变量值：`.;%JAVA_HOME%\lib;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;`
- ⚠️ 注意：不要忘记前面的点和中间的分号，且要在英文输入状态

**PATH 环境变量：**
- 在系统变量里对 path 环境变量进行编辑
- 新增变量值：`;%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin`

### 二、ADB 安装

1. 下载 platform-tools.zip（Wiki 附件）
2. 解压至任意文件夹
3. 编辑 path 环境变量，新增变量值为 platform-tools 文件路径

### 三、使用 install.bat 安装

#### 1. 准备工作
- 将 Unity 项目中 `client\Tools\BundleTool\install.bat` 添加至桌面快捷方式（不要直接拖到桌面）
- 设备使用数据线连接至电脑
- 打开开发者选项下的 USB 调试模式

⚠️ **注意：**
- 确认设备上同名程序已卸载
- 电脑仅连接 1 台待安装设备

#### 2. 安装步骤

**GP 渠道 aab 包安装：**
1. 双击运行 install.bat
2. 将需要安装的 aab 文件拖进窗口中，按回车
3. 输入证书别名：`tap4fun.p2`，再次回车
4. 等待安装完成

**马甲包 aab 安装：**
1. 双击运行 install.bat
2. 将需要安装的 aab 文件拖进窗口中，按回车
3. 输入证书别名：`tap4fun.p2.mjx`（x 为马甲包序号，如马甲1则输入 tap4fun.p2.mj1）
4. 等待安装完成

#### 证书别名对照表
| 渠道 | 证书别名 |
|------|----------|
| GP | tap4fun.p2 |
| 马甲包1 | tap4fun.p2.mj1 |
| 马甲包2 | tap4fun.p2.mj2 |
| 马甲包3 | tap4fun.p2.mj3 |
| 马甲包4 | tap4fun.p2.mj4 |
| 马甲包5 | tap4fun.p2.mj5 |
| 马甲包6 | tap4fun.p2.mj6 |

---

## 方式二：手机一键安装

### 设备要求
- Android 11 版本以上
- 打开开发者模式和**无线调试**功能
- 手机连接公司 Wi-Fi

### ⚠️ 注意事项
- 新安装版本必须高于已安装版本，否则报错：`INSTALL_FAILED_VERSION_DOWNGRADE`
- **华为鸿蒙系统无法通过该方式安装 aab 文件**
- 配对过程中出现报错，可先尝试重连 Wi-Fi 后重试

### 安装步骤

1. **下载 aab 包**
   - 在 Develop 群点击 aab 包下载链接，打开下载安装界面

2. **打开一键安装弹窗**
   - 点击【手机一键安装】按钮
   - 弹窗需要输入的信息要在手机**开发者选项 - 无线调试**中获取

3. **获取配对信息**
   - 打开手机无线调试功能
   - 选择"使用配对码进行配对"
   - 获取：IP 地址、端口、配对码

4. **填写信息并安装**
   - 将 IP 地址、端口、配对码分别填到一键安装弹窗内
   - 点击确认即可安装

---

## 常见坑点
- **Java 环境缺失**：需要安装 JDK 并配置环境变量
- **adb 未连接**：检查 USB 调试是否开启
- **签名不匹配**：卸载旧版本后重新安装
- **版本降级错误**：新版本必须高于已安装版本
- **华为鸿蒙系统**：无法使用手机一键安装，需用 PC 端方式

## 相关链接
- [PC 装包环境及过程 Wiki](https://wiki.tap4fun.com/pages/viewpage.action?pageId=71782874)
- [手机一键安装流程 Wiki](https://wiki.tap4fun.com/pages/viewpage.action?pageId=208824366)
- [系统开发部详细 Wiki](https://wiki.tap4fun.com/pages/viewpage.action?pageId=184576849)
