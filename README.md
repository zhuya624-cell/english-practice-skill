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

### 只需要一个东西：Claude Code

**Claude Code** 是 Anthropic 公司出的一个命令行 AI 编程助手，你可以免费装。

> 📌 **为什么需要 Claude Code？** 因为这个插件是给 Claude Code 用的"skill"（技能扩展），就像浏览器插件一样，装进去才能用。

| 你的电脑 | 需要装什么 |
|----------|-----------|
| **Mac** | Claude Code（通过终端安装） |
| **Windows** | Claude Code（通过 PowerShell 安装） |

下面手把手教你在两个平台装好所有东西。

---

## 🍎 Mac 安装教程（一步一步来）

### 第 1 步：安装 Claude Code

打开 **终端**（在"启动台 → 其他 → 终端"，或者按 `Command + 空格` 搜"终端"）。

复制下面这行命令，粘贴进去，按回车：

```bash
npm install -g @anthropic-ai/claude-code
```

> ❓ **如果报错 "npm: command not found"**
>
> 说明你电脑还没装 Node.js。去 [https://nodejs.org](https://nodejs.org) 下载左边的 LTS 版本，一路点"继续"安装，装完关掉终端重新打开，再试上面的命令。

装完后，输入下面命令验证一下：

```bash
claude --version
```

如果打印出一串版本号（比如 `v1.0.xx`），说明装好了 ✅

### 第 2 步：登录 Claude Code

还是在终端里，输入：

```bash
claude
```

首次运行会提示你登录。按提示操作：
- 会弹出一个网页让你授权
- 用 Anthropic 账号登录（可以用 Google 账号注册）
- 授权完成后，终端里就可以和 Claude 对话了

> ❓ **没账号怎么办？** 去 [https://console.anthropic.com](https://console.anthropic.com) 注册一个，需要绑定信用卡（有免费额度可以先用）。

### 第 3 步：安装这个英语口语插件

在终端里依次输入下面 4 行命令（一行一行复制粘贴，每行按回车）：

```bash
# 1. 创建技能目录
mkdir -p ~/.claude/skills/english-practice

# 2. 创建知识库目录
mkdir -p ~/.english-practice/history
mkdir -p ~/.english-practice/quiz_history
```

然后下载本仓库里的两个文件，放到对应位置：

```bash
# 3. 把 SKILL.md 复制到技能目录
cp ~/Downloads/english-practice-skill-main/SKILL.md ~/.claude/skills/english-practice/SKILL.md

# 4. 把 HTML 模板复制到知识库目录
cp ~/Downloads/english-practice-skill-main/template.html ~/.english-practice/template.html
```

> 💡 如果你的下载文件夹名字不一样，把路径换成你实际的就行（比如 "english-practice-skill"）。

### 第 4 步：开始用！

在终端里输入 `claude` 进入对话，然后输入 `/learn` 或 `练口语`，就开始了！

---

## 🪟 Windows 安装教程（一步一步来）

### 第 1 步：安装 Claude Code

按键盘 `Win + X`，选 **"终端"** 或 **"PowerShell"**。

复制下面这行命令，粘贴进去，按回车：

```powershell
npm install -g @anthropic-ai/claude-code
```

> ❓ **如果报错 "npm 不是可运行的程序"**
>
> 说明你电脑还没装 Node.js。去 [https://nodejs.org](https://nodejs.org) 下载左边的 LTS 版本（.msi 文件），双击安装，一路点 Next，装完重启 PowerShell，再试上面的命令。

装完后，输入下面命令验证：

```powershell
claude --version
```

如果打印出一串版本号，说明装好了 ✅

### 第 2 步：登录 Claude Code

在 PowerShell 里输入：

```powershell
claude
```

首次运行会让你登录，按提示操作：
- 会弹出浏览器让你授权
- 用 Anthropic 账号登录（可以用 Google 账号注册）
- 授权完成后，终端里就可以和 Claude 对话了

> ❓ **没账号怎么办？** 去 [https://console.anthropic.com](https://console.anthropic.com) 注册，需绑定信用卡（有免费额度可用）。

### 第 3 步：安装这个英语口语插件

在 PowerShell 里依次输入下面几行命令：

```powershell
# 1. 创建技能目录（把 "你的用户名" 换成你电脑的用户名）
mkdir C:\Users\你的用户名\.claude\skills\english-practice

# 2. 创建知识库目录
mkdir C:\Users\你的用户名\.english-practice\history
mkdir C:\Users\你的用户名\.english-practice\quiz_history
```

> 📌 **不知道用户名是什么？** 在 PowerShell 里输入 `echo $env:USERNAME`，输出的就是。

然后，把本仓库下载到电脑上，找到 `SKILL.md` 和 `template.html` 两个文件，手动复制到：

```
SKILL.md      →  复制到  C:\Users\你的用户名\.claude\skills\english-practice\
template.html →  复制到  C:\Users\你的用户名\.english-practice\
```

> 💡 `.claude` 文件夹默认是隐藏的。在文件管理器地址栏直接输入 `C:\Users\你的用户名\.claude` 就能进去。

### 第 4 步：开始用！

在 PowerShell 里输入 `claude` 进入对话，然后输入 `/learn` 或 `练口语`，搞定！

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
