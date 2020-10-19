---
type: business
layout: tech-faq-article
title: その他便利な機能
weight: 9
---

## IMAP フォルダのローカルコピーを一切残させたくない

キーワード：機能制限、情報漏洩対策

Thunderbird は IMAP サーバーを使用するメールアカウントについて、メールの本文をダウンロードせずヘッダ情報だけをダウンロードする設定が可能です。しかしながら、ヘッダ情報はローカルに保存される上、一度表示したメールについては本文のデータもディスクキャッシュ上に保存されるため、情報漏洩対策として IMAP を使用するという場合には、その設定だけでは目的を十分には達成できません。

アドオン [IMAP キャッシュの自動消去 (Clear IMAP Cache)](https://addons.mozilla.org/thunderbird/addon/clear-imap-local-cache/) を導入すると、Thunderbird を終了する度にダウンロード済みのヘッダ情報とディスクキャッシュを自動的に消去させることができます。これによって、情報漏洩対策としての実効性をより高めることができます。

### 注意事項

このアドオンを使うことで完全な情報漏洩対策が実現される、というわけではないことに注意してください。例えば、ヘッダ情報が保存されているファイルが使用中の場合には、このアドオンではヘッダ情報が消去されない場合があります。

## Outlookとの連携時にwinmail.datを簡単に開けるようにしたい

キーワード：アプリケーション連携

Outlook から送信したメールには、`winmail.dat` というファイルが添付されている場合があります。このファイルにはリッチテキスト形式の本文が保存されていますが、Thunderbird では内容を閲覧することができません。そのため、添付された winmail.dat をダブルクリック等で開こうとした場合には、ファイルが開かれるのではなくファイルのダウンロード (ファイルとして保存する処理) が開始されます。

`winmail.dat` の内容は、[WinmailOpener](https://www.google.co.jp/search?q=WinmailOpener) という別のソフトウェアで閲覧することができます。アドオン [Winmail Opener Bridge](https://addons.mozilla.org/thunderbird/addon/winmail-opener-bridge/) を導入すると、添付された `winmail.dat` を開こうとした時に自動的に WinmailOpener でファイルが開かれるようになります。

### 注意事項

Winmail Opener Bridge に はWinmailOpener は同梱されていません。利用にあたっては、別途 WinmailOpener をインストールしておく必要があります。

## メールアカウント作成ウィザードで特定組織向けのメールアカウントをもっと簡単に作成させたい

キーワード：導入時初期設定

Thunderbird のメールアカウント作成ウィザードでは、Mozilla 公式に提供されている ISP の情報や、メールサーバーに設置された設定情報、一般的なメールサーバーの設定の流儀などに従って、メールアドレスとパスワードを入力するだけでメールアカウントを半自動的に作成することができます。しかしながら、メールサーバーなどの基本的な設定以外の項目 (例えば HTML メールの利用の可否など) は、その後改めて手動で設定する必要があります。

アドオン [AutoConfiguration Hook](https://addons.mozilla.org/thunderbird/addon/autoconfiguration-hook/) を使用すると、あらかじめメールアカウント情報のテンプレートとなる設定ファイルを用意しておくことにより、基本設定以外の項目についてもメールアカウント作成時の初期値を指定することができます。また、メールアドレスのローカルパートのみを入力させてメールアカウントを作成できる、特定組織向けのメールアカウント作成専用のウィザードも利用可能になります。

## メールアドレス入力欄の2番目以降に不正なアドレスが入力されているときに警告のメッセージを出したい

キーワード：障害回避

Thunderbird は、メールの宛先が正しいメールアドレスでない場合、メール送信時に警告が表示される仕様になっています。しかしながら、2 つ目以降の宛先についてはこの確認が行われないという不具合 (制限事項) があります。

アドオン [不正なアドレスの警告表示パッチ (Patch to Alert Invalid Addresses)](https://addons.mozilla.org/thunderbird/addon/patch-to-alert-invalid-addr/) を使用すると、2 つ目以降の宛先についても最初の宛先と同様の妥当性検証が行われるようになります。

## ローカルファイルに対するリンクをメール本文中に挿入したい

キーワード：利便性向上

古いバージョンの Thunderbirdで は、メール編集ウィンドウの本文領域にファイルをドラッグ＆ドロップすると、ファイルの URL 文字列がその位置に挿入される仕様でした。しかしながら、現在のバージョンの Thunderbird では、この機能は廃止されています。

アドオン [ローカルファイルからのリンク挿入 (Insert Link from Local File)](https://addons.mozilla.org/thunderbird/addon/insert-link-from-local-file/) を導入すると、古いバージョンの Thunderbird と同様に、ファイルのドロップ位置にそのファイルの URL を挿入できるようになります。挿入された URL は、受信者側ではリンクとして利用することができます。

これによって、社内でのメールのやりとりにおいて、ファイルを添付する代わりに共有フォルダに置き URL だけをやりとりする、といった使い方が容易になります。

## Windows のショートカットを添付できるようにしたい、添付された Windows のショートカットを直接実行したい

キーワード：利便性向上

Thunderbird では、Windows のショートカットファイルをメールに添付することができません。また、添付されたショートカットファイルを受信した場合にも、それを直接開くことはできず、一旦ファイルとして保存してから改めて開く必要があります。

アドオン [Windows ショートカットの直接実行 (Open Windows Shortcuts Directly)](https://github.com/clear-code/openshortcuts/releases) を導入すると、ショートカットをメール編集ウィンドウの宛先領域周辺にドラッグ＆ドロップすることによってファイルとしてそのまま添付できるようになります (※メニューからの操作でコモンダイアログから選択した場合は、ショートカットのリンク先の実体ファイルが添付されます)。また、ショートカットが添付されたメールについては、ショートカットをダブルクリックするなどの操作によりリンク先の実体ファイルを直接開けるようになります。

これによって、社内でのメールのやりとりにおいて、ファイルを添付する代わりに共有フォルダに置きショートカットだけをやりとりする、といった使い方が容易になります。

## 添付ファイルの文字エンコーディングの自動判別をより賢くしたい

キーワード：利便性向上

Thunderbird では、プレーンテキスト形式のファイルを添付する際にファイルの文字エンコーディングを自動判別し、ヘッダ情報に含めるようになっています。しかしながら、この自動判別があまり正確でないため、Shift_JIS や EUC-JP のテキストファイルを添付した場合に受信者側で文字化けして表示されることがあります。

アドオン [添付ファイルの文字エンコーディングの自動判別 (Attachment Encoding Detector)](https://addons.mozilla.org/thunderbird/addon/attachemnt-encoding-detecto/) を導入することにより、上記処理における文字エンコーディングの自動判別において言語別の自動判別器が使われるようになり、文字化けの発生を低減することができます。

## アドレス帳を複数コンピュータ間で同期したい

キーワード：利便性向上

Thunderbird では、LDAP アドレス帳機能によって、ディレクトリサーバー内に格納されている情報をアドレス帳として参照することができます。しかしながら、この機能にはいくつかの制限事項があります。

* LDAP アドレス帳への書き込みはできません。読み込みのみの利用となります。
* ディレクトリサーバーに接続する際のユーザーを Windows のログオンユーザーと連携させること (シングルサインオン) はできません。

LDAP アドレス帳ではないアドレス帳の共有または同期を可能にする方法として、アドオン [Addressbooks Synchronizer](https://addons.mozilla.org/thunderbird/addon/addressbooks-synchronizer/) の使用が挙げられます。このアドオンを使用すると、例えば以下のような運用も可能となります。

* アドレス帳を IMAP サーバー上にメールの添付ファイルとして保存し、複数 PC 間でアドレス帳を同期する。
* アドレス帳を HTTP または FTP サーバー上に設置しておき、複数ユーザー・複数 PC から読み込み専用の共有アドレス帳として参照する。

## 初期状態で表示するカラムを変更しておきたい

キーワード：導入時初期設定

Thunderbird のスレッドペインでは、初期状態でどのカラムを表示しておくかが決め打ちになっており、例えば「重要度」のようなカラムをすべてのフォルダ・すべてのアカウントで最初から表示された状態にしておきたいと思っても、管理者がそれを全クライアントに反映することはできません。

アドオン [Set Default Columns](https://addons.mozilla.org/thunderbird/addon/set-default-columns/) を使用すると、初期状態で表示しておくカラムを [MCD (AutoConfig)](../setting-management/#mcd) の設定ファイルなどからカスタマイズすることができます。

### 設定方法

以下は、[MCD (AutoConfig)](../setting-management/#mcd) で、「重要度」のカラムを初期状態で表示するようにする設定例です。

    lockPref("extensions.set-default-columns@clear-code.com.columns", [
      "priorityCol", // 追加したカラム
      "threadCol",
      "threadCol",
      "attachmentCol",
      "flaggedCol",
      "subjectCol",
      "unreadButtonColHeader",
      "senderCol",
      "junkStatusCol",
      "dateCol",
      "locationCol"
    ].join(","));

既に 1 度でも内容を表示したことがあるフォルダについては、最後に内容を表示した時の表示カラムの状態が記憶されています。ここで設定した既定の表示カラムを反映するためには、カラム行の右端のアイコンをクリックしてメニューから「初期状態に戻す」を選択する必要があります。