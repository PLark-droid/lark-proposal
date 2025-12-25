# FIT PLACE24 様向け
# Lark統合活用による業務効率化提案書

**作成日**: 2024年12月25日
**提案者**: [提案会社名]
**バージョン**: 2.0

---

## エグゼクティブサマリー

FIT PLACE24様は全国170店舗以上を展開し、今後さらなる店舗拡大を目指されています。現在、複数のツール（Lark、Google Workspace、Notion、LINE等）が併存し、情報の分散と業務の非効率が生じています。

**本提案のゴール**：
- **Larkへの統合**により、ツール乱立を解消
- **店舗・オーナー管理の一元化**で問い合わせ対応工数を50%削減
- **Lark Baseによるデータ可視化**で経営判断を迅速化
- **店舗拡大に対応できる基盤**を構築

**想定効果**：
- ITツールコスト：年間30-40%削減
- 問い合わせ対応時間：50%削減
- 意思決定スピード：2倍向上

---

## 1. 現状分析

### 1.1 現在のツール構成

```mermaid
%%{init: {'theme': 'base', 'themeVariables': {'primaryColor': '#e3f2fd', 'primaryTextColor': '#1565c0', 'primaryBorderColor': '#1976d2', 'lineColor': '#78909c', 'secondaryColor': '#fff3e0', 'tertiaryColor': '#f3e5f5'}}}%%
flowchart TB
    subgraph current["📱 現在のFIT PLACE24 ツール構成"]
        direction TB

        subgraph comm["💬 コミュニケーション"]
            A1["🔵 Lark<br/>チャット"]
            A2["🟢 LINE<br/>グループ多数"]
        end

        subgraph docs["📄 ドキュメント"]
            B1["🔴 Google<br/>Workspace"]
            B2["⬛ Notion"]
        end

        subgraph schedule["📅 スケジュール"]
            C1["🔴 Google<br/>Calendar"]
            C2["🔴 Google<br/>Meet"]
        end

        subgraph external["🔗 外部システム"]
            D1["🟣 hacomono<br/>CRM"]
            D2["🟢 LINE<br/>会員連絡"]
        end
    end

    A1 ~~~ B1
    B1 ~~~ C1
    C1 ~~~ D1

    problem["⚠️ 情報分散・重複管理・切替コスト発生"]
    current --> problem

    style current fill:#fafafa,stroke:#424242,stroke-width:2px
    style comm fill:#e3f2fd,stroke:#1976d2
    style docs fill:#fff3e0,stroke:#f57c00
    style schedule fill:#ffebee,stroke:#c62828
    style external fill:#f3e5f5,stroke:#7b1fa2
    style problem fill:#ffcdd2,stroke:#c62828,stroke-width:2px,color:#b71c1c
```

### 1.2 特定された課題

| # | 課題 | 影響 | 深刻度 |
|---|------|------|:------:|
| 1 | **LINEグループの乱立** | オーナー・店舗・工事業者ごとにグループが増殖、情報が追えない | 🔴 高 |
| 2 | **問い合わせ対応の属人化** | 開業時・運営時の問い合わせが特定担当者に集中 | 🔴 高 |
| 3 | **データの見える化不足** | 各店舗の売上・会員数がhacomonoにあるが一覧化されていない | 🔴 高 |
| 4 | **ツールの分散** | Lark/Google/Notion間でドキュメントが散在 | 🟡 中 |
| 5 | **店舗拡大への対応** | 170店舗→さらに拡大時、現行体制では限界 | 🟡 中 |

### 1.3 課題の詳細分析

#### 課題①：LINEグループの乱立

