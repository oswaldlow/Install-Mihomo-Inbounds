[中文](/README.md) | [English](/README_en_US.md) | [日本語](/README_ja_JP.md) | [Русский](/README_ru_RU.md) 

# Caesar 特製 Mihomo ワンクリックインストール＆管理ツールボックス (Install-Mihomo-Inbounds)

これは、強力でモジュール化された、非常に互換性の高い Mihomo ノードのインストールおよび管理スクリプトのコレクションです。Xray の代わりに Mihomo (Meta Kernel) をプロキシサーバーのコアとして使用することで、Xray に存在する TCP コネクションリーク問題を解決します。1つのサーバー上で複数の主要なプロトコル（VLESS-Reality、VLESS Encryption、Shadowsocks 2022 など）を完全に共存・展開することをサポートし、便利な設定バックアップ、ルーティング管理、および Geo データの更新機能を提供します。

## ✨ 主な機能 (Core Features)

  * **Mihomo コア**: Mihomo (Clash Meta) をプロキシサーバーとして使用し、Xray の TCP コネクションリークのバグを解決します。リソース消費が少なく、安定性が向上しています。また、古い CPU 向けに `amd64-compatible` アーキテクチャの命令セットへの自動フォールバック適応機能もサポートしています。
  * **耐量子暗号化対応 (Post-Quantum)**: Xray が先駆けて開発した VLESS Encryption (ML-KEM-768, Post-Quantum) 機能をシームレスにサポートし、互換性の高い鍵の自動変換と生成を提供します。
  * **複数プロトコルのスマートな共存**: Python を使用して YAML 設定を解析し、スマートにリスナー (listeners) を追加します。複数の異なるプロトコルや複数ポートのノードを自由自在にインストールでき、元のノード設定を**絶対に上書きしません**。
  * **究極のシステム互換性**: Debian / Ubuntu などの Systemd ベースの主流システムを完全にサポートするだけでなく、**Alpine Linux (OpenRC) とも深く互換性があり**、極めてシンプルで軽量なシステムにも非常に適しています。
  * **NAT / DDNS フレンドリー**: 独立した接続先アドレスのカスタマイズ機能を内蔵しています。動的ポートを持つ NAT マシンを使用している場合でも、DDNS ドメイン名による名前解決を行っている場合でも、ワンクリックで正しい共有リンクを生成できます。
  * **一元管理**: グローバルな統合管理メニュー (`mihomo-manager`)、ルーティング設定ツール (`mihomo-routing`)、および設定のバックアップ・復元ツール (`mihomo-restore`) を提供します。
  * **安全で正確な削除**: ポートとプロトコルに基づいて特定のノード設定を正確に識別し削除することをサポートしており、関係のない設定を誤って削除することは絶対にありません。

-----

## 🚀 クイックスタート（推奨）

最も完全な管理機能を体験したい場合は、\*\*統合管理センター（Mihomo Manager）\*\*を直接インストールすることをお勧めします。

以下のコマンドを実行して、グローバル管理メニューをダウンロードし、起動します。

```bash
curl -L https://raw.githubusercontent.com/RomanovCaesar/Install-Mihomo-Inbounds/main/mihomo_manager.sh -o mihomo_manager.sh && chmod +x mihomo_manager.sh && sudo ./mihomo_manager.sh
```

**💡 ヒント:**
統合管理ツールをインストールすると、グローバルコマンドが自動的に登録されます。今後は、ターミナルで以下のコマンドを入力するだけで、いつでもメインメニューを素早く呼び出すことができます。

```bash
mihomo-manager
```

`mihomo-manager` メニュー内では、以下のすべての独立した機能をワンクリックで直接呼び出すことができるため、スクリプトを個別にダウンロードする必要はありません。

-----

## 📦 各機能モジュールの独立インストールガイド

このプロジェクトの特定の機能のみを使用したい場合は、以下の独立したインストールコマンドを直接使用することもできます。

### 1\. VLESS Encryption (Post-Quantum) ノード管理

最新世代の ML-KEM-768 耐量子暗号化テクノロジーをサポートします。煩雑な設定を排除し、ハンドシェイクキーだけで安全な接続を確立できます。

```bash
curl -L https://raw.githubusercontent.com/RomanovCaesar/Install-Mihomo-Inbounds/main/install_vless_encryption.sh -o install_vless_encryption.sh && chmod +x install_vless_encryption.sh && sudo ./install_vless_encryption.sh
```

### 2\. VLESS-Reality (Vision) ノード管理

X25519 キーペアの自動生成をサポートし、デフォルトで `xtls-rprx-vision` フロー制御を使用し、Mihomo のリスナー経由で接続します。

```bash
curl -L https://raw.githubusercontent.com/RomanovCaesar/Install-Mihomo-Inbounds/main/install_vless_reality.sh -o install_vless_reality.sh && chmod +x install_vless_reality.sh && sudo ./install_vless_reality.sh
```

### 3\. Shadowsocks 2022 & 従来の SS ノード管理

2022-blake3-aes などの超高速次世代暗号化プロトコルをサポートし、従来の aes-gcm 暗号化との下位互換性を保ちながら、強力なランダムパスワードを自動生成します。

```bash
curl -L https://raw.githubusercontent.com/RomanovCaesar/Install-Mihomo-Inbounds/main/install_ss2022.sh -o install_ss2022.sh && chmod +x install_ss2022.sh && sudo ./install_ss2022.sh
```

