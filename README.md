# uv-devcontainer-template

[uv](https://docs.astral.sh/uv/) を使った Python 開発用の [Dev Container](https://containers.dev/) テンプレートリポジトリです。  
VS Code の Dev Containers 拡張機能を使って、すぐに開発を始められる環境を提供します。

## 含まれるツール

| カテゴリ | ツール / バージョン |
| --- | --- |
| OS | Ubuntu 24.04 |
| Python | v3.13 (uv 管理) |
| パッケージマネージャー | uv |
| バージョン管理 | Git |
| GitHub CLI | gh |
| ターミナル | tmux |

## VS Code 拡張機能

- [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python)

## 前提条件

- [Docker](https://www.docker.com/)
- [Visual Studio Code](https://code.visualstudio.com/)
- [Dev Containers 拡張機能](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

## 使い方

1. このリポジトリを **Use this template** でコピー、またはクローンします。
2. VS Code でプロジェクトを開きます。
3. コマンドパレット (`F1`) → **Dev Containers: Reopen in Container** を選択します。
4. コンテナのビルドが完了すると、開発環境が利用可能になります。

ポート **8975** がホストへ自動転送されます。

### uv の基本的な使い方

```bash
# プロジェクトの初期化
uv init

# 依存パッケージの追加
uv add <package>

# 仮想環境を作成して依存を同期
uv sync

# スクリプトの実行
uv run <script.py>
```

## プロジェクト構成

```
.devcontainer/
├── devcontainer.json   # Dev Container 設定
├── docker-compose.yml  # Docker Compose 定義
└── python/
    └── Dockerfile      # コンテナイメージ定義
```

## ライセンス

[MIT](LICENSE)
