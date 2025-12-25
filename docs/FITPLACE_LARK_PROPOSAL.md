# FIT PLACE24 様向け
# Lark統合活用による業務効率化提案書

**作成日**: 2024年12月25日
**提案者**: [提案会社名]
**バージョン**: 1.0

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
flowchart TB
    subgraph 現状["⚠️ 現在のFIT PLACE24 ツール構成"]
        subgraph comm["コミュニケーション"]
            Lark["💬 Lark<br/>チャット"]
            LINE["📱 LINE<br/>グループ"]
        end

        subgraph docs["ドキュメント"]
            GWS["📄 Google<br/>Workspace"]
            Notion["📝 Notion"]
        end

        subgraph calendar["スケジュール"]
            GCal["📅 Google<br/>Calendar"]
            Meet["🎥 Google<br/>Meet"]
        end

        subgraph crm["顧客管理"]
            hacomono["🏋️ hacomono<br/>CRM"]
        end
    end

    style 現状 fill:#ffe6e6,stroke:#ff0000
    style Lark fill:#4285f4,color:#fff
    style LINE fill:#00c300,color:#fff
    style GWS fill:#fbbc04,color:#000
    style Notion fill:#000,color:#fff
    style GCal fill:#4285f4,color:#fff
    style Meet fill:#00897b,color:#fff
    style hacomono fill:#6366f1,color:#fff
```

**問題点**: 情報分散・重複管理・ツール切替コスト発生

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
flowchart TD
    HQ["🏢 本部"]

    HQ --> A1["FCオーナーA 開業準備"]
    HQ --> A2["FCオーナーA 運営相談"]
    HQ --> B1["FCオーナーB 開業準備"]
    HQ --> B2["FCオーナーB 運営相談"]
    HQ --> S1["店舗001 設備トラブル"]
    HQ --> S2["店舗002 工事業者連絡"]
    HQ --> C1["工事業者X ○○店工事"]
    HQ --> C2["工事業者Y △△店工事"]
    HQ --> ETC["... 数十〜数百グループ"]

    style HQ fill:#00c300,color:#fff
    style A1 fill:#00c300,color:#fff
    style A2 fill:#00c300,color:#fff
    style B1 fill:#00c300,color:#fff
    style B2 fill:#00c300,color:#fff
    style S1 fill:#00c300,color:#fff
    style S2 fill:#00c300,color:#fff
    style C1 fill:#00c300,color:#fff
    style C2 fill:#00c300,color:#fff
    style ETC fill:#ff6b6b,color:#fff
```

**問題点**：
- ❌ 重要な情報が埋もれる
- ❌ 誰が対応したか分からない
- ❌ 履歴検索が困難
- ❌ 担当者変更時の引継ぎが困難

#### 課題②：問い合わせ対応の肥大化

```mermaid
flowchart LR
    subgraph 現状フロー
        Owner["👤 オーナー<br/>店舗"]
        Channel["📱 LINE<br/>📧 メール"]
        Staff["👨‍💼 担当者A<br/>（属人化）"]
        Problem["⚠️ 対応漏れ<br/>遅延"]
        Result["😠 クレーム<br/>信頼低下"]
    end

    Owner --> Channel --> Staff --> Problem --> Result

    style Staff fill:#ff6b6b,color:#fff
    style Problem fill:#ffa500,color:#fff
    style Result fill:#ff0000,color:#fff
```

**対応件数（推定）**：
| カテゴリ | 件数/月 |
|----------|---------|
| 開業準備関連 | 50件 |
| 運営相談 | 100件 |
| 設備トラブル | 30件 |
| その他 | 50件 |
| **合計** | **約230件** |

#### 課題③：データの見える化不足

```mermaid
flowchart TB
    subgraph hacomono["🏋️ hacomono（CRM）に蓄積"]
        D1["📊 各店舗の売上データ"]
        D2["👥 会員数推移"]
        D3["🔄 入退会数"]
        D4["📅 予約状況"]
    end

    hacomono --> Problem["⚠️ 活用されていない"]

    Problem --> R1["❌ 経営会議で最新数字が出ない"]
    Problem --> R2["❌ 店舗比較ができない"]
    Problem --> R3["❌ 問題店舗の早期発見不可"]
    Problem --> R4["❌ 意思決定が感覚的"]

    style hacomono fill:#6366f1,color:#fff
    style Problem fill:#ff6b6b,color:#fff
    style R1 fill:#ffe6e6,stroke:#ff0000
    style R2 fill:#ffe6e6,stroke:#ff0000
    style R3 fill:#ffe6e6,stroke:#ff0000
    style R4 fill:#ffe6e6,stroke:#ff0000
```

---

## 2. 提案：Lark統合ソリューション

### 2.1 To-Be 構成