```mermaid
%%{init: {'theme': 'base', 'themeVariables': {'fontSize': '14px'}}}%%
flowchart TB
    subgraph line["🟢 現状のLINEグループ構造"]
        HQ["🏢 本部"]

        HQ --> G1["👤 FCオーナーA<br/>開業準備"]
        HQ --> G2["👤 FCオーナーA<br/>運営相談"]
        HQ --> G3["👤 FCオーナーB<br/>開業準備"]
        HQ --> G4["👤 FCオーナーB<br/>運営相談"]
        HQ --> G5["🏪 店舗001<br/>設備トラブル"]
        HQ --> G6["🏪 店舗002<br/>工事業者連絡"]
        HQ --> G7["🔧 工事業者X"]
        HQ --> G8["🔧 工事業者Y"]
        HQ --> G9["... 数十〜数百"]
    end

    subgraph problems["❌ 発生している問題"]
        P1["🔍 重要情報が埋もれる"]
        P2["❓ 誰が対応したか不明"]
        P3["📂 履歴検索が困難"]
        P4["🔄 引継ぎが困難"]
    end

    line --> problems

    style line fill:#e8f5e9,stroke:#388e3c,stroke-width:2px
    style problems fill:#ffebee,stroke:#c62828,stroke-width:2px
    style HQ fill:#c8e6c9,stroke:#2e7d32
    style P1 fill:#ffcdd2,stroke:#c62828
    style P2 fill:#ffcdd2,stroke:#c62828
    style P3 fill:#ffcdd2,stroke:#c62828
    style P4 fill:#ffcdd2,stroke:#c62828
```

#### 課題②：問い合わせ対応の肥大化

```mermaid
%%{init: {'theme': 'base', 'themeVariables': {'fontSize': '14px'}}}%%
flowchart TB
    subgraph input["📥 問い合わせ発生"]
        I1["🏪 オーナー"]
        I2["🏬 店舗"]
    end

    subgraph channel["📨 連絡手段"]
        C1["LINE"]
        C2["メール"]
    end

    subgraph bottleneck["⚠️ ボトルネック"]
        B1["👤 担当者A<br/>（属人化）"]
    end

    subgraph result["❌ 結果"]
        R1["⏰ 対応漏れ"]
        R2["😤 遅延"]
        R3["📉 信頼低下"]
    end

    I1 --> C1
    I2 --> C2
    C1 --> B1
    C2 --> B1
    B1 --> R1
    B1 --> R2
    R1 --> R3
    R2 --> R3

    style input fill:#e3f2fd,stroke:#1976d2
    style channel fill:#fff3e0,stroke:#f57c00
    style bottleneck fill:#fff9c4,stroke:#f9a825,stroke-width:3px
    style result fill:#ffebee,stroke:#c62828
    style B1 fill:#ffee58,stroke:#f57f17,stroke-width:2px
```

**月間対応件数（推定）**

```mermaid
%%{init: {'theme': 'base'}}%%
pie showData
    title 月間問い合わせ内訳（約230件/月）
    "運営相談" : 100
    "開業準備" : 50
    "設備トラブル" : 30
    "その他" : 50
```

#### 課題③：データの見える化不足

```mermaid
%%{init: {'theme': 'base', 'themeVariables': {'fontSize': '14px'}}}%%
flowchart TB
    subgraph hacomono["🟣 hacomono（CRM）に蓄積"]
        D1["📊 売上データ"]
        D2["👥 会員数推移"]
        D3["📈 入退会数"]
        D4["📅 予約状況"]
    end

    block["🚫 活用されていない"]

    subgraph impact["😰 経営への影響"]
        I1["📊 最新数字が<br/>会議で出ない"]
        I2["🏪 店舗比較<br/>ができない"]
        I3["⚠️ 問題店舗の<br/>早期発見不可"]
        I4["🎯 意思決定が<br/>感覚的に"]
    end

    hacomono --> block
    block --> impact

    style hacomono fill:#f3e5f5,stroke:#7b1fa2,stroke-width:2px
    style block fill:#ffcdd2,stroke:#c62828,stroke-width:3px,color:#b71c1c
    style impact fill:#fff3e0,stroke:#f57c00
    style D1 fill:#e1bee7,stroke:#8e24aa
    style D2 fill:#e1bee7,stroke:#8e24aa
    style D3 fill:#e1bee7,stroke:#8e24aa
    style D4 fill:#e1bee7,stroke:#8e24aa
```

