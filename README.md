<div align="center">

# Poem · PoemAI

**手机、电脑、智能体，一句话连成一个整体。**

在手机上说出你要办的事，Poem 在后台替你操作 App 和网页；在电脑上，PoemAI 是你的 AI Agent 工作台；两端互联，任务可以从任何一端发起。

简体中文


</div>

---

## 产品全景

| 产品 | 定位 | 平台 |
| --- | --- | --- |
| **Poem 手机端** | 手机上的 AI 助手，说一句话，自动操作 App 与网页直到完成 | Android |
| **PoemAI 电脑端** | 面向开发者的 AI Agent 工作台，集成对话、代码检索、文件编辑、工具执行、变更审阅与多智能体协作 | Windows（CLI / TUI / GUI） |
| **电脑操控插件** | 让智能体在隔离的虚拟桌面里操作电脑应用与浏览器，不抢占你的屏幕、鼠标与焦点 | Windows |
| **手机 ⇄ 电脑互联** | 电脑上的 AI 工具把任务交给手机；手机 App 远程查看并操控电脑上的会话 | USB / Wi-Fi / 私有 VPN |
| **官网与管理后台** | 产品官网、后台管理与服务端部署 | Web / Docker |

---

## 📱 Poem 手机端：一句话办成事

> 它在**隐藏的后台屏幕**上工作，你可以继续正常使用手机。


### 为什么选 Poem

| | |
| --- | --- |
| 📱 **不打扰你** | 在独立后台屏幕上点击、输入、滑动，随时可点小窗观看实时画面 |
| 🧩 **任何 App 都能用** | 像人一样看屏幕、找按钮，无需 App 提供接口，无需逐个适配 |
| 🌐 **任何网页都能唤起** | 内置桌面级浏览器，保持登录状态，在你正在读的页面上直接办事；你一碰页面它就停手 |
| 🧠 **越用越顺手** | 记住你的偏好，把完成过的任务沉淀成技能，下次更快更稳 |
| 🔒 **数据可控** | 模型供应商与同步中继分开配置，远程与同步功能按需开启；本地密钥使用 Android Keystore 加密 |
| 🆓 **开源** | Apache-2.0 |

### 功能一览

- **操作 App**：读长列表和聊天记录，点击、输入、分享文字；登录、验证码、付款交还给你
- **浏览网页**：读取页面、下载与上传；遇到风控页面交还给你
- **当前屏幕**：双击悬浮胶囊，把正在看的屏幕交给它——「这条怎么回？」「帮我记下来」
- **定时与条件任务**：「明早 9 点提醒我」「每周五做这件事」「每天 8 点查天气，只有下雨才告诉我」
- **随时插话或叫停**：任务进行中可追加或纠正；停下后会汇报进度，说「继续」即可接着做
- **按住说话**：按住输入框说话，松手前可编辑文字；长按悬浮胶囊直接语音下达任务
- **文件与计算**：每个对话一个 Linux 沙箱，可运行 Python、Node 与 Shell 处理你发来的文件（arm64）
- **两种模式**：默认「询问模式」仅在花钱（下单、付款）前确认，其余直接完成；也可切换为「自主模式」
- **多模型自由选**：预置 DeepSeek、通义千问、Kimi、智谱、火山方舟、MiniMax、OpenRouter、Anthropic、Gemini、OpenAI、xAI、Ollama 等，也可自定义任意 OpenAI 兼容 / Anthropic / Gemini 端点；支持 ChatGPT、Grok、OpenRouter 账号登录

内置使用经验的 App 与网站包括：微信、支付宝、淘宝、京东、美团、拼多多、抖音、小红书、B 站、知乎、BOSS 直聘、飞书、Telegram、WhatsApp、Gmail、Amazon、Google Maps、YouTube、GitHub 等；未列出的同样可用。

### 设备要求

| 用途 | 要求 |
| --- | --- |
| 对话、网页、文件 | Android 11+ |
| 操作手机 App | Android 12+，**推荐 Android 14+** |
| Linux 沙箱 | arm64 设备 |

详细文档：[`poemandroid/`](poemandroid/README.md) · [功能详解](poemandroid/docs/features.md) · [设置指南](poemandroid/docs/setup-guide.md) · [模型与登录](poemandroid/docs/models.md) · [免责声明](poemandroid/docs/disclaimer.md)

---

## 💻 PoemAI 电脑端：开发者的 AI Agent 工作台

基于 Rust 2024 workspace，提供 **CLI / TUI / GUI** 三种入口；桌面端使用 Tauri + React + TypeScript 构建。

| 能力 | 说明 |
| --- | --- |
| 三种入口 | CLI 用于命令与自动化，TUI 用于终端交互，GUI 用于可视化会话与任务管理 |
| 项目与会话 | 管理历史对话、多面板工作与独立工作目录 |
| 工具与文件工作流 | 检索、读取、写入、编辑文件，执行终端命令，查看工具参数、结果与错误 |
| 变更审阅 | 生成期间汇总文件改动，查看文件列表与版本差异，一键打开 / 定位 |
| 多智能体协作 | 把任务分派给子智能体，跟踪状态、输出与后续交互 |
| 模型与协议 | 支持 Anthropic Messages、OpenAI Chat Completions、Responses 等协议 |
| 记忆与检索 | 可配置的记忆模式，支持 MemOS 存储、检索与后台处理 |
| 扩展与权限 | Skill、MCP、插件、权限规则与沙箱配置，按环境和授权扩展能力 |

