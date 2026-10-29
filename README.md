# Bi

> 本地智能体工作台：对话、文件与产物在同一屏内。
> A local agent workbench — chat, files and artifacts on one screen.

**中文** ｜ [English](#english)

---

## 这是什么

Bi 是一个**跑在你自己机器上**的智能体工作台：你给它一个任务，它读文件、改代码、跑命令，
过程实时显示，敏感操作需要你确认。数据全部留在本地，服务端不向任何外部上报。

## 下载

本仓库的 [Releases](../../releases) 页面提供各平台压缩包，官网下载页同样列出
全部压缩包与 SHA-256 校验值：<https://basein.cn/zh/download>

| 文件 | 平台 |
|---|---|
| `bi-windows-amd64.zip` | Windows x64 |
| `bi-windows-arm64.zip` | Windows ARM64 |
| `bi-darwin-amd64.dmg` / `bi-darwin-arm64.dmg` | macOS 安装盘（推荐，Intel / Apple 芯片） |
| `bi-darwin-amd64-app.zip` / `bi-darwin-arm64-app.zip` | macOS `Bi.app`（解压即得，便携版） |
| `bi-darwin-amd64.zip` / `bi-darwin-arm64.zip` | macOS 绿色版（Intel / Apple 芯片） |
| `bi-linux-amd64.zip` / `bi-linux-arm64.zip` | Linux |

**macOS 推荐用安装盘（`.dmg`）**：双击挂载后把 `Bi` 拖入「应用程序」即可，带原生图标与菜单栏托盘，
双击即运行（放进 `/Applications` 这类不可写位置时，数据落在 `~/Library/Application Support/Bi`）。
也可下 `-app.zip` 解压得到 `Bi.app` 直接运行——数据（配置与工作区）就保存在 `Bi.app` **所在的目录**旁边；
绿色版 `bi-darwin-*.zip` 则**先解压再运行**，无需安装任何东西——压缩包里是可执行文件、
`ocr/`（文档 OCR 运行时，必须与可执行文件同级）、`.bi/config.json`（预置了官方更新源，
「检查更新」开箱可用）以及 Windows 版所需的 VC++ 运行库。
macOS 产物未签名，首次打开若被 Gatekeeper 拦截，右键「打开」或在「系统设置 → 隐私与安全性」里放行。

## 校验下载

```bash
# macOS / Linux
shasum -a 256 bi-linux-amd64.zip

# Windows PowerShell
Get-FileHash .\bi-windows-amd64.zip -Algorithm SHA256
```

输出与本仓库 `SHA256SUMS.txt` / 下载页上的值比对，一致即文件未被篡改。

## 快速开始

```bash
# macOS：双击 bi-darwin-arm64.dmg 挂载，把 Bi 拖入「应用程序」，然后从启动台打开
#         （绿色版）：unzip bi-darwin-arm64.zip -d bi && cd bi && chmod +x bi-darwin-arm64 && ./bi-darwin-arm64

# Linux
unzip bi-linux-amd64.zip -d bi && cd bi
chmod +x bi-linux-amd64 && ./bi-linux-amd64

# Windows：解压 bi-windows-amd64.zip 后双击 bi-windows-amd64.exe
```

- **不要直接在压缩包里双击**：那样 `ocr/` 不在可执行文件旁边，扫描件 OCR 会降级为不可用。

- Windows 与 macOS 版会自动打开浏览器（macOS 带菜单栏托盘）；Linux 版启动后，在浏览器打开
  `http://localhost:8080`（端口可在配置里改）。
- 首次运行会在当前目录创建 `.bi/`：`config.json`（本地配置）与 `bi.db`（会话数据库）。
- **Bi 不内置模型**：进入设置，至少配置一个模型服务商（OpenAI 兼容接口或本地模型）后才能对话。

## 能力

- **极简内核**：免安装、打开即用；为上下文预算而设计，符号级代码定位。
- **文档与产物**：图片 / 音频 / PDF / Office 就地预览；生成物集中在产物面板。
- **模型与上下文**：多服务商多模型、Auto 自动切换与故障转移、上下文压缩与前缀缓存。
- **信任与回退**：工具权限确认、行为拦截、每轮检查点可回退。
- **工作区**：文件树、变更面板、git 提交与回退，路径越界会被拒绝。

## 更新说明

- 每个版本的更新说明写在本仓库的 **Releases** 页面与官网下载页。
- 本仓库 [`CHANGELOG.md`](./CHANGELOG.md) 列出**当前版本**的更新内容。
- 客户端里「设置 → 关于 → 检查更新」会显示最新版本与说明。

## 文档

- 中文文档：<https://basein.cn/zh/docs>
- English docs: <https://basein.cn/en/docs>

---

## 这个仓库是什么

**本仓库只放编译好的发行物**：各平台的绿色版压缩包（内含二进制与 `ocr/`）、
macOS 安装盘（`.dmg`）与 `Bi.app` 压缩包、`releases.json`（升级检查清单）、
`SHA256SUMS.txt`（校验和）、`CHANGELOG.md`（当前版本更新）、`LICENSE`（开源协议）
与本文件。**不含源码**，分支内容由发布脚本整体覆盖。
问题反馈与文档请走官网。

## 许可证 / License

本仓库的发行物以 **MIT** 协议发布，全文见 [`LICENSE`](./LICENSE)。

---

<a id="english"></a>

## English

**Bi** is a local agent workbench: give it a task and it reads files, edits code and runs
commands, with every step shown as it happens. Sensitive actions require your confirmation.
Everything stays on your machine — the service reports nothing to any external server.

### Download

Each platform archive is attached to the [Releases](../../releases) page here; the download
page lists every archive together with its SHA-256 checksum: <https://basein.cn/en/download>

| File | Platform |
|---|---|
| `bi-windows-amd64.zip` | Windows x64 |
| `bi-windows-arm64.zip` | Windows ARM64 |
| `bi-darwin-amd64.dmg` / `bi-darwin-arm64.dmg` | macOS installer (recommended; Intel / Apple silicon) |
| `bi-darwin-amd64-app.zip` / `bi-darwin-arm64-app.zip` | macOS `Bi.app` (unzip and run, portable) |
| `bi-darwin-amd64.zip` / `bi-darwin-arm64.zip` | macOS portable (Intel / Apple silicon) |
| `bi-linux-amd64.zip` / `bi-linux-arm64.zip` | Linux |

**On macOS we recommend the installer (`.dmg`)**: mount it, drag `Bi` into Applications, then
just double-click — it ships a native icon and a menu bar tray. Data (config + workspace) is kept
next to `Bi.app`; when installed in a read-only location like `/Applications` it falls back to
`~/Library/Application Support/Bi`.
You can also grab `-app.zip` and run `Bi.app` directly. The portable `bi-darwin-*.zip` is
**unzip-then-run** — nothing to install. The archive holds the executable, `ocr/` (the document
OCR runtime, which must stay next to the executable) and, on Windows, the VC++ runtime.
The macOS build is unsigned — if Gatekeeper blocks it on first launch, right-click **Open**, or
allow it under **System Settings → Privacy & Security**.

### Verify the download

```bash
shasum -a 256 bi-linux-amd64.zip          # macOS / Linux
Get-FileHash .\bi-windows-amd64.zip -Algorithm SHA256   # Windows PowerShell
```

Compare the result with `SHA256SUMS.txt` in this repository.

### Quick start

```bash
# macOS: double-click bi-darwin-arm64.dmg, drag Bi into Applications, open from Launchpad
#        (portable): unzip bi-darwin-arm64.zip -d bi && cd bi && chmod +x bi-darwin-arm64 && ./bi-darwin-arm64

# Linux
unzip bi-linux-amd64.zip -d bi && cd bi
chmod +x bi-linux-amd64 && ./bi-linux-amd64

# Windows: unzip bi-windows-amd64.zip, then double-click bi-windows-amd64.exe
```

- **Do not double-click inside the archive**: `ocr/` would not sit next to the executable
  and scanned-document OCR falls back to "unavailable".

- The Windows and macOS builds open your browser automatically (macOS has a menu bar tray);
  on Linux open `http://localhost:8080` (configurable) once it is running.
- On first run it creates `.bi/` in the working directory: `config.json` (local settings)
  and `bi.db` (session database).
- **No model is bundled**: add at least one model provider (OpenAI-compatible endpoint or a
  local model) in Settings before chatting.

### Capabilities

- **Minimal core**: nothing to install; built for your context budget; symbol-level code navigation.
- **Documents & artifacts**: preview images, audio, PDF and Office files in place; generated
  output collects in the artifacts panel.
- **Models & context**: multiple providers and models, automatic failover, context compression
  and prefix caching.
- **Trust & rollback**: permission prompts for tools, behavior intercept rules, per-turn
  checkpoints you can revert to.
- **Workspace**: file tree, changes panel, git commit and revert; out-of-bounds paths are rejected.

### Release notes & docs

- What changed in each version is written on the **Releases** page here and on the download page.
- This repository's [`CHANGELOG.md`](./CHANGELOG.md) lists the **current version**'s changes.
- In the app: **Settings → About → Check for updates**.
- Documentation: <https://basein.cn/en/docs>

### About this repository

This repository holds **compiled release artifacts only** — the per-platform portable archives
(each containing the binary and its `ocr/` runtime), the macOS installer (`.dmg`) and `Bi.app`
archives, `releases.json` (update manifest), `SHA256SUMS.txt`,
`CHANGELOG.md` (current version notes), `LICENSE` (open source license) and this file. **No source code**;
its branch content is overwritten in full by the publish script.

### License

Release artifacts in this repository are published under the **MIT License** — see
[`LICENSE`](./LICENSE).
