GitHub Copilotに伝われば、形式はどのような形でもよいです。
このファイルは指示書の作成指針、使用法です。

# 重要ファイル

* README.md

このリポジトリの使い方

* README-copilot-instructions.md

指示書の書き方

* .github\copilot-instructions.md

GitHub Copilotの全体の指示書
通常は、指示書のの指定をしないと、このファイルが自動で読み込まれます。

* .github\prompts\20250401-000-template.prompt.md

プロンプトファイル(＝実装書)のテンプレートファイルです。

GitHub Copilotと会話してプロンプトファイルの詳細を詰めていきます。

このプロンプトファイルに、複数の指示書を登録して１ファイルにまとめます。


# Webアプリ開発でのGitHub Copilotの設計書、指示書、MCP

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
* 矛盾がないか？
* シンプルに書かれているか？
* 重複がないか？

## 指示書を書くうえでの べからず集

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



# フォルダ・ファイルの種類

* settings.json: VSCode用の設定ファイルです。

* 設計書
* 全体の指示書: プロジェクト全体で共通する指示
* 個別の指示書: 全体の指示書よりも詳細な指示
* プロンプトファイル: タスクの実装詳細情報

* タスクリストファイル: タスク一覧
* メモリーバンク: 開発記録

## 指示書の優先順位

プロンプトファイル＞個別の指示書＞全体の指示書
メモリーバンク

---

# このリポジトリについて

## 設計書のフォルダ

_design/
└── design.md (設計書)

## メモリーバンクのフォルダ

_memory-bank/ (メモリーバンク)
├── _memory-bank-instructions.md (メモリーバンクの指示書)
├── activeContext.md
├── productContext.md
├── progress.md
├── projectbrief.md
├── systemPatterns.md
└── techContext.md

## タスクリストのフォルダ

_task-list/
└── task-list.md (タスクリストファイル)

## GitHub Copilotへの指示書のフォルダ

.github/
├── copilot-instructions.md (全体の指示書)
├── .copilot-commit-message-instructions.md (以下、個別の指示書)
├── .copilot-review-instructions.md
├── .copilot-test-instructions.md
├── .copilot-codeGeneration-instructions.md
└── prompts/ (プロンプトファイル用のフォルダ)
     ├── completes/ (実装が終わったプロンプトファイルを入れるフォルダ)
     │   └── 20250401-007-user-profile.prompt.md
     ├── 20250401-001-code-style-doc.prompt.md (以下、プロンプトファイル)
     ├── 20250401-003-comment-rule-doc.prompt.md
     ├── 20250401-004-component-style-doc.prompt.md
     ├── 20250401-005-sample-doc.prompt.md
     ├── 20250401-002-test-rule-doc.prompt.md
     └── 20250401-006-user-authentication-feat.prompt.md


## MCP (Model Context Protocol) の設定

.vscode/
└── mcp.json



---

# フォルダ、ファイルの解説



## 設計書

`design.md`

Webアプリの設計図です。

## タスクリストファイル

`task-list.md`

設計書からタスク分解をしたタスクを登録したリストです。
実装リストとも言えます。

タスクは1タスク1機能の単位で分解されます。

## 全体の指示書

`copilot-instructions.md`

* GitHub Copilot に最初 `copilot-instructions.md` ファイルを参照してもらいます。
* プロジェクト全体、もしくはプロジェクト単位のルールを記述してあります。
* 概要、構造、アーキテクチャ、制約、技術スタック、ツールを記述してあります。
* プロンプトファイルを実装する時に毎回、プロジェクトのアーキテクチャ、目標、スタイル、制約を理解するために、新しい会話を始めるときは常に `copilot-instructions.md` を参照してください。
* タスクリストが出来たら優先度を付けましょう。設計書の段階でどの機能を優先してつけるかを決めてもいいです。
*

## 個別の指示書

全体の指示書にはかけなかった細かいルールを書きます。

* コード生成の指示書
`.github/.copilot-codeGeneration-instructions.md`

* コミットメッセージの指示書
`.github/.copilot-commit-message-instructions.md`

* レビューの指示書
`.github/.copilot-review-instructions.md`

* テストの指示書
`.github/.copilot-test-instructions.md`

## プロンプトファイル

