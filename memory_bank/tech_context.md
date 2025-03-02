# Cline 技術コンテキスト

## 使用技術

Clineは、最新のWeb技術とVSCode拡張機能APIを組み合わせて構築されています。以下は、プロジェクトで使用されている主要な技術スタックです。

### コア技術

1. **TypeScript**
   - 静的型付けによる堅牢なコード
   - インターフェースと型定義の広範な使用
   - 最新のECMAScript機能の活用

2. **VSCode拡張API**
   - Webviewインターフェース
   - コマンドとイベントの登録
   - ワークスペースとファイル操作
   - ターミナル統合
   - 状態管理（グローバル状態、ワークスペース状態、シークレット）

3. **React**
   - Webview UIのコンポーネントベース開発
   - コンテキストAPIによる状態管理
   - フック（Hooks）の広範な使用
   - 関数コンポーネントの優先

### 主要ライブラリとフレームワーク

1. **AI統合**
   - Anthropic SDK (`@anthropic-ai/sdk`)
   - OpenAI SDK (`openai`)
   - Google Generative AI (`@google/generative-ai`)
   - AWS Bedrock SDK (`@anthropic-ai/bedrock-sdk`)
   - Vertex AI SDK (`@anthropic-ai/vertex-sdk`, `@google-cloud/vertexai`)
   - Mistral AI SDK (`@mistralai/mistralai`)

2. **ブラウザ自動化**
   - Puppeteer Core (`puppeteer-core`)
   - Puppeteer Chromium Resolver (`puppeteer-chromium-resolver`)

3. **ファイル操作とパターンマッチング**
   - Globby (`globby`)
   - Chokidar (`chokidar`)
   - Ignore (`ignore`)
   - IsBinaryFile (`isbinaryfile`)

4. **ドキュメント処理**
   - PDF Parse (`pdf-parse`)
   - Mammoth (`mammoth`) - DOCXファイル処理
   - Turndown (`turndown`) - HTMLからMarkdownへの変換
   - Cheerio (`cheerio`) - HTMLパース
   - Open Graph Scraper (`open-graph-scraper`)

5. **バージョン管理と差分**
   - Simple Git (`simple-git`)
   - Diff (`diff`)

6. **ユーティリティ**
   - Delay (`delay`)
   - P-Wait-For (`p-wait-for`)
   - Fast Deep Equal (`fast-deep-equal`)
   - Clone Deep (`clone-deep`)
   - Strip ANSI (`strip-ansi`)
   - Serialize Error (`serialize-error`)
   - Zod (`zod`) - スキーマ検証

7. **MCP (Model Context Protocol)**
   - MCP SDK (`@modelcontextprotocol/sdk`)

### ビルドツールと開発環境

1. **ビルドツール**
   - esbuild - 高速なTypeScriptコンパイルとバンドル
   - Vite - Webview UIの開発とビルド

2. **テストフレームワーク**
   - Mocha - テスト実行
   - Chai - アサーション
   - VSCode Test Electron - 拡張機能テスト

3. **コード品質ツール**
   - ESLint - コード品質とスタイルチェック
   - Prettier - コードフォーマット
   - Husky - Gitフックの管理

4. **バージョン管理**
   - Changesets - バージョン管理と変更ログの生成

## 開発セットアップ

### 環境要件

1. **Node.js**
   - バージョン: プロジェクトの`.nvmrc`ファイルで指定（現在は最新のLTS）
   - npm: 最新バージョン推奨

2. **VSCode**
   - バージョン: 1.84.0以上
   - 推奨拡張機能:
     - ESLint
     - Prettier
     - esbuild Problem Matchers

3. **Git**
   - Git LFSのサポート（大きなバイナリファイル用）

### セットアップ手順

1. **リポジトリのクローン**
   ```bash
   git clone https://github.com/cline/cline.git
   ```

2. **VSCodeでプロジェクトを開く**
   ```bash
   code cline
   ```

