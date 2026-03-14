# research-beauty-idea スキル

女性向け美容アプリ・Webサービスの**ニッチなアイデアを発掘・評価する**ためのリサーチスキルです。
Reddit の美容コミュニティと Hacker News からユーザーのリアルな痛みを収集し、スコアリングして優先度を提示します。

---

## 使い方

Claude Code で以下のように呼び出すだけです。

```
research-beauty-idea
```

> **このスキルが自動的にトリガーされる場面**
> - 「美容アプリのアイデアを探したい」
> - 「スキンケアサービスの市場ギャップを調べて」
> - 「Reddit/HN から穴場の美容テーマを見つけて」
> - 「ニッチなプロダクトアイデアをリサーチして」（美容・スキンケア・パーソナルケア文脈）

---

## 処理フロー

```
1. 調査年号を確認（日本語で質問）
        ↓
2. データ収集（Reddit + HN を並列実行）
        ↓
3. アイデア合成（5〜10件に絞り込み）
        ↓
4. 5軸スコアリング
        ↓
5. レポート保存
```

### Step 1 — 調査年号の確認

スキル起動時に日本語で年号を確認します。未入力の場合は現在の年を使用します。

### Step 2 — データ収集

| ソース | スクリプト | 収集内容 |
|--------|-----------|---------|
| Reddit | `scripts/fetch_reddit.py` | 美容系サブレディットの高エンゲージメント投稿・フレア「Help/Rant/Question」 |
| Hacker News | `scripts/fetch_hn.py` | 美容テック関連スレッド（10pt以上 or 5コメント以上） |

Reddit は**ユーザーの生の痛み**、HN は**ビルダー・投資家の視点**を補完的に提供します。

### Step 3 — アイデア合成

複数のサブレディットをまたいで繰り返し登場する不満を抽出し、具体的なプロダクトアイデアとして整理します。各アイデアには「問題・解決コンセプト・エビデンス数」が含まれます。

### Step 4 — 5軸スコアリング

各アイデアを以下の5軸で1〜5点評価します（詳細: `references/scoring-rubric.md`）。

| 軸 | 説明 |
|----|------|
| 実現可能性 | 既存技術・APIで構築できるか |
| 開発期間 | ソロ/小チームで MVP を出せる期間 |
| 収益性 | 12〜18か月以内に収益化できるか |
| 競合優位性 | 差別化の余地があるか（Blue Ocean度） |
| 小規模開発適性 | 1〜3人のチームで継続運営できるか |

**合計25点満点で解釈：**

| スコア | 判定 |
|--------|------|
| 22〜25 | 最優先で着手 |
| 18〜21 | プロトタイプ推奨 |
| 13〜17 | 弱点を把握したうえで前進 |
| 8〜12 | 突破口となるインサイトが必要 |
| 5〜7 | 非推奨 |

### Step 5 — レポート保存

レポートは以下のパスに自動保存されます。

```
reports/{調査年号}/{YYYY-MM-DD}/{HH-MM}.md
```

---

## ディレクトリ構成

```
research-beauty-idea-skills/
├── SKILL.md                      # スキル本体（Claude が読む指示ファイル）
├── README.md                     # このファイル
├── memo.txt                      # スキル作成時のメモ
├── scripts/
│   ├── fetch_reddit.py           # Reddit データ収集スクリプト
│   └── fetch_hn.py               # Hacker News データ収集スクリプト
├── references/
│   ├── beauty-subreddits.md      # 調査対象サブレディット一覧
│   ├── hn-search-guide.md        # HN 検索クエリ・読み方ガイド
│   ├── scoring-rubric.md         # 5軸スコアリング詳細定義
│   └── report-template.md        # レポート出力テンプレート
├── reports/                      # 生成されたレポートの保存先
│   └── {year}/{date}/{time}.md
├── evals/                        # スキル評価用
└── workspace/                    # 作業用一時ファイル
```

---

## 調査対象サブレディット（主要）

| カテゴリ | 主なサブレディット |
|---------|-----------------|
| スキンケア | r/SkincareAddiction, r/AsianBeauty, r/30PlusSkinCare, r/acne, r/tretinoin |
| ヘア | r/femalehairadvice, r/curlyhair, r/NaturalHair, r/Hairloss |
| メイク | r/MakeupAddiction, r/drugstorebeauty, r/Indiemakeupandmore |
| ボディ・ウェルネス | r/NailArt, r/fragrance, r/xxfitness |

全リスト: `references/beauty-subreddits.md`

---

## 品質基準

- **Reddit と HN 双方にエビデンスがあるアイデアを優先**（クロスプラットフォームシグナル）
- 資金調達済みスタートアップと重複する場合は競合リスクとして明記
- ユーザー投稿の引用はプライバシー配慮のため言い換えて掲載
- スクリプトが失敗・データ不足の場合はレポート内に注記し、手動調査クエリを提示
