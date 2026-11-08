# sqs-skills

sqs 的个人 Claude Code 插件市场仓库，目前包含一个插件 `sqs`，其中有一个技能 `sqs:learn`。

`sqs:learn` 用于「学习型问答」：当你需要弄清一个工具、命令、技能、SDK、API、代码仓库或服务时，按 `是什么 / 怎么用 / 原理 / 讨论` 四种模式提问，技能会按固定规范回答。问答模式派生一次性子代理，不污染主会话；复杂结论会沉淀到项目根目录的 `learn-docs/`，便于以后回看。

## 安装

1. 添加插件市场（只需一次）：

   ```text
   /plugin marketplace add c0503sqs/sqs-skills
   ```

2. 安装插件：

   ```text
   /plugin install sqs@sqs-skills
   ```

   在打开的详情面板里确认内容，并选择安装范围。推荐 **Install for you**（本机所有项目可用）。

3. 确认已加载：

   ```text
   /plugin list
   ```

   应看到 `sqs@sqs-skills`，状态为 `enabled`。

## 更新

会话内刷新市场并更新插件：

```text
/plugin marketplace update sqs-skills
```

也可以在 `/plugin` → **Installed** → `sqs` → **Update now** 更新；或在 `/plugin` → **Marketplaces** 为 `sqs-skills` 打开 **Enable auto-update**。

在 shell 中：

```bash
claude plugin update sqs@sqs-skills
```

更新后当前会话执行 `/reload-plugins`，或等下次启动 Claude Code 自动生效。

## 卸载

```text
/plugin uninstall sqs@sqs-skills
/plugin marketplace remove sqs-skills
```

> 如果之前手动把插件目录复制到过 `~/.claude/skills/sqs`，建议删除，避免以 `sqs@skills-dir` 重复加载。

## 使用

```text
/sqs:learn 是什么 <对象>
/sqs:learn 怎么用 <对象>
/sqs:learn 原理 <对象>
/sqs:learn 讨论 <对象>
```

- `是什么` / `怎么用` / `原理`：派生一次性子代理回答，不污染主会话；复杂结论写入项目根目录的 `learn-docs/`。
- `讨论`：留在主会话，全程结合上文，写文档前需确认。

## 仓库结构

```text
.claude-plugin/
├── plugin.json        # 插件元信息（名称：sqs）
└── marketplace.json   # 市场定义（名称：sqs-skills）
skills/learn/SKILL.md  # learn 技能正文
```

本仓库同时是插件和 marketplace：`plugin.json` 不写 `version`，因此每次推送提交都会被识别为新版本，更新命令即可拉到最新内容。

## License

MIT
