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

## 2026-07-30 更新内容

### 7月29日版で更新できなかった不具合を修正

`更新する.bat` が次のエラーで止まる不具合を修正しました。

```text
'-NoProfile' is not recognized as an internal or external command
```

Windowsのコマンドプロンプトが日本語を含む行の読み取り位置を見失い、行の途中から実行していたことが原因です。入口のファイルから日本語を取り除いて修正しました。**7月29日版への更新に失敗した方は、7月30日版でもう一度更新してください。**

### 視聴ページの改善

- チャットと概要説明にある `https://`、`http://`、あぷ小の `fu7043289.jpg` 形式、あぷの `f351766.png` 形式を自動的にリンクへ変換します。`javascript:` など、それ以外の形式はリンクになりません。
- PCの別窓・全画面・シアター表示では、画面上部にマウスを乗せたときだけ操作ボタンを表示します。タッチ操作の画面では常に表示します。
- 再生の立て直しに失敗しても、60秒後にもう一度試みるようになりました（最大3回）。
- MediaMTXのポートを既定の8888から変更した場合に、表示上の接続先と実際の接続先が食い違う問題を修正しました。

### 診断とサポートを改善

- 不具合報告を約700字から約100〜150字へ短縮し、コメント欄の初期設定のまま貼り付けられるようにしました。
- 症状が変動する場合は、「直近60秒の揺れ 手元3.0-6.1」のような振れ幅が報告へ自動的に付きます。
- 管理画面の「ログ・診断」、視聴品質メトリクス、ログ絞り込みタグに各数値の読み方を追加しました。
- 「困ったときの対処ガイド.html」を同梱しました。12の症状に対する切り分け、対処、視聴者への案内文を確認できます。
- 管理画面と説明書にあった、報告番号を過去の配信から探せるという誤った記載を修正しました。過去の記録は保存されないため検索できません。

### 2026-07-29版からの更新方法

1. `2_配信をとめる.bat` で配信を止めます。
2. 「自鯖配信キット_更新」フォルダを、配信キットのフォルダの中に置きます。
3. `更新する.bat` を実行します。数分かかるため、処理中は窓を閉じないでください。
4. 「Update completed」と表示されたら完了です。

設定、管理パスワード、通知先、リアクション素材、録画、コメント履歴、待機画面の画像はそのまま残ります。

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