* 原則として1タスク1機能で、1つのプロンプトファイルを作成します。
* 1タスクの詳細を書いてあるファイルです。
* プロンプトファイルは、具体的な実装情報が書かれているファイルです。
* このプロンプトファイルに従ってGitHub Copilotにコードを生成してもらいます。

※実際にコードを生成する前にGitHub Copilotを話し合って内容をしっかり詰めておきます。

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

例

```
.github/prompts/completes/20250401-007-user-profile.prompt.md

```

* 実装が終わったプロンプトファイルを移動する場所です。

## メモリーバンクの指示書

_memory-bank-instructions.md

メモリ バンクは、GitHub Copilot がセッション間でコンテキストを維持できるようにする構造化されたドキュメント システムです。
これにより、GitHub Copilot はステートレス アシスタントから、時間の経過とともにプロジェクトの詳細を効果的に「記憶」できる永続的な開発パートナーへと変化します。



### 主なメリット

* コンテキストの保存: セッション間でプロジェクト知識を維持する
* 一貫した開発：Clineとの予測可能なやり取りを体験
* 自己文書化プロジェクト：副次効果として価値あるプロジェクト文書を作成する
* あらゆるプロジェクトに拡張可能: あらゆる規模や複雑さのプロジェクトに対応
* テクノロジーに依存しない: あらゆるテクノロジースタックや言語で機能します

### メモリーバンクの仕組み

メモリ バンクは GitHub Copilot 固有の機能ではなく、構造化されたドキュメントを通じて AI コンテキストを管理するための方法論です。
GitHub Copilot に「カスタム指示に従う」ように指示すると、メモリ バンク ファイルが読み取られ、プロジェクトに対する理解が再構築されます。

メモリーバンクは、プロジェクトで作成するマークダウンファイルです。隠しファイルや特別なファイルではなく、リポジトリに保存され、開発者と GitHub Copilot の両方がアクセスできる通常のドキュメントです。

ファイルは階層構造で整理されており、プロジェクトの全体像を構築します。

### コアファイル

1. projectbrief.md

* プロジェクトの基礎
* プロジェクトの概要
* 核となる要件と目標
* 例 "バーコードスキャンによる在庫管理のためのReactウェブアプリの構築"

2. productContext.md

* プロジェクトの存在理由を説明する
* 解決しようとする問題を説明する
* 製品がどのように機能すべきかを説明する
* 例 "在庫システムは複数の倉庫とリアルタイム更新をサポートする必要がある"

3. activeContext.md

* 最も頻繁に更新されるファイル
* 現在の仕事の焦点と最近の変更を含む
* 積極的な意思決定と検討事項の追跡
* 重要なパターンと学習を保存
* 例 例: "現在バーコードスキャナーコンポーネントを実装中、最後のセッションでAPI統合を完了"

4. systemPatterns.md

* システムアーキテクチャの文書化
* 主要な技術的決定を記録する
* 使用されているデザインパターンのリスト
* コンポーネントの関係を説明
* 例 "正規化されたストア構造で状態管理にReduxを使う"

5. techContext.md

* 使用したテクノロジーとフレームワークのリスト
* 開発セットアップの説明
* 技術的な制約を記す
* 依存関係とツール構成を記録する
* 例 "React 18、TypeScript、Firebase、テスト用Jest"

6. progress.md

* 何が機能し、何が作り残されているかを追跡する
* 機能の現状を記録
* 既知の問題と制限のリスト
* プロジェクト決定の変遷を文書化
* 例 "ユーザー認証完了、在庫管理80%完了、レポート未開始"

### 追加コンテキスト

整理する必要がある場合は、追加のファイルを作成します。

* 複雑な機能ドキュメント
* 統合仕様
* APIドキュメント
* テスト戦略
* 展開手順



### メモリーバンクの開始

メモリーバンクの初期化

1. プロジェクトルートに _memory-bankフォルダを作成します。

2. 基本的なプロジェクト概要、設計書を用意しておきます。

3. _memory-bank-instructions.md ファイルを読みます。

4. GitHub Copilotに「メモリバンクを初期化」するよう依頼します。

_memory-bankフォルダを作成し、以下のファイルを作成します。

```
_memory-bank/activeContext.md
_memory-bank/productContext.md
_memory-bank/progress.md
_memory-bank/projectbrief.md
_memory-bank/systemPatterns.md
_memory-bank/techContext.md

```

