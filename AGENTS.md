# AGENTS.md

このリポジトリは、React Native を hands-on 形式で学習・検証するための学習用リポジトリです。
小さく試し、記録し、振り返れることを最優先に運用します。

## 目的

- React Native / Expo の基本機能を短い実装単位で学ぶ。
- 実験的なコードは歓迎するが、学習記録として再現性を保つ。
- 学習単位ごとに変更点と学びを残す。

## ディレクトリ方針

- アプリはこのリポジトリ直下で管理する（単一アプリ運用）。
- 学習記録やノートは `docs/` 配下に置く。
- 画像やアイコンは `assets/` に集約する。

## 実行環境

- ローカルの Mac 上で devcontainer を起動して利用する。
- devcontainer 内で Expo を起動し、トンネル経由で端末に接続する。

## 開発・起動

```bash
npm install
npx expo start --tunnel
```

補足:
- Expo の開発ツールから Web/Android/iOS を選択して起動する。
- 依存管理は `package-lock.json` に合わせて npm を使用する。
- `--tunnel` を使うため、初回は `@expo/ngrok` のグローバルインストールを求められる。
  - 例: `The package @expo/ngrok@^4.1.0 is required to use tunnels, would you like to install it globally?`
  - プロンプトが出たら `yes` を選択する。

## `readMe.md` の補足解説

- 新規作成手順は `npx create-expo-app@latest <app-name> --template blank` を基準にする。
- 依存は `npm install` で導入する（pnpm が有効なら pnpm でもよい）。
- 起動は `npx expo start --tunnel` を使用する。
  - devcontainer 環境ではローカルネットワーク直結が難しい場合があるため、トンネル起動を標準にする。
  - `@expo/ngrok` が未導入なら自動でインストール確認が出るので許可する。

## 学習の進め方

- 1テーマ = 1コミットを目安にする。
- 変更内容は `docs/` に短いメモを残す（目的、やったこと、結果、次に試すこと）。
- 実装は小さく、壊したらすぐ戻せる単位に分割する。

## コーディング方針

- 可能な限り TypeScript を使う。
- UI の検証は最小コンポーネントで行い、複雑化する前に分割する。
- 実験用コードは `App.tsx` に集中させ、別コンポーネント化が必要になったら `components/` を作成する。

## テスト方針

- テストは必須ではないが、繰り返し検証する処理は簡単なスモークテストを追加する。
- テスト追加時は `docs/` にテストの意図を記録する。

## コミットメッセージ

- 日本語 + プレフィックス: `feat`, `fix`, `docs`, `refactor`, `test`, `chore`
- 例: `feat: ナビゲーションの基本遷移を追加`

## 禁止事項

- ルート直下で `create-expo-app` を実行しない。
- 学習の履歴を残さずに大規模変更を一度に入れない。

## 参考

- `docs/` 配下の学習メモ
- Expo 公式ドキュメント: https://docs.expo.dev/
