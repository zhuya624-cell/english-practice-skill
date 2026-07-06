# 🗣 英语口语练习 — Claude Code 插件

> 一个装在 Claude Code 里的 AI 英语口语教练。
> 用中文采访你，然后帮你生成地道的美式英语口语稿，拿起来就能开口练。

---

## 🤔 这到底是什么？能帮我干什么？

简单说：**你和一个 AI 用中文聊天，它把你说的内容变成一篇地道的英语口语稿**，还做成漂亮的网页让你对着练。

具体有三种用法：

| 模式 | 干嘛的 | 怎么聊 | 输出什么 |
|------|--------|--------|----------|
| **A. 口语练习** | 聊聊天，生成英语口语稿 | 你用中文回答，AI 用中文提问 | 一篇带生词标注的美式英语稿子（HTML 网页） |
| **B. 口语测验** | 模拟和老外对话，给你打分 | 全英文，你答完 AI 打分复盘 | 流利度/语法/词汇得分 + 改进建议 |
| **C. 随便聊聊** | 纯练习，无压力 | 全英文自由聊天，聊到你喊停 | 不输出文件，纯聊天 |

### 举个例子（A 模式）：

```
你：/learn
AI：欢迎！今天想做什么？
你：A
AI：今天聊啥方向？A1 今天的生活  A2 最近的新闻  A3 你出题
你：A1
AI：今天有没有什么有意思的事？   ← 第1轮，破冰
你：（用中文聊了聊今天做了什么）
AI：那你觉得最有收获的部分是什么？ ← 第2轮，感受
你：（分享感受）
AI：这让你对以后的工作有什么新的想法吗？ ← 第3轮，延伸
你：（聊聊启发）
AI：好的，帮你生成口语稿～
```

然后你的"下载"文件夹里会多出一个 HTML 文件，浏览器打开就是这样的：

> **📝 口语稿**
>
> So today was actually pretty interesting. I had this meeting with my team about the new project, and honestly, I didn't expect it to go that well. You know when you walk into a room thinking it's gonna be just another boring status update, but then someone says something that completely changes your perspective（看问题的角度）? That's exactly what happened...

每个超纲单词都标注了中文意思，文末还整理了 5-8 个地道表达，告诉你什么时候用、怎么用。

---

## 🧠 它会记住你（越用越懂你）

这个插件不是每次都从零开始。它有一个知识库，存在你的电脑上：

- 记住你的英语水平（不用每次都问）
- 记住你学过的生词，以后自动复习
- 记住你练过的句型，下次复现
- 记住你聊过的话题，避免重复

就像有个教练拿着笔记本，每次上课前翻一翻：「上次他学了 perspective 和 contemplate，今天稿子里带一下。」

**隐私放心**：所有数据都在你电脑本地（`~/.english-practice/` 文件夹），不上传任何地方。

---

## 📋 安装前：你需要什么软件

一共需要两个东西：

| 软件 | 干嘛的 | 怎么装 |
|------|--------|--------|
| **Claude Code** | AI 助手，插件跑在它上面 | 一条命令装好 |
| **Git** | 用来下载这个插件 | Mac 自带 / Windows 需安装 |

> 📌 如果你平时用 `git clone` 下载 GitHub 项目，那你会觉得这套流程非常熟悉——本质上就是把本仓库 clone 下来，复制两个文件到指定目录，完事。

---

## ⚡ 懒人极速版（Mac 用户，Claude Code 已装好）

如果你已经装好了 Claude Code 并且登录了，直接复制下面一整段，终端里粘贴回车：

```bash
git clone https://github.com/zhuya624-cell/english-practice-skill.git ~/english-practice-skill && \
mkdir -p ~/.claude/skills/english-practice && \
cp ~/english-practice-skill/SKILL.md ~/.claude/skills/english-practice/SKILL.md && \
cp ~/english-practice-skill/template.html ~/.english-practice/template.html && \
echo "✅ 装好了！输入 claude 然后说 /learn 开始吧"
```

一行梭哈，5 秒装完 🚀

想用 Homebrew 的朋友：

```bash
# 本质上就是 git clone + cp，没有专门的 formula
# 用上面的一行命令就行 👆
```

---

## 🍎 Mac 安装教程（详细版）

### 第 1 步：安装 Claude Code

打开 **终端**（`Command + 空格` → 搜"终端"）。

```bash
npm install -g @anthropic-ai/claude-code
```

