GitHub Copilotに伝われば、形式はどのような形でもよいです。
これは、指示書の作成例です。

# Webアプリ開発で設計書、指示書、MCP

指示書には
矛盾がないか？
シンプルに書かれているか？
重複がないか？



## べからず集 してはいけないこと

* 1回で複数の問題を解決しようとする。
1回のプロンプトファイルで1つの問題を解決することに集中する。
GitHub Copilotが可能な手段で考える必要がある。
まだ一度の指示ですべての問題を解決出来るほどGitHub Copilotはそれほど賢くない。

* 指示書に詰め込む。
指示が長過ぎると指示が反映されなくなります。
Gemini系など受け付ける容量が大きいとこの問題は小さくなります。

* 曖昧な指示をする。
「それっぽい感じで」「なんとなく」といった曖昧な表現は、GitHub Copilotが混乱します。
具体的な要件や期待する動作を明確にします。

* 複雑な指示をする
指示は出来る限りシンプルにしたほうが良いでしょう。

* 小さな違和感の放置
技術的負債が入り込みやすくなります。
徹底的に技術的負債と向き合います。

* 技術的負債を後回しにする。
技術的負債を後回しにすればするほど大きく、修正困難になっていきます。
技術的負債は小さいうちにどんどん片付けておきましょう。

* 余計な情報を与える。
GitHub Copilotは書かれてある指示通りに最後まで突き進もうとします。
余分な指示やコードはできるだけ排除します。

* GitHub Copilotは何でも出来るので何でも命令する。
GitHub Copilotはあくまでコーディングエージェント、アシストツールであり、完全な自動化ツールではありません。
複雑なロジックや高度な設計判断は、分解して問題を小さくするか、人間の手で行う必要があります。

* 自動生成だからテストを書かなくていい。
テストコードは重要です。
GitHub Copilotも気づかずに他の機能に関与したコードを書き換える可能性があります。
テストはレグレッションテスト(退行テスト)も兼ねています。
GitHub Copilotが生成したコードに対して、適切なテストコードを作成し動作確認を行います。
テストコードは、コードの品質を保証します。

* 盲目的にGitHub Copilotを信用する。
GitHub Copilotを信用してはいけません。
生成されたコードは、あくまで提案でしかありません。

* 失敗してもコードを残す。
失敗したコードは破棄しましょう。
サンクコストです、料金を払って提案されたコードといえどもプロジェクトに沿わないコードを残していけば、たちまち雪だるま式に負債が溜まっていきます。


## フォルダ・ファイルの種類

設計書
全体の指示書: プロジェクト全体で共通する指示
個別の指示書: 全体の指示書ではかけなかった個別の指示
プロンプトファイル: タスクの実装詳細情報

タスクリストファイル: タスク一覧
メモリーファイル: 実行履歴

* settings.json

VSCode用の設定ファイルです。
VSCodeの **設定** で呼び出して登録します。
自然言語で登録できます。
ファイルで登録できます。

開発者のための指示を書きます。

* 設計書のフォルダ

design/

design/design.md (設計書)

Webアプリの設計を書きます。

* GitHub Copilotへの 指示書・プロンプトファイル

プロジェクトのための指示を書きます。

.github/
├── copilot-instructions.md (全体の指示書)
├── memory.md (メモリーファイル)
├── .copilot-commit-message-instructions.md (以下、個別の指示書)
├── .copilot-review-instructions.md
├── .copilot-test-instructions.md
├── .copilot-codeGeneration-instructions.md
└── prompts/ (プロンプトファイル用のフォルダ)
     ├── task-list.prompt.md (タスクリストファイル)
     ├── completes/ (実装が終わったプロンプトファイルを入れるフォルダ)
     ├── 20250401-001-code-style-doc.prompt.md (以下、プロンプトファイル)
     ├── 20250401-003-comment-rule-doc.prompt.md
     ├── 20250401-004-component-style-doc.prompt.md
     ├── 20250401-005-sample-doc.prompt.md
     ├── 20250401-002-test-rule-doc.prompt.md
     └── 20250401-006-user-authentication-feat.prompt.md

* MCP (VSCode Insider)

.vscode
└── mcp.json



## 全体の指示書

