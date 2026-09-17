# OpenCode WebUI

Integrates the OpenCode web UI into a VS Code sidebar panel. Fork of [opencode-sidebar-web](https://github.com/agustin-gigena/opencode-sidebar-web) with a fixed port, a settings/theme bridge and Windows process detection.

将 OpenCode WebUI 集成到 VS Code 侧边栏面板。基于 opencode-sidebar-web 的改进版：固定端口、设置/主题桥接、Windows 进程检测。

## Features

- Opens the OpenCode web interface in the secondary sidebar (right side)
  在辅助侧边栏（右侧）打开 OpenCode Web 界面
- Starts the OpenCode server on-demand or automatically (fixed port, default 4096)
  按需或自动启动 OpenCode 服务器（固定端口，默认 4096）
- Connects to an existing OpenCode server, including locally (Windows process detection via CIM)
  连接已有的 OpenCode 服务器，包括本地环境（Windows 通过 CIM 进程检测）
- Fixed-port local proxy (default 4097) that strips frame-blocking headers and injects a bridge script into the WebUI page, so browser-stored settings (color scheme, theme) persist across restarts
  固定端口本地代理（默认 4097），剥离阻止 iframe 嵌入的响应头并向 WebUI 页面注入桥接脚本，浏览器存储的设置（配色方案、主题）在重启后保留
- **WebUI Settings button**: opens the OpenCode settings dialog in a dedicated editor tab (simulates `Ctrl+,` via the bridge, fullscreen layout)
  **WebUI 设置按钮**：在独立编辑器标签页打开 OpenCode 设置对话框（通过桥接模拟 `Ctrl+,`，全屏布局）
- **Settings page changes apply live**: editing settings in the settings tab reloads the sidebar automatically (via storage events)
  **设置页修改实时生效**：在设置标签页修改设置后自动刷新侧边栏（通过 storage 事件）
- Theme sync: the OpenCode web UI follows VS Code's light/dark theme
  主题同步：OpenCode Web UI 跟随 VS Code 的浅色/深色主题
- Auto-reconnect when the server disconnects; proxy retries its fixed port instead of falling back to a random one
  服务器断开时自动重连；代理被占时对固定端口重试，而不是退回随机端口
- Status bar indicator showing connection state (server port)
  状态栏指示器显示连接状态（服务器端口）
- Full support for remote development and devcontainers (detection, auto-connect, `asExternalUri` proxy, auto-install)
  完整支持远程开发与 devcontainer（检测、自动连接、`asExternalUri` 代理、自动安装）
- English + Chinese bilingual setting descriptions
  设置描述支持英文 + 中文双语

## Usage

- Click the OpenCode icon in the editor title bar, or press `Ctrl+Shift+O` (`Cmd+Shift+O` on macOS)
- The server starts automatically (or click "Start Server"); the web UI loads in the sidebar
- **Settings**: extension settings (VS Code) — panel behavior, ports, bridge
- **WebUI**: the OpenCode settings dialog (appearance, theme, language, fonts, notifications...) in an editor tab; changes apply to the sidebar immediately

## Extension Settings

This extension contributes the following settings (descriptions are bilingual English/Chinese):

- `opencode-webui.autoStart`: Start the OpenCode server automatically when VS Code opens
- `opencode-webui.serverPort`: Fixed port for the OpenCode server (0 = random, default 4096)
- `opencode-webui.hostname`: Hostname for the OpenCode server (default: 127.0.0.1)
- `opencode-webui.connectExistingLocal`: Detect and connect to an existing server locally (default: true)
- `opencode-webui.proxyPort`: Fixed port for the injecting proxy (0 = random, default 4097)
- `opencode-webui.webuiSettingsBridge`: Enable the settings/theme bridge (default: true)
- `opencode-webui.autoReconnect`: Retry connection automatically when the server goes down (default: true)
- `opencode-webui.maxReconnectAttempts`: Maximum reconnection attempts (default: 3)
- `opencode-webui.devcontainerMode`: Detect opencode running in devcontainer/remote automatically
- `opencode-webui.autoInstallInDevcontainer`: Auto-install opencode on activation in devcontainer
- `opencode-webui.hideButton`: Hide the OpenCode button from the editor title bar
- `opencode-webui.sidebarPosition`: Always secondary sidebar (kept for compatibility)

## Requirements

- VS Code 1.106.0 or higher
- The `opencode-ai` npm package (bundled) or an existing `opencode` installation
