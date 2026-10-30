# 脑叶公司 随时存档 Mod（Lobotomy Save Mod）

让《脑叶公司》支持**一天之内随时存档 / 读档**。

原版只能在"天结束"或"检查点"时存档，员工暴毙或操作失误后往往要重打一整天。本 mod 通过 **F5 存档 / F9 读档**，把当天实时状态一起保存下来，读档能回到存档那一刻——主要用于"防暴毙、防失误、回档重来"。

---

## 前置要求

- **游戏**：Steam 版《脑叶公司》（Lobotomy Corporation），64 位（Unity 2017 Mono）。
- **Mod 框架**：**BepInEx 5.4.x（x64）**。本 mod 依赖 BepInEx，必须先安装它。
  - 下载地址（官方）：`https://github.com/BepInEx/BepInEx/releases`
  - 选 `BepInEx_x64_5.4.21.0.zip`。

> 说明：本 mod 自包含，不依赖 BaseMod / Lobotomy Mod Manager，可与它们共存。

---

## 安装

1. **装 BepInEx**：解压 `BepInEx_x64_5.4.21.0.zip`，把里面的 `winhttp.dll`、`doorstop_config.ini`、`BepInEx\` 三个一起复制到游戏根目录：
   ```
   ...\steamapps\common\LobotomyCorp\
   ```
2. **装本 mod**：把 `LobotomySaveMod.dll` 复制到：
   ```
   ...\steamapps\common\LobotomyCorp\BepInEx\plugins\
   ```
3. 启动游戏即可（首次启动会生成 BepInEx 的配置文件，属正常现象）。

---

## 使用

| 按键 | 功能 |
|------|------|
| **F5** | 存档（保存当天实时状态 + 长期进度） |
| **F9** | 读档（回到 F5 存档那一刻） |

- 按 F5 / F9 后，屏幕会有短暂提示；打开 **ESC 暂停菜单**也能看到 "F5 存档 / F9 读档" 和最近一次操作结果。
- 暂停菜单里的"重新开始这一天 / 回到记忆库 / 退出"等官方选项不受影响，照常使用。

---

## 存档位置

- 游戏原版存档（不变）：`C:\Users\<用户名>\AppData\LocalLow\Project_Moon\Lobotomy\`
- 本 mod 的实时快照：同目录下的 `LobotomySaveMod.snap`

---

## 回档能恢复什么

**长期进度**（走游戏官方存档，完全一致）：
- 天数、员工基础属性与等级、装备、EGO、研发、库存、科技、异想体图鉴等。

**当天实时状态**（本 mod 额外保存）：
- 员工：血量、精神、死亡、恐慌值、位置、**当天工作攒的经验**（不会白干）。
- 异想体：Qliphoth 计数器、收容状态、超载状态。
- 能量进度、紧急等级、熔毁（Qliphoth overload）等级 / gauge、考验（ordeal）显示。
- 游戏速度。

---

## 已知限制

- 读档会先回到"当天开头"再重新套用快照，所以会有一次读条。
- 员工身上的临时 buff、进行中的工作动画等细微表现尚未 100% 还原；核心"防暴毙 / 回档重来"场景已可用。
- 员工属性**等级**要等"当天结算"时才上涨——这是游戏正常机制（工作先攒经验、结算时升级）；经验本身已保住。

---

## 备份建议

第一次使用前，建议手动备份整个文件夹：
```
C:\Users\<用户名>\AppData\LocalLow\Project_Moon\Lobotomy\
```

---

## 排错

出问题时查看日志：
```
...\steamapps\common\LobotomyCorp\BepInEx\LogOutput.log
```

---

## 备注

- 热键目前固定为 **F5 / F9**；如需改键，可修改源码 `Plugin.cs` 里的 `SaveKey` / `LoadKey` 后重新编译。
- 源码见 `ModSource\`。
