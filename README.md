# inspection-pages

「点検アプリ」のプライバシーポリシーとサポートページを、GitHub Pages で公開するためのリポジトリです。
このリポジトリは公開されています。アプリのコード・Excel の雛形・社内の資料・個人の情報は置かないでください。

## 公開されるもの

`docs/` フォルダの中だけが公開されます（Settings → Pages: `main` ・ `/docs`）。

| ファイル | 中身 |
|---|---|
| `docs/index.html` | 入口のページ（下の2つへのリンク） |
| `docs/privacy.html` | プライバシーポリシー |
| `docs/support.html` | サポートページ |

アドレスに `docs` は入りません（例: `https://<組織名>.github.io/inspection-pages/privacy.html`）。
組織の名前とこのリポジトリの名前は、後から変えないでください（変えると、App Store Connect に入れたアドレスが開けなくなります）。

## 文章の元（正）

ページを直接書き換えず、元を直してから作り直します。見た目は各ページの HTML の中に書いてあり、共通の CSS ファイルはありません。

- プライバシーポリシー: 点検アプリのリポジトリの `lib/constants/privacy_policy.dart`（アプリの画面と同じ文。提供者と連絡先は `kPrivacyPolicyProvider`・`kPrivacyPolicyContact`）
- サポートページ: 点検アプリのリポジトリの `docs/App_Store_サポートページ_本文_2026-11-10.md`（連絡先・プライバシーポリシーへのリンク・最終更新日だけは、HTML を作るときに足します）

## 直すとき

### プライバシーポリシーの文を直すとき
1. 点検アプリのリポジトリで `privacy_policy.dart` を直す。改定のときは、制定日は変えず、改定日（`kPrivacyPolicyRevisedDate`）に日付を入れる
2. `tool/gen_privacy_policy_html.dart` で `docs/privacy.html` を作り直して置き換える（`--provider` と `--contact` は付けない。アプリと同じ定数を使う）
3. 会社の Mac でアプリの新しいバージョンを出す（アプリの画面の文も変わるため）

`privacy.html` を手で直さないでください。アプリの中の文とウェブの文が食い違います。

### サポートページを直すとき
点検アプリのリポジトリの本文（md）を直してから、`docs/support.html` を作り直します。最終更新日も変えます。アプリのビルドは要りません。

### アプリを増やすとき
1. そのアプリの英小文字の呼び名を決め、リポジトリの名前を「呼び名＋`-pages`」にする（後から変えない）
2. 公開のリポジトリを作り、GitHub Pages（`main` の `docs` フォルダ）の設定は組織の管理者に頼む
3. `docs/` に `index.html`・`privacy.html`・`support.html`、いちばん上に `README.md` を置く。見た目はこのリポジトリのページの書き方を写す
4. 送る前に、個人の情報・社外に出さない情報が入っていないことを確かめる

## 送る前の決まり
- 個人の GitHub アカウント名・個人のメールアドレス・自宅の PC のフォルダの場所を書かない
- 送信（push）の前に、利用者の承認を取る