```mermaid
flowchart TB
    subgraph 提案後["✅ 提案後のFIT PLACE24 ツール構成"]
        subgraph LarkSuite["🟦 Lark Suite"]
            Messenger["💬 Messenger<br/>チャット"]
            Docs["📄 Docs<br/>ドキュメント"]
            Calendar["📅 Calendar<br/>予定管理"]
            Meetings["🎥 Meetings<br/>ビデオ会議"]
            Base["📊 Base<br/>データベース"]
            Approval["✅ Approval<br/>承認フロー"]
            Wiki["📚 Wiki<br/>ナレッジ"]
            Bot["🤖 Bot<br/>自動化"]
        end

        subgraph 継続["継続利用"]
            hacomono["🏋️ hacomono<br/>CRM"]
            LINE2["📱 LINE<br/>会員連絡のみ"]
        end
    end

    LarkSuite <--> |"API連携"| hacomono

    style 提案後 fill:#e6ffe6,stroke:#00aa00
    style LarkSuite fill:#4285f4,color:#fff
    style Messenger fill:#667eea,color:#fff
    style Docs fill:#667eea,color:#fff
    style Calendar fill:#667eea,color:#fff
    style Meetings fill:#667eea,color:#fff
    style Base fill:#667eea,color:#fff
    style Approval fill:#667eea,color:#fff
    style Wiki fill:#667eea,color:#fff
    style Bot fill:#667eea,color:#fff
    style hacomono fill:#6366f1,color:#fff
    style LINE2 fill:#00c300,color:#fff
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

```mermaid
flowchart TB
    subgraph Lark組織構造["🟦 FIT PLACE24 Lark組織構造"]
        subgraph HQ["📁 本部"]
            HQ1["📢 全社連絡<br/>読取専用"]
            HQ2["💬 経営会議"]
            HQ3["📊 KPIダッシュボード共有"]
        end

        subgraph FC["📁 FCオーナー"]
            FC1["📢 オーナー向け連絡"]
            FC2["📋 開業準備チャンネル<br/>└ スレッド: オーナーA, B..."]
            FC3["🔧 運営相談チャンネル<br/>└ スレッド: 案件ごと"]
            FC4["📚 オーナーWiki<br/>FAQ・マニュアル"]
        end

        subgraph Store["📁 店舗運営"]
            S1["📢 店舗向け連絡"]
            S2["🛠️ 設備トラブル報告<br/>└ Bot自動振り分け"]
            S3["📊 店舗別グループ"]
        end

        subgraph Partner["📁 外部パートナー"]
            P1["🏗️ 工事業者連絡"]
            P2["📦 備品発注"]
        end
    end

    style Lark組織構造 fill:#e3f2fd,stroke:#1976d2
    style HQ fill:#bbdefb,stroke:#1976d2
    style FC fill:#c8e6c9,stroke:#388e3c
    style Store fill:#fff3e0,stroke:#f57c00
    style Partner fill:#f3e5f5,stroke:#7b1fa2
```

**メリット**：
- ✅ **スレッド機能**で会話が整理される
- ✅ **検索機能**で過去の情報をすぐ発見
- ✅ **ファイル管理**でドキュメントを一元管理
- ✅ **権限設定**で情報アクセスを制御
- ✅ **Bot連携**で自動振り分け・通知

### 3.2 課題②解決：問い合わせ対応の自動化

```mermaid
flowchart TB
    Start["👤 オーナー/店舗<br/>問い合わせ発生"]

    Bot["🤖 Lark問い合わせBot<br/>24時間自動受付"]

    Menu{"何についての<br/>問い合わせ？"}

    Cat1["1️⃣ 開業準備"]
    Cat2["2️⃣ 運営相談"]
    Cat3["3️⃣ 設備トラブル"]
    Cat4["4️⃣ その他"]

    FAQ{"📚 FAQ<br/>自動回答"}

    Solved["✅ 即時解決<br/>30%はここで完了"]

    Approval["✅ Lark Approval<br/>担当者自動アサイン"]

    Base["📊 Lark Base<br/>対応履歴を自動記録"]

    Start --> Bot --> Menu
    Menu --> Cat1 & Cat2 & Cat3 & Cat4
    Cat1 & Cat2 & Cat3 & Cat4 --> FAQ
    FAQ -->|解決| Solved
    FAQ -->|未解決| Approval --> Base

    style Bot fill:#4285f4,color:#fff
    style FAQ fill:#34a853,color:#fff
    style Solved fill:#00c853,color:#fff
    style Approval fill:#fbbc04,color:#000
    style Base fill:#ea4335,color:#fff
