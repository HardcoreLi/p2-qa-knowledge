---
title: "P2 GM 指令大全"
aliases:
  - "gm指令"
  - "gm命令"
  - "测试指令"
  - "控制台命令"
  - "addasset"
  - "initbase"
  - "faddactv"
  - "nextsmall"
tags:
  - "参考"
  - "工具"
  - "测试"
updated: "2026-02-12"
source: "P2_GM指令 Google Sheet"
---

# P2 GM 指令大全

## 简答
> GM 指令用于游戏内测试，涵盖资产添加、英雄、建筑、活动、战斗等各模块。常用指令：`initbase`（初始化高级账号）、`addasset`（添加资产）、`faddactv`（开启活动）、`nextsmall`（天下大势跳阶段）。

---

## 资产相关

| 指令 | 说明 | 示例 |
|------|------|------|
| `addasset 资产id 数量` | 添加各种资产（道具1111、资源1114、货币1115、部队1121） | `addasset 11111001 10` |
| `setasset` | 将资产设置为指定数量（不是增加） | 用法同 addasset |
| `inithasset` | 所有部落资产 1 亿 | 无需参数 |
| `initasset` | 添加电池、CD、士兵各 100 万 | 无需参数 |
| `adduasset` | 增加联盟资产 | `adduasset vm 11151003 10` |
| `inituasset` | 所有联盟资产增加 100 万 | 无需参数 |
| `addallsoldier 数量` | 添加所有等级、兵种 | `addallsoldier 10000` |
| `addhsoldier 士兵id 数量` | 加伤兵 | `addhsoldier 11211005 1000` |
| `initallasset` | 初始化所有资产 | - |
| `initbase` | 设置当前账号为高级账号 | 无需参数 |
| `initnpc` | initasset + 设置野怪上限 | 无需重启 |

---

## 英雄相关

| 指令 | 说明 | 示例 |
|------|------|------|
| `addhero 英雄id` | 添加英雄 | `addhero 19201001` |
| `addallhero` | 添加所有英雄 | - |
| `delhero 英雄id` | 删除英雄（需重启客户端） | `delhero 19201001` |
| `setallherolv 数量` | 为所有英雄添加经验 | `setallherolv 1000` |
| `heroexp 英雄id lv/star 数量` | 指定英雄加经验/星级 | `heroexp 19201001 lv 10000` |
| `washtalp` | 全体英雄天赋洗点 | - |
| `settalecfg 英雄id 天赋id` | 指定英雄加天赋 | `settalecfg 19201001 19220011` |
| `resethero` | 重置所有英雄为初始状态 | - |
| `incht 英雄id 天赋树编号` | 点满指定英雄的第几个天赋树 | `incht 19201009 2` |
| `initherotest` | 所有英雄满星满级 | - |
| `addtalp 数量` | 增加英雄天赋点 | `addtalp 100` |

---

## 建筑相关

| 指令 | 说明 | 示例 |
|------|------|------|
| `setallbuildinglevel level` | 设置所有建筑等级（简化版：`blvl level`） | `blvl 30` |
| `setbuildinglevel 建筑id 等级` | 设置指定建筑等级 | `setbuildinglevel 111811 11` |
| `initbuilding` | 建造和升级所有建筑 | 第二行参数为等级 |
| `addallbuilding` | 一键建造所有建筑并升到满级 | 先用 initbase |

---

## 活动相关

| 指令 | 说明 | 示例 |
|------|------|------|
| `faddactv 2111xxxx` | 直接原地开启指定活动 | `faddactv 21111084` |
| `faddactv 2111 预告期 持续时间` | 开启活动（带参数） | `faddactv 2111 0 48h` |
| `delactv` | 删除活动（2112 表） | 需重启客户端 |
| `completeactv` | 完成所有活动 | - |
| `loadactv` | 热更分支配置/部署活动 | - |
| `setactvstart 2112id day` | 修改活动开启时间 | 负数往前，正数往后 |
| `setactvcalindex calendarID index` | 活动期数设置 | index 填期数 |

---

## 天下大势

