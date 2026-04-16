[中文](/README.md) | [English](/README_en_US.md) | [日本語](/README_ja_JP.md) | [Русский](/README_ru_RU.md) 

# Caesar's Mihomo Installation & Management Toolkit (Install-Mihomo-Inbounds)

This is a powerful, highly modular, and extremely compatible collection of Mihomo node installation and management scripts. It uses Mihomo (Meta Kernel) instead of Xray as the proxy server core to solve the TCP connection leak issue present in Xray. It supports the perfect co-deployment of multiple mainstream protocols (VLESS-Reality, VLESS Encryption, Shadowsocks 2022, etc.) on a single server, and provides convenient configuration backup, routing management, and Geo data update features.

## ✨ Core Features

  * **Mihomo Core**: Utilizes Mihomo (Clash Meta) as the proxy server, resolving Xray's TCP connection leak bug. It features lower resource consumption and stronger stability. It also supports automated fallback to the `amd64-compatible` instruction set architecture for older CPUs.
  * **Post-Quantum Encryption Support**: Seamlessly supports the VLESS Encryption (ML-KEM-768, Post-Quantum) feature pioneered by Xray, providing highly compatible automatic key conversion and generation.
  * **Smart Multi-Protocol Coexistence**: Uses Python to parse YAML configurations and intelligently appends listeners. You can install multiple different protocols or multi-port nodes as you wish, and it will **absolutely not overwrite** your original node configurations.
  * **Extreme System Compatibility**: Not only does it perfectly support mainstream Systemd-based distributions like Debian/Ubuntu, but it is also **deeply compatible with Alpine Linux (OpenRC)**, making it exceptionally friendly to ultra-minimalist lightweight systems.
  * **NAT / DDNS Friendly**: Built-in feature to customize independent connection addresses. Whether you are using a NAT machine with dynamic ports or resolving via a DDNS domain name, you can generate the correct sharing links with one click.
  * **All-in-One Management**: Provides a unified global management menu (`mihomo-manager`), a routing configuration tool (`mihomo-routing`), and a configuration backup/restore tool (`mihomo-restore`).
  * **Secure Precision Deletion**: Supports precise identification and deletion of specific node configurations by port and protocol, ensuring innocent configurations are never accidentally damaged.

-----

## 🚀 Quick Start (Recommended)

If you want to experience the complete set of management features, it is recommended to directly install the **Unified Management Center (Mihomo Manager)**.

Execute the following command to download and launch the global management menu:

```bash
curl -L https://raw.githubusercontent.com/RomanovCaesar/Install-Mihomo-Inbounds/main/mihomo_manager.sh -o mihomo_manager.sh && chmod +x mihomo_manager.sh && sudo ./mihomo_manager.sh
```

**💡 Pro Tip:**
After the unified management tool is installed, it will automatically register a global command. You can quickly wake up the main menu at any time by typing the following command in your terminal:

```bash
mihomo-manager
```

Within the `mihomo-manager` menu, you can directly invoke all the independent features listed below with a single click, eliminating the need to download scripts individually.

-----

## 📦 Independent Module Installation Guide

If you only want to use a specific feature of this project, you can use the following independent installation commands directly.

### 1\. VLESS Encryption (Post-Quantum) Node Management

Supports the latest generation ML-KEM-768 post-quantum encryption technology. Discards cumbersome configurations; secure connections can be established with just the handshake keys.

```bash
curl -L https://raw.githubusercontent.com/RomanovCaesar/Install-Mihomo-Inbounds/main/install_vless_encryption.sh -o install_vless_encryption.sh && chmod +x install_vless_encryption.sh && sudo ./install_vless_encryption.sh
```

### 2\. VLESS-Reality (Vision) Node Management

Supports automatic generation of X25519 key pairs, uses `xtls-rprx-vision` flow control by default, and connects via Mihomo's listeners.

```bash
curl -L https://raw.githubusercontent.com/RomanovCaesar/Install-Mihomo-Inbounds/main/install_vless_reality.sh -o install_vless_reality.sh && chmod +x install_vless_reality.sh && sudo ./install_vless_reality.sh
```

### 3\. Shadowsocks 2022 & Traditional SS Node Management

Supports blazing-fast next-generation encryption protocols like 2022-blake3-aes, maintains backward compatibility with traditional aes-gcm encryption, and automatically generates strong random passwords.

```bash
curl -L https://raw.githubusercontent.com/RomanovCaesar/Install-Mihomo-Inbounds/main/install_ss2022.sh -o install_ss2022.sh && chmod +x install_ss2022.sh && sudo ./install_ss2022.sh
```

