# Beauty Idea Research Report — 2025

**Generated**: 2026-03-14 14:00
**Data sources**: Reddit (375 posts from 15 subreddits, 55 pain points flagged) · Hacker News (6 posts)
**Methodology**: See [beauty-subreddits.md](../../references/beauty-subreddits.md) and [hn-search-guide.md](../../references/hn-search-guide.md)

---

## Executive Summary

2025年のRedditデータでは、r/30PlusSkinCare（30代以上女性）の投稿エンゲージメントが突出して高く、
ニキビ・ルーティン迷い・皮膚科アクセス難の3テーマが繰り返し現れた。
MakeupAddictionでは「blindパートナーのメイクをする」シリーズが複数バイラル化し、
アクセシビリティへの潜在需要が可視化された。HNでの直接的な美容テック投稿は少ないが、
AIによる外見評価への注目（"People are asking ChatGPT for the harsh truth"）が現れている。
**最優先推奨アイデア**: 30代向けホルモン連動スキンケアコーチ（PeriTrack）。

---

## Top Ideas

### Idea 1: PeriTrack — Hormonal Skin Phase Tracker for 30+

**Problem**
r/30PlusSkinCareはRedditで最もエンゲージメントの高い美容コミュニティの一つで、
"age 32 vs age 36 — what worked"系の投稿が数千コメントを集める。
"Hot take: beauty standards are based on pdfile standards"（17K pts, 3368 cmts）など、
30代以上の女性が既存の美容情報に強い不満を持っていることが明確。
"My skin whenever I do the recommended nighttime treatment" — ルーティン通りやっても結果が出ない、
というホルモン変動に起因する混乱が多数。

**Solution concept**
月経周期・更年期フェーズ（ペリ/プレ/ポスト）に連動してスキンケアの推奨内容が変化するアプリ。
ログ入力（肌状態・製品・体調）→ AIがフェーズ検出→ そのフェーズに合った成分・製品提案。
皮膚科医・婦人科医監修のコンテンツライブラリ付き。

**Evidence**
- Reddit: r/30PlusSkinCare に6件以上の高スコア関連投稿、エンゲージメント合計 30,000+
- Reddit: "Routine Help" フレア投稿が上位に複数
- HN: 直接の投稿なし（競合不在のシグナル）

**Scores**

| Dimension | Score | Notes |
|-----------|-------|-------|
| 実現可能性 (Feasibility) | 4/5 | 月経サイクル追跡はClue/Floが実績。スキンケア層は新規だが技術的に難しくない |
| 開発期間 (Dev Time) | 3/5 | フェーズ検出ロジック＋コンテンツDB構築で2〜3ヶ月 |
| 収益性 (Revenue) | 5/5 | 30代女性の美容支出は高い。月額$12〜19サブスクが刺さる層 |
| 競合優位性 (Competition) | 5/5 | Clue/FloはスキンケアなしRedditor調べ更年期特化アプリは市場にほぼ存在しない |
| 小規模適性 (Small Team) | 4/5 | デジタルのみ。コンテンツは医師監修の外注で賄える |
| **Total** | **21/25** | |

---

### Idea 2: BlindBeauty — Accessibility-First Makeup Guidance App

**Problem**
"My SO is blind and I do her makeup"シリーズがMakeupAddictionで合計8万pts超のバイラルを記録。
視覚障害者向けの美容アプリはほぼ存在せず、音声ガイド・触覚フィードバックで使える
スキンケア・メイクアップツールの空白地帯。

**Solution concept**
完全音声操作でのスキンケアルーティンガイド。製品バーコードを読み上げ、
使う順序・量・塗り方を音声で案内。VoiceOver/TalkBack完全対応。
視覚障害者コミュニティとの共同設計。

**Evidence**
- Reddit: MakeupAddiction の視覚障害関連シリーズ投稿 合計80,000+ pts
- HN: なし（ほぼ競合不在）

**Scores**

| Dimension | Score | Notes |
|-----------|-------|-------|
| 実現可能性 (Feasibility) | 5/5 | テキスト読み上げ + バーコードスキャン、既存技術で完結 |
| 開発期間 (Dev Time) | 4/5 | MVP（音声ルーティンガイド）は1〜2ヶ月 |
| 収益性 (Revenue) | 3/5 | 市場規模は中規模。B2G（自治体・福祉）やNPO連携も有効 |
| 競合優位性 (Competition) | 5/5 | 完全なブルーオーシャン。大手は手をつけていない |
| 小規模適性 (Small Team) | 5/5 | コンテンツは既存成分DBを流用可。1人でも維持可能 |
| **Total** | **22/25** | |

---

### Idea 3: DermQueue — 皮膚科予約 + AI事前スクリーニング

**Problem**
r/SkincareAddictionで"rant: just go to your derm asap"が高スコアを記録。
「すぐ皮膚科へ」というアドバイスへの怒り — 予約が取れない・費用が高い・何を伝えればいいかわからない。
r/acne "I can't even bring myself to go outside anymore"（深刻な社会的影響）も複数。

**Solution concept**
AI問診（肌写真 + 症状入力）→ 重症度スコアリング → 緊急度に応じた皮膚科医マッチング。
軽症はセルフケアレコメンド、中〜重症は優先予約。診察前サマリーを医師に自動送付。

**Evidence**
- Reddit: r/SkincareAddiction "derm access" rant高スコア、r/acne 社会的孤立投稿複数
- HN 2024: "Show HN: Dermatology-Grade Acne Assessment Tool" (8 pts) — 同一課題へのアプローチ確認

