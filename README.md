<!-- 外部参照リンクの定義 -->

<!-- WebClapModoki 標準動作用の Google スプレッドシート（テンプレート） -->
[SS_template]: https://docs.google.com/spreadsheets/d/1j_h4weHihW-uVeTFtHTwrs6QwRPAT36sEBf3DPbo3ms/edit?usp=sharing

<!-- WebClapModoki の GAS 本体 (v9) -->
[WebClapModoki-GAS]: /WebClapModoki-GAS.txt
<!-- WebClapModoki の GAS 本体中の、
  // ◆ 加工し終わった後の配列から、各パラメータを取り出す処理の行 -->
[WebClapModoki-GAS_param_ext]: /WebClapModoki-GAS.txt#L1068

<!-- WebClapModoki の GAS 本体 (v10) -->
[WebClapModoki-GAS_v10]: /WebClapModoki-GAS_v10.txt
<!-- WebClapModoki を里々から叩く場合のサンプルコード -->
[dic_wcm]: /dic_wcm.txt
<!-- WebClapModoki を里々から叩く場合のサンプルコード, 生テキスト形式表示 -->
[dic_wcm_raw]: https://raw.githubusercontent.com/dullNeko/WebClapModoki-GAS/main/WebClapModoki-GAS.txt
<!-- WebClapModoki の LICENSE -->
[LICENSE]: /LICENSE.md

<!-- Figure 0_0 / スクリプトプロパティの設定変更時の注意（保存を忘れずに！） -->
[Fig_0_0]: /files/Figure0_0.png
<!-- Figure 0_1 / トリガー条件設定例 -->
[Fig_0_1]: /files/Figure0_1.png
<!-- Figure 1 / 動作イメージ-->
[Fig_1]: /files/Figure1_v2.gif
<!-- Figure 2 / 動作概念図-->
[Fig_2]: /files/Figure2.png
<!-- Figure 3 / デプロイ時の最重要注意点-->
[Fig_3]: /files/Figure3.png
<!-- Figure 4 / v10 での動作イメージ-->
[Fig_4]: /files/Figure4.gif
<!-- Figure 5 / 使い続けていると起こるあるある状態 -->
[Fig_5]: /files/Figure5.png
<!-- Figure 6 / 配布用スクリプトと開発用スクリプトを分けた状態 -->
[Fig_6]: /files/Figure6.png
<!-- Figure 7 / 「デプロイの更新」の仕方（１／２） -->
[Fig_7]: /files/Figure7.png
<!-- Figure 8 / 「デプロイの更新」の仕方（２／２） -->
[Fig_8]: /files/Figure8.png
<!-- Figure 9 / 実際の運用方法イメージ -->
[Fig_9]: /files/Figure9.png


<!-- WebClapModoki-GAS 処理内容・導入手順の詳細説明スライド v8版 -->
[ExpSlide]: /files/ExpSlide_20221225.pdf

<!-- Web拍手公式サイト -->
[WebClapOrg]: http://www.webclap.com/index.html

<!-- 「Google アカウントのアクセス権の確認・削除」画面 -->
[g_perm]: https://myaccount.google.com/permissions
<!-- GAS の各種制限ページ -->
[GAS_quotas]: https://developers.google.com/apps-script/guides/services/quotas 

<!-- 伺的 Advent Calendar 2022 -->
[uka_adcurry2022]: https://adventar.org/calendars/8310
<!--伺的 Advent Calendar 2022 延長戦ハッシュタグ -->
[uka_adcurry2022_extended]: https://twitter.com/hashtag/uka_advent_2022

# WebClapModoki-GAS

WebClap-like system by using Google Apps Script & Google spreadsheet.

# バージョンごとの違いについて

増えてきたので整理してみました。

| ファイル名                     | ver |    更新日     | 要求権限                                                                                          | 長所                                                                             | 短所                                                                      |
|:--------------------------|:---:|:----------:|:----------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------|:------------------------------------------------------------------------|
| WebClapModoki-GAS.txt     | v9  | 2022-12-25 | ●Google スプレッドシートのすべてのスプレッドシートの参照、編集、作成、削除<br>●外部サービスへの接続                                      | ●記事通りの導入でOK<br>●安定版                                                            | ●（送信元）;（送信内容）;（メモ）の３要素でないと受け付けない制限あり<br>（この形式以外を受け取っても、スプレッドシートに記録しません） |
| WebClapModoki-GAS_v10.txt | v10 | 2022-12-27 | ●Google スプレッドシートのすべてのスプレッドシートの参照、編集、作成、削除<br>●外部サービスへの接続                                      | ●記事通りの導入でOK<br>●↑のv9の３要素縛りがなく、１～５個の要素を柔軟に受信できます                                | ●動作確認不十分な試験版です                                                          |
| WebClapModoki-GAS_v11.txt | v11 | 2023-01-17 | ●Google スプレッドシートのすべてのスプレッドシートの参照、編集、作成、削除<br>●外部サービスへの接続<br>●Gmailへの完全なアクセス<br>●本人に代わってのメール送信 | ●簡易的ですが「新着があればメールで通知」ができるようになりました<br>●スプレッドシートの id をハードコーディングしない方法も取れるようになりました | ●要求権限がデカいです<br>●動作確認不十分な試験版です<br>●導入・初期設定が面倒です                          |
| WebClapModoki-GAS_v12.txt | v12 | 2023-01-18 | ●Google スプレッドシートのすべてのスプレッドシートの参照、編集、作成、削除<br>●外部サービスへの接続<br>●Gmailへの完全なアクセス<br>●本人に代わってのメール送信 | ●v11 の長所に加えて、Discord の任意チャンネル（プライベートチャンネル含む）へ、投稿された内容を横流しできるようになりました           | ●要求権限がデカいです<br>●動作確認不十分な試験版です<br>●導入・初期設定が面倒です                          |


# 更新履歴

## 2023-01-18 : 記事更新、WebClapModoki-GAS_v12.txt の追加。

