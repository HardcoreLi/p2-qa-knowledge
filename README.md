# P2 QA 知识库

> 基于 Cursor AI 的 QA 团队知识管理系统，通过自然语言提问即可快速获取测试相关知识。

---

## 快速开始

### 1. 获取知识库

```bash
# 克隆仓库到本地
git clone https://git.tap4fun.com/p2/qa-knowledge.git ~/Desktop/Cursor/p2-qa-knowledge
```

### 2. 在 Cursor 中配置

**方式 A：添加到工作区（推荐）**
1. 打开 Cursor
2. 点击 `File` → `Add Folder to Workspace`
3. 选择 `~/Desktop/Cursor/p2-qa-knowledge` 文件夹
4. 完成！现在可以直接提问了

**方式 B：全局安装**
```bash
# 复制到 Cursor skills 目录，任何项目都可使用
cp -r ~/Desktop/Cursor/p2-qa-knowledge ~/.cursor/skills/p2-qa-knowledge
```

### 3. 开始使用

在 Cursor 的 AI 对话框中直接提问，例如：

| 问题示例 | 知识库会告诉你 |
|----------|----------------|
| "审核服怎么测" | 审核服 Checklist、环境配置、常见问题 |
| "GP 支付测试账号是什么" | 测试账号、支付流程、沙盒配置 |
| "怎么开 KVK" | KVK 开启指令、前置条件、注意事项 |
| "DLC 怎么打" | 打包机地址、构建流程、验证方法 |
| "新渠道包测试流程" | 完整的渠道包测试步骤 |

---

## 知识库内容

### 📊 统计概览

| 分类 | 条目数 | 主要内容 |
|------|--------|----------|
| 工具 | 4 | Kadmin、Jenkins、TGS、Postman |
| 环境 | 3 | AAB安装、客户端问题排查、环境回退 |
| 流程 | 16 | 新服/合服/DLC/渠道包/上线/审核服/活动等 |
| 参考 | 12 | 渠道列表/GM指令/测试账号/SDK功能等 |
| 入门 | 1 | 新人入职指南 |
| **总计** | **36** | - |

### 📁 目录结构

```
p2-qa-knowledge/
├── SKILL.md              # Cursor Skill 入口文件
├── README.md             # 本说明文档
├── _index.json           # 知识索引（AI 检索用）
├── SYNC_SOURCES.md       # 需定期同步的在线源
├── templates/            # 模板文件
└── categories/           # 知识分类目录
    ├── onboarding/       # 入门指南
    ├── tools/            # 工具使用
    ├── environment/      # 环境配置
    ├── workflows/        # 工作流程
    └── references/       # 参考资料
```

### 🔍 可检索的关键词

<details>
<summary>点击展开完整关键词列表</summary>

**工具类**
- kadmin、服务器管理、部署服务器、清服
- jenkins、打包机、打包、出包、workspace、下包地址
- tgs、entrance、dynamic、ondemand、hotfix、patch
- postman、热更、hotcfg、schema

**环境类**
- aab、aab安装、bundletool、无线调试
- 进不去、登录失败、闪退、internal error、白名单
- 回退、rollback、环境回退

**流程类**
- 新服、新服测试、开服测试
- 合服、合服测试、合服确认
- dlc、dlc测试、dlc验证、ondemand
- 渠道包测试、新渠道包、mj包
- 上线checklist、发正式包、提审
- 审核服、一级冒烟、正式包验证
- 活动开启、kvk开启、跨服活动
- 节日活动提测、活动提测

**参考类**
- 渠道列表、登录方式、支付方式
- gm指令、addasset、initbase、faddactv
- 测试账号、沙盒账号、支付测试
- 平台SDK、SDK功能、登录SDK
- 发言过滤、敏感词、文本过滤
- 名词解释、AC、KVK、GVG
- 本地化、翻译、多语言
- 功能屏蔽、dlc屏蔽

</details>

---

## 常用场景

### 场景 1：新人入职
```
提问：新人入职需要做什么准备
```

### 场景 2：打包出包
```
提问：国际服整包用哪个打包机
提问：workspace 下载地址是什么
```

### 场景 3：测试环境问题
```
提问：客户端进不去怎么办
提问：internal error 是什么原因
```

### 场景 4：活动测试
```
提问：怎么开 KVK
提问：活动开启机制有哪些
```

### 场景 5：发版上线
```
提问：审核服测试注意事项
提问：正式包验证流程
提问：DLC 验证准则
```

### 场景 6：查找账号/地址
```
提问：GP 支付测试账号
提问：Kadmin 地址是什么
提问：各渠道登录方式
```

---

## 获取更新

知识库会持续更新，定期拉取最新内容：

```bash
cd ~/Desktop/Cursor/p2-qa-knowledge
git pull
```

---

## 贡献知识

如果你有新的知识想要补充，可以：

### 方式 1：直接告诉我
在 Cursor 中对话，发送你想补充的内容，我会帮你整理入库。

### 方式 2：提交 MR
1. 创建新分支
2. 按照 `templates/entry-template.md` 格式添加新条目
3. 更新 `_index.json` 索引
4. 提交 Merge Request

### 知识条目格式

```markdown
---
title: "条目标题"
aliases:
  - "别名1"
  - "别名2"
tags:
  - "标签1"
  - "标签2"
updated: "2026-02-12"
source: "来源链接"
---

# 条目标题

## 简答
> 一句话总结

---

## 详细内容
...
```

---

## 常见问题

### Q: 提问后没有得到知识库的回答？
A: 确保 `p2-qa-knowledge` 文件夹已添加到 Cursor 工作区，且 `SKILL.md` 文件存在。

### Q: 知识库内容过时了怎么办？
A: 执行 `git pull` 获取最新内容，或联系李映荷更新。

### Q: 想添加新知识怎么办？
A: 直接在 Cursor 中告诉我你想补充的内容，或提交 MR。

### Q: 可以离线使用吗？
A: 可以，知识库是本地文件，克隆后无需联网即可使用。

---

## 联系方式

- **知识库维护**：李映荷
- **问题反馈**：P2 QA 群

---

*最后更新：2026-02-12*