3. **依存関係のインストール**
   ```bash
   npm run install:all
   ```
   このコマンドは、拡張機能とWebview UIの両方の依存関係をインストールします。

4. **開発モードでの実行**
   - `F5`キーを押す（または`実行`→`デバッグの開始`）
   - 新しいVSCodeウィンドウが拡張機能がロードされた状態で開きます

### プロジェクト構造

```
cline/
├── .vscode/             # VSCode設定
├── assets/              # アイコンやドキュメント用の静的アセット
├── docs/                # プロジェクトドキュメント
├── locales/             # 多言語サポートファイル
├── src/                 # コア拡張機能のソースコード
│   ├── api/             # AI APIプロバイダー統合
│   ├── core/            # コア機能（Clineクラス、状態管理など）
│   ├── exports/         # 公開API定義
│   ├── integrations/    # VSCode統合（ターミナル、エディタなど）
│   ├── services/        # サービス（ブラウザ、MCP、テレメトリなど）
│   ├── shared/          # 共有型と定数
│   ├── test/            # テストファイル
│   ├── utils/           # ユーティリティ関数
│   └── extension.ts     # 拡張機能のエントリポイント
├── webview-ui/          # Webview UIのソースコード
│   ├── src/             # Reactコンポーネントとコンテキスト
│   │   ├── components/  # UIコンポーネント
│   │   ├── context/     # Reactコンテキスト
│   │   └── utils/       # UIユーティリティ
│   ├── public/          # 静的アセット
│   └── index.html       # Webviewのエントリポイント
└── package.json         # プロジェクト設定と依存関係
```

### 開発ワークフロー

1. **機能開発**
   - 新しいブランチを作成
   - コードの変更を実装
   - テストを追加または更新
   - `npm run lint`と`npm run format`でコードスタイルを確認
   - `npm test`でテストを実行

2. **変更セットの作成**
   ```bash
   npm run changeset
   ```
   - 変更の種類を選択（major、minor、patch）
   - 変更の説明を提供

3. **プルリクエストの作成**
   - 変更とchangesetファイルをコミット
   - ブランチをプッシュ
   - GitHubでプルリクエストを作成

4. **レビューと統合**
   - CIチェックが通過することを確認
   - レビューフィードバックに対応
   - メインブランチにマージ

5. **リリース**
   - Version Packagesプルリクエストがマージされると、新しいリリースが自動的に公開されます

## 技術的制約

### VSCode拡張API制約

1. **Webview制限**
   - サンドボックス化されたコンテキストで実行
   - 限られたAPIアクセス
   - 拡張機能との通信はメッセージパッシングのみ

2. **パフォーマンス考慮事項**
   - 大量のデータ転送の最小化
   - メインスレッドのブロッキング操作の回避
   - メモリ使用量の管理

3. **セキュリティ制約**
   - ユーザー承認なしでのファイル変更の禁止
   - 機密情報の安全な保存
   - 外部リソースへの安全なアクセス

### AI API制約

1. **コンテキストウィンドウ制限**
   - モデルごとに異なるトークン制限
   - 長い会話の切り詰めの必要性
   - 重要なコンテキストの保持

2. **レート制限**
   - APIプロバイダーごとの異なるレート制限
   - 再試行と指数バックオフの実装
   - ユーザーへの明確なエラーメッセージ

3. **コスト考慮事項**
   - トークン使用量の追跡
   - 効率的なプロンプト設計
   - ユーザーへのコスト透明性

### ブラウザ自動化制約

1. **環境依存性**
   - Chromeの可用性
   - プラットフォーム固有の問題
   - ヘッドレスモードの制限

2. **UI相互作用の複雑さ**
   - 座標ベースのクリック
   - 動的コンテンツの処理
   - 非決定的なUI要素

## 依存関係

### コア依存関係

