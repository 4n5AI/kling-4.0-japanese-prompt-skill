# Kling 4.0 Japanese Prompt Skill

Kling 4.0（4.0 Flashを含む）の動画プロンプトを、日本語で作成・修正・翻訳・短縮するためのSkillです。参照素材、ショット構成、カメラワーク、音声を整理し、そのまま貼り付けて使えるプロンプトを作成します。特に、**日本語リップシンク用セリフの表記最適化（難読漢字・数字・英語）**、**Kling 4.0固有の書き方（ショット番号と秒数、30秒のワンカット、キーフレーム、万能リファレンスの`@`タグ、動画編集の定型文）**、**シネマトグラフィー（カメラワーク・ショットサイズ・レンズ・構図・ライティング）のリファレンス**、**色・エフェクト・編集・ジャンルのルックまで含む400種以上の映像技法辞典**を収録しています。

[Agent Skills](https://agentskills.io) 標準の `SKILL.md` 形式で書かれており、**OpenAI Codex、Claude Code、Google Antigravity、Gemini CLI、Cursor、GitHub Copilot、OpenCode** など、この形式に対応する生成AIエージェントで共通に使えます。特定のエージェント専用の記述は `SKILL.md` に含めていません。

リポジトリ名は `kling-4.0-japanese-prompt-skill`、**Skill名とインストール先のフォルダー名は `kling-40`** です。Kling AI（Kuaishou）が提供する公式Skillではありません。

## 特徴

### 1. リップシンク・セリフの3つのルール

1. **AIが読みにくい難しい漢字は、ひらがなにする。** 例：叡智 → えいち、躊躇 → ちゅうちょ
2. **数字は漢数字にせず、算用数字にする。** 例：二千年 → 2,000年、百九十二回 → 192回
3. **英語は発音に合うカタカナにする。** 例：AI → エーアイ、Hello → ハロー

これらは、発話時の読み間違い・不自然な発音を防ぐための最適化ルールです。発話部分に適用し、参照タグ（`@Aoi`・`@Image1`等）、URL、ファイル名、話さない画面上の文字は改変しません。

### 2. Kling 4.0 固有の書き方を収録

Kling公式の4.0リリースノートと、3.0／3.0 Omni／O1のユーザーガイド・公式ブログを基に、[`prompt-syntax.md`](references/prompt-syntax.md) にまとめています。

| 項目 | 内容 |
|---|---|
| 世代の違い | 4.0は3〜30秒、4.0 Flashは3〜20秒・720p。旧世代の「5秒か10秒」や他モデル向けの括弧記法を持ち込まない |
| ショット構成 | `Shot 1 (3s):` のショット番号と秒数、Multi-Shot／Custom Multi-Shot、`N秒間のワンカット` と「4秒目で」の時間指定 |
| キーフレーム | 最大10枚のキーフレーム画像と、区間ごとの変化の書き方 |
| 万能リファレンス | 合計15点（画像10・動画5本で合計30秒・被写体7）、`@タグ`の書き方、素材ごとの役割の宣言 |
| 動画編集 | 追加・削除・置き換え・背景・スタイル・天候・次ショット・始終フレームの公式構文 |
| セリフと音声 | `話者（話し方、言語）：「セリフ」` の形式、2chステレオ、9言語以上と方言・アクセント、`Audio:` の書き方 |
| 画面の文字・除外 | 表示する文字の書き方、ネガティブ欄と平文の使い分け |

### 3. シネマトグラフィーのリファレンスを収録

国際標準の映画用語（英語キーワード）＋日本語補足のハイブリッド形式で、撮影の意図を言語化します。必要な項目だけを読み込む構成です。

| リファレンス | 内容 |
|---|---|
| [`camera-movements.md`](references/camera-movements.md) | カメラの動きの原則と、仕組み別の早見表（前後・横移動・パン/チルト・ズーム・回り込み・昇降/空撮・視点/ピント） |
| [`shot-composition.md`](references/shot-composition.md) | ショットサイズ（ELS〜ECU）、アングルと高さ、構図11種 |
| [`lens-and-focus.md`](references/lens-and-focus.md) | 焦点距離と画角の早見表、被写界深度、アナモルフィック・ヴィンテージのルック |
| [`lighting-color.md`](references/lighting-color.md) | 三点照明とライティングパターン、光の質、時間帯、色温度、カラーグレード |
| [`multi-shot-continuity.md`](references/multi-shot-continuity.md) | 複数ショットの連続性、編集文法、絵コンテとの対応 |
| [`techniques/`](references/techniques/index.md) | 映像技法辞典400種以上（カメラの動き・ショット・アングル・構図・照明・レンズ・色・大気・時間・エフェクト・編集・ジャンル・トレンドのルック）。英語名や日本語の呼び名から、説明とプロンプトの記述例を引く |

### 4. 日本語の現場用語を国際標準の英語へ変換

日本の映像現場の用語は、英語圏の用語と意味がずれるものがあります。そのまま英訳すると意図と違う映像になるため、対応表で変換します。

| 日本語 | プロンプトに書く英語 | 誤訳すると |
|---|---|---|
| トラックアップ／T.U | `dolly in` | 英語の `truck` は**横移動**なので、前進しない |
| ズームアップ | `zoom in` | `zoom up` は和製英語（英語では「急上昇」） |
| パンアップ | `tilt up` | 英語の `pan` は**水平方向のみ** |
| `WS`（ウエストショット＝腰上） | `waist-up medium shot` | 英語の `WS` は Wide Shot（引き）で**意味が反転** |

## 対応エージェントと配置先

Skillは `<skillsディレクトリ>/kling-40/SKILL.md` の形で配置します。フォルダー名は必ず `kling-40` にしてください（frontmatterの `name` と一致させる必要があります）。

| エージェント | プロジェクト内 | ユーザー全体 | 明示的な呼び出し | 常時読み込む指示ファイル |
|---|---|---|---|---|
| 共通（Agent Skills 標準の慣例） | `.agents/skills/` | `~/.agents/skills/` | エージェントに従う | — |
| OpenAI Codex | `.agents/skills/`（`.codex/skills/` も可） | `~/.agents/skills/`（従来の `${CODEX_HOME:-~/.codex}/skills/` も可） | `$kling-40` | `AGENTS.md`（全体は `~/.codex/AGENTS.md`） |
| Claude Code | `.claude/skills/` | `~/.claude/skills/` | `/kling-40` | `CLAUDE.md`（全体は `~/.claude/CLAUDE.md`） |
| Google Antigravity ※1 | `.agents/skills/`（旧 `.agent/skills/`） | `~/.gemini/config/skills/` または `~/.gemini/antigravity/skills/` | 自然文で依頼。CLI（agy）は `/kling-40` | `~/.gemini/GEMINI.md`、`.agents/rules/` |
| Gemini CLI | `.gemini/skills/` または `.agents/skills/` | `~/.gemini/skills/` または `~/.agents/skills/` | 自然文で依頼（有効化の確認あり） | `GEMINI.md`（全体は `~/.gemini/GEMINI.md`） |
| Cursor ※2 | `.cursor/skills/` または `.agents/skills/` | `~/.cursor/skills/` または `~/.agents/skills/` | `/kling-40` | `.cursor/rules/`、`AGENTS.md` |
| GitHub Copilot | `.github/skills/` または `.agents/skills/` | `~/.copilot/skills/` または `~/.agents/skills/` | CLIは「`/kling-40` skill を使って…」、VS Codeは `/kling-40` | `.github/copilot-instructions.md`、`AGENTS.md`（CLIの全体は `~/.copilot/copilot-instructions.md`） |
| OpenCode | `.opencode/skills/` または `.agents/skills/` | `~/.config/opencode/skills/` または `~/.agents/skills/` | 自然文で依頼 | `AGENTS.md` |

- 共通ディレクトリ `.agents/skills/` は Codex、Gemini CLI、GitHub Copilot、OpenCode、Cursor、Antigravity（プロジェクト内）などが読みます。**Claude Code は読まない**ので、Claude Code には `.claude/skills/` または `~/.claude/skills/` へ別途配置してください。
- 環境変数 `CODEX_HOME`・`CLAUDE_CONFIG_DIR`・`XDG_CONFIG_HOME` を設定している場合、`install.sh` はそれぞれ Codex・Claude Code・OpenCode の配置先としてその値を優先します。
- ※1 Antigravityのユーザー全体の配置先は、製品（IDE／CLI）とバージョンで異なる報告があります。`~/.gemini/config/skills/`（Google公式サンプルが「グローバル設定ディレクトリ」として案内し、IDE・CLIの両方で読まれると報告されているパス）と `~/.gemini/antigravity/skills/`（Google公式サンプルがIDEのユーザー全体向けとして案内するパス）の両方を候補とし、認識されない場合はお使いのバージョンの公式ドキュメントで確認してください。Antigravity CLI（agy）では `~/.gemini/antigravity-cli/skills/` と表示される報告もあり、必要なら `install.sh --dir ~/.gemini/antigravity-cli/skills` で追加できます。Antigravity CLIが `~/.agents/skills/` を読まないという報告もあるため、Antigravityでは `~/.agents/skills/` に依存しないでください。
- ※2 Cursorの配置先は執筆時点で公式ドキュメントを直接参照できず、検索結果とインストーラーの実装を基にしています（未検証）。認識されない場合は公式ドキュメントで確認してください。

各エージェントの仕様確認日：**2026-09-07**。配置先や呼び出し方は変わることがあります。

## インストール

### A. 生成AIにリポジトリのURLを渡す（最も簡単）

ターミナルで動く生成AIエージェント（Claude Code、OpenAI Codex、Gemini CLI、Cursor、GitHub Copilot、OpenCode など）のチャット欄に、次の文をそのまま貼り付けて送ります。

```text
https://github.com/4n5AI/kling-4.0-japanese-prompt-skill
上記のリポジトリのSkillをインストールしてください。READMEのインストール手順に従い、Skillのフォルダー名は kling-40 にしてください。
```

エージェントがリポジトリを取得し、このREADMEを読んで自分の skills ディレクトリへ配置します。ユーザー全体とプロジェクト内のどちらに入れたいかを決めている場合は、「ユーザー全体（`~/.claude/skills`）に」のように文へ添えてください。

- エージェントがシェルコマンド（`git` など）とインターネットへアクセスできる必要があります。ファイル操作ができないブラウザー版のチャットでは使えないため、B〜D の方法を使ってください。
- 完了後、`<skillsディレクトリ>/kling-40/SKILL.md` が存在することを確認してください。Skillは新しいセッション（会話）を開いてから認識されます。
- エージェントが配置先を迷う場合は、上の「対応エージェントと配置先」の表と B の `install.sh` の使い方を示してください。

### B. スクリプトで配置する（推奨）

このリポジトリをクローンし、その中の `install.sh` を実行します（どのディレクトリからでも実行できます。`--project` は実行時のカレントディレクトリ配下に配置します）。POSIX sh 互換で、`SKILL.md`・`references/`・`agents/` を `kling-40` ディレクトリへコピーします。既に同名のSkillがある配置先は上書きせずスキップし、他の配置先には配置したうえで終了コード1で終了します（`--force` で置き換え）。

```sh
git clone https://github.com/4n5AI/kling-4.0-japanese-prompt-skill.git
cd kling-4.0-japanese-prompt-skill

sh install.sh agents claude           # 使うエージェントを列挙する（共通ディレクトリ＋Claude Code）
sh install.sh all                     # agents + claude + antigravity（重複なしで全エージェントをカバー）
sh install.sh agents --project        # 今いるプロジェクトの .agents/skills へ
sh install.sh --dir ~/.gemini/config/skills   # 任意の skills ディレクトリへ
sh install.sh all --list              # 配置先を表示するだけ
```

| 指定 | 説明 |
|---|---|
| `agents` | 共通ディレクトリ `~/.agents/skills/`（Codex・Gemini CLI・GitHub Copilot・OpenCode・Cursor が読みます） |
| `claude` `antigravity` `gemini` `cursor` `copilot` `opencode` | 各エージェント専用のディレクトリ（上の表の「ユーザー全体」列。`--project` では「プロジェクト内」列） |
| `codex` | Codexの従来パス `${CODEX_HOME:-~/.codex}/skills/`。通常は `agents` を使ってください |
| `all` | `agents` + `claude` + `antigravity`。同じエージェントが複数のディレクトリから同じSkillを読んで重複しないよう、専用ディレクトリには配置しません |
| `--project` | ホームではなく、現在のディレクトリ配下（プロジェクト内のパス）へ配置します |
| `--dir <path>` | 任意の skills ディレクトリへ配置します（`<path>/kling-40` が作られます）。ターゲットと併用できます |
| `--link` | コピーの代わりに、このリポジトリへのシンボリックリンクを置きます。`git pull` で更新できます |
| `--force` | 既存の同名Skillを削除して置き換えます |
| `--list` | 配置先を表示して終了します |

`--link` はシンボリックリンクを読めないエージェント・環境（Cursorでの報告あり、WindowsではDeveloper Modeが必要）では使わず、コピーしてください。

### C. `git clone` で直接配置する

skills ディレクトリの中へ、**フォルダー名を `kling-40` にして**クローンします。`SKILL.md` がリポジトリ直下にあるため、これだけで完了です。

```sh
git clone https://github.com/4n5AI/kling-4.0-japanese-prompt-skill.git ~/.claude/skills/kling-40   # Claude Code
git clone https://github.com/4n5AI/kling-4.0-japanese-prompt-skill.git ~/.agents/skills/kling-40   # Codex・Gemini CLI・Copilot・OpenCode など
git clone https://github.com/4n5AI/kling-4.0-japanese-prompt-skill.git .agents/skills/kling-40     # プロジェクト内で共有
```

### D. 各エージェントのインストール機能を使う

- **Codex**：同梱の `$skill-installer` はリポジトリ内のサブディレクトリを `--path` で指定する前提のため、このリポジトリのURLだけを渡すと「Missing --path for GitHub URL.」で失敗します。`SKILL.md` がリポジトリ直下にあるこのリポジトリでは、「`$skill-installer` で `--repo 4n5AI/kling-4.0-japanese-prompt-skill --path . --name kling-40` を指定してインストールして」のようにパスと名前を明示してください（`${CODEX_HOME:-~/.codex}/skills/kling-40` に入ります）。確実に配置したい場合は B または C を使ってください。
- **Gemini CLI**：`gemini skills install https://github.com/4n5AI/kling-4.0-japanese-prompt-skill`（`--scope user|workspace`）。
- **GitHub Copilot**：`~/.copilot/skills/kling-40`（または `.github/skills/kling-40`）へコピーします（B の `copilot`、または C）。`copilot skill add <ディレクトリ>` はそのディレクトリを skills の格納場所として登録する動作のため、このリポジトリのディレクトリを直接指定しないでください。
- **skills CLI（サードパーティ）**：`npx skills add 4n5AI/kling-4.0-japanese-prompt-skill`（ユーザー全体は `-g`、コピーは `--copy`）。検出したエージェントへまとめて配置しますが、Vercel Labsが提供する非公式ツールで、利用統計を送信します。使用前に内容を確認してください。

Windowsでは、`SKILL.md`・`references/`・`agents/` を含むフォルダーを `kling-40` の名前で同じ配置先（`%USERPROFILE%\.claude\skills\` など）へコピーしてください。

## 使い方

SkillはKling 4.0（4.0 Flashを含む）の依頼で毎回適用するよう設計されており、どのエージェントでも `SKILL.md` の `description` を基に自動的に選択されます。会話の続きや短縮・修正も対象です。明示されたKling 3.0以前や他モデルの依頼には自動適用しません。動画の実生成やアップロード、クレジット消費は行いません。

確実に使いたいときは、エージェントごとの方法で明示します。

- **Codex**：依頼に `$kling-40` を含める
- **Claude Code・Cursor・VS Code（Copilot）・Antigravity CLI**：`/kling-40` に続けて依頼を書く
- **GitHub Copilot CLI**：「`/kling-40` skill を使って…」のように書く
- **Gemini CLI・Antigravity IDE・OpenCode**：「kling-40 Skillを使って」と自然文で書く。Gemini CLIでは有効化の確認ダイアログが表示されたら承認する

依頼の例：

```text
Kling 4.0用に、縦型20秒の商品紹介プロンプトを作って。商品は@Bottle、背景は@Image1。
セリフ「二千年の叡智をAIで未来へ」を自然なリップシンク用に整えて。
```

明示する場合は、Codexでは先頭に `$kling-40 ` を、Claude Code・Cursor・VS Code・Antigravity CLIでは先頭に `/kling-40 ` を付け、同じ行に続けて依頼を書きます。Gemini CLI・Antigravity IDE・OpenCodeでは依頼文に「kling-40 Skillを使って」と添えます。自動選択に任せる場合はそのまま送って構いません。

## 毎回適用させたい場合（任意）

Skillを配置しただけでは、各エージェントの常時読み込み指示は更新されません。毎回の利用を指示として残したい場合は、お使いのエージェントの指示ファイルの既存内容を残して、次を追記してください。

```text
Kling 4.0のプロンプトを作成・修正・翻訳・短縮するときは、会話の続きも含め、毎回kling-40 Skillを適用する。
Skill本文はインストール先の skills/kling-40/SKILL.md にある。
同じ会話で読んだ本文が有効なら再読は不要だが、リップシンク用セリフの3つの表記規則は毎回確認する。
```

| エージェント | ユーザー全体 | プロジェクト内 |
|---|---|---|
| Codex | `~/.codex/AGENTS.md` | `AGENTS.md` |
| Claude Code | `~/.claude/CLAUDE.md` | `CLAUDE.md` |
| Gemini CLI | `~/.gemini/GEMINI.md`（Antigravityと共有されます） | `GEMINI.md` |
| Antigravity | `~/.gemini/GEMINI.md`（Gemini CLIと共有されます） | `.agents/rules/` |
| Cursor | User Rules | `.cursor/rules/`、`AGENTS.md` |
| GitHub Copilot | `~/.copilot/copilot-instructions.md`（Copilot CLIのみ。VS Code等はプロジェクト内ファイルか設定を使用） | `.github/copilot-instructions.md`、`AGENTS.md` |
| OpenCode | `~/.config/opencode/AGENTS.md` | `AGENTS.md` |

## 内容と出典

- [`SKILL.md`](SKILL.md)：プロンプトの作成手順とセリフの表記ルール。frontmatterは Agent Skills 仕様のフィールド（`name`・`description`・`metadata`）のみを使用
- [`references/prompt-syntax.md`](references/prompt-syntax.md)：Kling 4.0固有の記法（世代の違い、ショット番号と秒数、ワンカットとキーフレーム、万能リファレンスと`@`タグ、編集の定型文、セリフと音声、画面の文字、除外指定、公式の語彙）
- [`references/camera-movements.md`](references/camera-movements.md)：カメラワークの原則・早見表と日本語現場用語の対応表
- [`references/shot-composition.md`](references/shot-composition.md)：ショットサイズ、アングルと高さ、構図
- [`references/lens-and-focus.md`](references/lens-and-focus.md)：焦点距離と画角、被写界深度、レンズのルック
- [`references/lighting-color.md`](references/lighting-color.md)：ライティング、時間帯、色温度、カラーグレード
- [`references/multi-shot-continuity.md`](references/multi-shot-continuity.md)：複数ショットの連続性、編集文法、絵コンテとの対応
- [`references/techniques/`](references/techniques/index.md)：映像技法辞典400種以上（13分類）。索引の `index.md` から分類ごとのファイルを引く
- [`references/source-guide.md`](references/source-guide.md)：出典、4.0／4.0 Flashの仕様表、モード別条件、確度の区分
- [`agents/openai.yaml`](agents/openai.yaml)：Codex向けの表示・呼び出し設定（任意。Codex以外のエージェントは無視します）
- [`install.sh`](install.sh)：各エージェントの skills ディレクトリへ配置するスクリプト
- [`LICENSE`](LICENSE)：MIT License

### 出典

Kling公式資料（確認日：**2026-09-29**）。

- [Kling 4.0 さらに進化！ You call the shots（リリースノート）](https://kling.ai/release-note/release-notes/Kling_4)：ページ本文は作成環境から直接取得できなかったため、ユーザーが提供した日本語版のスクリーンショットで仕様表と本文を確認
- [Kling VIDEO 3.0 Model User Guide](https://kling.ai/quickstart/klingai-video-3-model-user-guide)（本文取得済み）
- [Kling VIDEO 3.0 Omni Model User Guide](https://kling.ai/quickstart/klingai-video-3-omni-model-user-guide)（本文取得済み）
- [KLING VIDEO O1 User Guide](https://kling.ai/quickstart/klingai-video-o1-user-guide)（本文取得済み）
- [Kling Element Library User Guide](https://kling.ai/quickstart/klingai-element-library-3-user-guide)（本文取得済み）
- [Kling AI Prompt Guide（公式ブログ）](https://kling.ai/blog/kling-ai-prompt-guide) ほか公式ブログ・旧ガイド（一覧は [出典ガイド](references/source-guide.md)）

シネマトグラフィーの各ガイドと映像技法辞典（`references/techniques/`）の説明と記述例は、一般的な撮影・編集・映像表現の知識を基にこのリポジトリで書き下ろしたものです。Kling 4.0 での効き目は検証していません。

**確度の扱い**：Skillの各記述には確度を付けています。公式資料で本文を確認したもの（3.0以前の資料に由来するものは世代を明記）、複数の第三者情報源が一致するもの、裏付けが弱いものを区別し、公式で未確認の事項をユーザーへ断定して伝えない方針です。シネマトグラフィーの知識は一般的な撮影知識であり、Klingの公式資料には含まれません。「どの語彙がAI動画モデルに効くか」の記述は第三者の検証報告に基づき、その多くは他モデルでの検証です。

公式の仕様表では、Kling 4.0 は3〜30秒・720p／1080p／4K、Kling 4.0 Flash は3〜20秒・720p・8bit SDR です。10bit HDRと最長2分の延長は「近日対応予定／近日公開予定」と表記されています。Kling 4.0 Flash は2026-09-28から一部ユーザー向けに先行提供され、4.0 本体は「まもなく登場」と案内されています。利用可能なモードや設定はサービス・提供時期によって確認が必要です。Web版の説明を他サービスやAPIへそのまま適用せず、変更され得る仕様は現行の公式情報または利用画面で確認します。詳細は出典ガイドを参照してください。

## ライセンス

[MIT License](LICENSE) です。個人・商用を問わず、誰でも無料で自由に使用・複製・改変・再配布できます。条件は、著作権表示とライセンス文を残すことだけです。ライセンスの対象はこのリポジトリに含まれるファイルであり、「出典」に挙げた外部資料（Kling AI ほか）の権利は各提供元に帰属します。

## 既知の注意点

- **Codex**：`~/.codex/skills/` はソース上「後方互換のために残された従来パス」ですが、現在も読み込まれ、`$skill-installer` の配置先でもあります。新規は `~/.agents/skills/` を推奨します。
- **Claude Code**：`.agents/skills/` を読みません。`~/.claude/skills/` または `.claude/skills/` へ配置してください。frontmatterを Agent Skills 仕様の6フィールド内に留めているため、claude.aiへのアップロードやSkills APIでもそのまま使えます。
- **Gemini CLI**：プロジェクト内のSkill（`.gemini/skills/`・`.agents/skills/`）は信頼したディレクトリでのみ読み込まれます。信頼は初回起動時のダイアログ、または `/permissions trust` で設定します（ユーザー全体の `~/.gemini/skills/`・`~/.agents/skills/` は信頼設定の影響を受けません）。また、Skillの有効化のたびに承認を求められます。
- **Antigravity**：ユーザー全体の配置先は※1のとおり複数の候補があります。`install.sh antigravity` は `~/.gemini/config/skills/` と `~/.gemini/antigravity/skills/` の両方へ配置します。
- **同名Skillの重複**：同じエージェントが読む複数のディレクトリ（例：`~/.agents/skills/` と `~/.codex/skills/`、`~/.agents/skills/` と `~/.gemini/skills/`）に同じSkillを置くと、重複して表示されたり、Gemini CLIのように競合の警告が出たりします。`install.sh all` が専用ディレクトリに配置しないのはこのためです。専用ディレクトリのターゲット（`codex`・`gemini`・`cursor`・`copilot`・`opencode`）は、`agents` と併用せず、そのエージェントが共通ディレクトリを読まない場合にだけ使ってください。
