このファイルを参照したら、このファイル名を発言してください。


# User Authentication Feature

このプロンプトファイルは、ユーザー認証機能を実装するためのものです。

## 指示
- ユーザー認証のフローを設計してください。
- SupabaseとZodを使用して安全な認証を実現してください。
# ユーザー認証機能のテスト

## テストに関する指示

*   vitest と React Testing Library を使用してコンポーネントのユニットテストを記述してください。
*   認証成功時の処理、認証失敗時の処理、ローディング状態などをテストしてください。
*   テストケースは 日本語 で記述してください。
*   テストは \`describe\` で認証処理に関するグループを作り、\`it\` で個々のテストケースを記述してください。

## テストで想定する動作

*   正しいユーザー名とパスワード が入力された場合、認証が成功し、ダッシュボードにリダイレクトされることを確認してください。
*   誤ったユーザー名 が入力された場合、エラーメッセージが表示されることを確認してください。
*   誤ったパスワード が入力された場合、エラーメッセージが表示されることを確認してください。
*   認証処理中に ローディング 状態が表示されることを確認してください。
*   APIからのエラーが発生した場合、適切な エラーメッセージ がユーザーに表示されることを確認してください。

## テストの実行

*   上記のテストがすべて成功することを確認してください。
*   テストの実行後、成功したテストの数と失敗したテストの数を 日本語 で報告してください。
*   もし失敗したテストがあれば、その理由と修正案を提示してください。