* GitHub Copilot に最初 `copilot-instructions.md` ファイルを参照してもらいます。
* プロジェクト全体、もしくはプロジェクト単位のルールを記述してあります。
* 概要、構造、アーキテクチャ、制約、技術スタック、ツールを記述してあります。
* プロンプトファイルを実装する時に毎回、プロジェクトのアーキテクチャ、目標、スタイル、制約を理解するために、新しい会話を始めるときは常に `copilot-instructions.md` を参照してください。
* タスクリストが出来たら優先度を付けましょう。設計書の段階でどの機能を優先してつけるかを決めてもいいです。

## メモリーファイル

`.github/memory.md`

コード生成や、チャットで決めてきた仕様を記録するファイルです。
メモリーファイルを利用することで、途中から再開することが容易くなります。

## 個別の指示書

全体の指示書以外に個別に決めた指示です。
全体の指示書よりも、個別の指示書を優先してもらいます。

* コード生成の指示書
`.github/.copilot-codeGeneration-instructions.md`

* コミットメッセージの指示書
`.github/.copilot-commit-message-instructions.md`

* レビューの指示書
`.github/.copilot-review-instructions.md`

* テストの指示書
`.github/.copilot-test-instructions.md`











## タスク

原則として、1タスク1機能で作ります。

* タスクリストファイル
`.github/prompts/task-list.prompt.md`
設計書をタスクに分解を登録したリストです。


## プロンプトファイル

* 1タスクの詳細を書いてあるファイルです。
* プロンプトファイルは、具体的な実装を書いたファイルです、このプロンプトファイルに従ってGitHub Copilotにコードを生成してもらいます。実際にコードを生成する前にGitHub Copilotを話し合って内容をしっかり詰めておきましょう。
* 原則として1タスク1機能で、1つのプロンプトファイルを作成します。
* プロンプトファイルには実際にコードを生成する情報が書かれています。
* GitHub Copilotはこのプロンプトファイルの指示に従ってコードを生成してください。



### プロンプトファイルのフォーマット
`.github/prompts/[YYYYMMDD]-[タスクid]-[タスク名]-[タスクの種類].prompt.md`

例: 20250401-123-loginFeature-feat.prompt.md

feat: 機能開発（新しい機能の追加）
fix: バグ修正
test: テスト関連
doc: ドキュメント関連
refactor: リファクタリング
style: スタイル調整


プロンプトファイルの例

```
.github/prompts/20250401-001-code-style-doc.prompt.md
.github/prompts/20250401-002-test-rule-doc.prompt.md
.github/prompts/20250401-003-comment-rule-doc.prompt.md
.github/prompts/20250401-004-component-style-doc.prompt.md
.github/prompts/20250401-005-sample-doc.prompt.md
.github/prompts/20250401-006-user-authentication-feat.prompt.md

```

## completesフォルダ

`.github/prompts/completes/`

```
.github/prompts/completes/20250401-007-user-profile.prompt.md

```

* 実装が終わったプロンプトファイルを入れる場所です。





## MCP設定ファイル

.vscode
└── mcp.json




# GitHub Copilot への指示書

## 指示書より前の準備

* 設計書を作成しておきます。
* 設計書は開発しながら一緒に成長させます。
* 設計書から、まず人間がプロジェクトの大枠、ドメインの範囲を設定します。
* 例えば、テンプレート、スターター等を用意します。
* その枠内を一つ一つ確実に積んでいくというイメージで作ります。
* 環境変数を開発者の手で設定しておきます。
* メモリーファイルをリセットしておきます。

## 指示書の書き方

* コードを作成する前に、開発者と GitHub Copilot で十分に話し合ってください。
* プロジェクト開始時に、スコープとタスクを明確に定義してください。
* コンテキストは詳細であればあるほど、より適切なコード生成に繋がります。
* 具体的なサンプルコードは、GitHub Copilot の理解を助けます。
* コードとドキュメントは同時に記述することを推奨します。
* 環境変数の実装は、開発者が責任を持って行ってください。

第二版 VSCode の Rules for AI 全体のルール設定 翻訳 GitHub Copilot #githubcopilot - Qiita
https://qiita.com/masakinihirota/items/247bee4bd66ace86e1da

VSCode(ネイティブ)にMCPを設定して、GitHub Copilot Agent modeでSupabaseを操作する。 #githubcopilot - Qiita
https://qiita.com/masakinihirota/items/b5ae692191d197eb5ad7






# 指示書

## VSCodeの設定ファイル内に記入

settings.json

