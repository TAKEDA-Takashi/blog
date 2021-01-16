---
title: Google AdSenseに備え、ドメインを取得してはてなブログProにしてみた
summary: ""
description: ""
toc: true
date: 2017-12-06 23:30:00 +0900 JST
categories: ""
tags: ["Google AdSense"]
slug: hatena-blog-plan-to-pro
archives:
    - 2017
    - 2017-12
    - 2017-12-06
draft: false
---

連日飲み会で更新できていませんでした。飲み会では、前職の人に会ったり、ベルリンで働いている人に会ったりしました。

さて今日は、`Google AdSense`というのを使ってみたかったので、そのために必要なことをやっていました。

AdSenseは使いたいといって使えるものではなく、申請して審査に通過しないと利用できません。

本当についさっき申請をしたので、現在審査待ちというステータスになっています。

## はてなブログでAdSenseを申請するために最低限必要なこと

**申請をする** ことと、**申請を通過する** ことは分けて考えます。

申請をするだけであれば、本当に必要なのは次の1点だけです。

1.  独自ドメインでサイトを運営していること

では、はてなブログで独自ドメインを設定するためにはどうすればよいのでしょうか。実は無料版では独自ドメインは設定できず、**はてなブログ Pro** にアップグレードする必要があります。

Proは月額600円〜となっていますが、30日間は無料のお試し期間があります。`〜`となっているのは、プランが3種類用意されており、2年コースが一番お得で600円/月という料金設定になっているためです。詳細は[公式のドキュメント](http://hatenablog.com/guide/pro)をどうぞ。

というわけで、申請に必要な作業は次の3点ということになります。

1.  独自ドメインの取得
2.  はてなブログProにアップグレード
3.  はてなブログを独自ドメインで運営できるように設定する

### 独自ドメインの取得

今回は[お名前.com](https://www.onamae.com/)を利用して、ドメインを取得しました。

`.tech`が1年目30円で「おおっ！？」と思ったんですが、2年目からは普通に4980円かかるため、コスパのよい`.com`にしました。とりあえず1年で。

ドメイン取得がまったくはじめてという方は、次の記事などを参考にしてください。

<iframe class="hatenablogcard" style="width:100%;" frameborder="0" scrolling="no" src="https://hatenablog-parts.com/embed?url=https://jisedai-lab.com/onamae-com-original-domain/"></iframe>

### はてなブログProにアップグレード

ブログのダッシュボードにアクセスすると、サイドバーの一番下に30日間無料のリンクが見つかります（時期によって表示のさせ方は変わっているかも）。

<img src="/images/20171206/20171206_hatena-blog-plan-to-pro_01.png" style="height: 500px; width: auto;">

とりあえず最初ということもあるため、ドメインと同じ1年間のコースにしてみました。

### はてなブログを独自ドメインで運営できるように設定する

最後に、お名前.comとはてなブログ、それぞれに設定をします。

お名前.comには`hatenablog.com`の`CNAME`レコードの作成。はてなブログには取得した独自ドメインの設定を行います。

次のブログの **お名前.comでの設定** 以降の説明が、画面キャプチャ付きでわかりやすかったです。

<iframe class="hatenablogcard" style="width:100%;" frameborder="0" scrolling="no" src="https://hatenablog-parts.com/embed?url=https://kototoka.com/entry/2014/07/22/Setting-hatena-own-blog-domain/"></iframe>

## AdSenseに申請

ここまでの作業が完了したら、申請はもうすぐそこです。

具体的には次の2点の作業を行います。

1.  [AdSenseのサイト](https://www.google.co.jp/adsense/start/#/?modal_active=none)で申し込む（アカウントを作成する）
2.  サイトにスクリプトを埋め込む

AdSenseの申し込み手順を解説しているサイトはいろいろと出てきたんですが、割と変更が多いようで、古い情報が多かった印象です。

その中でも現在の実態にそった内容として、次のブログが参考になりました。

<iframe class="hatenablogcard" style="width:100%;" frameborder="0" scrolling="no" src="https://hatenablog-parts.com/embed?url=https://www.tabi-lion.net/entry/adsense-sinsei"></iframe>

ただ、これもすぐに古い情報になってしまう可能性がありますので、注意が必要です。

このブログの方はライブドアブログを使っているので、はてなブログとは若干違いがあります。

![image2](/images/20171206/20171206_hatena-blog-plan-to-pro_02.png)

はてなブログの場合は、ダッシュボードから [設定] > [詳細設定] と進み。

![image3](/images/20171206/20171206_hatena-blog-plan-to-pro_03.png)

`headに要素を追加`のテキストエリアにスクリプトを貼り付けます。

あとは参考記事の通り、「サイトにコードを貼り付けました」のチェックを入れ、残りの作業を済ませれば終了です。

![image4](/images/20171206/20171206_hatena-blog-plan-to-pro_04.png)

あとは待つだけ！

## 最後に

ということで、ドメイン取得からAdSenseの申し込みまでやってみました。

一発で審査が通るかまったくわかりませんが、ダメならダメで改善して再申請していく所存です。

実際には申請を通りやすくするためにいくつかやったことなどがありますが、それはまた別の機会に書いていきます。

それでは、おやすみなさい。
