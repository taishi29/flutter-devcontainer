# Flutter DevContainer 環境構築テンプレート

Flutterの構築環境が、WindowsとMacで異なると動かないみたいなので、Dockerコンテナ上で環境構築をし、VSCodeの拡張機能である、Dev Containerを用いてコンテナ内のファイルをVsCodeで編集できるようにする。

## 📚 参考記事

以下の記事を参考にしました！！

📄 [Flutter開発環境をDockerで構築し、Androidアプリを実行する方法 (Qiita)](https://qiita.com/ozuaq/items/12bca991cbad9e18302e)

執筆者: [@ozuaq](https://qiita.com/ozuaq)

## 📁 プロジェクト構成

```
.
├── .devcontainer/
│   ├── Dockerfile
│   ├── devcontainer.json
│   └── docker-compose.yml
├── flutter_app/ （flutter createで生成）
└── README.md
```

## 🛠 使い方

### 前提

- Docker Desktopをダウンロード
- VSCode に Dev Containers 拡張機能ダウンロード
- Android Studio（エミュレータ用）。※ Dockerコンテナ内でGUI操作できないので、ホストOSで立ち上げて、Dockerコンテナ内から接続して、表示させる。

### セットアップ手順

1. Android Studio でエミュレータを作成しておく
2. VSCode で本プロジェクトを開く
3. コマンドパレット `Ctrl + Shift + P` →\
   `Dev Containers: Reopen in Container` を実行

```bash
echo 'org.gradle.unsafe.watch-fs=false' >> android/gradle.properties
```

6. エミュレータとの接続（ホスト側でADBポートを開放しておく）

```bash
adb connect host.docker.internal:5555
```

7. アプリを起動

```bash
flutter run
```

---

## 💡 Tips

- `r`: Hot Reload
- `R`: Hot Restart
- `q`: アプリ終了
- `.gitignore` に `build/`, `.dart_tool/` などを追加推奨