| 指令 | 说明 | 示例 |
|------|------|------|
| `nextsmall` | 立即完成当前小阶段，跳到下一个 | 无参数 |
| `nextsmallnum x` | 直接跳过 x 个小阶段 | `nextsmallnum 35` |
| `addsmcount stage/extra val` | 对当前小阶段任务进度加值 | `addsmcount stage 10` |
| `idleover` | 立即结束休赛期 | - |
| `newga` | 重置天下大势 | fire 之后可用 |
| `setgadau num` | 设置天下大势的 dau 值 | - |

---

## 时间相关

| 指令 | 说明 | 示例 |
|------|------|------|
| `nextday` | 下一天 | - |
| `nexthour` | 下一小时 | - |
| `nextmin` | 下一分钟 | - |
| `nextutc` | 下个 UTC 0 点前 1 分钟 | - |
| `tofakeday 2006-01-02 15:04:05` | 调整到指定时间 | `tofakeday 2023-07-02 23:59:00` |
| `opents` | 以当前时间为开服时间 | - |

---

## 火车/火箭

| 指令 | 说明 | 示例 |
|------|------|------|
| `traingocenter 部落序号` | 让火车跑起来 | 1红 2橙 3蓝 4紫 5绿 6黑 |
| `traingo 部落序号` | 让某一个部落火箭跑起来 | - |
| `fire` | 直接发射火箭 | - |
| `speeduptrain 部落序号 速度` | 设置火车某一段的速度 | - |
| `trainreset` | 把火车重置到部落基地 | - |
| `addtrainu 部落编号 数量` | 给某个部落增加铀 | - |

---

## 大地图

| 指令 | 说明 | 示例 |
|------|------|------|
| `refreshnpc` | 重刷全图 NPC（资源也会刷新） | - |
| `newnpcat npcid x y` | 刷出一个野怪 | `newnpcat 13176001 xxx yyy` |
| `newgather 类型 x y level` | 刷出矿点 | `newgather u x y level` |
| `fogall` | 大地图迷雾范围驱散 | - |
| `mc` | 传送主城到屏幕中央 | - |
| `mc x y f` | 强制传送主城到坐标 | `mc 1867 5254 f` |
| `oc` | 移动其他人主城到屏幕中心 | - |

---

## 联盟相关

| 指令 | 说明 | 示例 |
|------|------|------|
| `unionmember 人数 阶层` | 增加帮派人数 | 阶层 1-4 |
| `initruintest` | 自动创联盟并加入 20 个人 | - |
| `unionleader` | 和盟主交换阶级 | - |
| `setselfmemberclass 等级` | 修改个人在联盟中的阶层 | 1-4，不能改成 R5 |
| `newunionflag` | 在屏幕中间建造旗帜 | - |
| `newunioncenter` | 联盟总部 | - |
| `completeuf` | 立即完成修建 | - |
| `utechall` | 联盟科研全部升满（除主动技能） | - |

---

## 氏族/部落

| 指令 | 说明 | 示例 |
|------|------|------|
| `sethorde X` | 更换部落 | 1无 2红 3橙 4蓝 5紫 6绿 7黑 |
| `ujoinh 氏族序号` | 加入不抢夺首领 | 2-6 |
| `cleanhordetime` / `cleanuhts` | 清除转换部落 CD | - |
| `sethordeleader` | 设置部落首领 | - |
| `sethordeelite eliteID` | 给与玩家某个官职 | 1734 表 |

---

## Buff 相关

| 指令 | 说明 | 示例 |
|------|------|------|
| `addbuff p buffID 数量 时间` | 玩家 buff | `addbuff p 12111001 2000 60` |
| `addbuff u buffID 数量 时间` | 联盟 buff | 时间单位毫秒，-1 永久 |
| `addbuff h buffID 数量 时间` | 氏族 buff | - |
| `delbuff 1211id` | 删除玩家 buff | - |
| `delbuffx u 联盟id 1211id` | 删除联盟 buff | - |

---

## 科研相关