Discord の WebHook URL を利用して通知を行う機能を追加した、
WebClapModoki-GAS_v12.txt を追加しました。

__WebClapModoki-GAS_v12.txt__ は、  
WebClapModoki-GAS_v11.txt に、

- Discord WebHook URL 経由で通知を投げる関数（sendDiscordWebHook(post_content)）
- initPropertyValues() に DISCORD_WEBHOOK_URL, SPREADSHEET_ID の作成・確認を追加
- doPost(e) 内の GAS_Date_Time の取得処理変更。
- doPost(e) 内に「◆ 外部（WebHookなど）に投げる content を用意する」「◆ ついでに Discord Webhook URL に投げてみる処理」の追加

の機能追加・修正を加えた __試験版__ となっております。

…なんだか永遠に試験版を出すことになりそうな気がしますが、  
今後も自分が欲しいと思った機能は（気分次第で）追加していきますので、  
何卒よろしくお願い申し上げます。

ついで…と申し上げては何ですが、  
__２点ほど、設定で分かりづらそうな所__ を、以下に画像で示しておきます。  
自分もよく引っかかるので、備忘録です…。

１つ目（Fig.0.0）は、スクリプトプロパティの設定変更時の注意です。  
__「スクリプトプロパティの保存」ボタンのクリック__ を忘れると、  
__せっかく設定を変更しても反映されない__ ため「なんでや…」に良くなります。

![Figure0_0][Fig_0_0]
<p align="center"><strong>
Fig.0.0 スクリプトプロパティの設定変更時の注意点（保存を忘れると、設定変更が反映されません！）
</strong></p>

２つ目（Fig.0.1）は、メール通知用関数（dailyCheckTotalCounts_v2）を、  
「トリガー」機能で定期的に実行する際の設定例です。  

注意点としては…  
__実行するデプロイを「Head」にしておくと、常に最新のデプロイ版が実行される__ 点でしょうか。  
__「更新する度にトリガ設定を（忘れずに）弄る」のはとても面倒__ なので、  
__基本的には Head にしておく__ ことを薦めたい…のですが、  
バグ等があった場合にも気にせず実行してしまう、という欠点もあります。  

画像の設定なら、一日一回（２４時～２５時の間のどこか）の実行頻度なので、  
気にするほどではないと思いますが…念のため申し添えておきます。


![Figure0_1][Fig_0_1]
<p align="center"><strong>
Fig.0.1 メール通知用関数の、トリガ条件設定例
</strong></p>


## 2023-01-17 : 記事更新、WebClapModoki-GAS_v11.txt の追加。

本「更新履歴」セクションを新設しました。  
また、WebClapModoki-GAS_v11.txt を追加しました。

__WebClapModoki-GAS_v11.txt__ は、  
WebClapModoki-GAS_v10.txt に、追加で

- メール通知用関数（sendMailAlert(count)、dailyCheckTotalCounts_v2()）  
- 並びにその初期化用関数（initPropertyValues()）  
- スプレッドシートの id のハードコーディング回避策（プロパティサービスから SPREADSHEET_ID を読み込んで使用する）  

を __試験実装した版__ になります。

上記の追加・変更のため、新たに  

- メール関係の権限を追加で許可する（Gmailへのフルアクセス、本人に代わってのメール送信）  
- プロパティサービスの EMAIL_ADDRESS , ROWS_COUNT の適切な設定  
- トリガ条件を設定して、定期的に dailyCheckTotalCounts_v2() を実行させる設定
- （スプレッドシートの id のハードコーディング回避策を利用する場合）プロパティサービスに SPREADSHEET_ID を手動で追加・値を登録

を行う必要があり、__要求権限が大きく、導入も煩雑__ になっています。  

__※ 導入手順については、WebClapModoki-GAS_v11.txt の冒頭部分にある更新履歴に書いてみました。__  
（スクリプトプロパティの操作など、エディタ画面からの操作が多くなってしまうので…）

そのため、

- __WebClapModoki-GAS.txt (v9)__
  - 記事通りの導入手順でOK。
  - 動作安定版。
  - ただし「（送信元）;（コメント）;（メモ）」の形式以外は受け付けない。
- __WebClapModoki-GAS_v10.txt__
  - 記事通りの導入手順でOK。
  - 要素数３個縛りを撤廃しているので、柔軟にデータの受付ができます。
  - ただし開発版扱いです。テスト不足気味…。
- __WebClapModoki-GAS_v11.txt__
  - v10にメール通知機能を試験実装した版。
  - ただしメール関係の権限＆記事にない設定手順が必要で、設置が面倒。
  - 相変わらずテスト不十分な開発版です…。

…として、使い分けて頂ければ幸いです。

## 2022-12-28 : 記事更新、「Tips: Versioned Deployments の扱い方」を追記。

実運用時に（自分が）困りがちだった問題、  
すなわち __「デプロイする度にURLが変わって管理が煩雑」__ という問題に対する、  
__「こうしたらURL不変で運用できます」__ な説明セクションです。

## 2022-12-27 : 記事更新、WebClapModoki-GAS_v10.txt の追加。

__WebClapModoki-GAS_v10.txt__ は、  
WebClapModoki-GAS.txt (v9) から、  
てにてにさんのツイートを参考にして、  
（送信元）１つだけ～  
（送信元）;（コメント）;（メモ）;（追加情報１）;（追加情報２）  
の５つまで、 __データを可変で受け取れるようにした版__ です。

__POSTする側での縛り（＝（送信元）;（コメント）;（メモ）の形でないと受け付けない）が無くなっただけ__ なので、  
__導入手順自体は、記事通りでOK__ です。

## 2022/12/25 : 記事公開。WebClapModoki-GAS.txt (v9) リリース。

最初の公開日。

記事通りの手順で導入・安定動作させたい場合は、
WebClapModoki-GAS.txt (v9) をお使いください。

# 前書き

