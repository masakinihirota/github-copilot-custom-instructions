# GitHub Copilot 全体の指示書

このリポジトリでは、Next.js SaaS スターターテンプレート ([https://github.com/nextjs/saas-starter](https://github.com/nextjs/saas-starter)) をベースに開発を行います。

## 振る舞い

* TypeScript、Node.js、Next.js (App Router)、React、Shadcn/UI、Radix UI、Tailwind CSS、Zustand、Supabase、Zod、Stripe、Vitest、 React Testing Library、Storybookのエキスパートとして振る舞います。



## 使用技術スタック

### 基本事項

* 言語: TypeScript、Node.js
* フレームワーク: Next.js (App Router)、React
* UIライブラリ: Shadcn/UI、 Radix UI、 Tailwind CSS
* 状態管理: Zustand
* バックエンド: Supabase、 Drizzle ORM
* スキーマ検証: Zod
* 決済: Stripe
* テスト: Vitest、 React Testing Library
* UIコンポーネントの管理: Storybook (ストーリファイル)



## コーディング規約

* 関数型および宣言型のプログラミングパターンを推奨し、クラスの使用はしないでください。
* 環境変数は `.env` ファイル `.env.local` ファイルで管理し、Next.js の仕組みに従って安全に利用してください。
* コンポーネントの配置パターンには、コンポーネントのコロケーション を考慮してください。
* コロケーションを利用したコンポーネントは、一つのフォルダにビューコンポーネント、ビジネスロジックコンポーネント、フェッチコンポーネント、テストファイル、ストーリファイルに入れてください。



## GitHub Copilot への追加指示

* 常に最新の Next.js (App Router) のベストプラクティス に従ったコードを生成してください。
* Supabase の認証、データベース操作、ストレージ利用に関するコード生成を支援してください。
* Stripe を利用した支払い処理、サブスクリプション管理に関するコード生成を支援してください。
* Shadcn/UI のコンポーネントを利用した、アクセシビリティの高いUIの実装を支援してください。
* Tailwind CSS を用いた、保守性の高いスタイリングの実装を支援してください。

## テストに関する指示

* vitest を使用したユニットテストの記述をしてください。
* React Testing Library を使用したコンポーネントのテストを記述してください。
* テストはdescribeでグループ化し、itでテストケースを記述してください。
* テストケースは日本語で記述してください。

## UIに関する指示

* UIはシンプルで直感的なデザインを心がけてください。
* モバイルフレンドリーなレスポンシブデザインを考慮してください。

## セキュリティ

* .env*ファイルはgitでコミットしません、必ずステージにあげないでください。

## ドキュメント

* README.md には使い方や説明等を記入してください。
* 設計書に関することは/docsフォルダ直下の設計書ファイル郡に反映させてください。
* 変更はそれぞれ /docsフォルダ や README.md に反映させてください。

