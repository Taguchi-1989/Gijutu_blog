## 最近の投稿
<ul>
  {% for post in site.posts limit:5 %}  {# 最近の投稿を5件まで表示 #}
    <li>
      {# 各投稿へのリンクとタイトルを表示 #}
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      {# 投稿日を表示 #}
      - {{ post.date | date: "%Y年%m月%d日" }}
    </li>
  {% endfor %}
</ul>