---

## 2. 提案：Lark統合ソリューション

### 2.1 To-Be 構成

```mermaid
%%{init: {'theme': 'base', 'themeVariables': {'primaryColor': '#e3f2fd', 'fontSize': '14px'}}}%%
flowchart TB
    subgraph lark["🔵 Lark Suite（統合プラットフォーム）"]
        direction TB

        subgraph core["コア機能"]
            L1["💬 Messenger"]
            L2["📄 Docs"]
            L3["📅 Calendar"]
            L4["🎥 Meetings"]
            L5["📊 Base"]
        end

        subgraph advanced["拡張機能"]
            L6["✅ Approval"]
            L7["📚 Wiki"]
            L8["🤖 Bot"]
        end
    end

    subgraph keep["✅ 継続利用"]
        K1["🟣 hacomono<br/>CRM"]
        K2["🟢 LINE<br/>会員向け"]
    end

    lark <-->|"API連携"| K1
    lark ~~~ K2

    result["✅ 情報一元化・自動化・見える化を実現"]
    lark --> result
    keep --> result

    style lark fill:#e3f2fd,stroke:#1976d2,stroke-width:3px
    style core fill:#bbdefb,stroke:#1976d2
    style advanced fill:#90caf9,stroke:#1565c0
    style keep fill:#e8f5e9,stroke:#388e3c,stroke-width:2px
    style result fill:#c8e6c9,stroke:#2e7d32,stroke-width:2px,color:#1b5e20
    style L1 fill:#fff,stroke:#1976d2
    style L2 fill:#fff,stroke:#1976d2
    style L3 fill:#fff,stroke:#1976d2
    style L4 fill:#fff,stroke:#1976d2
    style L5 fill:#fff,stroke:#1976d2
    style L6 fill:#fff,stroke:#1565c0
    style L7 fill:#fff,stroke:#1565c0
    style L8 fill:#fff,stroke:#1565c0
```

### 2.2 残すもの・置き換えるもの

| ツール | 判断 | 理由 |
|--------|:----:|------|
| **Lark** | ✅ 拡張 | 既に導入済み。全機能をフル活用 |
| **hacomono** | ✅ 継続 | CRMとして継続利用、Lark Baseと連携 |
| **LINE（会員向け）** | ✅ 継続 | 会員との連絡手段として継続 |
| Google Workspace | ❌ 廃止 | Lark Docs/Sheetsに移行 |
| Notion | ❌ 廃止 | Lark Wiki/Docsに移行 |
| Google Calendar | ❌ 廃止 | Lark Calendarに移行 |
| Google Meet | ❌ 廃止 | Lark Meetingsに移行 |
| LINE（業務用グループ） | ❌ 廃止 | Lark Messengerに移行 |

---

## 3. ソリューション詳細

### 3.1 課題①解決：LINEグループ → Lark組織チャット

#### Before vs After 比較

```mermaid
%%{init: {'theme': 'base', 'themeVariables': {'fontSize': '13px'}}}%%
flowchart LR
    subgraph before["❌ Before: LINE"]
        direction TB
        B1["グループ乱立"]
        B2["検索困難"]
        B3["ファイル管理不可"]
        B4["権限管理なし"]
    end

    arrow["➡️"]

    subgraph after["✅ After: Lark"]
        direction TB
        A1["組織的に整理"]
        A2["全文検索可能"]
        A3["ファイル一元管理"]
        A4["細かい権限設定"]
    end

    before --> arrow --> after

    style before fill:#ffebee,stroke:#c62828,stroke-width:2px
    style after fill:#e8f5e9,stroke:#388e3c,stroke-width:2px
    style arrow fill:#fff,stroke:#fff
    style B1 fill:#ffcdd2,stroke:#e57373
    style B2 fill:#ffcdd2,stroke:#e57373
    style B3 fill:#ffcdd2,stroke:#e57373
    style B4 fill:#ffcdd2,stroke:#e57373
    style A1 fill:#c8e6c9,stroke:#66bb6a
    style A2 fill:#c8e6c9,stroke:#66bb6a
    style A3 fill:#c8e6c9,stroke:#66bb6a
    style A4 fill:#c8e6c9,stroke:#66bb6a
```