### 4\. Server Routing Tool (Mihomo Routing)

A powerful control panel for server outbound routing. Supports parsing SS and VLESS sharing links and allows visual configuration of routing rules.

```bash
curl -L https://raw.githubusercontent.com/RomanovCaesar/Install-Mihomo-Inbounds/main/mihomo_routing.sh -o mihomo_routing.sh && chmod +x mihomo_routing.sh && sudo ./mihomo_routing.sh
```

*Can be launched at any time after installation using the `mihomo-routing` command.*

### 5\. Backup and Restore Tool (Mihomo Restore)

Accidentally messed up your configuration? Want to migrate your setup? This tool allows you to import configuration files via direct URLs or by manually pasting the `config.yaml` into the console, complete with built-in safety checks to prevent fatal errors.

```bash
curl -L https://raw.githubusercontent.com/RomanovCaesar/Install-Mihomo-Inbounds/main/mihomo_restore.sh -o mihomo_restore.sh && chmod +x mihomo_restore.sh && sudo ./mihomo_restore.sh
```

*Can be launched at any time after installation using the `mihomo-restore` command.*

### 6\. Complete Uninstallation Tool

If you encounter unresolvable critical issues or simply want to clean your server completely, you can use this script. It cleanly wipes system services (Systemd/OpenRC), binaries, logs, and residual configurations.

```bash
curl -L https://raw.githubusercontent.com/RomanovCaesar/Install-Mihomo-Inbounds/main/uninstall_mihomo.sh -o uninstall_mihomo.sh && chmod +x uninstall_mihomo.sh && sudo ./uninstall_mihomo.sh
```

-----

## 🔄 Mapping to Xray Versions

| Xray Script | Mihomo Script | Function |
|---|---|---|
| `install_vless_encryption.sh` | `install_vless_encryption.sh` | VLESS Encryption (PQ) Node Mgmt |
| `install_vless_reality.sh` | `install_vless_reality.sh` | VLESS-Reality Node Mgmt |
| `install_ss2022.sh` | `install_ss2022.sh` | Shadowsocks 2022 Node Mgmt |
| `xray_manager.sh` | `mihomo_manager.sh` | Unified Management Menu |
| `xray_routing.sh` | `mihomo_routing.sh` | Server Routing Config |
| `xray_restore.sh` | `mihomo_restore.sh` | Config Backup & Restore |
| `uninstall_xray.sh` | `uninstall_mihomo.sh` | Complete Uninstallation |
| `update_geo.sh` | `update_geo.sh` | Geo Data Update |

> **Note**: Mihomo now fully supports the new features of VLESS, including Reality and the ML-KEM-768 based Encryption protocol. All components in this toolkit can function normally under this framework.

-----

## 🛠️ Frequently Asked Questions (FAQ)

**Q: Why migrate from Xray to Mihomo?**

**A:** The Xray proxy server suffers from a severe TCP connection leak bug. Mihomo (Meta Kernel) does not have this issue and performs better in terms of resource consumption and stability, making it especially suitable for high-concurrency commercial environments or shared instances.

**Q: My server is a NAT VPS, or my ingress IP is different from my egress IP. What should I do if the generated nodes don't connect?**

**A:** Please select the **"Set Connection Address (NAT/DDNS)"** option in any of the installation menus. Enter the IP address or DDNS domain name you actually use for external connections.

**Q: My older E5 processor cannot install the new version and reports that the v3 architecture is not supported. What should I do?**

**A:** The installation scripts in this repository have been smartly optimized for CPU architecture recognition. For older hardware lacking AVX2 instruction set support (like some E5 v2 and Atom processors), the script will automatically pull the `amd64-compatible` kernel to prevent installation failures.

**Q: How do I view Mihomo's running logs?**

**A:** There is a **"View Logs"** option in the menus of all installation and management scripts. Selecting it allows you to view real-time operation logs. Press `Ctrl + C` to stop.

**Q: How do I update the GeoIP and GeoSite routing rule files?**

**A:** Use the one-click automated cron job setup feature within `mihomo-routing` (Server Routing Tool), which will update them automatically every morning. You can also manually trigger an immediate update from the main management tool (`mihomo-manager`).

**Q: Where is the Mihomo configuration file located?**

**A:** The configuration file is located at `/usr/local/etc/mihomo/config.yaml`. Mihomo uses the YAML format rather than Xray's JSON format.
