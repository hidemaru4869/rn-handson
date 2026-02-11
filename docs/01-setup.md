# 01 Setup - React Native + Expo 初期構築

## ゴール

- devcontainer から Expo を起動できる
- Expo Go で実機確認できる
- Fast Refresh の仕組みを説明できる

## 手順

前章はないので、まず開発環境の前提を固める。

用語定義:
- devcontainer: ローカル Mac 上で動く開発用コンテナ環境。実行はコンテナ内だが、端末はコンテナ外にある。
- tunnel: コンテナ内サーバへ端末から到達するための中継経路。LAN 経由より安定する。
- Expo Go: 端末に入れる実行アプリ。開発中の JS を受け取って実行する。
- Fast Refresh: 変更したモジュールを差し替え、アプリ全体を再起動せずに反映する機構。

補足:
devcontainer 内の IP（例: 172.x.x.x）は LAN から直接アクセスできない。
そのため Expo CLI は ngrok を使って外部公開 URL を生成する。

1. Expo プロジェクトを作成する

```bash
npx create-expo-app rn-handson --template blank-typescript
```

2. devcontainer 内で起動する

```bash
cd rn-handson
npx expo start --tunnel
```

3. Expo Go で実機起動する

- Expo Go を起動し、表示された QR を読み取る
- 端末でアプリが起動することを確認する

実行フロー:

```mermaid
flowchart LR
  Mac[ローカル Mac] --> Devcontainer[devcontainer]
  Devcontainer -->|expo start --tunnel| ExpoCLI[Expo CLI]
  ExpoCLI --> Metro[Metro bundler]
  Metro --> Tunnel[Tunnel]
  Tunnel --> ExpoGo[Expo Go]
  ExpoGo --> RN[React Native ランタイム]
  RN --> UI[ネイティブ UI]
```

実装例:

`App.tsx` の表示を変えて Fast Refresh を体験する。

```tsx
import { View, Text } from "react-native";

export default function App() {
  return (
    <View style={{ padding: 24 }}>
      <Text>Fast Refresh OK</Text>
    </View>
  );
}
```

## 詰まりポイント

- `--tunnel` 未使用だと端末から到達できない場合がある
- Expo Go が古いと QR を読めても起動に失敗する
- 反映されない場合は Metro の再起動が必要になることがある

## Webとの差分

- Web は `localhost` に直接アクセスできるが、RN は端末に配信する必要がある
- Web の HMR はブラウザ前提だが、RN は Metro と Expo Go の組み合わせで動く

## 振り返り

- devcontainer と端末の間に tunnel が必要な理由を説明できるか
- Fast Refresh が「差分配信」であることを言語化できるか
- 次はプロジェクト構成を理解する
