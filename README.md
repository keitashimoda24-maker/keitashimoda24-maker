# Keita Shimoda

> Non-engineer area manager running **10 convenience stores in Japan**, building daily operational automation with **Claude Code** — currently maintaining 30+ systems.
>
> Exploring **Forward Deployed Engineer (FDE)** opportunities — remote or contract.

[English](#english) | [日本語](#日本語)

---

## English

### What I do (day job)

Area manager for 10 Lawson/FamilyMart-style convenience stores in Japan. Day-to-day involves staffing 25-30 employees, monthly shift design, payroll distribution, expense ops, inventory forecasting, attendance auditing, and a long tail of "small but mandatory" admin work.

### What I actually build (using Claude Code)

| Category | Examples |
|---|---|
| **Operational automation** | 9-store shift generator (Claude Sonnet + OR-Tools CP-SAT), 25-staff payroll PDF distributor, attendance checker, expense manager |
| **Information pipelines** | 17-source AI news collector (Cloud Run / Scheduler / Firestore, 30-min interval, Haiku-scored), morning briefing, OCR pipelines |
| **macOS productivity** | 7 menu-bar indicators (Claude usage, monthly tasks, USB tether status, clipboard image preview, etc.), 5 Dock launchers, custom Claude Code hooks |
| **LINE bots** | 3-bot architecture (secretary / Claude Code bridge / business reports) — Cloud Run + LINE Messaging API |
| **Constraint solving** | OR-Tools CP-SAT shift optimizer with 4 selectable generation modes (prompt-first / balanced / veteran-first / pattern-strong) |

### Scale (representative numbers)

- **10 stores / 25-30 staff** under direct management
- **~140 automated jobs/month** (payroll x25, attendance x9 stores, expense x6 services, shift x9 stores)
- **Estimated time savings: 40-60 hours/month** (~500-700 hours/year)
- **30+ automation systems** built and maintained personally

### Open Source

| Repo | Description |
|---|---|
| [claude-code-smart-hooks](https://github.com/keitashimoda24-maker/claude-code-smart-hooks) | Conditional ultrathink injection for Claude Code — forces deep-reasoning structure at the hook level so output quality stops drifting between sessions |
| [devils-advocate](https://github.com/keitashimoda24-maker/devils-advocate) | A Claude Code agent that runs as the final adversarial gate against groupthink in multi-agent pipelines (in review on the official marketplace) |
| [slash-commands-jp](https://github.com/keitashimoda24-maker/slash-commands-jp) | Plugin that renders the latest Claude Code slash-command catalog in Japanese with operational usage examples (in review on the official marketplace) |
| [mac-pixel-bridge](https://github.com/keitashimoda24-maker/mac-pixel-bridge) | ADB toolkit with tiered USB / LAN / gateway / mDNS fallback for Mac &lt;-&gt; Android clipboard and screenshot bridging |

### Tech surface

- **Languages**: Python, GAS (V8), AppleScript, Bash, Lua, HTML/JS, CSS
- **Cloud (GCP)**: Cloud Run, Cloud Scheduler, Firestore, GCS, Vercel, Cloud Functions
- **APIs**: Anthropic, OpenAI, Gemini, LINE Messaging, Google Drive / Gmail / Calendar
- **OS integration**: launchd, Hammerspoon, py2app, rumps, ADB, TCC permissions
- **AI orchestration**: multi-model routing (Sonnet for depth, Haiku for triage, Gemini for vision)
- **Optimization**: OR-Tools CP-SAT (shift constraint solving)
- **Security**: macOS Keychain, GCP Secret Manager, Bearer token + jti + tokenVersion, HMAC compare_digest, Firestore-persisted rate limiting, magic-byte upload validation

### War stories (incidents I shipped fixes for)

- **Cross-store shift mass-overwrite (2026-05-01)**: a race condition in client-side localStorage->Firestore bulk sync silently corrupted 6 production shift cells. Root caused, hot-patched, and replaced the bulk sync with explicit save-on-action.
- **Cross-tenant data bleed (2026-04-20)**: AI shift generation could write into the *previously selected* store if the user switched stores mid-`await`. Added active-store re-check immediately after every async boundary and early-return on mismatch.
- **Silent backup failure (3 weeks)**: Firestore daily backup had been failing since 2026-04-08 due to a `(default)` vs named-database mismatch *and* a fixed `outputUriPrefix` causing path collisions. Migrated to Cloud Run-hosted backup endpoint with date-keyed paths.
- **Vercel / Cloud Run deployment confusion**: spent a day debugging "the fix isn't taking effect" because I was deploying the API to Vercel while the frontend was hitting Cloud Run. Documented the topology and added pre-deploy guards.

### Why FDE

Most of the above started from a domain problem, not a tech problem. FDE roles reward exactly that loop — sit next to a customer's pain, design with AI tooling, ship, measure. That's already what I do; the customer just happens to be me right now.

### Contact

- Email: keitashimoda24@gmail.com
- GitHub: [@keitashimoda24-maker](https://github.com/keitashimoda24-maker)

---

## 日本語

### 本業

ファミリーマート系列のコンビニ10店舗を統括するエリアマネージャー。スタッフ約25-30名、月次シフト作成、給与明細配布、経費処理、発注予測、勤怠監査などのオペレーションを担当。

### 作っているもの（Claude Code 活用）

| カテゴリ | 例 |
|---|---|
| **業務自動化** | 9店舗対応シフト生成（Claude Sonnet + OR-Tools CP-SAT）、25名分給与明細PDF配布、勤怠チェッカー、経費管理 |
| **情報収集パイプライン** | 17ソースAI最前線情報収集（Cloud Run / Scheduler / Firestore・30分毎・Haikuスコア）、朝ブリーフィング、OCRパイプライン |
| **macOS生産性** | メニューバー常駐7件（Claude使用量・今月タスク・USBテザリング状態・クリップボード画像プレビュー等）、Dockランチャー5件、Claude Codeカスタムhook |
| **LINE Bot** | 3 Bot構成（秘書 / Claude Code連携 / 業務レポート）— Cloud Run + LINE Messaging API |
| **制約最適化** | OR-Tools CP-SAT によるシフト最適化エンジン、4モード切替可能 |

### 規模（代表的な数値）

- 直接管理: **10店舗 / スタッフ25-30名**
- 月次自動処理件数: **約140件**（給与25 + 勤怠9店舗 + 経費6 + シフト9 等）
- 削減労働時間（推定）: **月40-60時間**（年間500-700時間相当）
- 構築・運用中の自動化システム: **30件以上**

### オープンソース

上記の英語表参照（4リポジトリ）。

### 技術カバレッジ

- **言語**: Python / GAS (V8) / AppleScript / Bash / Lua / HTML/JS / CSS
- **クラウド (GCP)**: Cloud Run / Scheduler / Firestore / GCS / Vercel / Cloud Functions
- **API**: Anthropic / OpenAI / Gemini / LINE Messaging / Google Drive / Gmail / Calendar
- **OS統合**: launchd / Hammerspoon / py2app / rumps / ADB / TCC権限管理
- **AI使い分け**: Sonnet=深掘り / Haiku=要約 / Gemini=画像
- **最適化**: OR-Tools CP-SAT（シフト制約最適化）
- **セキュリティ**: macOS Keychain / Secret Manager / Bearer token + jti / HMAC compare_digest / Firestore永続化型 rate limit / マジックバイト検証

### なぜ FDE か

これら全ては「技術問題」ではなく「業務の困りごと」から始まったもの。FDE はまさにそのループ（顧客の痛みの隣に座る → AI ツールで設計 → 出荷 → 計測）が報酬源。今は顧客が自分なだけで、やっていることは同じです。

### 連絡先

- Email: keitashimoda24@gmail.com
- GitHub: [@keitashimoda24-maker](https://github.com/keitashimoda24-maker)