```bash
# 交互式 CLI / TUI
cargo run -p poem-cli -- --tui

# 一次性提问（适合脚本）
cargo run -p poem-cli -- query "解释 Rust 的所有权"
```

在线模型需自行配置供应商与凭据。详见 [`poemcomputer/README.md`](poemcomputer/README.md)。

### 🖱️ 电脑操控插件（Computer Use）

让智能体真正「动手」操作电脑：

- **隔离的虚拟桌面**：在后台桌面里操作应用，不抢占你的屏幕、光标和焦点
- **浏览器可用**：Chromium 系浏览器（Chrome、Edge、Brave）通过 DevTools 管道投递键鼠事件，支持中文输入与组合键
- **按应用授权**：授权按应用、按权限等级，30 分钟自动过期，每次新增权限都会询问
- **输入可验证**：输入后读回确认，失败给出明确原因，不再静默丢失
- **安全边界**：浏览器仅开放固定输入方法，不执行页面脚本、不读取 Cookie，使用匿名管道、不开放网络端口

更新记录见 [`PoemComputerPlugin/CHANGELOG.md`](PoemComputerPlugin/CHANGELOG.md)。

### 🧰 SideX 编辑器

`PoemComputerPlugin/VScodeSidex` 是去除 Electron 的 VS Code 工作台（Rust + Tauri），内置 AI Agent，让 AI 与编辑器、终端、Git 在同一界面协同。

---

## 🔗 互联：手机与电脑，双向打通

### 电脑 → 手机：让电脑上的智能体指挥 Poem

电脑上的 AI 工具（或你自己的终端）把「要办成什么」交给手机，怎么做由手机上的 Poem 决定，并能查进度、答追问、取回结果。

| 入口 | 适用场景 |
| --- | --- |
| **Skill** | 电脑 Agent 支持 Skill：自带 CLI 脚本，无需另装 |
| **CLI** | 在终端或脚本里派任务：`poem` 命令 |
| **MCP** | 支持 MCP 的客户端：Poem 作为 MCP 服务器 |

| 连法 | 说明 |
| --- | --- |
| **USB（推荐）** | 数据线连接，电脑一条命令即可，监听仅限手机本机 |
| **Wi-Fi / 私有 VPN** | 不插线、可远程；只接受局域网和私有 VPN 地址，拒绝公网与移动数据 |

- **电脑任务台 `poem ui`**：浏览器里派任务、看步骤进度、回答追问、追加要求、取消任务；支持按对话归组、过程与 Trace 查看、任务完成/需接管时的桌面通知
- **飞书连接器**：扫码关联机器人，在飞书私聊中派任务、收结果
- **让 AI 帮你装**：手机 USB 连电脑后，把安装说明交给电脑上的 AI 助手，它会自动把 Poem 装好、配好
- 付款与需要你同意的操作始终只能在手机上处理，电脑派来的任务不会替你点

### 手机 → 电脑：用 Happy 手机 App 远程操控

`poem Androidlogin` 用 Rust 原生实现 Happy 客户端协议，终端显示二维码，手机扫码即可查看并操控本机 PoemAI 会话，不依赖 Node。审批超时、断线、回复缺字段一律按拒绝处理。

> 状态说明：加密格式已与 Happy 参照实现逐字节对照通过，与真实手机的完整联调仍在进行中。

---

## 🤖 智能体能力总览

| 层次 | 能力 |
| --- | --- |
| **手机智能体** | 看屏幕、点按输入、浏览网页、定时与条件触发、技能沉淀、记忆偏好、Linux 沙箱计算 |
| **电脑智能体** | 代码检索、文件编辑、终端执行、变更审阅、子智能体协作、记忆与检索 |
| **桌面操控智能体** | 在虚拟桌面里操作任意应用与浏览器，按应用授权 |
| **跨端智能体** | 电脑 Agent ⇄ 手机 Agent 通过 CLI / Skill / MCP 互相调度，任务可从任一端发起 |
| **可扩展** | Skill、MCP、插件体系；手机端可「写技能」，电脑端可接入第三方工具 |

---

## 🚀 快速开始

**手机**

1. 安装 Poem APK（包名 `jensen.poem`，见[本地分发说明](poemandroid/docs/source-distribution.md)）
2. 登录并配置模型（[模型与登录](poemandroid/docs/models.md)）
3. 需要操作 App 时，按设置里的「设置手机控制」向导配对一次无线调试（[设置指南](poemandroid/docs/setup-guide.md)）

试试说：「明早 9:40 和 10:00 各设一个闹钟」。

**电脑**

- 使用安装包 `PoemAI-Setup.exe` 安装，或按 [`poemcomputer/README.md`](poemcomputer/README.md) 从源码构建
- 连接手机：见[从电脑使用 Poem](poemandroid/docs/computer.md)



## 📄 许可

手机端 Poem 采用 Apache-2.0；SideX 为 MIT；其余组件的许可证见各子目录。