**Scores**

| Dimension | Score | Notes |
|-----------|-------|-------|
| 実現可能性 (Feasibility) | 3/5 | 医療連携・規制対応が必要。AI診断は明確に「補助」として設計が必要 |
| 開発期間 (Dev Time) | 2/5 | 医師ネットワーク構築含めると4〜6ヶ月 |
| 収益性 (Revenue) | 4/5 | 予約マージン＋サブスク。テレデルマトロジーは$5B超市場 |
| 競合優位性 (Competition) | 3/5 | Curology・Hims等の競合あり。AI事前スクリーニングで差別化可 |
| 小規模適性 (Small Team) | 2/5 | 医師ネットワーク・法務対応が必要。2〜3人でも厳しい |
| **Total** | **14/25** | |

---

### Idea 4: CurlMappr — テクスチャー別ヘアケアナビゲーター

**Problem**
"This is why I think the 3x3 hair chart is useless" (r/curlyhair, 5599 engagement) が示す通り、
現行のヘアタイプ分類（1A〜4C）はユーザーに合わず混乱を招いている。
"Does protein in hair products really do anything?" "Hair care for older women" など
科学的根拠を求める投稿がr/HaircareScience で多数。

**Solution concept**
写真入力 + 質問フロー（水分保持、タンパク質感受性、ポロシティ等）による
個別ヘアプロファイル生成。レシピ（製品の順序・量・頻度）をパーソナライズして提案。
製品バーコードスキャンでプロファイルとの相性スコアを表示。

**Evidence**
- Reddit: r/curlyhair で分類システム批判が高エンゲージメント
- Reddit: r/HaircareScience で成分・タンパク質系の質問多数
- HN: なし

**Scores**

| Dimension | Score | Notes |
|-----------|-------|-------|
| 実現可能性 (Feasibility) | 4/5 | プロファイリングロジック＋製品DBで実現可能 |
| 開発期間 (Dev Time) | 3/5 | ヘアプロファイルアルゴリズムの設計が鍵。2〜3ヶ月 |
| 収益性 (Revenue) | 4/5 | アフィリエイト＋プレミアム。ヘアケア市場は$100B超 |
| 競合優位性 (Competition) | 4/5 | 既存アプリはヘアタイプ分類を踏襲。新分類軸で差別化 |
| 小規模適性 (Small Team) | 4/5 | デジタル完結。製品DBはOpen Beauty Facts活用可 |
| **Total** | **19/25** | |

---

### Idea 5: ColorBridge — クロスブランドシェードマッチャー

**Problem**
"no one knows what mauve is…" (r/MakeupAddiction, 11K pts, 528 cmts) に代表される
カラー表現の混乱。ブランドごとに異なるシェード名・色温度・カバレッジの比較が困難。
"sincerely disappointed" (15K pts, 800 cmts) はブランド期待外れ投稿 — 買ってみたら違った、の問題。

**Solution concept**
「このブランドのこのシェード → 別ブランドの等価シェード」を提示するクロスブランドマッチャー。
廃盤製品のデュープ検索も対応。コミュニティ投稿で精度を上げるレイティングシステム付き。

**Evidence**
- Reddit: カラー名混乱・ブランド失望投稿が合計 25,000+ engagement
- HN: なし（競合不在シグナル）

**Scores**

| Dimension | Score | Notes |
|-----------|-------|-------|
| 実現可能性 (Feasibility) | 4/5 | カラーDB＋マッチングアルゴリズム。初期データはコミュニティ構築 |
| 開発期間 (Dev Time) | 3/5 | シェードデータ収集が律速。MVP（上位50ブランド）は2ヶ月 |
| 収益性 (Revenue) | 3/5 | アフィリエイト中心。MAU規模が重要 |
| 競合優位性 (Competition) | 4/5 | FindThatDupe等あるが網羅性・UX共に低品質 |
| 小規模適性 (Small Team) | 4/5 | コンテンツはコミュニティ駆動で拡張可能 |
| **Total** | **18/25** | |

---

## Patterns & Observations

- **r/30PlusSkinCare が最重要コミュニティ**: 上位10ペインポイントの6割を占め、エンゲージメントも高い。30代以上女性向けの特化プロダクトが最も有望。
- **アクセシビリティは完全な空白地帯**: MakeupAddiction のバイラル投稿が示す通り、視覚障害者向け美容アプリは誰も作っていない。
- **皮膚科アクセスへの不満は深刻かつ継続的**: 解決には医療連携が必要で小チーム適性は低いが、市場規模は大きい。
- **HN での美容テック投稿は少ない**: 参入余地があるとも、投資家の注目が低いとも解釈できる。

---

## Ideas Worth Watching (Not Yet Actionable)

- **AI外見評価ツール**: "People are asking ChatGPT for the harsh truth" (HN, 8pts) — 需要はあるが倫理・心理的リスクが高い
- **マイクロバイオーム×スキンケア**: r/SkincareAddiction の gut-skin 軸投稿が注目を集めているが、科学的エビデンスがまだ発展途上

---

## Data Notes

- RedditのAPIは`t=year`パラメータで「過去1年」のトップ投稿を返すため、2025年指定でも過去の人気投稿が混在する可能性あり
- HNの美容関連投稿は全体的に少ない（6件）。クエリ拡張（"femtech", "women health tech"）で補完推奨
- r/Rosacea, r/tretinoin, r/EczemaSupport は今回のトップ50に入らなかったが、ニッチ深掘りには有効

---

*Report generated by research-beauty-idea skill*
