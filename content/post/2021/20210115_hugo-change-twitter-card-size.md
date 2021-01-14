---
title: HugoのTwitterカードサイズを変更する
summary: ""
description: ""
date: 2021-01-15 02:00:00 +0900 JST
categories: "Hugo"
tags: ["Hugo", "Twitter"]
slug: hugo-change-twitter-card-size
archives:
    - 2021
    - 2021-01
    - 2021-01-15
draft: false
---

ブログをHugoに移行したわけですが、何も設定しないとTwitterシェアした際のカードに画像が載りません。これは設定ファイルあるいは個別のポストで画像を指定すれば自動的に反映されます。ところが、その際のTwitterカードのサイズが`summary_large_image`固定です。これも設定できた方がいいと思うんですが、issueとか検索しても特に起票された形跡がないので誰も困ってないってことなんでしょうかね？で、このサイズのカードはちょっと主張が強いので`summary`を使いたいです。

<iframe class="hatenablogcard" style="width:100%;" frameborder="0" scrolling="no" src="https://hatenablog-parts.com/embed?url=https://developer.twitter.com/ja/docs/tweets/optimize-with-cards/guides/getting-started"></iframe>

このサイトはHugoのテーマとして[Gohugo Theme Ananke](https://themes.gohugo.io/gohugo-theme-ananke/)を使用しています。このテーマではTwitterカードのテンプレートはHugoが提供しているものを使っています。他のテーマは調べていないですが、大体のテーマは同様なのではないでしょうか。

<iframe class="hatenablogcard" style="width:100%;" frameborder="0" scrolling="no" src="https://hatenablog-parts.com/embed?url=https://gohugo.io/templates/internal/"></iframe>

で、残念ながらこのinternalなテンプレートは上書きできません（少なくとも調べても情報はでてきませんでした）。そのためカードを`summary`にするのは少し手間がかかります。そんわけで、このエントリではその手順を紹介します。

## 画像の指定

まずはカードに表示される画像ですが、上記のドキュメントを参照してもらうと設定方法が書かれています。一番手っ取り早いのは`config.toml`に設定することでしょう。

```toml
[params]
  images = ["site-feature-image.jpg"]
```

実際には使用したい画像を`static`ディレクトリに配置してそのパスを指定すればOKです。

## テンプレートファイルとパーシャルファイルを用意する

画像を指定しただけですとカードが`summary_large_image`になってしまいますので、これを変更していきます。やるべきことは次の2つです。

1. internalテンプレートをコピーしてきて編集する
2. テーマのtwitter_cardsを読み込んでいるテンプレートを上書きする

[internalテンプレート](https://github.com/gohugoio/hugo/blob/master/tpl/tplimpl/embedded/templates/twitter_cards.html)をまずはコピーしてきます。コピー先は`layouts/partials/twitter_cards.html`としました。`content=summary_large_image`となっている箇所が3箇所ありますので、すべて`content=summary`に変更します。

次にテンプレートですが、anankeの場合は`{ananke_root}/layouts/_default/baseof.html`が該当のファイルでした。このファイルを`layouts/_default/baseof.html`としてコピーします。コピーできたら読み込み箇所を変更しましょう。

```go
{{- template "_internal/twitter_cards.html" . -}}
```

を

```go
{{- partial "twitter_cards.html" . -}}
```

に書き換えます。

作業は以上です。実際に確認してみてください。

## まとめ

設定ファイルでカードの指定ができれば早かったのですが、残念ながらその機能はありませんでした。とはいえHugoはテンプレートの上書きが簡単にできるため、少しの手間で対応できました。カードでけぇ！とお困りの方は試してみてください。
