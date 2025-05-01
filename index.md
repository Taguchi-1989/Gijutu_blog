---
# index.md
layout: default # default.html レイアウトを使用
title: ホーム
---

# ようこそ！

これはNetlify上でJekyllを使って構築されたサイトのホームページです。

## 最近の投稿
<ul>
  {% raw %}{% for post in site.posts limit:5 %}{% endraw %}  {# 最近の投稿を5件まで表示 #}
    <li>
      {# 各投稿へのリンクとタイトルを表示 #}
      <a href="{% raw %}{{ post.url | relative_url }}{% endraw %}">{% raw %}{{ post.title }}{% endraw %}</a>
      {# 投稿日を表示 #}
      - {% raw %}{{ post.date | date: "%Y年%m月%d日" }}{% endraw %}
    </li>
  {% raw %}{% endfor %}{% endraw %}
</ul>

---
**（重要）上記の「最近の投稿」リストについて:**

* このリストは、`_posts` フォルダ内の投稿ファイルを自動的に読み込んで表示します。新しい投稿を追加してGitにPushし、Netlifyでビルドされれば、自動的にここにも反映されるはずです。
* 今回追加された `20250501_技術ブログ_1_導入.md` と `20250501_技術ブログ_概要.md` がリストに**正しく表示される（特にタイトルが表示される）**ためには、これらのファイルの中に **Front Matter** が適切に記述されている必要があります。最低限、以下のように `title:` と `layout:` を指定してください。

    **例 (`20250501_技術ブログ_概要.md` の場合):**
    ```markdown
    ---
    layout: default  # または post などの適切なレイアウト
    title: "技術ブログ 概要"
    # date: 2025-05-01 # ファイル名から日付が認識されない場合や指定したい場合に記述
    ---

    （ここにMarkdownで書かれた記事本文）
    ```

* `{{ post.title }}` や `{{ post.date }}` といった情報は、各投稿ファイルのFront Matterから取得されます。`title:` がないと、リストにタイトルが表示されません。
* 表示される順番は、通常、日付の新しい順（降順）になります。
* ファイル名の標準的な日付形式は `YYYY-MM-DD` ですが、`YYYYMMDD` でもJekyllが認識してくれる場合があります。もし日付がうまく表示されない場合は、Front Matter内に `date: YYYY-MM-DD` を追加してみてください。

この修正版 `index.md` をリポジトリに追加（または上書き）し、GitHub Desktopなどでコミット＆プッシュしてください。Netlifyでビルドが完了すれば、新しい投稿がトップページのリストに表示されるはずです。