---
title: Home
---

<h1>Upcoming Talks</h1>
{% assign current_date = "now" | date: "%Y-%m-%d" %}
{% for talk in site.talks %}
  {% if talk.date | date: "%Y-%m-%d" >= current_date %}
    {% raw %}
    <div class="talk-item">
      <h2 onclick="toggleAbstract('{{ talk.title | slugify }}')">{{ talk.title }}</h2>
      <p><strong>Speaker:</strong> {{ talk.speaker }}</p>
      <p><strong>Date:</strong> {{ talk.date | date: "%B %d, %Y" }}</p>
      <div id="{{ talk.title | slugify }}" class="abstract-content" style="display: none;">
        <p>{{ talk.abstract }}</p>
      </div>
    </div>
    {% endraw %}
  {% endif %}
{% endfor %}

<h1>Past Talks</h1>
{% for talk in site.talks %}
  {% if talk.date | date: "%Y-%m-%d" < current_date %}
    {% raw %}
    <div class="talk-item">
      <h2 onclick="toggleAbstract('{{ talk.title | slugify }}')">{{ talk.title }}</h2>
      <p><strong>Speaker:</strong> {{ talk.speaker }}</p>
      <p><strong>Date:</strong> {{ talk.date | date: "%B %d, %Y" }}</p>
      <div id="{{ talk.title | slugify }}" class="abstract-content" style="display: none;">
        <p>{{ talk.abstract }}</p>
      </div>
    </div>
    {% endraw %}
  {% endif %}
{% endfor %}

<script>
  function toggleAbstract(id) {
    var content = document.getElementById(id);
    if (content.style.display === "none") {
      content.style.display = "block";
    } else {
      content.style.display = "none";
    }
  }
</script>



