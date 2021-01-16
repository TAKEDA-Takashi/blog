---
title: はてなブログでTwitterアカウントへのリンクと画像サイズの指定をする
summary: ""
description: ""
toc: true
date: 2018-01-05 00:00:00 +0900 JST
categories: "Tips"
tags: []
slug: hatena-blog-twitter-link-image-size
archives:
    - 2018
    - 2018-01
    - 2018-01-05
draft: false
---

新年明けましておめでとうございます。今年も一年、良い年となるよう頑張っていきたいと思います。

年末年始はAWSの各サービスを調べて、自分なりにまとめて消化していました。これについては会社のブログで近々公開予定です。

あんまり期間が空いてしまうと書くモチベーションも下がってしまうので、はてなブログで記事を書く中で調べたTipsを2つばかり紹介します。

なお編集モードは **Markdown** で確認しています（他のモードは未検証）。

## Twitterアカウントへのリンク
はてなブログでは、はてなダイアリーと共通の **はてな記法** が使用できます。どうやらマニュアルからは消えているようですが、次の記法が使用できます。

```
[twitter:@ユーザー名]
```

使用例は次のようになります。

```
[twitter:@2017takeda]
```

<iframe class="hatenablogcard" style="width:100%;" frameborder="0" scrolling="no" src="https://hatenablog-parts.com/embed?url=https://taityo-diary.hatenablog.jp/entry/2017/09/17/225555"></iframe>

## 画像サイズの指定
こちらもはてな記法で対応できます。

- 横幅指定（例として100px）

```
[f:id:tkd2017:20181234567890p:plain:w100]
```

- 高さ指定（例として100px）

```
[f:id:tkd2017:20181234567890p:plain:h100]
```

[はてなブログ ヘルプ](https://help.hatenablog.com/)

## まとめ
基本的にMarkdownで記述できるため書きやすいですよね。

またはてな記法も併用することで、HTMLタグを直接使わずに書くことができます。

今後も新しいTipsを見つけたら紹介していきたいと思います。
