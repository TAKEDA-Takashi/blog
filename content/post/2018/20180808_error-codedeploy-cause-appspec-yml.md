---
title: appspec.ymlが原因でCodeDeployがエラーになって失敗した
summary: ""
description: ""
date: 2018-08-08 01:15:00 +0900 JST
categories: "AWS"
tags: ["AWS", "AWS CodeDeploy"]
slug: error-codedeploy-cause-appspec-yml
archives:
    - 2018
    - 2018-08
    - 2018-08-08
draft: false
---

こんにちは、お久しぶりです。最近CloudFormationやCodeDeployを触っているんですが、その中で大分ハマった現象を紹介します。

## appspec.ymlが原因？

CodeDeploy用に次のような`appspec.yml`を作りました。ベースはネットからコピってきて、`hooks`やコメントなどを取り除いたものです。

```yaml
version: 0.0
os: windows
files:
  – source: app
    destination: c:\temp
```

この`appspec.yml`をディレクトリのルートに置き、`aws deploy push`して`aws deploy create-deployment`しました。そうすると次のようなエラーが吐かれてデプロイが失敗します。

```
(<unknown>): mapping values are not allowed in this context at line 5 column 16
```

はてさて、一体何がいけないんでしょうか？

そうですね、悪いのは4行目ですね。これを次のように直すと無事にデプロイできるようになりました。


```yaml
version: 0.0
os: windows
files:
  - source: app
    destination: c:\temp
```

## 結局原因はなんだったのか

原因は4行目の`–`が正しくありませんでした。これは **ダッシュであってハイフンではありません** 。どういうことかというと、これは[U+2013（UTF-8だとe28093）](https://www.fileformat.info/info/unicode/char/2013/index.htm)のエムダッシュという記号なんです。正しくは[U+002D](https://www.fileformat.info/info/unicode/char/2d/index.htm)のハイフンマイナスを使う必要があります。

どうやらコピーした際にダッシュとしてコピーしてしまい、それが原因でYAMLとして正しくないということでエラーになっていたようでした。

**そんなんわかるか！**

とは言え、「あれ、なんかこのハイフン（エディタ上での）表示おかしくね？」と疑問に思ったのがきっかけなので、気づけるもんですね。大分かかりましたが。

## 最後に

多分YAMLのシンタックスハイライトのあるエディタを使えばもっと早く気づけたと思うので、そういうの使いましょう。
