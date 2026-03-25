# Film Echo

Film Echo 是一个实验性的电影复盘 skill。

Film Echo 帮用户回到自己的观影记忆，再通过多轮提问把感受、困惑、判断和细节慢慢整理出来，最后进入写作，整个流程更像一次电影访谈 + 共写，而非一个通用影评生成器。

## 它做什么

- 在宿主支持搜索时，先做轻量 research，再提问。
- 先建立最小 `film_model`，尽量避免凭空生成问题。
- 用多线程访谈方式挖 scene、emotion、form、relationship、confusion、personal stake。
- 起稿前检查材料是否够用，而不是太早下结论。
- 默认输出第一人称中文观后感 / 影评 / 电影随笔。

## 它不做什么

- 不负责秒出一篇通用影评。
- 不把公共讨论直接当成用户自己的观点。
- 不默认只聊主题，也会尽量追问镜头、表演、声音、节奏和细节。

## 安装

如果你是从远端仓库安装，可以先 clone：

```bash
git clone https://github.com/sonicpic/film-echo
cd film-echo
```

### Codex

把整个目录放到个人 skill 目录即可：

- macOS / Linux: `~/.codex/skills/film-echo`
- Windows PowerShell: `$HOME\.codex\skills\film-echo`

安装后打开新会话，直接在提示里写 `Use $film-echo ...` 即可。

### Claude Code

Claude Code 支持个人级和项目级 skills：

- 个人技能: `~/.claude/skills/film-echo`
- 项目技能: `.claude/skills/film-echo`

安装后可以让 Claude Code 自动触发，也可以显式使用 `/film-echo`。

## 仓库结构

- [SKILL.md](./SKILL.md): 主 skill 入口
- [references/](./references): 访谈、grounding、research、输出规范等辅助文档
- [agents/openai.yaml](./agents/openai.yaml): 元信息和默认配置

## 当前问题

这个项目已经有比较完整的结构，但还不是稳定成品。

当前最明显的问题有这些：

- skill 本质上还是软约束，不同宿主执行力度不同。
- research-first 并不等于模型每次都会真的先 research。
- 模型天然更容易先讲主旨，不一定愿意老老实实追问形式细节。
- 输入太薄、宿主又没有搜索能力时，效果会明显变差。

## License

本仓库使用 [MIT License](./LICENSE)。