```

**期待効果**：
| 効果 | 詳細 |
|------|------|
| FAQ自動回答 | 30%の問い合わせを即時解決 |
| 自動アサイン | 属人化を解消 |
| 対応履歴蓄積 | ナレッジ化 |
| 対応時間計測 | SLA管理可能 |

### 3.3 課題③解決：Lark Baseによるデータ可視化

```mermaid
flowchart LR
    subgraph hacomono["🏋️ hacomono API"]
        H1["👥 会員データ"]
        H2["💰 売上データ"]
        H3["📅 予約データ"]
    end

    subgraph Sync["🔄 自動同期<br/>毎日"]
        API["API連携"]
    end

    subgraph LarkBase["📊 Lark Base ダッシュボード"]
        B1["📈 全店舗サマリー"]
        B2["🏪 店舗別比較"]
        B3["🚨 アラート通知"]
        B4["📅 開業予定管理"]
    end

    hacomono --> API --> LarkBase

    style hacomono fill:#6366f1,color:#fff
    style Sync fill:#ffa500,color:#fff
    style LarkBase fill:#4285f4,color:#fff
```

#### 経営ダッシュボードイメージ

```mermaid
block-beta
    columns 3

    block:header:3
        title["📊 FIT PLACE24 経営ダッシュボード"]
    end

    block:summary:3
        sum["📈 全店舗サマリー | 総会員: 45,230人 (+2.3%) | 総売上: ¥148.5M (+5.1%)"]
    end

    block:stores:3
        store1["🟢 渋谷店<br/>会員1,250 | 売上¥4.1M"]
        store2["🟡 新宿店<br/>会員980 | 売上¥3.2M"]
        store3["🔴 池袋店<br/>会員650 | 売上¥2.1M"]
    end

    block:alerts:3
        alert["🚨 アラート: 池袋店 退会率超過 | 横浜店 売上-15%"]
    end

    style header fill:#1976d2,color:#fff
    style summary fill:#e3f2fd
    style store1 fill:#c8e6c9
    style store2 fill:#fff3e0
    style store3 fill:#ffcdd2
    style alerts fill:#ffebee
```

### 3.4 店舗拡大対応：開業オペレーションの標準化

```mermaid
gantt
    title 新店舗開業プロジェクト（90日）
    dateFormat  X
    axisFormat %s日前

    section Phase1 契約・準備
    FC契約締結        :done, p1a, 90, 80
    物件契約          :done, p1b, 85, 75
    内装設計確定      :done, p1c, 80, 70
    機器発注          :done, p1d, 75, 65

    section Phase2 工事
    内装工事          :active, p2a, 60, 40
    電気工事          :active, p2b, 55, 40
    空調工事          :active, p2c, 50, 35
    機器搬入          :p2d, 35, 30

    section Phase3 開業準備
    スタッフ採用      :p3a, 30, 15
    システム設定      :p3b, 20, 10
    プレオープン      :p3c, 7, 3
    グランドオープン  :milestone, p3d, 0, 0
```

**自動化ポイント**：
- ✅ タスク完了 → 次担当者に自動通知
- ✅ 期限超過 → エスカレーション
- ✅ 進捗 → 本部ダッシュボードに自動反映

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
pie title 月間削減時間（130時間）
    "LINE管理工数" : 40
    "問い合わせ対応" : 60
    "ツール切替・検索" : 20
    "会議準備" : 10
```

| 効果項目 | 削減時間/月 | 金額換算（時給¥3,000） |
|----------|------------|----------------------|
| LINE管理工数削減 | 40時間 | ¥120,000 |
| 問い合わせ対応効率化 | 60時間 | ¥180,000 |
| ツール切替・検索時間 | 20時間 | ¥60,000 |
| 会議準備時間 | 10時間 | ¥30,000 |
| **合計** | **130時間** | **¥390,000/月** |

### 🎯 年間削減効果: 約470万円相当

### 4.3 定性的効果

- **意思決定スピード向上**: データがリアルタイムで見える
- **店舗拡大の加速**: 開業オペレーションが標準化
- **属人化解消**: ナレッジが組織に蓄積
- **従業員満足度向上**: ツールのストレス軽減

---

## 5. 導入スケジュール

### 全体スケジュール（3ヶ月）

