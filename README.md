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

## 2026-08-04 更新内容

### コメントを配信ごとに区切るようにしました

前回の配信コメントが次の配信にも残り続けないよう、コメントを「1回の配信」単位で管理します。

- 新しい配信を始めると、通常のコメント欄は空の状態から始まります。
- 過去のコメントログは削除せず、そのまま保存します。
- 30秒以内の瞬断やNodeの再起動では、同じ配信として復元します。
- 30秒を超えて停止したあと再開すると、新しい配信として扱います。
- 配信停止中に書かれたコメントは、次の配信へ持ち越しません。

### アーカイブに、その配信のコメントを表示できるようになりました

録画の時刻から対応する配信を特定できる場合、その配信中のコメントをアーカイブ画面へ表示します。自動で判定できない録画は、録画ファイルの隣にあるJSONへ配信セッションIDを指定して手動で関連付けられます。

古い録画や古いコメントは削除せず、関連付けなしの状態で保持します。

### Discord通知で `@everyone` と `@here` を使えるようになりました

管理画面に、Discord通知の全員メンションを許可する設定を追加しました。

- 初期設定はOFFです。
- ONにしても、通知文に実際に `@everyone` または `@here` が書かれている場合だけ反応します。
- ユーザーやロールへの任意メンションは許可しません。

### MediaMTXを差し替えたあとの復旧を改善しました

MediaMTXのバージョンを差し替えたあと、HEVCや互換高画質などの選択肢が消え、元へ戻しても復旧しない場合がありました。

今回から、配信開始時に `mediamtx.yml` を再確認し、不足している安全な設定だけをバックアップ付きで修復します。

- 推奨・確認済みバージョンは引き続き **v1.19.1** です。
- それ以外のバージョンでは警告を出します。
- バージョン番号だけを理由に画質を消しません。
- Control APIが復旧すると、更新BATを再実行しなくても画質状態を再判定します。
- 修復前の設定は `mediamtx\self-stream-config-backups` に保存します。

### コメントのピン止め機能を追加しました

管理者が、現在の配信中のコメントを1件だけチャット上部へ固定できます。

- ピン止めと解除は管理者だけが行えます。
- 削除・通報されたコメントは自動で解除されます。
- 配信終了時に解除され、次の配信には持ち越しません。
- Nodeを再起動しても、同じ配信中であればピン止めを復元します。

### アンケートとピン止めが重ならないようにしました

チャット上部を共通の固定表示エリアに変更しました。表示順は、アンケート、ピン止めコメント、通常コメントです。PC、スマートフォン、別窓表示でも縦に並び、互いに重なりません。

### そのほかの修正

- Node再起動時のコメントログと集計の復元処理を改善しました。
- 一部だけ書き込まれたログは、欠けた処理だけを再開するよう修正しました。
- 配布元の診断BATを、Windowsで安定して読めるCRLF・UTF-8 BOMなしへ修正しました。
- 不要になったAPIや重複していた処理を整理しました。
- 同梱テストを **743件から764件** に増やしました。

### 2026-07-30版からの更新方法

1. 配信を止めます（`2_配信をとめる.bat`）。
2. 「自鯖配信キット_更新」フォルダを、配信キットのフォルダの中に置きます。
3. `更新する.bat` を実行します。数分かかるため、処理中は窓を閉じないでください。
4. 「Update completed」と表示されたら完了です。

設定、管理パスワード、通知先、リアクション素材、録画、コメント履歴、待機画面の画像、`mediamtx.exe` はそのまま残ります。

更新がうまくいかない場合は、`もとに戻す.bat` を実行すると更新前の状態へ戻せます。

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

不具合の経過を確認したいときや、開発者とやり取りしながら詳しく報告したい内容は[GitHub Issues](https://github.com/ginsabo/self-stream-kit/issues)をご利用ください。Windowsのバージョン、再現手順、表示されたメッセージを添えると、問題を確認しやすくなります。

どちらに送ればよいか迷った場合は、匿名ご意見ボックスで構いません。内容を確認し、必要に応じて開発用のIssueとして整理します。
