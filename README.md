# self-stream-kit

**OBS Studio と MediaMTX を使って、Windows PC に自分専用の配信環境を用意するための自鯖配信キットです。**

[![Latest Release](https://img.shields.io/github/v/release/ginsabo/self-stream-kit?label=latest&style=flat-square)](https://github.com/ginsabo/self-stream-kit/releases/latest)
[![GitHub Pages](https://img.shields.io/badge/Web-site-67e8c2?style=flat-square)](https://ginsabo.github.io/self-stream-kit/)

[最新版をダウンロード](https://github.com/ginsabo/self-stream-kit/releases/latest) ・ [紹介ページを見る](https://ginsabo.github.io/self-stream-kit/) ・ [匿名で意見を送る](https://box.hat-work.com) ・ [GitHub Issues](https://github.com/ginsabo/self-stream-kit/issues)

## self-stream-kit とは

普段の配信操作には **OBS Studio**、映像を受け取って配信するサーバーには **MediaMTX** を利用します。外部の配信サービスだけに頼らず、自分で管理できるストリーミング環境をWindows上に作りたい人向けのプロジェクトです。

```text
┌────────────────┐        映像を送信        ┌────────────────┐
│   OBS Studio   │ ───────────────────────▶ │    MediaMTX    │
│   配信・録画    │                          │  配信サーバー   │
└────────────────┘                          └────────────────┘
```

## 特長

- **Windows向け** — Windows PCでの利用を想定しています。
- **OBS Studioを利用** — 使い慣れた画面から配信を開始できます。
- **MediaMTXを利用** — 軽量なストリーミングサーバーで映像を扱います。
- **自分で管理** — 配信環境を自分のPC・ネットワーク上に用意できます。

## はじめ方

1. [最新リリース](https://github.com/ginsabo/self-stream-kit/releases/latest)を開きます。
2. リリースページから最新版をダウンロードします。
3. ダウンロードしたリリースに付属する案内とリリースノートを確認して、セットアップを進めます。
4. OBS StudioからMediaMTXへ映像を送り、配信を開始します。

> [!IMPORTANT]
> インターネット経由で配信を公開する場合は、認証、ファイアウォール、ルーターなどの設定を確認してください。意図しない第三者からアクセスされないよう、公開範囲は利用者自身の責任で適切に管理してください。

## 2026-07-29 更新内容

### 視聴数の表示を改善

- 表示名を「再生中の視聴数」に変更しました。実際に映像が流れているタブの数です。
- 視聴者がページを閉じると、すぐに数へ反映されます。
- 0人と表示された理由を管理画面で確認できます。
- 数の取得に失敗したときは、古い数を残さず「取得できず」と表示します。

### 導入ガイドに固定URLの取得方法を追加

Cloudflareで独自ドメインを取得し、起動するたびに変わらないURLで配信する手順を追加しました。

- **A：一時URL** — すぐに使えますが、URLは起動のたびに変わります。
- **B：固定URL** — ドメインの購入、トンネルの作成、経路の設定を行います。

### 2026-07-27版からの更新方法

1. 配信を止めます（キットの窓で `Q`、または `2_配信をとめる.bat`）。
2. 「自鯖配信キット_更新」フォルダを、配信キットのフォルダの中に置きます。
3. `更新する.bat` を実行します。数分かかるため、処理中は窓を閉じないでください。
4. 「Update completed」と表示されたら完了です。

設定、管理パスワード、通知先、リアクション素材、録画、コメント履歴、待機画面の画像、`mediamtx.exe` はそのまま残ります。プログラム、入口のBAT、案内書、OBSプロファイルは最新版に入れ替わります。

更新がうまくいかない場合は、`もとに戻す.bat` を実行すると更新前の状態へ戻せます。復元する控えは自動で選択されるため、場所の入力は不要です。

## 必要なもの

- Windows PC
- OBS Studio
- ネットワーク接続
- self-stream-kit の最新リリース

対応バージョンやリリース固有の注意事項は、[最新リリースの説明](https://github.com/ginsabo/self-stream-kit/releases/latest)を確認してください。

## リンク

| 内容 | URL |
| --- | --- |
| 紹介ページ | <https://ginsabo.github.io/self-stream-kit/> |
| 最新版ダウンロード | <https://github.com/ginsabo/self-stream-kit/releases/latest> |
| リリース一覧 | <https://github.com/ginsabo/self-stream-kit/releases> |
| 匿名の感想・気軽な要望 | <https://box.hat-work.com> |
| 詳細な不具合報告・開発相談 | <https://github.com/ginsabo/self-stream-kit/issues> |

## このリポジトリについて

リポジトリ直下の [`index.html`](./index.html) は、GitHub Pagesで公開する紹介ページです。外部ライブラリやビルド処理を必要とせず、HTMLファイル単体で動作します。

```text
self-stream-kit/
├── index.html   # GitHub Pages用の紹介ページ
└── README.md    # このドキュメント
```

## フィードバック

目的に合わせて、2つの窓口を利用できます。

### 匿名ご意見ボックス

「ちょっと気になった」「こんな機能がほしい」など、気軽に伝えたいときは[匿名ご意見ボックス](https://box.hat-work.com)をご利用ください。GitHubアカウントは必要ありません。

### GitHub Issues

不具合の経過を確認したいときや、開発者とやり取りしながら詳しく報告したいときは[GitHub Issues](https://github.com/ginsabo/self-stream-kit/issues)をご利用ください。Windowsのバージョン、再現手順、表示されたメッセージを添えると、問題を確認しやすくなります。

どちらに送ればよいか迷った場合は、匿名ご意見ボックスで構いません。内容を確認し、必要に応じて開発用のIssueとして整理します。
