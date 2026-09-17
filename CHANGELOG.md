# Change Log

All notable changes to the "opencode-webui" extension will be documented in this file.

Check [Keep a Changelog](http://keepachangelog.com/) for recommendations on how to structure this file.

## [Unreleased]

## [1.0.0] - 2026-09-17

Fork of agustin-gigena/opencode-sidebar-web v0.7.2, rebranded as `jtian.opencode-webui`.

### Added
- Fixed server port setting (`opencode-webui.serverPort`, default 4096) so browser-stored WebUI settings persist across restarts
- Fixed-port local proxy (`opencode-webui.proxyPort`, default 4097) that strips frame-blocking headers and injects a bridge script into the WebUI page
- WebUI settings bridge (`opencode-webui.webuiSettingsBridge`): "WebUI" button opens the OpenCode settings dialog in a dedicated editor tab (simulated `Ctrl+,`, fullscreen layout, all settings interactive)
- Live settings sync: editing settings in the settings tab auto-reloads the sidebar via storage events
- Windows process detection (CIM) to connect to an existing local server
- Child process tree cleanup on stop
- Proxy self-healing: `ensureProxyAlive` restarts a dead proxy when opening the settings tab; fixed-port retry (10x300ms) instead of random-port fallback
- Bilingual (English/Chinese) setting descriptions

### Changed
- Status bar shows the fixed server port
- All settings/command IDs renamed from `opencode-sidebar-web.*` to `opencode-webui.*`
- Spanish UI strings translated to English

## [0.7.1] - 2026-05-24

### Fixed
- Fix extension activation before checking commands in test
- Various bug fixes

## [0.7.0] - 2026-05-24

### Added
- Comando para instalar OpenCode desde VS Code

### Fixed
- Fix release workflow

## [0.6.0] - 2026-05-20

### Added
- Tests automatizados para detección remota y servidor existente
- CI/CD: ejecución de tests en workflows
- CI/CD: instalación de opencode-ai antes de tests
- Acción de deploy automatizada

## [0.5.0] - 2026-05-18

### Added
- CSP dinámico y URL de webview para soporte de devcontainer
- Configuración de devcontainer para desarrollo
- Auto-conexión a servidor existente en remoto
- Mejora en UI de instalación con logs en vivo

## [0.4.0] - 2026-05-15

### Added
- Detección automática de entorno remoto
- Conexión a servidor existente en remoto
- Instalación con streaming de logs vía `asExternalUri` proxy
- Configuración `devcontainerMode`

### Changed
- Forzar remote extension host

## [0.3.0] - 2026-05-10

### Changed
- Migración de panel a webview view en secondary sidebar

## [0.2.0] - 2026-05-01

### Added
- Sistema de deploy automatizado
- Acción de GitHub para release

### Changed
- Actualización del sistema de deploy y optimización de peso

## [0.1.0] - 2026-04-01

### Added
- Proyecto inicial con panel lateral
- Sistema de autostart
- Licencia MIT
- README con instrucciones básicas