[伺的アドベントカレンダー2022][uka_adcurry2022]、25日の記事です。  
[24日の Zichqec 氏の記事](https://zichqec.github.io/s-the-skeleton/advent_calendar_2022_02) に続いて、dullNeko がお送りします。

伺か界隈で良くお見掛けする [Web拍手][WebClapOrg] が長らくメンテされていない（らしい）と知り、  
手持ちの技術（Google Apps Script & Google スプレッドシートの組み合わせ）で、  
代替になりそうな何かを組んでみた…という記事になっております。

長い事ユーザ専門だったので、  
こういった記事を書くのも、人様に使って頂く目的でスクリプトを公開するのも、初めてです…  
何卒、お手柔らかにお願い申し上げます。


# これは何？

- __Web拍手と同じような使い勝手__ で
  - （＝外部サイトに誘導せず、SSP内での \![open,inputbox,...] と \![execute,http-POST,...] の組み合わせだけで使えて）
- ユーザさんから直接「感想」「バグ報告」などコメントを投げてもらえて
- __デべさんのGoogleアカウント内に作成したGoogleスプレッドシート__ に、投稿されたコメントを記録する

…ことができる __Web拍手"もどき"__ です。


# どんなことができるの？

動作イメージは…↓のGIF画像（Fig.1）をご覧頂ければわかりやすいかと思います。  
SSPのインプットボックスから入力した「いいね！」と、付随する情報が Google スプレッドシートに記録されている様子のGIF動画です。  
__画面遷移を伴わず、SSPからWeb拍手と同じ様に扱える__ のが最大の特徴です。

※お借りしているシェルは [にはちびっとさんのフリーシェル「和装のおばあさん01」](https://waka.edo-jidai.com/sub/freeshell.html) です。  
※マウスカーソルは [ゴースト回覧板３ｒｄ「ロスト・ユー・サムウェア」スレの2214氏作ルストリカマウスカーソル](https://jbbs.shitaraba.net/bbs/read.cgi/computer/44300/1432111308/2214) です。

![Figure1][Fig_1]
<p align="center"><strong>
Fig.1 動作イメージ（こんな感じの動作をします、というデモGIF動画）
</strong></p>



# どういう仕組みなの？

本システムの動作図解…というか概念図のようなものとして、↓の画像（Fig.2）を作ってみました。

お伝えしたい最重要ポイントは、  
「本スクリプトで作れるWeb拍手もどきシステムは、  
　（ここでスクリプトを公開してる dullNeko の Google ドライブではなく）  
 　__デべさんご自身の Google ドライブ上（に設置されたスクリプト）で動くもの__」  
という点です。

なので、ご自分の Google ドライブ上へのスクリプトの導入・初期設定など、  
__デべさんご自身に、手動で実行して頂かなければならない作業__ があります。

![Figure2][Fig_2]
<p align="center"><strong>
Fig.2 動作の図解というか概念図っぽいもの
</strong></p>


# なんで作ったの？

伺かのゴーストをtkっていて、久々に [Web拍手][WebClapOrg] を利用させて頂こうと思って調べ直したところ、  
かなり前から

- [公式サイト][WebClapOrg] に繋がらない？
- 既知の不具合（絵文字などが入力されると、以降の文字列が読めなくなる等）が複数あるが、更新・対応される気配はない（っぽい）
- SSL (暗号化通信) への対応が行われる可能性も…無さそう…

な状態にある、と知って採用を見送った…のですが、  
「SSP からさくらスクリプトの \![execute,http-POST,...] 使って、inputbox から __直接__ 一言感想出せるの、ユーザ的には気楽だし手軽でいいのよね…何か他の手はないかな…」などと諦めきれずに考えた結果、  
「そういやラズパイからセンサのデータを POST で投げて、__Google Apps Script(GAS)__ で受けてスプレッドシートに記録するとかやってたな？」と思い出し、  
突貫で試作してみたものがこちらになります。  


# さっきから出てくる GAS…Google Apps Script？って何？

公式サイトは  
https://workspace.google.co.jp/intl/ja/products/apps-script/  
…なんですが、このページを見て何なのか／何をするものかパッと分かる人は…  
多分、控えめに言っても少数派ですよね…

Googleさんの公式な説明として（まだ）分かりやすいのは  
__[「Google プロダクト全体でタスクと統合して自動化できる"クラウドベースの JavaScript プラットフォーム"」](https://developers.google.com/apps-script/)__  
でしょうか。

身も蓋もない言い方をしてしまえば、  
__「サーバサイドのプログラムを、サーバの立ち上げ・維持管理不要で組める」__  
代物です。  

Google さんが提供するサービスなので、  
__「他の各種 Google サービス（Google スプレッドシート、Gmail、カレンダー、etc...）と連携して処理する機能」__  
もついてきます。  
（というか、公式の謳い文句的にはこちらがメインですね）


## GAS の良い所は？

前節の繰り返しになってしまいますが、  
__「サーバ側でないと難しい処理」__  
…本プロジェクトで言えば、

- 不特定多数のユーザさん（のSSP）から送られるHTTPリクエスト（※POSTメソッド限定）を受信し
- 受け取ったデータを適当な形の文字列・配列に整形し
- スプレッドシートに記録するなど、様々な後処理を行う

といった動作を、

- 自分でサーバを立ち上げたり維持管理することなく
- JavaScript（ライクなGoogle Apps Scriptという）言語で処理を記述できて
- Google アカウント（Goodle ドライブにアクセスできる環境）さえあれば無償で利用可能で
- さらに、Google の各種サービス（スプレッドシート等）に接続・連携して処理できる機能が実装されている

…というのが、GASの良い所です。


## 逆に、GAS の悪い所は？

悪い所…というか、  
（dullNekoが調べた範囲で、 __誰からもアクセスできるWebアプリ__ とした場合に）  
__GASでできないこと／問題点になりそうな所__ を挙げておきますね。

- __アクセス元情報など「サーバ側でないと得られない上に重要な情報」が取得できない__
  - 標準仕様の「ご自身の Google ドライブ上にある Google スプレッドシートに、受け取ったコメントを書き込んでいくだけ」なら、特に問題にならないと思います。
  - …ですが、 __外部のAPIを叩く処理（例：「Mastodon へのトゥート機能」など）を実装し、運用した場合には厳しい点__ です。  
  - 対象のサーバさんから見れば、 __アクセス元はあなた（のGoogleアカウント内のスクリプト）__ であって、大本のHTTPリクエストを送信した方ではありません。
  - 原因が何であろうと（例え、悪意のないスクリプトの誤動作だったにせよ）、結果として相手様から DoS 攻撃と認識される事態が生じた場合、 __責任を追及される可能性が極めて高い__ のは __スクリプトを設置し、動作させたあなた__ です。
  - __2010年に起こった「岡崎市立中央図書館事件（Librahack事件）」と似たケースになる可能性__ を、私は否定できません…。
  - そのため、__標準仕様では「Mastodonへのトゥート機能」は使えないように細工__ してあります。
  - ご自身に責任が降りかかる危険性を認識した上で、十分な注意を払っての使用をお願いいたします。
- __「一日あたりの処理量」に制限があり、それらのほとんどは有償プランでも緩和されない__
  - 処理量制限の詳細は [こちらのページ][GAS_quotas] にある通りです。
  - [WebClapModoki-GAS.txt][WebClapModoki-GAS] の冒頭、「★ 参考資料」セクション内「★ GAS全体の制限について」でも記述しましたが、結構厳しめの制限です。
  - この制限のため、スクリプトを組む際には「セル参照を行う回数をできるだけ減らし、書き込み・読み出しは一括で行う」などのテクニックを使う必要性が高くなっています。
- __Google さんのサービスなので、唐突にサービス終了して使えなくなる可能性がある__
  - 2009年から続いている古株サービスですし、利用者も少なくない（はず）ですし、何より Google のサービス全体を連携させて使うための仕組みなので、可能性は低め…だとは思いますが…無い、とは言い切れません。
- __Google Apps Script の詳細な全仕様は公開されていない__
  - 大元としては JavaScript1.6 がベースである（らしい）のですが、ECMAScriptの"一部"取り入れ（例：[V8ランタイムは使用可能だが、ES6 モジュールはサポートされてない](https://developers.google.com/apps-script/guides/v8-runtime?hl=ja)等）や、独自実装（例：Google ドライブ上にあるデータ内でのみ扱える[プロパティサービス](https://developers.google.com/apps-script/guides/properties)等、Google サービスに紐づいたAPI）等もあり、やや複雑な言語になっています。
  - また、予告なく機能や仕様が変更される（例：上のプロパティサービスに関わる関数群）こともあり、今の所使えている実装が気付いたら動かなくなっていた…というパターンが無きにしも非ず。


# 他のサービスと比べてどう？わざわざ自作する意味あるの？

真剣に比較検討したわけではない…ので恐縮ですが、

- __GAS は Google アカウントさえあれば、すぐに使える__
  - ＝Web拍手等、CGIプログラム設置の為だけにサーバをお借りする…ような手間が無く、手軽に使い始めることができます。
  - Twitter（各種SNS）との連携等も必要なく、単体（GAS＋Googleスプレッドシート）で動作するので、SNSやりたくない派／サービス紐づけとかしたくない派の方にもおススメ。
- __基本的に無償で使用可能__
  - ※同じ日に大量にアクセスがあったりすると制限がかかり、通信を遮断される可能性はあります。
  - これはまあ…他サービスもそんな変わらないかな…。
- __頂いた感想について、スプレッドシート上で一覧・集計・検索したりできる__
  - 特定の条件（例えば「バグ報告だけ」）拾うとか、対応状況（した／してない／できない）の列を右端に足して管理したり、といった工夫ができるのは便利…だと思うのですけれど…
- __感想の回収・保全が簡単__
  - 頂いた感想・バグ報告等、コメントの記録先が __自分の Google ドライブ上のスプレッドシート__ なので、「サービスの終了で突然データが消えちゃう」とか「まとめてダウンロードできない」とか、そういう類の心配はなさげです。
  - 定期的にダウンロードしてローカルに保存する、コピーを作って別の場所に保存する、程度の単純なバックアップ操作がし易いのは良い点だと思います。
  - …逆に __うっかり記録先シートを削除しちゃうような、致命的な操作ミスもできてしまう__ あたりは痛し痒し。
- __自分用にカスタマイズする難易度が低め__
  - JavaScriptが全然書けない（アロー関数すらまともに使えない）私でも、本スクリプトを作れる位には低めです。
  - オリジナルのWeb拍手から少しだけ拡張して、__【送信元】;【送信内容（コメント）】;【その他メモ】 の３情報を ;(半角セミコロン) 区切りで取得する__ ようにしたり、位ならできました。
  - 他には…「予め記述したNGワードを弾く関数」を実装してあります。とても原始的な処理ですし、他サービスの高度で自動的なフィルタリング機能に比べると…悲しくなるレベルですが…。
  - GASから更にPOSTメソッドでHTTPリクエストを出す例として、「Mastodon API を利用してトゥートする関数」も実装してあったり。 __（※↑の「悪い所」で前述した問題点／危険性があるので、そのままでは使えないようセーフティをかけてあります）__

…と、__「お手軽＆いろいろ自分好みにカスタムできる点」__ については、  
他のサービスとかと比べてもいいところでは…？と感じたので、  
GitHubの練習がてら公開してみることにした次第です。


# 環境作成・設定方法、使い方の説明は？

## __※作業する前に、下記【注意喚起】を必ずお読みください！__

README.md内にて画像付きで説明…してみようとして挫折したので、  
次の PDFファイル (詳細説明スライド) もご覧くださいまし。

[WebClapModoki-GAS 処理内容・導入手順の詳細説明スライド][ExpSlide]

__【注意】__  
※2022/12 時点での Google Apps Script の UI での操作手順なので、  
　今後、Google さん側で UI の更新があると、古い資料になる可能性が高いです。  
　「画面全然違うんだけど！」ということがあれば、  
　↓の連絡先のフォーム等でお知らせ頂ければ幸いです。

一応、文章のみの簡易な説明も、  
手順X. として下に記述しておきます。


## 【注意喚起】

本スクリプトを導入後、最初に「実行」を試みた際、  
__「承認が必要です：このプロジェクトがあなたのデータへのアクセス権限を必要としています」__  
というウィンドウが出てきます。  
__ここで要求されるアクセス権限を許可しなければ、本スクリプトは実行できません。__

要求される権限は、以下の２つです。  
__「Google スプレッドシートのすべてのスプレッドシートの参照、編集、作成、削除」__  
__「外部サービスへの接続」__  
…２つだけですが、要求される内容はかなり重いものです。

長くなってしまいますが… __大事な所__ なので、できるだけ詳しく説明しますね。

- __「Google スプレッドシートのすべてのスプレッドシートの参照、編集、作成、削除」__  
  - SpreadsheetApp.openById(SPREADSHEET_ID); を使用しているため、要求されます。
  - __本スクリプトでは上記１シートの参照・編集（書込）しか実行しません__ が、__コードを書き換えれば別のシートを操作できますし、シートの作成・削除も可能__ です。
  - __悪意あるスクリプトの場合（あるいはご自分で組んだスクリプトであっても、処理の記述ミス等があれば）、「ドライブに存在するスプレッドシート全てを列挙し、削除する」「スプレッドシート内の機密情報を、外部に吐き出す」などといった悪辣な動作をさせることも可能です。__
  - ？マークをクリックした際の詳細（この権限が要求し、結果としてスクリプトができるようになることの詳細）は、次の通りです。
    - このアプリが次の権限を求めています。
    - スプレッドシートの参照、編集（設定、メタデータを含む）
    - スプレッドシートの新規作成
    - __スプレッドシートのアップロード、ダウンロード__
    - __スプレッドシートの整理、削除__
    - __スプレッドシートを共有しているユーザーの名前、メールアドレスの参照__
    - __他のユーザーとのスプレッドシートの共有、共有停止__
    - __このアプリは、ユーザーが行える操作と同じ操作を行うことができます。このアプリが加えた変更は、ユーザーによるものと見なされます。__
    - __スプレッドシートには、財務記録や個人的リストなどの機密情報が含まれている可能性があります。__
  - ご覧の通り、__「自分が操作する場合にできること全て」ができます__ し、
  - 同時に __「スクリプトが行ったことであっても、ユーザ本人が操作したものと見做される」__ という、強い文言も入っています。
- __「外部サービスへの接続」__  
  - tootByMastodonAPI(toot_content) 関数内で UrlFetchApp.fetch を使用しているため、要求されます。
  - __本スクリプトではコメントアウト＆セーフティがかけられているため、細工を回避しない限り機能しません（＝標準構成で、この権限を使用することはありません）__ が、それでも「記述がある以上、実行される可能性がある」として、要求されます。
  - ？マークの説明に「外部サービスへのネットワーク接続の作成（例: データの読み取りまたは書き込み）」とある通り、UrlFetchApp.fetch はHTTPリクエストを通じてデータのスクレイピング（収集・抽出）を行うものであるため、場合によっては他サーバへの攻撃・業務妨害と見做される動作をしてしまう危険性があります。

ここは…私からは、  
__「スクリプトのソースを読み、（特に、doPost(e)の）実際の処理を見て、判断してください」__  
としか申し上げられません。  
__「dullNeko の書いたスクリプトを信用できない」と思われた場合は、ここまで__ です。  

もし、この権限を要求される段階まで操作を進めてしまっていた場合は、  
アクセス権の付与をキャンセルし、  
作成したスプレッドシートやスクリプトを削除して下されば、元通りの状態に戻せます。  
お手数をおかけして申し訳ありませんが…この点は、何卒ご容赦ください。


## 手順1.  
__ご自身の Google ドライブ__ に、[このスプレッドシート][SS_template] のコピーを作成してください。  
Googleアカウントでログインしたブラウザ上で開けば、メニューの「ファイル」→「コピーを作成」で簡単にコピーできます。  
また、名前（WebClapModoki (template) のコピー）は好きに変えて大丈夫です。


## 手順2.  
同じくご自分の Google ドライブに「新規 Google Apps Script」を作成し、  
[WebClapModoki.txt][WebClapModoki-GAS] の中身をコピペして、上書き保存してください。  
[RAW表示][dic_wcm_raw] からコピペするのが楽かもです。

__【注意】__  
1.のスプレッドシート、2. の Google Apps Script の共有設定  
（「右クリックメニュー」→「共有」→「一般的なアクセス」の設定値）は、  
初期状態の __「制限付き」でOK__ です。  
これらのURLを公開する必要もありません。むしろ秘密にしておいて下さいまし。


## 手順3.
1.でコピーしたスプレッドシートの 'id'、すなわち
```
（ブラウザで開いた時のURL）
https://docs.google.com/spreadsheets/d/XXX...XXX/edit#gid=0
```
の __XXX...XXX__ をコピーし、
2.の Google Apps Script 内
```
const SPREADSHEET_ID = 'XXX...XXX';
```
の __XXX...XXX__ を  
ご自分のスプレッドシートの 'id' に書き換えて、上書き保存してください。


## 手順4.
3.で修正した WebClapModoki の Google Apps Script を開き、  
doPostTest 関数（動作テスト用関数）を実行してみてください。   

__【注意】__  

この時、__【注意喚起】で先述した__ 警告画面が出て、  
__「この Google Apps Script に Google アカウントへのアクセス権限権を与えてもいいのか？」__  
と尋ねられます。

本スクリプトを利用する場合は「許可」を選択して下さい。  

アクセス権限の付与を許可した場合は、  
画面が元に戻り、doPostTest 関数の実行が継続されます。  
特にエラーが出ず、実行ログに「お知らせ　実行完了」と表示されればOKです。 

もしもエラーが出た場合、  
「3.で置換した 'id' の指定をミスっていないか」  
「スクリプト全体を過不足なくコピペできているか」あたりを見直してみるといいかもです。

なお、doPostTest 関数の実行後、
1.でコピーしたスプレッドシートの "posted_comment" シートの「コメント」列に、  
「いいね！ 【NG】」が入力されているのは、正常な動作です。  
（checkContentTextByNGWordsList() 関数が仕事して、  
　"URLらしき文字列" を【NG】に置換した結果です）

使っていて「ちょっとこれは見たくないな…」という文字列が出てきたら、  
"NG_words_list" 上に行を追加して、単語を増やしたり書き換えたりしてみてください。 


## 手順5.  
4.で問題がなければ WebClapModoki-GAS を __Webアプリとしてデプロイ__ し、  
```
https://script.google.com/macros/s/YYY~YYY/exec  
```
形式のURLを取得してください。

__【注意】__  
デプロイの際は、下記画像の通り、  
__「アクセスできるユーザー」__ を __「全員」に変更しなければならない__ 点にご注意下さい。  
ここの設定を間違えると、SSP等「外部からのPOST」では動作しなくなってしまいます。  
（Google アカウントでのログインが必須となり、「401 Unauthorized」が返ってきます）

※また、__「新しい説明文」に「分かりやすいメモ文章」を記入__ しておくと、  
　後のセクションで触れる __「デプロイの管理」画面上で、__  
　__どれを操作すべきか区別できて分かりやすくなる__ のでおススメしておきます。

![Figure3][Fig_3]  
<p align="center"><strong>
Fig.3 デプロイ時の重要な注意点
</strong></p>

## 手順6.
5.で取得したURLを [dic_wcm.txt][dic_wcm] の中の  
```
＄WCM_URL	https://script.google.com/macros/s/YYY~YYY/exec  
```
に上書きして、ご自身のゴーストさんに実装してください。  

サンプルコード ([dic_wcm.txt][dic_wcm]) は里々での実装例ですが、  
実体はさくらスクリプト  
```
\![execute,http-POST,（WCM_URL）,--param=message_body="（送信元）;（送信内容）;（メモ）",（オプション）]  
```
の実行ですので、  
上記さくらスクリプトを呼び出せるのであれば、特にSHIORIを選ばず動かせると思います。  

__【注意】__  
現行安定版の __WebClapModoki-GAS_v9__ の仕様では、  
以下の「 ;(半角セミコロン) 区切りで、要素を３つ並べた文字列」しか受け付けないようになっています。
```
（送信元）;（送信内容）;（メモ）
```
これは、スクリプト中の  
[// ◆ 加工し終わった後の配列から、各パラメータを取り出す処理][WebClapModoki-GAS_param_ext]  
セクション内にて、  
「POSTされた文字列を ;(半角セミコロン) で区切って配列に格納する」  
「配列の範囲外へのアクセスを防ぐため、要素数が３であるか（＝上記の３要素が確実に入っているか）チェックする」
処理を行っているために生じている制限です。

…ただ、記事公開後に検証した限り、  

- __「JavaScript（Google Apps Script）では、配列の範囲外にアクセスしても大きな問題は起こらない」__
  - 単に undefined が代入されるだけで、Out of Bounds のような例外で動作が止まったりしない
  - 何なら undefined をセルに書き込みしても、単に空白セルになるだけで何のエラーも出ない
  - 列数が足りない（例えば３列しかない）場合に .appendRow メソッドで５列１行追加を行っても、エラーにならないどころか３列→５列への拡張（右側に２列足す）も自動で行ってくれる

ということが判明し、それなら  
__別に要素を３つに限定しなくても、誤動作・動作不良の心配は無いのでは？__  
という発想に至って、

```
（送信元）
（送信元）;（送信内容）
（送信元）;（送信内容）;（メモ）
（送信元）;（送信内容）;（メモ）;（追加情報１）
（送信元）;（送信内容）;（メモ）;（追加情報１）;（追加情報２）
```
の、どのパターン（要素数１～５）でも受け付けるように変更した、  
__[WebClapModoki-GAS_v10][WebClapModoki-GAS_v10]__ も公開してみました。  
動作イメージは下のGIF画像の通りです。

![Figure4][Fig_4]  
<p align="center"><strong>
Fig.4 WebClapModoki-GAS_v10の動作イメージ（要素数を変えてPOSTした時の挙動）
</strong></p>

こちらは…まだ想定入力パターンの列挙、およびその検証が不十分で、  
上手く動かない可能性もあるのですが…  
もし良ければ、お試しください。


## 手順7.  
SSP 上で実行してみて、サンプルGIF画像のように、  
ご自身のスプレッドシートの "posted_comment" シートに POST した内容が追加されれば成功です。  
お疲れ様でした！


## 使用を止めたい時は？

使い始めてから「微妙だな…もう使うの止めたい」と思った時は、  
[「Google アカウントのアクセス権の確認・削除」画面][g_perm]   
__https://myaccount.google.com/permissions__  
にアクセスして、  
「アカウントにアクセスできるアプリ」の一覧から、  
__当該スクリプトのアクセス権限を削除__ してください。  
4.で付与されたアクセス権が無くなれば、スクリプトは何もできません。

あと、ゴーストさん側の記述（dic_wcm.txt）を削除した上で、  
Google ドライブ上にある 2. の Google Apps Script のファイルの削除も行えば、  
きれいさっぱりです。

最後に、念のため 5.で取得したURLの  
```
https://script.google.com/macros/s/YYY~YYY/exec
```
に、ブラウザからアクセスしてみて下さい。  

「リクエストされたファイルは存在しません。」(404 Not Found)  
が返ってくれば、スクリプトの動作は完全に停止しています。


## Tips: Versioned Deployments の扱い方（継続して使っている内に起こりうる問題と、その "事前" 対処方法）

さて、これで使用開始＆終了のやり方の説明はおしまい…なのですが、  
もう一点、お伝えしておきたいことがございます。

それは、  
次の Fig.5 に示すような __「新規デプロイ」を繰り返した場合によく陥る状況、__  
すなわち  
__［１］「もう使う予定のない、古いWebアプリのURLが生きたままになってる…流石に邪魔になってきたぞ…」__   
__［２］「毎回URL変わるの面倒だなあ…辞書毎回書き換えないといけないの…？」__  
という __煩雑さ・面倒さへの対処・回避方法__ です。

![Figure5][Fig_5]
<p align="center"><strong>
Fig.5 新規デプロイをしながら使い続ける内に生じる問題の一つ：デプロイ時に発行されたURLが多すぎる！
</strong></p>

これは Versioned Deployments (Google さんの機械翻訳だと「バージョニングされたデプロイ」) という機能によるもので、  
例えば __「機能の異なる２つのバージョンを使い比べてみて、どっちが良いか検討する」__  
…といった際には、非常に便利な機能です。  

しかし、ゴーストさんに本スクリプトへの投稿機能を搭載して実運用する場合、  
__「ネットワーク更新された（新URLを使う）ゴーストさんと、  
　ネットワーク更新されてない（旧URLを使ったままな）ゴーストさんが混在する状態」__  
になることは…  
__容易に想像ができる（上に高確率で面倒なことになりそうな）事態__、ですよね。

実際、WebアプリのURLを配布して運用していれば、  
__［３］「実際に運用してみたらバグがあった！このまま受付続けたらおかしくなっちゃう…どうしよう…」__  
というトラブルも（あって欲しくはありませんが）十分にありうるケースですし、  
（ユーザさんへの問題発生周知＆移行確認完了を徹底しないといけなくなるので）  
__問題発生時の対応が面倒極まりないことになる__ のも、極力避けたいところ。  

大体、［２］の  
__「ちょっとスクリプト更新する度に新しいURLになる…管理も辞書更新も面倒すぎる…」__  
という煩雑さも、正直言って嫌になるポイントだと思います…。  

…前置きが長くなりましたが、  
そこで __「このバージョン管理機能を上手く使うにはどうすればいいの？」__ という疑問に対するお答え、  
__「こういう風に運用すれば楽でした」が、この節でお伝えしたいこと__ です。

（2022年12月時点での）dullNeko の対応方法は、完璧ではないかもですが…  
__上記の［１］［２］を最初から起こさない__ ようにして、  
かつ __［３］の問題発生時にも苦労せずに済む方法__ として、  
次の __［A］［B］で運用する__ やり方をおススメしておきます。

- __［A］「配布用スクリプトファイル」と「開発用スクリプトファイル」を分ける__
- __［B］『配布用スクリプトのデプロイで「新規デプロイ」を使わず、「デプロイの管理」を使う』ことで、WebアプリのURLを不変にする__

以下、順に説明していきますね。


### ［A］「配布用スクリプトファイル」と「開発用スクリプトファイル」を分ける

まず、ファイルの配置を次の Fig.6 の様に変更します。  

ポイントは、  
__「ゴーストさんの辞書に記載するURLを、公開用スクリプトのURLにする」__  
__「かつ、そのURLが不変になるよう「デプロイの管理」機能を活用する」__  
ことです。

開発用スクリプトは（ここでは一個しか示していませんが）  
何個あってもOKですし、公開用スクリプトのバックアップを作ったりしても可。  
こちらは外部に公開しないので、作業し易さ優先で管理してくださいまし。

__【注意】__  
__付与したアクセス権限は、勝手には消えない__ ので、  
（特に開発用スクリプトを何個も作って開発した場合など）  
適宜 [「Google アカウントのアクセス権の確認・削除」画面][g_perm] にて、  
こまめに __不要な権限の削除__ を行い、  
アクセス権限の整理整頓をしておくことを推奨します。


![Figure6][Fig_6]
<p align="center"><strong>
Fig.6 「配布用スクリプトファイル」と「開発用スクリプトファイル」を分けた状態
</strong></p>


### ［B］『配布用スクリプトのデプロイで「新規デプロイ」を使わず、「デプロイの管理」を使う』ことで、WebアプリのURLを不変にする

さて、お次は、  
__「デプロイの管理」を使って、  
具体的にどう作業すれば、  
WebアプリのURLを不変にできるのか__、  
をお伝えします。

ここは…文章だけだと説明が大変だったので、  
次の Fig.7 & Fig.8 に、図入りで説明を書いてみました。  

要点としては、  
「デプロイ」メニューの中にある  
「新しいデプロイ」は __使わず__ に、   
__「デプロイを管理」の方を使う__ こと、

__前にデプロイした（固定したいURLの）ものを指定__ して、  
__「編集」→「新バージョン」__ を選び、  
__ウェブアプリのURLが、前と同じであることを確認__ した上で、  
__デプロイを実行する__ こと、です。

こうすることで、  
__最初に一回だけ「新しいデプロイ」を行って発行したURLを、ずっと使い続ける__  
ことができます。

![Figure7][Fig_7]
<p align="center"><strong>
Fig.7 「デプロイの更新」の仕方（１／２）
</strong></p>

![Figure8][Fig_8]
<p align="center"><strong>
Fig.8 「デプロイの更新」の仕方（２／２）
</strong></p>

---

その結果、実際の運用としては、  
Fig.9 の図のような形になります。


![Figure9][Fig_9]
<p align="center"><strong>
Fig.9 実運用時のイメージ
</strong></p>


こうすることで、

- __［１］「もう使う予定のない、古いWebアプリのURLが生きたままになってる…流石に邪魔になってきたぞ…」__
- __［２］「毎回URL変わるの面倒だなあ…辞書毎回書き換えないといけないの…？」__  

は __「そもそも起こらない」__ ようになりますし、

- __［３］「実際に運用してみたらバグがあった！このまま受付続けたらおかしくなっちゃう…どうしよう…」__  

などの問題発生時も、  
落ち着いてバグを修正して  
（あるいは、バックアップしておいた古いコードをコピペで上書きして）  
Fig.9 で言えば… __「デプロイを管理」から、同じ手順でバージョン３を更新すればよいだけ__ になります。

（例えば「v9 へのロールバック」、「v10 バグ修正」あたりの説明を書き、  
　「デプロイを管理」から「編集」→「新バージョン」→「デプロイ」すればOK）

これで、  
__ゴーストさん側の記述を一切触ることなく  
（＝ネットワーク更新を促したりすることなく）、  
デべさん側の作業だけで、修正が可能に__ なります。

※なお、アーカイブされたデプロイを復帰させる方法は×でした。  
　（URLが変わってしまいました）


### 補足情報：参考にしたWebサイト・ページ

上記手順の参考にしたページを、次に示します。  
有益な記事を公開して下さっている先人に感謝です…。

■ GASのWebアプリでURLを変えずに新バージョンを公開する（新エディタ） - make it easy  
https://ryjkmr.com/gas-web-app-deploy-new-same-url/  
■ GoogleAppsScriptの新しいエディタで更新デプロイする方法  
https://ymt43.com/gas-new-editor-deploy/  

なお、Versioned Deployment に関する Google 公式の案内・説明は  
[Deployment を作成して管理する](https://developers.google.com/apps-script/concepts/deployments)  
にあります。  

※本セクションの説明（対処方法の例）は、あくまで  
　2022年12月 時点での dullNeko の検証結果に基づくものです。  

　今後 Google さん側で仕様変更があった場合など、  
　ここに記載した方法が通用しなくなる可能性もございます。  
　この点は、どうかご了承頂ければ幸いです。


# 連絡先

Pull Requests や Issues にコメントを投げて頂くのが、本来の運用方法…だと思うのですが、  
「dullNeko が GitHub に不慣れで、使い方を理解できてない」状態なのと、  
「GitHub アカウントを持ってない方もいらっしゃるはず…」と思ったので、  
↓の Google フォームを用意してみました。お気軽にどうぞ。

https://docs.google.com/forms/d/e/1FAIpQLSflhEpY-kmYyDT87xbUyB0sqA88rkK9oxrXjGw0W2EcDHIg6g/viewform?usp=sf_link

~~ぶっちゃけこのスクリプト使うより Google フォームと Google スプレッドシートの連携の方が手軽で早いし十分なのでは？と思ったのはひみつ~~  
い、一応「どこからでも画面遷移なしで使える」のと「受け取った時点での処理ができる」所は勝ってる…はずなので…（震え声）

あ、  
[Twitter](https://twitter.com/dullNeko) と [Mastodon（うかどん）](https://ukadon.shillest.net/@dullNeko) にもおりますので、  
そちらでお声がけ頂いても大丈夫です。


# ライセンスおよび免責事項

本スクリプト [WebClapModoki-GAS.txt][WebClapModoki-GAS] は NYSL Version 0.9982 に従います。  
ライセンス全文は [LICENSE.md][LICENSE] に示しております。


# 謝辞

- だんでぃ こと りょうすけ氏（オリジナルの「Web拍手」作者様）

[だんでぃ こと りょうすけ氏](https://twitter.com/webclap_dandy) が、Web拍手というアイデアを実装し、公開されていなければ、  
本スクリプトを書くどころか思いつくこともなかったと思います。  
個人Webサイトを持ってた時代はお世話になりました…。  
先人に敬意と感謝を。

- 伺か界隈の皆さま

数々の魅力的なゴーストさん達が公開されていなければ、  
ゴーストさんに、Web拍手経由で気軽に感想を送信できる仕組みが実装された例を見ていなければ、  
[2022年度の伺的アドカレー（伺的 Advent Calendar 2022 - Adventar）][uka_adcurry2022] が開催されておらず、他の方々の記事を読んで刺激を受けていなければ、  
また、 [ぽなさんのトゥート](https://ukadon.shillest.net/@ponapalt/109520146570230914) で背中を押して頂いていなければ、  
本記事を公開することはありませんでした。

ユーザ歴ばかり長い新参者ですが、今後とも何卒よろしくお願い申し上げます…。


# 最後に

こんな長文乱筆の記事を最後までお読み下さり、ありがとうございます…。  
改めて、心より感謝申し上げます。

…あくまで dullNeko 個人の思想ですが、  
```
「記事」や「プログラムコード」も「表現媒体」の一つ、
　そのお方が、この世界をどう捉え、どのようなモノの見方をして、
　どんな "カタチ" が良いもの・好ましいもの・大切なもの・理想と考えておられるのか、  
　如実に物語る創作物だ
```
と感じる勢なので、  

今回、伺的 Advent Calendar 2022 で皆様の記事を拝読し、  
各々方の観点・考え方、意見・失敗談・創作物の数々に触れることができて、  
大変幸せな時間を過ごせました。  

…ところで皆様、  
伺的 Advent Calendar 2022 延長戦ハッシュタグこと、  
[#uka_advent_2022][uka_adcurry2022_extended] はご存じでしょうか？  
既に [古閑未善さんが23日に発表された記事](https://kogami.sakura.ne.jp/uka_adv_2022.html) もございます。  

語りたいこと、 これからやってみたいこと、やってみたこと、やらかしたこと…などなど、  
こういう "機会" がなければ、中々 "自分の外" に出せないこと、多いなあ…  
などと、この記事を書き終わった今、ぼんやり感じております。  
（上でも書きましたが、自分が記事を書いて公開する側になるとは思っていませんでしたし）

もし、本記事を読んで下さった貴方様が、  
何か "自分の外" に出してみたいものをお持ちであるのなら…  
[#uka_advent_2022][uka_adcurry2022_extended] という機会をお借りして、  
記事の形で出してみると、きっと良い経験になりますよ…と、  
お誘いの言葉を投げて、本記事の締めとさせて頂きます。
