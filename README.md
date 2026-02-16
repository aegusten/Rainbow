# Rainbow

Owner: **Yan**

## About

Rainbow is a self-hosted remote access app for desktop control.

This codebase is based on **RustDesk**.  
Core networking and remote-control functionality comes from RustDesk, with Rainbow-specific branding and UI changes.

## What this build is for

- Remote desktop control by ID/password
- Self-hosted server usage (ID/Relay server)
- Two desktop UI modes:
  - **Admin UI** (full controls)
  - **User UI** (display-only host panel)
- English-only UI

## Prerequisites (Windows)

- Rust toolchain (`rustup`, `cargo`)
- Flutter SDK (for desktop UI)
- Visual Studio C++ Build Tools
- `vcpkg` dependencies (required by RustDesk core)

## Build and Run (Windows)

### 1) Clone and enter project

```powershell
git clone https://github.com/aegusten/Rainbow.git
cd Rainbow
```

### 2) Install native dependencies with vcpkg

```powershell
# Example (adjust VCPKG_ROOT path to your machine)
$env:VCPKG_ROOT="D:\vcpkg"

# Required libraries
vcpkg install libvpx:x64-windows-static libyuv:x64-windows-static opus:x64-windows-static aom:x64-windows-static
```

### 3) Build Flutter desktop bundle

```powershell
cd flutter
flutter pub get
cd ..
```

### 4) Run debug build

```powershell
cargo run
```

### 5) Build release

```powershell
cargo build --release
```

Output binary:

```text
target\release\rainbow.exe
```

## Install / Deploy

For simple internal deployment:

1. Build release on your main machine.
2. Copy `target\release\rainbow.exe` and required runtime files to target machine.
3. Run as standard app (or install via your own packaging flow).

## Basic usage

1. Open Rainbow on host machine.
2. Share host ID and password.
3. Remote side enters host ID and connects.
4. Use **Admin/User UI mode** from Settings depending on operator needs.

## Notes

- This project keeps RustDesk core design and protocol behavior.
- If you change server endpoints, configure your ID/Relay server in settings before testing.
