---
layout: page
title: tags
---

<p>
{% for tag in site.tags %}
{% capture tag_name %}{{ tag | first }}{% endcapture %}
<a href = "#{{ tag_name }}" class ="tagbox">{{ tag_name }}</a>
{% endfor %}

{% assign tags2 =  site.notes | map: 'tags' | uniq %}
{% for tag in tags2 %}
<a href = "#{{ tag }}" class ="tagbox">{{ tag }}</a>
{% endfor %}

</p>



{% for tag2 in tags2 %}
<h3 id="{{ tag2 }}">{{ tag2 }} </h3>
<p></p>
{% for post in site.notes %}
    {% if post.tags contains tag2 %}
  * {{ post.date | date_to_string }} &raquo; [ {{ post.title }} ]({{ post.url }})
    {% endif %}
{% endfor %}

{% endfor %}

{% for tag in site.tags %}
{% capture tag_name %}{{ tag | first }}{% endcapture %}
<h3 id="{{ tag_name }}">{{ tag_name }} </h3>
<p></p>
{% for post in site.tags[tag_name] %}
 * {{ post.date | date_to_string }} &raquo; [ {{ post.title }} ]({{ post.url }})
{% endfor %}

{% endfor %}