> ❓ **如果报错 "npm: command not found"** → 去 [nodejs.org](https://nodejs.org) 下载 LTS 版，一路"继续"安装，装完关掉终端重开，再试。

验证装好了没：

```bash
claude --version
```

打印出 `v1.x.x` 就对了 ✅

### 第 2 步：登录 Claude Code

```bash
claude
```

首次运行会弹浏览器让你授权登录。用 Anthropic 账号登录（可用 Google 注册）。

> ❓ 没账号？去 [console.anthropic.com](https://console.anthropic.com) 注册，绑信用卡（有免费额度）。

### 第 3 步：一键安装本插件

```bash
# 克隆仓库到本地
git clone https://github.com/zhuya624-cell/english-practice-skill.git ~/english-practice-skill

# 创建技能目录，复制核心文件
mkdir -p ~/.claude/skills/english-practice
cp ~/english-practice-skill/SKILL.md ~/.claude/skills/english-practice/SKILL.md

# 复制 HTML 模板
cp ~/english-practice-skill/template.html ~/.english-practice/template.html
```

就这三条命令，完事 ✅

> 装完之后 `~/english-practice-skill/` 文件夹可以删掉（核心文件已经复制到位了）。想更新时再 `git clone` 一次覆盖即可。

### 第 4 步：开练！

```bash
claude
```

进对话后输入 `/learn` 或 `练口语`，开始！

---

## 🪟 Windows 安装教程

### 第 1 步：安装必要软件

按 `Win + X`，选 **"终端"** 或 **"PowerShell"**。

**先装 Git**（如果还没装）：

去 [https://git-scm.com/download/win](https://git-scm.com/download/win) 下载，双击安装，一路 Next 就行。

装完**关掉 PowerShell 重新打开**，验证：

```powershell
git --version
```

**再装 Claude Code：**

```powershell
npm install -g @anthropic-ai/claude-code
```

> ❓ **如果报错 "npm 不是可运行的程序"** → 去 [nodejs.org](https://nodejs.org) 下载 LTS 版（.msi），双击安装，一路 Next，装完重启 PowerShell 再试。

验证：

```powershell
claude --version
```

### 第 2 步：登录 Claude Code

```powershell
claude
```

首次运行弹浏览器授权，用 Anthropic 账号登录。

### 第 3 步：一键安装本插件

```powershell
# 克隆仓库到用户目录
git clone https://github.com/zhuya624-cell/english-practice-skill.git $env:USERPROFILE\english-practice-skill

# 创建技能目录，复制核心文件
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.claude\skills\english-practice"
Copy-Item "$env:USERPROFILE\english-practice-skill\SKILL.md" -Destination "$env:USERPROFILE\.claude\skills\english-practice\SKILL.md"

# 复制 HTML 模板
Copy-Item "$env:USERPROFILE\english-practice-skill\template.html" -Destination "$env:USERPROFILE\.english-practice\template.html"
```

完事 ✅

> `$env:USERPROFILE` 就是你的用户目录（等同于 `C:\Users\你的用户名`），PowerShell 会自动解析，不用手动替换。

### 第 4 步：开练！

```powershell
claude
```

输入 `/learn` 或 `练口语`，搞定！

---

## 🎮 怎么用？完整操作指南

进入 Claude Code 后（终端里输入 `claude`），用下面任意一句话触发：

| 你说什么 | 效果 |
|----------|------|
| `/learn` | 启动英语口语教练 |
| `练口语` | 同上 |
| `英语口语练习` | 同上 |
| `采访我` | 同上 |

然后 AI 会问你今天想干嘛，选 A / B / C 就行。

### 模式 A：口语练习（最常用）

1. AI 会问你想聊什么：**今天的生活** / **最近的新闻** / **你出题**
2. 如果选新闻，AI 会自动搜最近的热门话题，挑几个给你选
3. 然后 AI 会像记者采访一样问你 3 轮问题，你用中文自然回答就行
4. 聊完后，AI 自动生成一篇英语口语稿，存为 HTML 文件

**口语稿在哪？**

| 系统 | 路径 |
|------|------|
| Mac | `~/Downloads/英语/2026年07月06日.html` |
| Windows | `C:\Users\你的用户名\Downloads\英语\2026年07月06日.html` |

双击 HTML 文件，浏览器打开，就能看到漂亮排版的口语稿了。

### 模式 B：口语测验

全英文模拟对话，3 个问题，答完 AI 给你的流利度、语法、词汇分别打分，告诉你怎么改进。

### 模式 C：随便聊聊

全英文自由聊天，AI 不评分、不记录、不输出文件。聊爽了就喊"停"。

---

## 📊 你的练习数据存在哪？

所有学习记录都**只存在你本地电脑**，不上传任何地方：

```
~/.english-practice/              ← 你的个人学习数据库
├── profile.yaml                  ← 你的水平、兴趣、练习次数
├── vocabulary.yaml               ← 你学过的所有超纲生词
├── expressions.yaml              ← 你学过的所有地道句型
├── quiz_results.yaml             ← 测验成绩单
├── history/                      ← 每次练习的会话记录
│   ├── 2026-07-03.md
│   └── ...
└── quiz_history/                 ← 每次测验的详细记录
    └── ...
```

想看看自己学了什么？在 Claude Code 里说 **"看看我的数据"** 就行。

---

## ❓ 常见问题

### Q：这东西要钱吗？
插件本身免费。但 Claude Code 本身需要 Anthropic 账号，按使用量付费（有免费额度）。

### Q：能练发音吗？
不能，AI 听不到你说话。这是练**表达**和**口语组织能力**的——把想说的话用地道英文表达出来。发音建议配合其他 App。

### Q：和雅思口语有关系吗？
这个侧重日常口语。如果你要备考雅思，我有另一套雅思专用的插件（搜 `/ielts-speaking`）。

### Q：ChatGPT 能用吗？
不行，这是 Claude Code 专用的 skill，只能用在 Claude Code 里。

### Q：我的数据安全吗？
所有数据都存在你电脑本地，文件夹叫 `.english-practice`，在用户目录下。不联网、不上传、不出你电脑。

---

## 📦 本仓库文件说明

| 文件 | 干嘛的 |
|------|--------|
| `SKILL.md` | 插件的核心文件，给 Claude Code 读的（里面写了所有规则和逻辑） |
| `template.html` | HTML 排版模板，用来生成漂亮的口语稿网页 |
| `examples/` | 示例输出文件，你可以看看成品的口语稿长什么样 |

---

## 📝 License

MIT — 随便用、改、分享。

---

<p align="center">
  <sub>❤️ 希望这个插件能帮你开口说地道英语</sub>
</p>
