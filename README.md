# Bridge (Enhanced Multi-Monitor Edition)

[![Release](https://img.shields.io/github/v/release/davidcasanovasola-git/bridge?color=blue&label=Latest%20Release)](https://github.com/davidcasanovasola-git/bridge/releases/latest)
[![CI](https://github.com/davidcasanovasola-git/bridge/actions/workflows/ci.yml/badge.svg)](https://github.com/davidcasanovasola-git/bridge/actions/workflows/ci.yml)
[![License: PolyForm Noncommercial 1.0.0](https://img.shields.io/badge/License-PolyForm%20Noncommercial-blue.svg)](LICENSE)

> **One keyboard and mouse for a Mac and a PC, taken to the next level.**  
> Seamless peer-to-peer control with full multi-monitor setups, an interactive visual display layout designer, dynamic network synchronization, and unified cursor tracking.

---

### Acknowledgement & Upstream Credit
This repository is an enhanced fork of [**Bridge** by Ishan Malu](https://github.com/ishanmalu/bridge). The original Bridge established the rock-solid Rust foundation: direct peer-to-peer communication over encrypted Noise KK sockets, zero-latency input transmission, bidirectional clipboard synchronization, and no third-party servers or accounts. All core protocol and architectural foundations belong to the original author.

---

## Why This Fork?

Upstream Bridge works well for simple single-monitor setups, but modern desk workflows frequently span multiple monitors of different sizes, resolutions, and orientations.

This fork turns Bridge into a powerhouse for power users, dual-workstation setups, and multi-monitor desk layouts:

### 🖥️ Full Multi-Monitor Detection & Physical Geometry
- **Dynamic Multi-Screen Detection**: Automatically queries all attached displays on both Windows and macOS.
- **Physical Size & DPI Calculations**: Computes real physical display dimensions (inches) and DPI scaling rather than relying on arbitrary 24-inch fallbacks.
- **Persistent Monitor Topologies**: Remembers peer multi-monitor setups across restarts.

### 🎨 Interactive Visual Layout Designer
- **Visual Display Canvas**: Built-in interactive display designer accessible directly from the app interface (`bridge settings` or tray/menu bar).
- **Magnetic Snapping & Dual Cluster Dragging**: Drag entire machine display clusters or snap monitor edges together effortlessly.
- **Millimeter-Precision Offset Fine-Tuning**: Fine-tune vertical and horizontal monitor alignments to perfectly mirror your physical desk layout.
- **Clean Labeling & Scaling**: Displays clean, readable monitor labels and auto-centers the layout scene dynamically.

### ⚡ Live Network Topology Synchronization
- **Real-Time Layout Sync**: When you adjust your monitor arrangement on one machine, the layout (`peer_side` and offsets) automatically synchronizes across the network to the other machine in real time—no reconnections or manual edits required.

### 🎯 Unified Follow-The-Cursor & Split Hardware
- **Follow-The-Cursor Mode**: The active focus follows the cursor naturally. Move your mouse to the other machine, and your local keyboard automatically forwards to that screen.
- **Split Peripherals**: Allows using Mac keyboard + PC mouse or any combination interchangeably across both systems.

### 🚀 Ultra-Smooth Transitions & Zero Flicker
- **Anti-Flicker Pre-Warping**: Pre-warps the cursor to the exact entry boundary before unhiding, eliminating center-screen cursor flickers during transitions.
- **Accurate 1:1 Edge Crossing**: Precise mathematical border crossing even between screens with vastly different resolutions or vertical offsets.
- **Windows Mouse Delta Accuracy**: Re-centers cursor during raw input capture to eliminate edge race conditions and sudden jumps with high-polling USB mice.

### 🛡️ System Polish & Reliability
- **Clean Goodbye Protocol**: Graceful peripheral release and instant state handover on system quit, sleep, or shutdown.
- **macOS Menu Bar Title**: Clear status visibility right on the macOS menu bar.
- **Windows Path Handling**: Fixes PowerShell relaunch behavior to eliminate quoting bugs on install paths with spaces.

---

## Downloads

Precompiled release binaries are available on the [**Releases Page**](https://github.com/davidcasanovasola-git/bridge/releases/latest):

| Platform | Download | Description |
|---|---|---|
| **Windows** (10 / 11, x64) | [`Bridge-windows.zip`](https://github.com/davidcasanovasola-git/bridge/releases/latest/download/Bridge-windows.zip) / [`.exe`](https://github.com/davidcasanovasola-git/bridge/releases/latest/download/Bridge-windows.exe) | Single standalone executable (MSVC build with embedded WebView2) |
| **macOS** (11+, Universal) | [`Bridge-mac.zip`](https://github.com/davidcasanovasola-git/bridge/releases/latest/download/Bridge-mac.zip) | Universal binary bundle (Apple Silicon M1/M2/M3/M4 & Intel) |

*Checksums are verified in `SHA256SUMS.txt`.*

---

## Quick Setup

1. **Mac**: Unzip `Bridge-mac.zip`, drag `Bridge.app` to `/Applications`, and open it. Grant **Accessibility** permissions when prompted (System Settings → Privacy & Security → Accessibility).
2. **PC**: Download `Bridge-windows.zip` (or `.exe`), move it to `C:\Program Files\Bridge\Bridge.exe`, and right-click → **Run as administrator** (enables elevated window input and adds firewall rules).
3. **Pair**:
   - On the PC: Choose *Pair → Show a pairing code*.
   - On the Mac: Choose *Pair → Enter a pairing code…* and enter the 6-digit code.
4. **Arrange**:
   - Open the **Display Designer** from the menu or CLI (`bridge settings`).
   - Drag your screens to match your desk layout, and enjoy seamless multi-monitor edge crossing!

---

## Building from Source

Requirements:
- Rust 1.80+ (`stable`)
- Windows (MSVC toolchain) or macOS (Xcode Command Line Tools)

```sh
# Clone repository
git clone https://github.com/davidcasanovasola-git/bridge.git
cd bridge

# Run tests
cargo test

# Build optimized release binary
cargo build --release
```

---

## License

Derived from the original Bridge project by Ishan Malu, released under the [PolyForm Noncommercial 1.0.0 License](LICENSE).