```mermaid
gantt
    title Lark統合プロジェクト スケジュール
    dateFormat  YYYY-MM-DD

    section Phase 1: 設計・準備
    現状詳細ヒアリング      :p1a, 2025-01-06, 1w
    Lark組織構造設計        :p1b, 2025-01-06, 2w
    Base/Approval設計       :p1c, 2025-01-13, 2w
    Bot開発                 :p1d, 2025-01-20, 2w

    section Phase 2: 移行・展開
    本部先行展開            :p2a, 2025-02-03, 1w
    Google/Notion移行       :p2b, 2025-02-03, 2w
    LINE業務移行            :p2c, 2025-02-10, 2w
    オーナー・店舗展開      :p2d, 2025-02-17, 2w

    section Phase 3: 定着・最適化
    全店舗展開完了          :p3a, 2025-03-03, 1w
    旧ツール停止            :p3b, 2025-03-10, 1w
    効果測定・改善          :p3c, 2025-03-10, 2w
    運用定着                :p3d, 2025-03-17, 2w
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
mindmap
  root((成功の<br/>4つの鍵))
    経営層コミット
      公式ツール宣言
      自ら率先利用
      会議でBase活用
    段階的移行
      並行期間設置
      成功事例先行
      抵抗者フォロー
    チャンピオン育成
      部門推進担当
      社内サポート
      好事例共有
    継続的改善
      月次レビュー
      フィードバック
      新機能活用
```

---

## 7. なぜ今Larkなのか

### 7.1 店舗拡大フェーズに最適

```mermaid
graph LR
    A["🏪 現在<br/>170店舗"] --> B["🏪🏪 目標<br/>300店舗"] --> C["🏪🏪🏪 将来<br/>500店舗+"]

    subgraph 課題["店舗増加に伴う課題"]
        D["📈 情報管理の複雑化"]
        E["👤 属人対応の限界"]
        F["📊 データ判断の必要性"]
    end

    B --> D & E & F

    G["🟦 Lark基盤整備"] --> H["✅ スケーラブルな成長"]

    D & E & F --> G

    style A fill:#ffeb3b,color:#000
    style B fill:#ff9800,color:#fff
    style C fill:#f44336,color:#fff
    style G fill:#4285f4,color:#fff
    style H fill:#4caf50,color:#fff
```

### 7.2 Larkの強み（フランチャイズ運営向け）

| 機能 | フランチャイズ運営でのメリット |
|------|-------------------------------|
| **組織構造** | 本部→オーナー→店舗の階層管理 |
| **Base** | 全店舗KPIの一元管理・可視化 |
| **Approval** | 承認フローの標準化・自動化 |
| **Bot** | 定型問い合わせの自動対応 |
| **Wiki** | マニュアル・FAQの一元管理 |
| **外部ユーザー招待** | オーナー・業者を柔軟に招待 |

### 7.3 競合ツールとの比較（フランチャイズ観点）

| 要件 | Lark | Slack+他 | Teams |
|------|:----:|:--------:|:-----:|
| オールインワン | ⭕ | ❌ | 🔺 |
| 外部ユーザー管理 | ⭕ | 🔺 | 🔺 |
| ノーコードDB | ⭕ | ❌ | ❌ |
| ワークフロー | ⭕ | 🔺 | 🔺 |
| コスト | ◎ | ❌ | 🔺 |
| 導入しやすさ | ⭕ | 🔺 | ❌ |

---

## 8. 次のステップ

### 即時アクション

```mermaid
flowchart LR
    A["1️⃣ 詳細ヒアリング"] --> B["2️⃣ PoC実施<br/>2-4週間"] --> C["3️⃣ 見積・契約"]

    A1["業務フロー確認"]
    A2["優先課題特定"]
    A3["関係者インタビュー"]

    B1["本部1チーム先行"]
    B2["効果検証"]
    B3["課題洗い出し"]

    C1["Lark Pro/Enterprise見積"]
    C2["導入支援検討"]
    C3["契約条件確認"]

    A --> A1 & A2 & A3
    B --> B1 & B2 & B3
    C --> C1 & C2 & C3

    style A fill:#4285f4,color:#fff
    style B fill:#34a853,color:#fff
    style C fill:#fbbc04,color:#000
```

### お問い合わせ

本提案についてのご質問・ご相談は下記までお気軽にご連絡ください。

| 項目 | 内容 |
|------|------|
| 会社名 | [提案会社名] |
| 担当者 | [担当者名] |
| Email | [email] |
| Tel | [電話番号] |

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
flowchart TB
    subgraph hacomono["🏋️ hacomono API"]
        H1["👥 会員データ<br/>店舗別会員数、入退会数"]
        H2["💰 売上データ<br/>店舗別売上、客単価"]
        H3["📅 予約データ<br/>予約件数、利用率"]
    end

    API["🔄 API連携<br/>日次自動同期"]

    subgraph LarkBase["📊 Lark Base"]
        L1["📋 日次集計テーブル"]
        L2["📈 店舗比較ダッシュボード"]
        L3["🚨 アラート条件設定"]
    end

    Notify["💬 Lark通知<br/>異常値検知時"]

    H1 & H2 & H3 --> API --> L1 & L2 & L3
    L3 --> Notify

    style hacomono fill:#6366f1,color:#fff
    style API fill:#ff9800,color:#fff
    style LarkBase fill:#4285f4,color:#fff
    style Notify fill:#4caf50,color:#fff
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