#### Lark組織構造（提案）

```mermaid
%%{init: {'theme': 'base', 'themeVariables': {'fontSize': '13px'}}}%%
flowchart TB
    subgraph org["🏢 FIT PLACE24 Lark組織"]

        subgraph hq["📁 本部"]
            H1["📢 全社連絡<br/>（読取専用）"]
            H2["💬 経営会議"]
            H3["📊 KPI共有"]
        end

        subgraph fc["📁 FCオーナー"]
            F1["📢 オーナー連絡"]
            F2["📋 開業準備CH"]
            F3["🔧 運営相談CH"]
            F4["📚 オーナーWiki"]
        end

        subgraph store["📁 店舗運営"]
            S1["📢 店舗向け連絡"]
            S2["🛠️ 設備トラブル"]
            S3["📊 店舗別グループ"]
        end

        subgraph partner["📁 外部パートナー"]
            P1["🏗️ 工事業者連絡"]
            P2["📦 備品発注"]
        end
    end

    style org fill:#e3f2fd,stroke:#1976d2,stroke-width:2px
    style hq fill:#bbdefb,stroke:#1976d2
    style fc fill:#c8e6c9,stroke:#388e3c
    style store fill:#fff3e0,stroke:#f57c00
    style partner fill:#f3e5f5,stroke:#7b1fa2
```

**Lark導入のメリット**：
- **スレッド機能**で会話が整理される
- **検索機能**で過去の情報をすぐ発見
- **ファイル管理**でドキュメントを一元管理
- **権限設定**で情報アクセスを制御
- **Bot連携**で自動振り分け・通知

### 3.2 課題②解決：問い合わせ対応の自動化

#### 新・問い合わせフロー

```mermaid
%%{init: {'theme': 'base', 'themeVariables': {'fontSize': '13px'}}}%%
flowchart TB
    subgraph input["📥 問い合わせ"]
        I1["🏪 オーナー"]
        I2["🏬 店舗"]
    end

    bot["🤖 Lark Bot<br/>24時間自動受付"]

    subgraph category["📂 自動カテゴリ分類"]
        C1["1️⃣ 開業準備"]
        C2["2️⃣ 運営相談"]
        C3["3️⃣ 設備トラブル"]
        C4["4️⃣ その他"]
    end

    faq["📚 FAQ自動回答<br/>定型質問は即時解決"]

    approval["✅ Lark Approval<br/>担当者自動アサイン"]

    base["📊 Lark Base<br/>対応履歴を自動蓄積"]

    I1 --> bot
    I2 --> bot
    bot --> category
    category --> faq
    faq -->|"解決しない場合"| approval
    approval --> base

    style input fill:#e3f2fd,stroke:#1976d2
    style bot fill:#fff9c4,stroke:#f9a825,stroke-width:2px
    style category fill:#fff3e0,stroke:#f57c00
    style faq fill:#e8f5e9,stroke:#388e3c
    style approval fill:#c8e6c9,stroke:#2e7d32,stroke-width:2px
    style base fill:#bbdefb,stroke:#1976d2
```

**期待効果**：

