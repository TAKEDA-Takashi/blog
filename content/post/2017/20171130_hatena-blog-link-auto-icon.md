---
title: はてなブログ内の記事にある外部リンクにアイコンをつけよう 〜ついでに自動リンクもなくす〜
summary: ""
description: ""
toc: true
date: 2017-11-30 02:45:00 +0900 JST
categories: "Tips"
tags: ["HTML", "JavaScript"]
slug: hatena-blog-link-auto-icon
archives:
    - 2017
    - 2017-11
    - 2017-11-30
draft: false
---

昨日こんな記事を書きました。

{{< inner_ref 20171129_hatena-blog-link-auto-target-brank.md >}}

外部リンクは別タブで開くようにしたわけですね。

ところで、いろんなサイトを見ていると外部リンクには別タブで開かれると分かるようなアイコンが表示されているものも多く見られます。

視覚的にわかりやすくなるのはよいことですね。というわけでやってみました。

## アイコンが表示されるようにする

大方針としてJavaScriptでやる方法とCSSでやる方法があります。少し考えて、`_blank`を設定するJavaScriptを修正すればすぐに実現できそうだったのでJavaScriptでやることにしました。

まずはアイコンを入手しましょう。自分で書いてもよいですし、出来合いのものをダウンロードしてもよいですね。ただしライセンスには気をつけましょう。今回は[100 External Link Icons (PNG, PSD) | Vector Icons](http://www.shapes4free.com/vector-icons/external-link-icons/)さんからいただきました。

Zipファイルがダウンロードされるので、その中から使いたいアイコンを探して画像ホスティングサービスにアップロードします。アップロード先はどこでもよいですが、今回は[はてなフォトライフ - 無料・大容量、写真を共有できるウェブアルバム](http://f.hatena.ne.jp/)にアップロードしました。

アップロードできたら画像のリンクを調べてメモしておきます。

![image1](/images/20171130/20171130_hatena-blog-link-auto-icon_01.png)

画像のURLがメモできたら、前回の記事で追加した **headに要素を追加** のソースコードを修正します。

====

```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
<script>
$(function() {
    $('a[href^="http"]:not([href*="' + location.hostname + '"])').attr('target', '_blank').attr('rel', 'noopener noreferrer')
        .append('<img src="http://img.f.hatena.ne.jp/images/fotolife/t/tkd2017/20171129/20171129234426.png" style="margin-left: 3px">');
})
</script>
```

`http://img.f.hatena.ne.jp/images/fotolife/t/tkd2017/20171129/20171129234426.png`のURLは、 **先ほどメモした自分の画像のURL** に変えてください。

これで記事内の外部リンクにすべてアイコンが表示されるようになりました。

## キーワードの自動リンクが邪魔

これで一安心と思いきや問題が発生しました。

実際にやってもらうとわかりますが、記事内の **キーワードリンクすべてに** アイコンが表示されます。これはとてつもなく嫌だったのでなんとかしたいと調べました。

そうするとやはり同じ問題にあたっている人は多くいて、提示されている解決策は主に次の3つでした。

1.  はてなブログProを契約する
2.  CSSで非表示にする
3.  自動リンク停止記法を使う

1は課金が発生するので最後の手段かなと。

2は本質的な解決にはなっていないので却下。

3はブログ書くのが嫌になりそうなので却下。

というわけで何か別の方法を考えないといけなさそうです。ところで、2のときに「本質的な解決」と言いましたが、どういうことでしょう？

キーワードの自動リンクというのは、HTMLレベルでいえば要は`aタグ`なわけですね。ということは、`aタグ`を除去してプレーンテキストにできれば解決になるのではないでしょうか。

ということで、これもjQueryの力を借りれば解決できそうなのでやってみました。

先ほどの **headに要素を追加** のソースコードをさらに修正します。

```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
<script>
$(function() {
    $('a.keyword').replaceWith(function() {
        var $this = $(this);
        $this.replaceWith($this.text());
    });
    $('a[href^="http"]:not([href*="' + location.hostname + '"])').attr('target', '_blank').attr('rel', 'noopener noreferrer')
        .append('<img src="http://img.f.hatena.ne.jp/images/fotolife/t/tkd2017/20171129/20171129234426.png" style="margin-left: 3px">');
})
</script>
```

はい、これで、ひと仕事おしまい。
