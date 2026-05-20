# CLAUDE.md

## プロジェクト概要

タスクボード (task-board) プロジェクト。タスクの追加・完了・削除ができるシンプルな Web アプリ。

## デプロイ先

https://sadahirodev-source.github.io/task-board/

`main` ブランチへのプッシュで GitHub Actions が自動ビルド & デプロイする。

## Git 運用ルール

### 基本方針

- **コードを変更するたびに GitHub へプッシュすること。**
- コミットは意味のある単位でまとめる（機能追加・バグ修正・リファクタなど）。
- コミットメッセージは変更の「なぜ」を簡潔に日本語または英語で書く。

### ブランチ戦略

- `main` ブランチを本番相当として扱う。
- 機能開発は `feature/<名前>` ブランチで行い、完成後に `main` へマージする。
- バグ修正は `fix/<名前>` ブランチで行う。

### コミット & プッシュ手順

```bash
git add <変更ファイル>
git commit -m "変更内容の説明"
git push origin <ブランチ名>
```

### 禁止事項

- `main` への直接 force-push は禁止。
- `--no-verify` でフックをスキップしない。
- 未コミットの変更を残したまま作業を切り替えない。

## コーディング規約

- コメントは WHY（なぜそうしたか）が非自明な場合のみ書く。
- 不要なコード・デッドコードは残さず削除する。
- セキュリティ: ユーザー入力・外部 API の境界でのみバリデーションを行う。

## 技術スタック

| 役割 | 技術 |
|------|------|
| UI ライブラリ | React 18 |
| ビルドツール | Vite 6 |
| スタイリング | Plain CSS (CSS Modules 不使用) |
| 状態永続化 | localStorage |
| CI/CD | GitHub Actions |
| ホスティング | GitHub Pages |

## コンポーネント命名規約

- コンポーネントファイルは **PascalCase** (`App.jsx`, `TaskItem.jsx`)
- 関数コンポーネントは **PascalCase** で定義する
- CSS クラス名は **kebab-case** (`.task-item`, `.delete-btn`)
- イベントハンドラは `handle` プレフィックス (`handleKeyDown`, `handleSubmit`)
- state の setter 以外の内部関数は動詞で始める (`addTask`, `toggleTask`, `deleteTask`)

## 開発環境セットアップ

```bash
npm install
npm run dev    # 開発サーバー起動 → http://localhost:5173
npm run build  # 本番ビルド → dist/
```

## テスト

現時点でテストは未導入。