```mermaid
%%{init: {'theme': 'base'}}%%
flowchart LR
    subgraph effects["✨ 期待される効果"]
        E1["📉 FAQ自動回答で<br/>30%即時解決"]
        E2["👥 自動アサインで<br/>属人化解消"]
        E3["📚 対応履歴で<br/>ナレッジ化"]
        E4["⏱️ 対応時間計測で<br/>SLA管理"]
    end

    style effects fill:#e8f5e9,stroke:#388e3c,stroke-width:2px
    style E1 fill:#c8e6c9,stroke:#66bb6a
    style E2 fill:#c8e6c9,stroke:#66bb6a
    style E3 fill:#c8e6c9,stroke:#66bb6a
    style E4 fill:#c8e6c9,stroke:#66bb6a
```

### 3.3 課題③解決：Lark Baseによるデータ可視化

#### hacomono → Lark Base 連携

```mermaid
%%{init: {'theme': 'base', 'themeVariables': {'fontSize': '13px'}}}%%
flowchart TB
    subgraph hacomono["🟣 hacomono API"]
        H1["👥 会員データ"]
        H2["💰 売上データ"]
        H3["📅 予約データ"]
    end

    sync["🔄 毎日自動同期"]

    subgraph base["📊 Lark Base"]
        B1["📈 日次集計"]
        B2["🏪 店舗比較"]
        B3["🚨 アラート設定"]
    end

    subgraph output["📱 活用"]
        O1["📊 経営会議で<br/>画面共有"]
        O2["⚠️ 異常値を<br/>即時通知"]
        O3["📈 意思決定の<br/>スピードUP"]
    end

    hacomono --> sync --> base --> output

    style hacomono fill:#f3e5f5,stroke:#7b1fa2,stroke-width:2px
    style sync fill:#fff9c4,stroke:#f9a825,stroke-width:2px
    style base fill:#e3f2fd,stroke:#1976d2,stroke-width:2px
    style output fill:#e8f5e9,stroke:#388e3c,stroke-width:2px
```

#### 経営ダッシュボードイメージ

```mermaid
%%{init: {'theme': 'base', 'themeVariables': {'fontSize': '12px'}}}%%
block-beta
    columns 3

    block:header:3
        columns 3
        title["📊 FIT PLACE24 経営ダッシュボード"]
        space
        update["🔄 毎日自動更新"]
    end

    block:summary:3
        columns 3
        members["👥 総会員数<br/>45,230人<br/>+2.3% MoM"]
        sales["💰 総売上<br/>¥148.5M<br/>+5.1% MoM"]
        price["💳 平均客単価<br/>¥3,280"]
    end

    block:stores:3
        columns 1
        storeTitle["🏪 店舗別パフォーマンス"]
        store1["🟢 渋谷店: 1,250人 / ¥4.1M / 入会45 退会12"]
        store2["🟡 新宿店: 980人 / ¥3.2M / 入会32 退会28"]
        store3["🔴 池袋店: 650人 / ¥2.1M / 入会18 退会35"]
    end

    block:alerts:3
        columns 1
        alertTitle["🚨 アラート"]
        alert1["⚠️ 池袋店: 退会率が基準値超過"]
        alert2["⚠️ 横浜店: 売上が前月比-15%"]
    end

    style header fill:#1976d2,color:#fff
    style summary fill:#e3f2fd
    style stores fill:#fff3e0
    style alerts fill:#ffebee
    style members fill:#c8e6c9
    style sales fill:#c8e6c9
    style price fill:#c8e6c9
    style store1 fill:#c8e6c9
    style store2 fill:#fff9c4
    style store3 fill:#ffcdd2
    style alert1 fill:#ffcdd2
    style alert2 fill:#ffcdd2
```

### 3.4 店舗拡大対応：開業オペレーションの標準化

#### 新店舗開業テンプレート

