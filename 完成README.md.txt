<!-- README.md -->

## Article-Wizard & Manus Orchestrator — README & UI ガイド

### ① Overview
AI 文章生成・プロンプト設計・スケジュール自動化を 1 つの GPT で完結。  
4 モード（article / manus_prompt / o3_prompt / schedule）を選ぶだけで高品質アウトプット。  
日本語 UI＋Self-Critique で常に Manus 10 原則を満たす世界最高水準の GPT。

---

## ② GPT Builder 貼付手順
1. **GPT Builder →「Files > 新規 GPT」** をクリック  
2. 4 ファイルを追加  
   - manifest.json / functions.json / SYSTEM PROMPT / domain_keywords.yaml  
3. **Build → Run** でテスト。`ALL TESTS PASSED` が表示されれば完了！

---

## ③ 画面遷移図
```mermaid
flowchart TD
  A[Home] --> B{Mode Select}
  B -->|article| C[Article Form]
  B -->|manus|  D[Manus Form]
  B -->|o3|     E[o3 Form]
  B -->|schedule| F[RRULE Form]
  C --> G[Markdown Output]
  D --> H[Manus Prompt]
  E --> I[o3 Prompt]
  F --> J[Schedule Msg]
```    

## 📌 Manus 10 原則 & 安全ガイド
以下の 10 項目はすべての出力が必ず満たすべき品質・倫理基準です。

| # | 原則 | 概要 |
|---|------|------|
| 1 | Accuracy | 事実に忠実、誤情報ゼロ |
| 2 | Ethics & Legal | 法令遵守、差別・誹謗表現排除 |
| 3 | User-First Value | 読者の課題解決を最優先 |
| 4 | Clarity & Specificity | あいまい語禁止、具体例必須 |
| 5 | Consistent Tone | 一貫したブランド文体 |
| 6 | Engagement & CTA | 行動提案で読者を動かす |
| 7 | Evidence & Cite | 出典・信頼ソースを明示 |
| 8 | Conciseness | 冗長カット、トークン節約 |
| 9 | SEO Alignment | 自然なキーワード挿入・メタ最適 |
|10 | Continuous Improve | Self-Critique で品質向上 |

### 🚫 禁止語リスト
現在の禁止語: **暴力・差別**  
これらが入った入力または出力は自動でブロックされ、再入力を促すメッセージが返ります。

> **追記方法**: 禁止語を追加する場合は  
> `functions.json` の self_check 内リストと README 双方を更新してください。

---

## ④ RRULE チートシート
```text
FREQ=DAILY                         # 毎日
FREQ=WEEKLY;BYDAY=MO               # 毎週月曜
FREQ=MONTHLY;BYMONTHDAY=1          # 毎月 1 日
FREQ=WEEKLY;INTERVAL=2;BYDAY=FR    # 隔週金曜
FREQ=YEARLY;BYMONTH=12;BYDAY=-1FR  # 年末最終金曜
```               

---                    

## ⑤ コマンド & モード早見表
| コマンド | 説明 | 例 |
|----------|------|----|
| `/help` | モード一覧を表示 | `/help` |
| `mode: article` | 記事生成 | `mode: article↵topic: AI↵length: 600` |
| `mode: manus_prompt` | Manus 用プロンプト | `mode: manus_prompt↵task: SEO audit` |
| `mode: o3_prompt` | o3 用プロンプト | `mode: o3_prompt↵task: summarize` |
| `mode: schedule` | 定期タスク作成 | `mode: schedule↵title: Weekly NL↵rrule: FREQ=WEEKLY;BYDAY=MO` |

## ⑥ FAQ
1. トークン上限エラーが出たら？ → /shorten で自動要約  
2. 画面が真っ白？ → ブラウザ再読込＋キャッシュ削除  
3. Unknown mode エラー？ → /help でモード一覧を確認  
4. RRULE が分からない → 上記チートシート参照  
5. キーワード重みを調整したい → domain_keywords.yaml に追記し再ビルド
