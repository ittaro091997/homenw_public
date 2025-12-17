# Cloudflare Zero Trust × Home Lab Network (Portfolio)

個人の自宅ラボ環境で、Cloudflare Zero Trust（WARP / Gateway / Access / Tunnel / CASB）を用いた
リモートアクセスと、家庭内ネットワークで監視や自動化などを検証するために構築した環境です。  
転職活動におけるポートフォリオとして、全体像が一目で伝わるようにドキュメントを作成いたしました。

---

## ドキュメント

### 1. ネットワーク構成図（境界・セグメント・経路）
- `ネットワーク構成図.drawio.svg`

![ネットワーク構成図](./ネットワーク構成図.drawio.svg)

### 2. サーバ構成図（セグメント別に記載）
- `サーバ構成図.drawio.svg`

![サーバ構成図](./サーバ構成図.drawio.svg)

---

## 設計のポイント
- **Zero Trust フロー**
  - WARP によるフルトンネルを前提に、Gateway（DNS/HTTP/L4）と Access（Private Network）で制御
  - IdP（Azure AD）による認証（MFA前提）＋デバイスポスチャを組み合わせて許可判断
- **オンプレ（自宅）× SaaS の統合**
  - CASB により GitHub / Google Cloud の設定リスクを可視化し、運用目線の検証も実施
- **多層防御とネットワーク分離**
  - HomeGW → UTM → FortiGate のレイヤ構造
  - 生活系とサーバ系のセグメントを分離し、経路と制御点を明確化
- **Automation / Monitoring**
  - Proxmox 上で監視（Zabbix）／自動化（Ansible AWX/Terraform）

---
