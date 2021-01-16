---
title: はてなブログにGoogle AnalyticsとGoogle Search Consoleを導入してみた
summary: ""
description: ""
toc: true
date: 2017-12-03 18:10:00 +0900 JST
categories: ""
tags: ["Google Analytics", "Google Search Console"]
slug: hatena-blog-add-google-analytics-and-search-console
archives:
    - 2017
    - 2017-12
    - 2017-12-03
draft: false
---

以前Bloggerを少し触ってたことがあるんですが、そのときは特に設定をしなても各ページビューや流入キーワードなどが確認できました。

はてなブログにも **アクセス解析** という機能がありますが、シンプルな機能となっており、詳細は確認できません。

というわけで、みんなどうしているのかな？ と探してみたところ、サイト内のアクティビティ分析に`Google Analytics`、サイトへの流入分析に`Google Search Console`を使うのが王道のようです。ちなみに`Search Console`は、以前はWebマスターツールと呼ばれていたそうです。

## Google Analyticsの導入

はてなブログと`Analytics`はともにユーザーが多いので、探せばいろいろ情報が出てきますね。

今回は次の記事を参考にさせていただきました。

<iframe class="hatenablogcard" style="width:100%;" frameborder="0" scrolling="no" src="https://hatenablog-parts.com/embed?url=http://memobiz.net/how-to-setting-analytics"></iframe>

「ステップ4：正確なアクセス解析のためのフィルター設定」の補足をしておきます。

IPアドレスを調べて除外設定をしているわけですが、ここで設定しているのはいわゆる **グローバルIPアドレス** というもので、PC一台一台に設定されているものとは異なります。この **グローバルIPアドレス** はどこに付与されているのかといえば、一般家庭であれば **ブロードバンドルータ** になります。

そのため調べる環境によって変化しますし、場合によっては自宅のアドレスが変化することもあり、その場合は再設定が必要なので注意しましょう。

## Google Search Consoleの導入

`Search Console`の導入については、次の記事を参考にさせていただきました。

<iframe class="hatenablogcard" style="width:100%;" frameborder="0" scrolling="no" src="https://hatenablog-parts.com/embed?url=https://www.heymilelab.com/entry/google-search-console-hatena"></iframe>

参考にする中で一ヵ所だけミスがあったので補足しておきます。

> ブログURLの後に「 sitemap_index_xml 」を入力して、「送信」をクリック。

と紹介されていますが、実際に入力するのは`sitemap_index.xml`です（スクショでは`.xml`になっている）。

/// 2017/12/09追記 ///

どうやら`sitemap_index.xml`だけでなく、`sitemap.xml`も登録するとよいようです。

<iframe class="hatenablogcard" style="width:100%;" frameborder="0" scrolling="no" src="https://hatenablog-parts.com/embed?url=http://www.okigaru-migaru.net/entry/hatenablof-sitemap-url"></iframe>

/// 追記ここまで///

## AnalyticsとSearch Consoleの連携

2つのツールの初期設定ができたので、最後に連携設定をします。ツールの連携も次の記事を参考にすることで、簡単にできました。

<iframe class="hatenablogcard" style="width:100%;" frameborder="0" scrolling="no" src="https://hatenablog-parts.com/embed?url=https://wacul-ai.com/blog/access-analysis/google-analytics-setting/googleanalytics-searchconsole/"></iframe>

## まとめ

以上、はじめて導入してみましたが、解説記事も多いためそれらを参考にすることで思ったより簡単に導入できました。

まだ導入していない方は導入してみてはいかがでしょうか。