5. GitHub Copilot のチャットモードで戦略の議論をします。

6. 実装にはGitHub Copilot Agent modeを使用します。


### プロジェクト概要のヒント

* シンプルに始めましょう。詳細でも高レベルでもお好みに合わせてください。
* あなたにとって最も重要なことに焦点を当てる
* クライン氏はギャップを埋め、質問するのを手伝います
* プロジェクトの進展に合わせて更新します。

### コアワークフロー

GitHub Copilot でチャットを行い実装を詰めていきます。

GitHub Copilot Agent modeで特定のタスクの実装と実行をします。


### メモリーバンクへの指示

* メモリーバンクの指示書に従う

これは、GitHub Copilot にメモリーバンク ファイルを読み取り、中断したところから続行するように指示します。 (タスクの開始時にこれを使用します)

* メモリーバンクを初期化する

新しいプロジェクトを開始するときに使用します。

* メモリーバンクを更新する

タスクの完全なドキュメントのレビューと更新をします。

### メモリーバンクの更新のタイミング

* プロジェクトで新しいパターンを発見する
* 大きな変更を実施した後
* 文脈を明確にする必要があると感じたとき

### メモリーバンクの新しいチャットのタイミング

* 新しくプロンプトファイルで実装を開始する時。
* コンテキストが大きくなり、応答が遅くなったり、会話の以前への部分への参照が正確でなくなった時

新しいチャットでGitHub Copilotに「`copilot-instructions.md` (全体の指示書)に従う」ようにお願いします。

### メモリーバンクに関する質問

メモリーバンクはどのくらいの頻度で更新するか？
一区切りついた時
方向転換をした時
改めてやり直したい時
数回の会話ごと
自分が更新したい時




## MCP (Model Context Protocol)

mcp.json

MCPの設定ファイルです。
GitHub Copilot Agent modeで利用します。


---

# 指示書の読み込み指定

プロンプトファイルに
読み込む指示書を指定します。



## 指示書を複数指定する方法

プロンプトファイルの先頭に書いておきます。

プロンプトファイルのテンプレート

20250401-000-template.prompt.md





```
## 指示書と優先順位

以下の指示書を参照し、優先順位に従って作業を進めてください。

### 指示書一覧
1. **全体のルール:** `.github/copilot-instructions.md`
2. **コード生成に関するルール:** `.github/.copilot-codeGeneration-instructions.md`
3. **テストに関するルール:** `.github/.copilot-test-instructions.md`

### 優先順位
指示内容が競合する場合、以下の優先順位に従ってください：
1. `.github/.copilot-codeGeneration-instructions.md`（コード生成に関するルール）
2. `.github/.copilot-test-instructions.md`（テストに関するルール）
3. `.github/copilot-instructions.md`（全体のルール）

```

















```
>ルールを確認します。
どの指示書のファイルを読んでいるのか？そして、読み込んでいるルールを読み上げて下さい。

```




---

# タスク

タスクは、設計書からタスク分解をしてタスクリストファイルに登録します。

原則として、1タスクごとに1機能を実装する単位とします。
これをプロンプトファイルに登録して。
GitHub Copilotと会話をしてプロンプトファイルに実装する詳細な情報を登録します。

---

# .gitignoreファイルの設定

※設計書や指示書をコードのリポジトリに含めたくない場合に追加します。

```.gitignore
# 設計書
/_design

# 指示書
/.github
/_memory-bank
/_task-list

```



---

# 参考

第二版 VSCode の Rules for AI 全体のルール設定 翻訳 GitHub Copilot #githubcopilot - Qiita
https://qiita.com/masakinihirota/items/247bee4bd66ace86e1da

VSCode(ネイティブ)にMCPを設定して、GitHub Copilot Agent modeでSupabaseを操作する。 #githubcopilot - Qiita
https://qiita.com/masakinihirota/items/b5ae692191d197eb5ad7

Clineが記憶喪失にならないようにMemory Bankを使う #LLM - Qiita

https://qiita.com/reoring/items/0c359cc4323bf89965a1

クライン メモリー バンク | クライン

https://docs.cline.bot/improving-your-prompting-skills/cline-memory-bank

GitHub Copilot AgentモードでもMemory Bankを使えるようにしてみる #AI - Qiita

https://qiita.com/getty104/items/68bfdd8e24ab5afbc676

