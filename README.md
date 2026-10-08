# oobiew: Sovereign BINARY DISSECT

<div align="center">

```
================================================================================
                                oobiew
               Sovereign openOODA BINARY DISSECT
================================================================================
```

**Sovereign BINARY DISSECT**  
*Interactive binary and ELF executable dissector showing headers, symbols, and code.*  
*Two Faces, One Engine:* Modern terminal ergonomics for humans • Zero-leakage MCP for AI agents  
Written in 100% pure [openOODA](https://github.com/openOODA).

[![License: Apache-2.0](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![openOODA](https://img.shields.io/badge/openOODA-1.0-emerald.svg)](https://openooda.org)
[![Architecture: x86_64 | aarch64](https://img.shields.io/badge/Arch-x86__64%20%7C%20aarch64-lightgrey.svg)]()

</div>

---

## 1. Quick Install

### Automated Installer (Linux x86_64 & aarch64)
```bash
curl -fsSL https://openooda-tools.github.io/oobiew/install.sh | bash
```

### Native Package Managers
```bash
# Arch Linux (AUR / PKGBUILD)
yay -S oobiew-bin
# Or manual PKGBUILD:
cd packaging/arch && makepkg -si

# Debian / Ubuntu (.deb)
curl -fsSL https://openooda-tools.github.io/oobiew/install.sh | bash -s -- --deb

# Fedora / RHEL (.rpm)
curl -fsSL https://openooda-tools.github.io/oobiew/install.sh | bash -s -- --rpm
```

### Uninstallation
```bash
oobiew-uninstall
# or: curl -fsSL https://openooda-tools.github.io/oobiew/uninstall.sh | bash
```

---

## 2. CLI Usage

```
usage: oobiew [options] <FILE>

Capability-bounded binary file and ELF executable header dissector.

Options:
  -h, --help               display this help and exit
  -v, --version            output version information and exit
  -H, --header             display executable headers only
  -x, --hex                display canonical hexdump view
  -o, --offset <N>         start offset for hexdump inspection [default: 0]
  -n, --length <N>         maximum bytes to dissect in hexdump [default: 256]
      --json               output telemetry as formatted JSON
      --mcp                run as Model Context Protocol stdio server
```

---

## 3. Model Context Protocol (MCP)

When invoked with `--mcp`, `oobiew` runs a JSON-RPC 2.0 stdio server providing structured tools for AI coding agents:

* `biew_detect`: Detect file format (ELF, PE, Mach-O, WASM, Shebang, ZIP, etc.) and file size.
* `biew_elf`: Dissect ELF header parameters (class, endianness, ABI, type, machine architecture, entry point).
* `biew_hexdump`: Slice canonical hexdump window with offset, hex pairs, and ASCII representation.
* `biew_stats`: Query oobiew dissector engine metadata and supported formats.

```bash
oobiew --mcp
```

---

## 4. Security & Zero Ambient Authority

* **Pure Capability Bounded:** Operates strictly with explicit tokens (`&FsReadCap`, `&ProcessCap`, `&EnvCap`, `&McpCap`). Physical absence of ambient disk/net leakage.
* **Negative-Trust Architecture:** Strict input validation and bounded byte slice limits.
* **Hermetic Binary:** Standalone zero-dependency executable.

---

## 5. License

Apache License, Version 2.0. See [LICENSE](LICENSE) for details.
