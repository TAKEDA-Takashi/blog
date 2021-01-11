---
title: はてなブログの記事内の外部リンクにtarget="_blank"を自動で追加する
summary: ""
description: ""
date: 2017-11-29 03:00:00 +0900 JST
categories: "Tips"
tags: ["HTML", "JavaScript"]
slug: hatena-blog-link-auto-target-brank
archives:
    - 2017
    - 2017-11
    - 2017-11-29
draft: false
---

はてなブログを始めたはいいのですが、外部リンクを別タブを開かせる方法が分からず調べていました。

一番単純な方法は`<a href="" target="_blank"></a>`を使う方法ですが、せっかくMarkdownで書いているのに残念感が漂います。

で、調べてみるとやはり同じ問題に突き当たっている方は多くおり、解決方法も紹介されてました。

- [markdown記法でリンクをtarget="_blank"にする - エンジニアをリングする](http://yoshiko.hatenablog.jp/entry/2014/02/27/markdown%E8%A8%98%E6%B3%95%E3%81%A7%E3%83%AA%E3%83%B3%E3%82%AF%E3%82%92target%3D%22_blank%22%E3%81%AB%E3%81%99%E3%82%8B)
- [はてなブログでMarkdown記法の時にリンクにtarget="_blank"を付加する方法 - ひびきあい。](http://step-it-up.hatenablog.com/entry/markdown-link-taget_blank)
- [はてなブログで「はてな記法」「markdown記法」のどちらも別窓リンクを設定する方法](https://yousayblog.com/hatena_blank_set/)

毎年誰かしら書いてるんですねw

で、参照先の記事を見れば解決できるんですが、スクリプトが若干古い感じがするので、今バージョンを残しておきます。

```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
<script>
$(function() {
    $('a[href^="http"]:not([href*="' + location.hostname + '"])').attr('target', '_blank').attr('rel', 'noopener noreferrer');
})
</script>
```

これを`設定 > 詳細設定 > headに要素を追加`にコピペすれば、外部リンクが別タブで開かれるようになります。

主な変更点。

- jQueryのバージョンを上げた
- `rel="noopener noreferrer"`も付与されるようにした

ぜひお試しあれ。
