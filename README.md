# AIMind.ing

> **The Reliable Dev Pal for CLI and Agents.**  
> A local workspace for developers and AI agents, bringing project context, AI conversations, tasks, terminal execution, goals, and knowledge graphs together in one place.

[Download from Releases](https://github.com/AIMind-ing/release/releases) · [Latest Stable Release](https://github.com/AIMind-ing/release/releases/latest) · [Product Website](https://aimind.llm.ist/)

> This repository is used only to distribute public AIMind.ing installers and release information. It does not contain the application, Electron, Tauri, packaging, or build source code.

## What is AIMind.ing?

AIMind.ing is more than an AI chat window. It is a desktop workspace designed around real project work, bringing the full workflow of **understanding a project, planning tasks, using tools, running commands, and preserving results** into one connected environment.

## Key features

- **Workspace-driven project organization**  
  Create separate workspaces for different projects, associate them with local directories, and access project files, recent sessions, and work status from one interface.

- **AI conversations with project context**  
  Attach Todos, Targets, Graph Nodes, Shell tasks, and Timeline events from the current workspace to a conversation, so the selected model can respond with relevant project context instead of starting from scratch.

- **Flexible cloud and local model support**  
  Connect to OpenAI Responses, OpenAI Chat Completions, Anthropic, Gemini, and Ollama-compatible APIs. You can also configure OpenRouter, DeepSeek, Groq, LM Studio, or a self-hosted model gateway. API endpoints, credentials, and models remain under your control.

- **Todos connected to a real terminal**  
  Keep tasks and the Shell Runner in the same workflow. Desktop builds can run real terminal sessions, display live output, and preserve commands and execution context associated with each task.

- **Timeline for project history**  
  Review important project activity and changes over time, making it easier to trace tasks, decisions, and execution results instead of seeing only the current state.

- **Targets and OKRs**  
  Organize Objectives and Key Results, track progress, and keep daily tasks connected to longer-term project direction.

- **Graph-based project visualization**  
  Use nodes and relationships to represent modules, tasks, risks, resources, and dependencies, providing a structural view beyond conventional lists.

- **Local-first data experience**  
  Workspace data, model configuration, conversations, and terminal records can be persisted locally, making AIMind.ing suitable for personal development environments while maintaining clear boundaries for migration, auditing, and future synchronization.

## Electron or Tauri: which version should I choose?

Both editions provide the same core AIMind.ing workspace experience. Their main differences are the desktop runtime, installer size, resource usage, supported platforms, and environment compatibility.

| Category | Electron edition | Tauri edition |
| --- | --- | --- |
| Runtime | Bundles Chromium and a Node.js desktop runtime | Uses the system WebView with a native Tauri host |
| Installer size | Larger, typically around 70–110 MB | Smaller, typically around 20–35 MB on Windows |
| Resource usage | Usually higher | Usually lower, with a lighter desktop shell |
| UI and network consistency | Bundled runtime generally behaves more consistently across computers | Behavior can be affected by WebView2, certificates, proxies, and system configuration |
| Local terminal | Electron with `node-pty`; the more established compatibility path | Tauri native bridge with a bundled terminal sidecar |
| Current platforms | Windows, macOS, and Linux, depending on the assets included in a release | Public packages are currently focused on Windows x64 |
| Best for | Compatibility, cross-platform use, and complex development environments | Lightweight installation and modern Windows environments |

### Electron edition

**Advantages**

- Includes a complete Chromium runtime, providing more consistent UI rendering, network behavior, and local service access.
- Usually easier to troubleshoot when working with proxies, certificates, local model servers, terminals, or complex developer toolchains.
- Currently provides release assets for Windows, macOS, and Linux.

**Trade-offs**

- Larger installer and generally higher disk and memory usage.
- The desktop runtime is included in every installation, making downloads and updates larger than the Tauri edition.

**Recommended for:** users who prioritize compatibility and predictable behavior; macOS or Linux users; and developers using enterprise proxies, self-signed certificates, local models, or complex CLI environments.

### Tauri edition

**Advantages**

- Significantly smaller installer with generally lower resource usage.
- Uses the system WebView and a lightweight native desktop host.
- Well suited to everyday use on modern Windows 10/11 x64 systems.

**Trade-offs**

- Requires Microsoft Edge WebView2 Runtime. It is already present or installed automatically on most modern Windows systems, but older or stripped-down environments may require manual installation.
- Access to local services, enterprise proxies, HTTPS certificates, and security policies may behave differently depending on the system WebView environment.
- Currently offers fewer public platform and architecture options than the Electron edition.

**Recommended for:** Windows x64 users who prefer a smaller installer and lower resource usage and have a modern, up-to-date system environment.

## Quick selection guide

- **Not sure which one to use? Choose the stable Electron edition.** It is larger, but its bundled runtime generally provides the most predictable compatibility.
- **Using Windows 10/11 x64 and prefer a lightweight app? Choose the stable Tauri edition.**
- **Using macOS or Linux? Choose the Electron edition.**
- **Using Ollama, LM Studio, or another localhost model service? Electron is the recommended first choice.** If you use Tauri, also verify WebView2, the local port, firewall rules, proxy settings, and certificates.
- **For regular or long-term use, choose the release marked `Latest` rather than an `rc` release.**
- **To try the newest fixes and provide feedback, choose a `vX.Y.Z-rc.N` pre-release.**

## Download guide

Open the [GitHub Releases page](https://github.com/AIMind-ing/release/releases), select a release, and then download the file that matches your operating system and CPU architecture.

### Windows x64

| Filename pattern | Package type | Recommendation |
| --- | --- | --- |
| `Electron-Compat-Setup-...-x64.exe` or the older `Compat-Setup-...-x64.exe` naming | Electron installer | **Default choice when compatibility is the priority** |
| `Tauri_..._x64-setup.exe` or the older `AIMind.ing_..._x64-setup.exe` naming | Tauri NSIS installer | **Default lightweight choice** with a straightforward installation experience |
| `Tauri_..._x64_en-US.msi` or the older `AIMind.ing_..._x64_en-US.msi` naming | Tauri MSI installer | Suitable for managed deployment, system administration, or users who prefer MSI packages |

### macOS — Electron

| Filename pattern | Compatible device |
| --- | --- |
| `Electron-...-arm64.dmg` | Apple Silicon Macs, including M1, M2, M3, and M4 |
| `Electron-...-x64.dmg` | Intel-based Macs |
| `Electron-...-arm64.zip` or `Electron-...-x64.zip` | Archive distribution; most users should prefer the `.dmg` installer |

### Linux — Electron

| Filename pattern | Compatible distribution |
| --- | --- |
| `Electron-...-x86_64.AppImage` | General-purpose x86_64 Linux package; make it executable before launching |
| `Electron-...-amd64.deb` | Ubuntu, Debian, and related distributions |

### Files you do not need to download manually

- `*.blockmap`: metadata used for incremental application updates; it is not an installer.
- Automatically generated `Source code (zip/tar.gz)` archives: these contain only the contents of this public distribution repository. They are **not the AIMind.ing application source code and cannot be used to install the application**.

## Stable releases and RC releases

- **Stable release:** a version such as `v0.2.5`, intended for most users.
- **RC / Pre-release:** a version such as `v0.2.6-rc.2`, which may include newer platform packages, fixes, or release-validation changes but can still contain unresolved issues.

Recommended selection order:

1. Identify your operating system and CPU architecture.
2. Choose Electron for compatibility or Tauri for a lightweight installation.
3. Choose a stable release for reliability or an RC release for early access.

## Installation notes

- AIMind.ing is evolving quickly. Back up or export important workspace data before upgrading.
- If Windows SmartScreen, macOS Gatekeeper, or a Linux desktop environment displays a security warning, first confirm that the installer came from this repository's official Releases page and verify its version and filename.
- If the Tauri edition does not start on Windows, check or install [Microsoft Edge WebView2 Runtime](https://developer.microsoft.com/microsoft-edge/webview2/).
- If a local model cannot be reached, verify that the model service is running, the Base URL and port are correct, and your `localhost` / `127.0.0.1`, proxy, firewall, and certificate settings allow the connection.

## About this repository

This repository is responsible only for:

- Publishing public releases and finished installers;
- Providing release metadata and public release automation;
- Helping users understand AIMind.ing and select the appropriate desktop package.

The AIMind.ing application source code, Electron and Tauri source code, and production build process are maintained in a private source repository and are not included in this public distribution repository.

---

**Download AIMind.ing:** <https://github.com/AIMind-ing/release/releases>