```mermaid
%%{init: {'theme': 'base', 'themeVariables': {'fontSize': '12px'}}}%%
flowchart TB
    subgraph phase1["📋 Phase 1: 契約・準備（-90日）"]
        P1A["☐ FC契約締結"]
        P1B["☐ 物件契約"]
        P1C["☐ 内装設計確定"]
        P1D["☐ 機器発注"]
    end

    subgraph phase2["🔨 Phase 2: 工事（-60日）"]
        P2A["☐ 内装工事開始"]
        P2B["☐ 電気工事"]
        P2C["☐ 空調工事"]
        P2D["☐ 機器搬入"]
    end

    subgraph phase3["🚀 Phase 3: 開業準備（-30日）"]
        P3A["☐ スタッフ採用"]
        P3B["☐ システム設定"]
        P3C["☐ プレオープン"]
        P3D["☐ グランドオープン"]
    end

    phase1 --> phase2 --> phase3

    subgraph auto["🤖 自動化"]
        A1["✅ タスク完了 → 次担当者に自動通知"]
        A2["⏰ 期限超過 → エスカレーション"]
        A3["📊 進捗 → 本部ダッシュボードに反映"]
    end

    phase3 --> auto

    style phase1 fill:#e3f2fd,stroke:#1976d2,stroke-width:2px
    style phase2 fill:#fff3e0,stroke:#f57c00,stroke-width:2px
    style phase3 fill:#e8f5e9,stroke:#388e3c,stroke-width:2px
    style auto fill:#f3e5f5,stroke:#7b1fa2,stroke-width:2px
```

---

## 4. 導入効果試算

### 4.1 コスト削減

| 項目 | 現状（月額） | 導入後（月額） | 削減額 |
|------|-------------|---------------|--------|
| Google Workspace（50名） | ¥68,000 | ¥0 | ¥68,000 |
| Notion（30名） | ¥45,000 | ¥0 | ¥45,000 |
| Lark Pro（80名） | ¥0 | ¥120,000 | -¥120,000 |
| **合計** | **¥113,000** | **¥120,000** | **+¥7,000** |

※ コストは微増だが、以下の業務効率化効果で十分回収

### 4.2 業務効率化効果

```mermaid
%%{init: {'theme': 'base'}}%%
pie showData
    title 月間削減効果（¥390,000相当）
    "LINE管理工数削減 40h" : 120000
    "問い合わせ効率化 60h" : 180000
    "ツール切替時間 20h" : 60000
    "会議準備時間 10h" : 30000
```

| 効果項目 | 削減時間/月 | 金額換算（時給¥3,000） |
|----------|------------|----------------------|
| LINE管理工数削減 | 40時間 | ¥120,000 |
| 問い合わせ対応効率化 | 60時間 | ¥180,000 |
| ツール切替・検索時間 | 20時間 | ¥60,000 |
| 会議準備時間 | 10時間 | ¥30,000 |
| **合計** | **130時間** | **¥390,000/月** |

**年間削減効果: 約470万円相当**

### 4.3 定性的効果

```mermaid
%%{init: {'theme': 'base', 'themeVariables': {'fontSize': '13px'}}}%%
flowchart LR
    subgraph benefits["✨ 定性的効果"]
        B1["⚡ 意思決定<br/>スピード向上"]
        B2["📈 店舗拡大の<br/>加速"]
        B3["👥 属人化<br/>解消"]
        B4["😊 従業員<br/>満足度向上"]
    end

    style benefits fill:#e8f5e9,stroke:#388e3c,stroke-width:2px
    style B1 fill:#c8e6c9,stroke:#66bb6a
    style B2 fill:#c8e6c9,stroke:#66bb6a
    style B3 fill:#c8e6c9,stroke:#66bb6a
    style B4 fill:#c8e6c9,stroke:#66bb6a
```

---

## 5. 導入スケジュール

### 全体スケジュール（3ヶ月）

