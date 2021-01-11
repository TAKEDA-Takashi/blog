---
title: textlint-filter-rule-whitelistが外部ファイルに対応しました（v1.2.1）
summary: ""
description: ""
date: 2017-12-02 23:00:00 +0900 JST
categories: "textlint"
tags: ["textlint", "JavaScript"]
slug: textlint-filter-rule-whilelist-support-external-file
archives:
    - 2017
    - 2017-12
    - 2017-12-02
draft: false
---

[textlint](https://github.com/textlint)という日本語文章の校正に便利なツールを使っています。[会社のブログ](https://dev.classmethod.jp/devenv/atom-textlint-proofreading/)でも紹介しました。

textlintのチェックルールはプラグインとして提供されています。その中に[textlint-filter-rule-whitelist](https://github.com/textlint/textlint-filter-rule-whitelist)という、指定した単語（または正規表現）をチェック対象から外せるフィルタルールがあります。

次のように`.textlintrc`に除外したい単語を指定することで、チェック時に無視できます。

```json
{
  "filters": {
    "whitelist": {
      "allow": [
        "はてなブログ"
      ]
    }
  }
}
```

ただ単語が増えてくると`.textlintrc`が肥えていきそうだったのが気になりました。これをTwitterでつぶやいたところ開発者の[azuさん](https://twitter.com/azu_re)に捕捉され、言われるがままissue立てたらあっという間に実装されてました（v1.2.1）。

{{< twitter 936023590176153601 >}}

{{< twitter 936549689809281024 >}}

圧倒的感謝。

これで次のように定義できるようになりました。

- whitelist/proper-noun.yml

```yaml
- はてなブログ
```

- .textlintrc

```json
{
  "filters": {
    "whitelist": {
      "whitelistConfigPaths": [
        "./whitelist/proper-noun.yml"
      ]
    }
  }
}
```

後はこのファイルに単語を追加していけばよくなりました。ファイルで分類することも容易にできます。便利！[^footnote_allow]

実は実装の連絡をもらってアップデートしたらエラーで動きませんでした。結論としては、原因はatom pluginで使われているtextlintのバージョンが古いことでした。が、azuさんにhotfixで神速対応していただきすぐに使えるようになりました（v1.2.2）。

この辺のやりとりもissueでさせてもらいました。

<iframe class="hatenablogcard" style="width:100%;" frameborder="0" scrolling="no" src="https://hatenablog-parts.com/embed?url=https://github.com/textlint/textlint-filter-rule-allowlist/issues/4"></iframe>

issueオープンからリリースまで18分！

というわけで、ちょっとしたつぶやきから新機能を実装してもらえました。ありがとうございました！

（本当は自分でPR出せたらよかったなぁ）

[^footnote_allow]: allowも引き続き使えます
