# 01 Setup - React Native + Expo 初期構築

## 🎯 ゴール

- Expo で空プロジェクトを作成できる
- Expo Go で実機確認できる
- Fast Refresh の動作を理解する

---

## 🛠 実行コマンド

### プロジェクト作成

`npx create-expo-app rn-handson --template blank-typescript`

### 起動

```
cd rn-handson
npx expo start
```

---

## 📱 実機確認（Expo Go）

1. App Store で Expo Go をインストール
2. 同じWi-Fiに接続
3. QRコードを読み取り

---

## 🔁 開発ループの理解

1. コードを書く
2. 保存する
3. Fast Refresh で即反映

→ ビルド不要で反映されるのがExpoの強み

---

## 🌐 Web React との違い

| Web React    | React Native |
| ------------ | ------------ |
| ブラウザ表示 | Expo Go      |
| div          | View         |
| p / span     | Text         |
| CSS          | StyleSheet   |
| localhost    | LAN経由      |

---

## ⚠ 詰まりポイント

- 同一Wi-Fiでないと繋がらない
- VPNが干渉する場合がある
- Firewallで通信ブロックされることがある

---

## 🧠 理解メモ

- Expoは「開発ランタイム」
- React Nativeは「UIレンダリングエンジン」
- Expo Goは「実機テスト用アプリ」

---

## ✅ チェックリスト

- [ ] QRで起動できた
- [ ] 文字変更が即反映された
- [ ] 開発ループを理解した
