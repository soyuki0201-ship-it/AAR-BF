# bf解析skill

把达人营销选号 **Brand Brief**（项目组的自然语言需求）转换成「业务可确认、AI 审核模型可执行」的选号要求。

- **数据要求**：匹配系统筛选器字段（小红书 31 项 / 抖音 28 项），标准化为可执行条件；匹配不上的明确归为"无法AI审号"，绝不编造指标、阈值、名单
- **内容要求**：理解为业务意图，按 多选一 / 必须满足（含排除）/ 加分项 三分区整理，拆解为审核模型可判断的 Rule（构成要件 × 产品植入路径）
- **两轮输出**：第一轮给业务核对修改（自然语言，直接回复即可改）→ 第二轮输出 AI 审号产品专用的最终 Brief

格式遵循 [Agent Skills 开放标准](https://agentskills.io/specification)（SKILL.md）。

---

## 安装（按你的工具选一档）

### 第一档：支持 Agent Skills 标准的 agent（Claude Code / Codex / Gemini CLI / Cursor 等）

对 agent 说一句话即可：

```
从 github.com/soyuki0201-ship-it/AAR-BF 安装 bf解析skill
```

或手动克隆到本机 skills 目录（以 Claude Code 为例）：

```
git clone https://github.com/soyuki0201-ship-it/AAR-BF
cp -r AAR-BF/bf解析skill ~/.claude/skills/
```

### 第二档：能读网页/文件、但不认 skill 标准的 AI

把仓库链接发给它，说：

```
读取 https://github.com/soyuki0201-ship-it/AAR-BF 里 bf解析skill/SKILL.md，按里面的规则处理我的 Brief
```

（若该产品支持自定义指令/长期记忆，把 SKILL.md 内容贴进去可常驻）

### 第三档：纯对话框产品（无文件读取）

打开 [`prompt/bf解析_通用Prompt.md`](prompt/bf解析_通用Prompt.md)，把 Prompt 正文 + 数据项清单整体粘贴到 system prompt / 自定义指令位。

---

## 使用（装好后三步，无需任何技术知识）

1. 对 AI 说「**bf解析**」，把 Brief 粘贴进去（平台和推广产品写在 Brief 里或随口说一句都行）
2. AI 给你一版「整理结果」——看着不对就直接说话改，比如"数据2 改成 70%"；不改就回"可以"
3. 拿到最终版（AI 审号产品专用 BF），交给媒介或贴进产品入口

**它会怎么回你**（真实示例节选）：

```
—— 数据要求 ——

可AI审号：
数据1｜达人类目 ∈ {职场, 运动健身, 美食, 生活记录}，其余类型转入下方内容要求
数据2｜CPM < 150
数据3｜粉丝年龄 18-24岁段占比 > 50%
数据4｜女性粉丝占比 > 50%

无法AI审号：
无法1｜"两个月内没合作过品牌B扫地机"——现有数据项查不到品牌合作历史
```

## FAQ

- **改错了 / 反悔了** → 再说一遍就行（"刚才数据3改成60%"），以最新回复为准
- **Brief 是两个平台的** → 分两次发，一次一个平台
- **预填的数值不对**（如"占比高"默认填了 >50%）→ 直接改，AI 填的只是建议值
- **字段清单变更** → 修改 `bf解析skill/数据项清单.md` 即可，SKILL.md 不用动

## 维护

- 字段/规则变更请更新本仓库并打 tag（当前 v1.0.0，见 [CHANGELOG](CHANGELOG.md)）
- Brief 样例已做品牌脱敏（品牌A~E 代号），条件数字保留原样

## 许可

[MIT](LICENSE)
