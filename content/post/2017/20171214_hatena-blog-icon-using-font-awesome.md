---
title: はてなブログ内の外部リンクのアイコンにFont Awesomeを使ってみた
summary: ""
description: ""
toc: true
date: 2017-12-14 01:00:00 +0900 JST
categories: "Tips"
tags: ["Font Awesome"]
slug: hatena-blog-icon-using-font-awesome
archives:
    - 2017
    - 2017-12
    - 2017-12-14
draft: false
---

以前、外部リンクにアイコンをつける記事を書きました。

{{< inner_ref 20171130_hatena-blog-link-auto-icon.md >}}

このときはフリーのアイコンを見つけて、それを利用しました。最近アイコンフォント＆CSSフレームワークである、Font Awesomeというものを知ったのでこちらに切り替えてみました。

[Font Awesome](https://fontawesome.com/)

Font Awesomeは現在5.0.1が最新版となっています。Free版とPro版があり、Pro版は$60で永続ライセンスが付与されるようです。1200以上のアイコンが追加で使用できるようですので、プロダクトなどで使いたい場合はそちらも検討するとよさそうですね。

## Font Awesomeの読み込み方法
使い方は大きく分けて2つあり、JavaScriptを読み込む方法と、CSSを読み込む方法があります。推奨はJavaScriptで読み込む方法ですので、今回はこちらの方法を使用します。

次に読み込む方法も2種類用意されており、CDNを利用する方法と、Downloadして自分のサイトにアップする方法があります。推奨はCDNですので、今回はCDNを利用します。

まとめます。

1. JavaScriptを、CDNを利用して読み込む（最も推奨）
2. JavaScriptを、自サイトにアップして読み込む
3. CSSを、CDNを利用して読み込む
4. CSSを、自サイトにアップして読み込む

はてなブログで利用する場合は、1の方法が簡単に導入できます（手間としては3も同じですが）。

## アイコンの探し方
アイコンは、公式サイトの **Icons** メニューをクリックすることで検索できます。

![image1](/images/20171214/20171214_hatena-blog-icon-using-font-awesome_01.png)

アイコン一覧が表示されます。2177種類のアイコンがありますが、Pro版のも含まれています。Free版のみに絞り込んでみましょう。サイドメニューの「Free」をクリックすることで絞り込みができます。

![image2](/images/20171214/20171214_hatena-blog-icon-using-font-awesome_02.png)

Free版のみとなりました。899種類のアイコンが使えるようです。次に外部リンクのアイコンを検索してみます。サーチバーに **external** と入力してみます。

![image3](/images/20171214/20171214_hatena-blog-icon-using-font-awesome_03.png)

external-linkは2種類あるみたいですね。今回は右側の「external-link-alt」気に入ったのでクリックします。

![image4](/images/20171214/20171214_hatena-blog-icon-using-font-awesome_04.png)

アイコンの詳細画面に移りました。左下にあるタグをコピーして貼り付けるだけで、このアイコンを表示させることができます。

## はてなブログで利用
以上を踏まえて、はてなブログに設定をします。

設定は毎度お馴染み、詳細設定の **headに要素を追加** です。今回は、次のようなコードとなりました。

```html
<script defer src="https://use.fontawesome.com/releases/v5.0.1/js/all.js"></script>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
<script>
$(function() {
    $('a[href^="http"]:not([href*="' + location.hostname + '"])').attr('target', '_blank').attr('rel', 'noopener noreferrer')
        .append('<i class="fas fa-external-link-alt" style="margin-left: 3px"></i>');
})
</script>
```

確認してみます。

![image5](/images/20171214/20171214_hatena-blog-icon-using-font-awesome_05.png)

おお、よい感じですね！

## まとめ
というわけで、フロント界隈では有名だと思われるFont Awesomeを使ってみました。

ブログでアイコンを使う機会はそう多くないですが、サイト作成などではすごく助かりますね。

今後もお世話になります。ではでは。
