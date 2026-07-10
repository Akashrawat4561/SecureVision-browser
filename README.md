# SecureVision AI Browser 🛡️

![SecureVision Browser Banner](../assets/banner.png)

> **The Next-Generation Security-First Browser.** Built on Electron and Chromium, SecureVision AI Browser is designed from the ground up for researchers, threat analysts, and security-conscious individuals.

## Overview

SecureVision AI Browser replaces the traditional browsing experience with a highly hardened, workspace-driven environment. It natively integrates with the SecureVision Python Backend for real-time AI deepfake scanning, heuristic phishing classification, and live network anomaly detection directly inside your New Tab Dashboard.

## Key Features

### Workspace Session Isolation

- **100% Isolated Partitions:** Workspaces (e.g., *Personal*, *Work*, *Secure*) operate in entirely distinct storage partitions (`persist:<workspaceId>`).
- **Complete Separation:** Cookies, Local Storage, IndexedDB, Cache, and Service Workers never bleed across workspaces.
- **Persistent Tab States:** Tabs are securely persisted to disk and restored instantly when switching between isolated workspaces.

### Built-in Security Dashboard (New Tab)

Every time you open a new tab, you are presented with the SecureVision AI Command Center instead of a blank page.

- **Deepfake Forensic Scanner:** Analyze media URLs using AI-powered forensic models.
- **Phishing Heuristics Scanner:** Evaluate suspicious emails, domains, and messages using real-time detection techniques.
- **Honeypot Decoy Injection:** Deploy honeytoken credentials to detect credential-stealing malware through silent security alerts.

### Ghost Mode & Browser Hardening

- **Ghost Mode:** One-click toggle for stealth sessions with sandboxed routing.
- **Zero-Trust IPC:** A strict Zod-validated IPC layer between the React frontend and Electron backend prevents privilege escalation.
- **Memory Orchestration:** Intelligent background tab throttling and memory cleanup reduce resource consumption and mitigate abusive scripts.

## Technology Stack

| Layer | Technologies |
| :--- | :--- |
| **Core Framework** | Electron, Node.js, Chromium |
| **Frontend** | React 19, Vite, TypeScript |
| **Styling** | Tailwind CSS v4, Framer Motion, Lucide Icons |
| **State Management** | Zustand |
| **Validation** | Zod |
| **Build System** | Electron Builder, pnpm Workspaces |

## Getting Started

### Prerequisites

- Node.js 18+
- pnpm installed globally

```bash
npm install -g pnpm
```

- SecureVision AI Python Backend running on port `8000` for AI-powered features.

### Installation

Navigate to the browser directory:

```bash
cd browser
```

Install dependencies:

```bash
pnpm install
```

Start the development environment:

```bash
pnpm run dev
```

This command starts the Electron main process, Vite development server, and launches the desktop application.

## Production Build

Build distributable installers for your platform:

```bash
# Windows
pnpm run dist:win

# macOS
pnpm run dist:mac

# Linux
pnpm run dist:linux
```

Generated installers will be available in:

```text
browser/dist
```

## Architecture

The browser follows a security-first multi-process architecture.

### Main Process (`src/main/`)

- Window management
- Workspace isolation
- Session partitioning
- Native OS integrations
- Secure file I/O

### Renderer Process (`src/renderer/`)

- Context-isolated React application
- Sidebar
- Workspace management
- SecureVision Dashboard

### BrowserView Layer

- Websites are rendered inside isolated `BrowserView` instances.
- Web content remains completely separated from the React UI layer.
- Each workspace maintains its own dedicated Chromium storage partition.

## License

This project is part of the SecureVision AI ecosystem and is licensed under the MIT License.

---

**Developed by SecureVision AI Systems**