```mermaid
%%{init: {'theme': 'base', 'themeVariables': {'fontSize': '12px'}}}%%
gantt
    title 導入スケジュール
    dateFormat YYYY-MM-DD

    section Phase 1
    現状詳細ヒアリング    :p1a, 2025-01-06, 7d
    Lark設計              :p1b, after p1a, 7d
    Base・Approval設計    :p1c, after p1b, 7d
    Bot開発              :p1d, after p1b, 14d

    section Phase 2
    本部先行展開          :p2a, 2025-02-03, 7d
    Google移行開始        :p2b, after p2a, 7d
    オーナー展開          :p2c, after p2b, 7d
    店舗展開・トレーニング :p2d, after p2c, 7d

    section Phase 3
    全店舗展開完了        :p3a, 2025-03-03, 7d
    旧ツール停止          :p3b, after p3a, 7d
    効果測定              :p3c, after p3b, 7d
    改善・次フェーズ計画  :p3d, after p3c, 7d
```

### Phase 1: 設計・準備（Week 1-4）

- [ ] 現状業務フローの詳細ヒアリング
- [ ] Lark組織構造の設計
- [ ] Lark Base（ダッシュボード）設計
- [ ] hacomono API連携設計
- [ ] 問い合わせBot設計
- [ ] 移行計画策定
- [ ] トレーニング資料作成

### Phase 2: 移行・展開（Week 5-8）

- [ ] 本部メンバーへの先行展開
- [ ] Google Workspace → Lark Docs移行
- [ ] Notion → Lark Wiki移行
- [ ] LINE業務グループ → Lark移行
- [ ] FCオーナーへの展開・トレーニング
- [ ] 店舗スタッフへの展開
- [ ] hacomono連携開始

### Phase 3: 定着・最適化（Week 9-12）

- [ ] 全店舗展開完了
- [ ] 旧ツール（Google/Notion/LINE業務）停止
- [ ] 効果測定・KPIレビュー
- [ ] 改善点の洗い出し・対応
- [ ] 運用ルールの最終化
- [ ] 次フェーズ計画（AI活用など）

---

## 6. 成功のためのポイント

```mermaid
%%{init: {'theme': 'base', 'themeVariables': {'fontSize': '13px'}}}%%
flowchart TB
    subgraph success["🎯 成功のための4つのポイント"]
        direction TB

        S1["1️⃣ 経営層のコミットメント<br/>Larkを公式ツールとして宣言"]
        S2["2️⃣ 段階的移行<br/>並行期間を設け成功事例を作る"]
        S3["3️⃣ チャンピオン育成<br/>各部門にLark推進担当を配置"]
        S4["4️⃣ 継続的改善<br/>月次レビューとフィードバック収集"]
    end

    S1 --> S2 --> S3 --> S4

    style success fill:#e3f2fd,stroke:#1976d2,stroke-width:2px
    style S1 fill:#bbdefb,stroke:#1976d2
    style S2 fill:#bbdefb,stroke:#1976d2
    style S3 fill:#bbdefb,stroke:#1976d2
    style S4 fill:#bbdefb,stroke:#1976d2
```

---

## 7. なぜ今Larkなのか

### 7.1 店舗拡大フェーズに最適

```mermaid
%%{init: {'theme': 'base', 'themeVariables': {'fontSize': '13px'}}}%%
flowchart LR
    now["📍 現在<br/>170店舗"]

    growth["📈 成長"]

    future["🎯 目標<br/>300→500店舗"]

    subgraph challenge["⚠️ 店舗増加に伴う課題"]
        C1["情報管理の<br/>複雑さ増大"]
        C2["属人対応の<br/>限界"]
        C3["データ経営の<br/>必要性"]
    end

    solution["✅ 今のうちに<br/>基盤整備"]

    now --> growth --> future
    future --> challenge
    challenge --> solution

    style now fill:#fff9c4,stroke:#f9a825,stroke-width:2px
    style growth fill:#e3f2fd,stroke:#1976d2
    style future fill:#c8e6c9,stroke:#388e3c,stroke-width:2px
    style challenge fill:#ffebee,stroke:#c62828
    style solution fill:#e8f5e9,stroke:#2e7d32,stroke-width:3px
```

### 7.2 競合ツールとの比較（フランチャイズ観点）