| 指令 | 说明 | 示例 |
|------|------|------|
| `researchone 科研ID 等级` | 指定某研究到指定等级 | 1119 表 |
| `researchAll` | 解锁所有个人科研 | 使用后点研究所 |
| `techup page col row` | 个人科研 | 第几页 第几列 第几个 |
| `uniontechup page col row` | 联盟科研 | - |

---

## 账号切换

| 指令 | 说明 | 示例 |
|------|------|------|
| `changeaccount 参数` | 创建 UDID 并登录 | `changeaccount 123` |
| `loginwithuniversaludid xxxx` | 设置万能 UDID 并登录 | - |
| `clearuniversaludid` | 移除万能 UDID | - |
| `charproxy 玩家ID` | 登录某个玩家账号 | 需重启客户端 |

---

## KVK 相关

| 指令 | 说明 | 示例 |
|------|------|------|
| `movekvk 战场id` | 进入 KVK 地图 | `movekvk 2405` |
| `movekvk 战场id 氏族序号` | 进入指定阵营 | `movekvk 2405 2` |
| `backkvk` | 返回原服 | - |
| `addkvkscore 数量` | 添加星际蓝图积分 | `addkvkscore 10000` |
| `kvkbattleend` | 结束 kvk 当前赛季 | - |
| `dkprt` | 禁用 kvk 玩家注册时间限制 | 仅当次登录生效 |

---

## 战场相关

| 指令 | 说明 | 示例 |
|------|------|------|
| `ubattleapply XX` | 一键进普通战场 | XX 为敌方联盟简称 |
| `ubattleapply 1 XX` | 一键进高级战场 | - |
| `enterub` | 进入战场 | 先报名 |
| `exitub` | 退出战场 | - |
| `addscore 玩家分 联盟分` | 增加积分 | `addscore 3000 2000` |

---

## 机甲相关

| 指令 | 说明 | 示例 |
|------|------|------|
| `addmecha cfgID` | 解锁某个机甲 | `addmecha 40011001` |
| `addmechaexp cfgID 经验` | 增减机甲经验 | `addmechaexp 40011002 999999999` |
| `setmechaenergy cfgID energy` | 设置机甲血量 | - |
| `unlockmechaq` | 解锁机甲治疗队列 | - |

---

## 任务相关

| 指令 | 说明 | 示例 |
|------|------|------|
| `setcounter catID ID val` | 直接给任务添加计数 | `setcounter 10145055 0 10` |
| `domq` | 完成并领取主线任务奖励 | 点一次跳一个 |
| `dmcq X` | 完成 X 个章节任务 | - |
| `docq` | 完成章节任务 | - |
| `dodq` | 完成当前所有每日任务 | - |
| `doquest 1421xxxx` | 完成某条章节任务 | - |

---

## 其他常用

| 指令 | 说明 | 示例 |
|------|------|------|
| `closefte` | 关掉引导 | - |
| `clearitem` | 清空背包 | 需重启客户端 |
| `fixwall` | 修满城墙耐久（可灭火） | - |
| `fixtower` | 修满防御塔耐久 | - |
| `fixcitydefend` | 斗士不空闲状态解除 | - |
| `saveallplay` | 游戏数据落地 | - |
| `allarms` | 解锁军备 | 0 橙色满级，1 红色满级 |
| `speedup speed` | 修改行军速度 | - |
| `deltroop` | 消除所有普通行军 | - |

---

## 付费相关

| 指令 | 说明 | 示例 |
|------|------|------|
| `setpaytotal 数值` | 修改玩家付费总值 | `setpaytotal 1000` |
| `inner_charge xxxxxx` | 内部充值支付 | 切换为内部货币 |
| `buygift 礼包id_类型` | 买礼包 | 2013 表 |
| `prlevel xiaoR/zhongR/daR/chaoR` | 设置玩家 R 级 | 礼包开启前设置 |

---

## 常见坑点

- **需重启客户端**：部分指令（如 delhero、clearitem、charproxy）需要重启客户端才生效
- **时间单位**：buff 时间单位是毫秒，-1 表示永久
- **配置表对应**：不同指令需要查对应配置表（1111 道具、1119 科研、2111 活动等）
- **服务器指令**：部分指令需要在 postman 中执行，不能在客户端使用
