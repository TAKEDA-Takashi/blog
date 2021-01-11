---
title: Vagrantで起動したCentOS 7に日本語ロケールがない問題
summary: ""
description: ""
date: 2017-12-25 01:40:00 +0900 JST
categories: "Linux"
tags: ["Linux", "Vagrant", "CentOS"]
slug: run-vagrant-centos7-not-found-ja-locale
archives:
    - 2017
    - 2017-12
    - 2017-12-25
draft: false
---

便利ですよね、Vagrant。使ってますか？ 先日、起動したVMに日本語ロケールがなかったので、その対処法を紹介します。

## 環境
今回の環境は次のようになっています。

Vagrantに限らず、同様の問題が発生した場合は、同じ解決方法が使えるはずです。

```shell
$ vbox-img --version
5.2.2r119230

$ vagrant --version
Vagrant 2.0.1

$ vagrant box list
centos/7         (virtualbox, 1710.01)
```

## 問題の再現
次のコマンドを実行することで問題の再現が可能です。

```shell
$ vagrant init centos/7

$ vagrant up && vagrant ssh

[vagrant@localhost ~]$ locale
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=ja_JP.UTF-8
LC_CTYPE="ja_JP.UTF-8"
LC_NUMERIC="ja_JP.UTF-8"
LC_TIME="ja_JP.UTF-8"
LC_COLLATE="ja_JP.UTF-8"
LC_MONETARY="ja_JP.UTF-8"
LC_MESSAGES="ja_JP.UTF-8"
LC_PAPER="ja_JP.UTF-8"
LC_NAME="ja_JP.UTF-8"
LC_ADDRESS="ja_JP.UTF-8"
LC_TELEPHONE="ja_JP.UTF-8"
LC_MEASUREMENT="ja_JP.UTF-8"
LC_IDENTIFICATION="ja_JP.UTF-8"
LC_ALL=
```

`locale: Cannot set LC_XXX to default locale: No such file or directory`というメッセージが表示されています。

`localectl`コマンドを利用することで、ロケールがないことを確認できます。

```shell
$ localectl list-locales | grep '^ja'
```

## 解決方法
本来ならすべてのロケールが入っているはずですが、何らかの理由で見つからない場合、再インストールすればよいようです。

```shell
[vagrant@localhost ~]$ sudo yum reinstall -y glibc glibc-common

[vagrant@localhost ~]$ locale
LANG=ja_JP.UTF-8
LC_CTYPE="ja_JP.UTF-8"
LC_NUMERIC="ja_JP.UTF-8"
LC_TIME="ja_JP.UTF-8"
LC_COLLATE="ja_JP.UTF-8"
LC_MONETARY="ja_JP.UTF-8"
LC_MESSAGES="ja_JP.UTF-8"
LC_PAPER="ja_JP.UTF-8"
LC_NAME="ja_JP.UTF-8"
LC_ADDRESS="ja_JP.UTF-8"
LC_TELEPHONE="ja_JP.UTF-8"
LC_MEASUREMENT="ja_JP.UTF-8"
LC_IDENTIFICATION="ja_JP.UTF-8"
LC_ALL=

$ localectl list-locales | grep '^ja'
ja_JP
ja_JP.eucjp
ja_JP.ujis
ja_JP.utf8
japanese
japanese.euc
```

解決方法の調査には少し時間がかかりましたが、対策は非常にシンプルでした。