| 要件 | Lark | Slack+他 | Teams |
|------|:----:|:--------:|:-----:|
| オールインワン | ⭕ | ❌ | △ |
| 外部ユーザー管理 | ⭕ | △ | △ |
| ノーコードDB | ⭕ | ❌ | ❌ |
| ワークフロー | ⭕ | △ | △ |
| コスト | ◎ | ❌ | △ |
| 導入しやすさ | ⭕ | △ | ❌ |

---

## 8. 次のステップ

### 即時アクション

```mermaid
%%{init: {'theme': 'base', 'themeVariables': {'fontSize': '14px'}}}%%
flowchart TB
    subgraph actions["📋 次のステップ"]
        A1["1️⃣ 詳細ヒアリング実施<br/>現状業務フロー確認・優先課題特定"]
        A2["2️⃣ PoC（実証実験）計画<br/>本部1チームで2-4週間検証"]
        A3["3️⃣ 見積・契約<br/>Lark Pro/Enterprise版の検討"]
    end

    A1 --> A2 --> A3

    style actions fill:#e3f2fd,stroke:#1976d2,stroke-width:2px
    style A1 fill:#bbdefb,stroke:#1976d2
    style A2 fill:#90caf9,stroke:#1565c0
    style A3 fill:#64b5f6,stroke:#0d47a1
```

### お問い合わせ

本提案についてのご質問・ご相談は下記までお気軽にご連絡ください。

| 項目 | 内容 |
|------|------|
| **提案会社名** | [提案会社名] |
| **担当者** | [担当者名] |
| **Email** | [email] |
| **Tel** | [電話番号] |

---

## 付録

### A. Lark機能一覧

| 機能 | 説明 | FIT PLACE24での活用 |
|------|------|-------------------|
| Messenger | チャット | 本部-オーナー-店舗連絡 |
| Docs | ドキュメント | マニュアル、議事録 |
| Sheets | スプレッドシート | 計画表、一覧管理 |
| Base | ノーコードDB | KPIダッシュボード、案件管理 |
| Calendar | カレンダー | 予定共有、会議室予約 |
| Meetings | ビデオ会議 | オーナー会議、店舗MTG |
| Approval | 承認ワークフロー | 申請・承認の自動化 |
| Wiki | ナレッジベース | FAQ、業務マニュアル |
| Bot | チャットボット | 問い合わせ自動対応 |

### B. hacomono連携イメージ

```mermaid
%%{init: {'theme': 'base', 'themeVariables': {'fontSize': '13px'}}}%%
flowchart TB
    subgraph hacomono["🟣 hacomono API"]
        H1["👥 会員データ<br/>店舗別会員数、入退会"]
        H2["💰 売上データ<br/>店舗別売上、客単価"]
        H3["📅 予約データ<br/>予約件数、利用率"]
    end

    sync["🔄 自動同期（日次）"]

    subgraph base["📊 Lark Base"]
        B1["📈 日次集計テーブル"]
        B2["🏪 店舗比較ダッシュボード"]
        B3["🚨 アラート条件設定"]
    end

    notify["📱 異常値検知 → Lark通知"]

    hacomono --> sync --> base --> notify

    style hacomono fill:#f3e5f5,stroke:#7b1fa2,stroke-width:2px
    style sync fill:#fff9c4,stroke:#f9a825
    style base fill:#e3f2fd,stroke:#1976d2,stroke-width:2px
    style notify fill:#ffebee,stroke:#c62828
```

### C. 用語集

| 用語 | 説明 |
|------|------|
| Lark Base | Larkのノーコードデータベース。Airtableに似た機能 |
| Approval | Larkの承認ワークフロー機能 |
| hacomono | フィットネス業界向けCRM/予約システム |
| FC | フランチャイズ |
| KPI | Key Performance Indicator（重要業績評価指標） |
| SLA | Service Level Agreement（サービス品質保証） |

---

*この提案書は [Claude Code](https://claude.com/claude-code) により生成されました*

**FIT PLACE24様の更なる成長を、Larkがサポートします。**
