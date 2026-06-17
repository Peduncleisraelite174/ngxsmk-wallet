# NGXSMK Wallet

**Privacy-first, fully local Digital Identity, Secrets, Password & Secure Document Manager**

NGXSMK Wallet is a zero-knowledge, offline-first desktop vault that keeps your digital life encrypted and under your control. No cloud, no telemetry, no tracking — everything stays on your device.

---

## Features

### Password Management
- AES-256-GCM encrypted credential storage
- Categories: password, passkey, secure note, API key, SSH key, database creds, certificates, software licenses, recovery codes, custom
- Built-in password generator with strength estimation
- Favorites, folders, and search

### Passkeys & WebAuthn
- FIDO2/WebAuthn credential management
- Store and organize passkey metadata

### Secure Documents
- Encrypted file storage with versioning
- Upload, download, and delete directly in-app

### Identity Records
- Store identity documents: passports, national IDs, driver's licenses, insurance, certificates
- Categorized and searchable

### Multi-Factor Authentication (TOTP)
- TOTP token management with live code generation & countdown timer
- QR code setup

### Security Dashboard
- Password strength analysis & scoring
- Weak, reused, old, and breached credential detection
- Have I Been Pwned (HIBP) integration for breach checking
- Actionable recommendations

### Local Secret Scanner
- Scan directories or system environment for exposed credentials
- Pattern-based detection of API keys, tokens, and secrets

### Backup & Recovery
- Encrypted backups with AES + Argon2
- Cloud sync: Google Drive, Dropbox, OneDrive
- Shamir's Secret Sharing for recovery key splitting
- Scheduled automatic backups

### Import & Export
- JSON & CSV export/import
- Bitwarden format import
- Chrome & Edge browser password import

### Platform Security
- Windows Hello biometric unlock
- Auto-lock on idle timeout
- Clipboard auto-clearing
- Anti-devtools detection
- Strict Content Security Policy

### User Experience
- Dark, Light, and System themes
- Accent color customization
- Compact sidebar mode
- Global command palette (`Ctrl+K` / `Cmd+K`)
- Keyboard shortcuts

---

## Architecture

```
┌─────────────────────────────────────────────────────┐
│                    Desktop Shell                     │
│                    Tauri v2                          │
├──────────────────────┬──────────────────────────────┤
│    Frontend (React)  │    Backend (Rust)             │
│                      │                              │
│  · React 19          │  · Tauri Commands            │
│  · TypeScript        │  · Services Layer            │
│  · Tailwind CSS      │  · Crypto Engine             │
│  · Radix UI          │  · Vault Engine              │
│  · Zustand           │  · SQLite (SQLx)             │
│  · TanStack Query    │  · AES-256-GCM / Argon2      │
│  · Framer Motion     │  · Shamir's Secret Sharing   │
└──────────────────────┴──────────────────────────────┘
         │                        │
         └──────── IPC ───────────┘
              (Tauri Commands)
```

### Tech Stack

| Layer | Technology |
|---|---|
| Desktop Framework | Tauri v2 |
| Frontend | React 19, TypeScript, Tailwind CSS, Radix UI, Zustand |
| Backend | Rust, Tokio, SQLx, Serde |
| Database | SQLite (local, auto-created) |
| Cryptography | AES-256-GCM, ChaCha20Poly1305, Argon2, HKDF, HMAC, SHA-2 |
| Authentication | Master password + Windows Hello biometrics |
| Secret Sharing | Shamir's Secret Sharing |
| Backup | Zstd compression, encrypted export, cloud sync (OAuth2) |

---

## System Requirements

| Platform | Minimum | Recommended |
|---|---|---|
| **Windows** | Windows 10 1803+ | Windows 11 |
| **macOS** | macOS 10.15+ | macOS 14+ |
| **Linux** | WebKit2GTK 4.1+ | Ubuntu 22.04+ / Fedora 38+ |
| **RAM** | 512 MB | 2 GB |
| **Storage** | 200 MB | 500 MB |

---

## Download

> Placeholder — add your download links below once binaries are built.

### Latest Release

| Platform | Installer | Portable |
|---|---|---|
| Windows | [Download .msi]() | [Download .exe]() |
| macOS | [Download .dmg]() | — |
| Linux | [Download .AppImage]() | [Download .deb]() |

### All Releases

See the [Releases](https://github.com/YOUR_USERNAME/ngxsmk-wallet/releases) page for all versions and changelogs.

---

## Quick Start

1. **Download** the installer for your platform from the links above
2. **Install** and launch NGXSMK Wallet
3. **Create** your master password on first run
4. **Save** your recovery key in a safe place
5. **Start** adding your passwords, identities, and documents

All data is stored locally in your platform's app data directory. Your master password is the only key.

---

## Building from Source

Building from source requires the Rust backend which is proprietary. Pre-built binaries are the recommended way to use NGXSMK Wallet.

If you have a licensed backend, see [BUILDING.md](./BUILDING.md) for instructions.

---

## Security

NGXSMK Wallet is designed with security as the primary concern:

- **Zero-knowledge architecture** — encryption keys are derived from your master password at runtime and never stored
- **AES-256-GCM** — all vault data encrypted at rest
- **Argon2id** — memory-hard key derivation resists GPU/ASIC attacks
- **Secure memory** — cryptographic material zeroed on lock/exit
- **Constant-time operations** — mitigates timing side-channel attacks
- **Offline-first** — no network requests, no telemetry, no cloud dependence

Found a vulnerability? Contact **[security@ngxsmk.com](mailto:security@ngxsmk.com)**

---

## License

- **Frontend (React/TypeScript):** MIT License
- **Backend (Rust):** Proprietary — All Rights Reserved

See [LICENSE](./LICENSE) for full terms.

---

## About NGXSMK

NGXSMK builds privacy-first tools for individuals and organizations who value digital sovereignty. Learn more at [ngxsmk.com](https://ngxsmk.com).