### 4\. サーバー側ルーティングツール (Mihomo Routing)

強力なサーバー側のアウトバウンド（送信）ルーティングコントロールパネルです。SS や VLESS の共有リンクの解析をサポートし、ルーティングルールを視覚的に設定できます。

```bash
curl -L https://raw.githubusercontent.com/RomanovCaesar/Install-Mihomo-Inbounds/main/mihomo_routing.sh -o mihomo_routing.sh && chmod +x mihomo_routing.sh && sudo ./mihomo_routing.sh
```

*インストール後は、いつでも `mihomo-routing` コマンドで呼び出すことができます。*

### 5\. バックアップと復元ツール (Mihomo Restore)

誤って設定を変更してしまった場合や、設定を移行したい場合に最適です。このツールを使用すると、直接の URL 経由で設定ファイルをインポートしたり、コンソールを開いて手動で `config.yaml` を貼り付けたりすることができます。エラーを防ぐ安全テスト機能が組み込まれています。

```bash
curl -L https://raw.githubusercontent.com/RomanovCaesar/Install-Mihomo-Inbounds/main/mihomo_restore.sh -o mihomo_restore.sh && chmod +x mihomo_restore.sh && sudo ./mihomo_restore.sh
```

*インストール後は、いつでも `mihomo-restore` コマンドで呼び出すことができます。*

### 6\. 完全アンインストールツール

解決できない深刻な問題が発生した場合や、サーバーを完全にクリーンアップしたい場合は、このスクリプトを使用できます。システムサービス (Systemd/OpenRC)、バイナリファイル、ログ、および残留設定を極めてクリーンに消去します。

```bash
curl -L https://raw.githubusercontent.com/RomanovCaesar/Install-Mihomo-Inbounds/main/uninstall_mihomo.sh -o uninstall_mihomo.sh && chmod +x uninstall_mihomo.sh && sudo ./uninstall_mihomo.sh
```

-----

## 🔄 Xray バージョンとの対応関係

| Xray スクリプト | Mihomo スクリプト | 機能 |
|---|---|---|
| `install_vless_encryption.sh` | `install_vless_encryption.sh` | VLESS Encryption (PQ) ノード管理 |
| `install_vless_reality.sh` | `install_vless_reality.sh` | VLESS-Reality ノード管理 |
| `install_ss2022.sh` | `install_ss2022.sh` | Shadowsocks 2022 ノード管理 |
| `xray_manager.sh` | `mihomo_manager.sh` | 統合管理メニュー |
| `xray_routing.sh` | `mihomo_routing.sh` | サーバー側ルーティング設定 |
| `xray_restore.sh` | `mihomo_restore.sh` | 設定のバックアップと復元 |
| `uninstall_xray.sh` | `uninstall_mihomo.sh` | 完全アンインストール |
| `update_geo.sh` | `update_geo.sh` | Geo データの更新 |

> **ヒント**: Mihomo は、Reality や ML-KEM-768 ベースの Encryption プロトコルを含む VLESS の新機能を全面的にサポートするようになりました。このツールボックスのすべてのコンポーネントは、このフレームワークの下で正常に機能します。

-----

## 🛠️ よくある質問 (FAQ)

**Q: なぜ Xray から Mihomo に移行するのですか？**

**A:** Xray プロキシサーバーには、深刻な TCP コネクションリークのバグが存在します。Mihomo (Meta Kernel) にはこの問題がなく、リソース消費と安定性の面で優れており、特に同時接続数の多い商用環境や共有（合乗り）サーバーに最適です。

**Q: 私のサーバーは NAT VPS であるか、または入口（Ingress）IP と出口（Egress）IP が異なります。生成されたノードが繋がらない場合はどうすればよいですか？**

**A:** 任意のインストールメニューで **「接続アドレスの設定 (NAT/DDNS)」(设置连接地址 (NAT/DDNS))** オプションを選択してください。実際に外部接続に使用している IP アドレスまたは DDNS ドメイン名を入力してください。

**Q: 私の古い E5 プロセッサに新しいバージョンをインストールできず、v3 アーキテクチャがサポートされていないというエラーが出ます。どうすればよいですか？**

**A:** 本リポジトリのインストールスクリプトは、CPU アーキテクチャの認識をスマートに最適化しています。AVX2 命令セットをサポートしていない古いハードウェア（一部の E5 v2 や Atom プロセッサなど）に対して、スクリプトは自動的に `amd64-compatible` 互換バージョンのカーネルを取得し、インストールの失敗を防ぎます。

**Q: Mihomo の実行ログを表示するにはどうすればよいですか？**

**A:** 各インストールおよび管理スクリプトのメニューには、**「ログの表示」(查看日志)** オプションがあります。これを選択すると、実行ログをリアルタイムで表示できます。`Ctrl + C` を押すと停止します。

**Q: GeoIP と GeoSite ルーティングルールファイルを更新するにはどうすればよいですか？**

**A:** `mihomo-routing`（サーバー側ルーティングツール）内のワンクリック自動 Cron ジョブ設定機能を使用すると、毎日未明に自動的に更新されます。また、メイン管理ツール (`mihomo-manager`) から手動で即時更新を実行することもできます。

**Q: Mihomo の設定ファイルはどこにありますか？**

**A:** 設定ファイルは `/usr/local/etc/mihomo/config.yaml` にあります。Mihomo は Xray の JSON 形式ではなく YAML 形式を使用します。
