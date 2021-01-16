---
title: はてなブログ内の外部リンクにつけるアイコンを制御する
summary: ""
description: ""
toc: true
date: 2017-12-23 13:00:00 +0900 JST
categories: "Tips"
tags: ["HTML", "JavaScript"]
slug: hatena-blog-control-icon-external-link
archives:
    - 2017
    - 2017-12
    - 2017-12-23
draft: false
---

何度も更新しては記事にしていますが、前回はこんなことをしていました。

{{< inner_ref 20171214_hatena-blog-icon-using-font-awesome.md >}}

これで外部リンクは別タブで開き、さらにアイコン付与ができたわけですが、プロフィール画面がこうなっていました。

<img src="/images/20171223/20171223_hatena-blog-control-icon-external-link_01.png" style="height: auto; width: 500px;">

うーん、これはちょっとアレですね。

というわけで、外部リンクであっても画像の場合はアイコンを付与しないようにします。

## 構造の確認
ChromeのDevToolsを使って確認してみます。

<img src="/images/20171223/20171223_hatena-blog-control-icon-external-link_02.png" style="height: auto; width: 400px;">

aタグの子要素としてimgタグがあります。つまりアイコンを付与するのは **外部リンクのaタグ かつ 子にimgタグをもたない** ということになります。

これはCSSでは難しい（というかできない？）のですが、jQueryでは簡単に実現できます。

## 設定変更
設定は毎度お馴染み、詳細設定の headに要素を追加 です。今回修正されたコードは次のようになりました。

```html
<script defer src="https://use.fontawesome.com/releases/v5.0.1/js/all.js"></script>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
<script>
$(function() {
    $('a[href^="http"]:not([href*="' + location.hostname + '"])').attr('target', '_blank').attr('rel', 'noopener noreferrer')
      .not(':has(img)').append('<i class="fas fa-external-link-alt" style="margin-left: 3px"></i>');
})
</script>
```

`$el.not(':has(img)')`によって、`$el`のうち、子要素にimgタグをもたない要素のみを対象に操作をすることができます。

結果は次のようになりました。

<img src="/images/20171223/20171223_hatena-blog-control-icon-external-link_03.png" style="height: auto; width: 500px;">

## まとめ
最近のフロント開発ではAngularやReactにおされjQueryの出番は減ってきていますが、こういうちょっとした操作にはとても便利ですね。