```json
"dependencies": {
  "@anthropic-ai/bedrock-sdk": "^0.12.4",
  "@anthropic-ai/sdk": "^0.37.0",
  "@anthropic-ai/vertex-sdk": "^0.6.4",
  "@google-cloud/vertexai": "^1.9.3",
  "@google/generative-ai": "^0.18.0",
  "@mistralai/mistralai": "^1.5.0",
  "@modelcontextprotocol/sdk": "^1.0.1",
  "axios": "^1.7.4",
  "cheerio": "^1.0.0",
  "chokidar": "^4.0.1",
  "clone-deep": "^4.0.1",
  "default-shell": "^2.2.0",
  "delay": "^6.0.0",
  "diff": "^5.2.0",
  "execa": "^9.5.2",
  "fast-deep-equal": "^3.1.3",
  "firebase": "^11.2.0",
  "get-folder-size": "^5.0.0",
  "globby": "^14.0.2",
  "ignore": "^7.0.3",
  "isbinaryfile": "^5.0.2",
  "mammoth": "^1.8.0",
  "monaco-vscode-textmate-theme-converter": "^0.1.7",
  "open-graph-scraper": "^6.9.0",
  "openai": "^4.83.0",
  "os-name": "^6.0.0",
  "p-wait-for": "^5.0.2",
  "pdf-parse": "^1.1.1",
  "posthog-node": "^4.8.1",
  "puppeteer-chromium-resolver": "^23.0.0",
  "puppeteer-core": "^23.4.0",
  "serialize-error": "^11.0.3",
  "simple-git": "^3.27.0",
  "strip-ansi": "^7.1.0",
  "tree-sitter-wasms": "^0.1.11",
  "turndown": "^7.2.0",
  "web-tree-sitter": "^0.22.6",
  "zod": "^3.24.2"
}
```

### 開発依存関係

```json
"devDependencies": {
  "@changesets/cli": "^2.27.12",
  "@types/chai": "^5.0.1",
  "@types/diff": "^5.2.1",
  "@types/mocha": "^10.0.7",
  "@types/node": "20.x",
  "@types/should": "^11.2.0",
  "@types/vscode": "^1.84.0",
  "@typescript-eslint/eslint-plugin": "^7.14.1",
  "@typescript-eslint/parser": "^7.11.0",
  "@vscode/test-cli": "^0.0.9",
  "@vscode/test-electron": "^2.4.0",
  "chai": "^4.3.10",
  "esbuild": "^0.25.0",
  "eslint": "^8.57.0",
  "husky": "^9.1.7",
  "npm-run-all": "^4.1.5",
  "prettier": "^3.3.3",
  "should": "^13.2.3",
  "typescript": "^5.4.5"
}
```

### Webview UI依存関係

Webview UIは独自の`package.json`ファイルを持ち、以下のような依存関係があります：

- React
- React DOM
- Vite（開発とビルド）
- TypeScript
- その他のUIコンポーネントライブラリ

## バージョン管理と互換性

### VSCode互換性

- 最小要件: VSCode 1.84.0以上
- 推奨: 最新の安定版VSCode

### Node.js互換性

- 最小要件: `.nvmrc`ファイルで指定されたバージョン
- 推奨: 最新のLTSバージョン

### ブラウザ互換性

- Webview UI: VSCodeのWebviewコンテナで実行（Chromiumベース）
- ブラウザ自動化: Chrome/Chromiumが必要

## 将来の技術的方向性

1. **パフォーマンス最適化**
   - 大規模プロジェクトでのファイル操作の効率化
   - メモリ使用量の最適化
   - 起動時間の短縮

2. **拡張性の向上**
   - プラグインシステムの強化
   - カスタムツールの開発を容易にするAPI
   - サードパーティ統合のためのフック

3. **クロスプラットフォームの改善**
   - 異なるOSでの一貫した動作
   - プラットフォーム固有の問題の解決
   - 環境依存性の最小化

4. **AI機能の拡張**
   - 新しいモデルとプロバイダーのサポート
   - コンテキスト管理の改善
   - 特定のドメイン向けの最適化

5. **開発者エクスペリエンスの向上**
   - より良いデバッグツール
   - 拡張開発のドキュメント改善
   - コントリビューションプロセスの簡素化
