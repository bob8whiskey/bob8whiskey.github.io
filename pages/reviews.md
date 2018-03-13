---
layout: page
title: Reviews
permalink: /reviews-old/
---
<div id="archives">
{% for category in site.categories %}
  <div class="archive-group">
    {% capture category_name %}{{ category | first }}{% endcapture %}
    <div id="#{{ category_name | slugize }}"></div>
    <p></p>

    <h3 class="category-head">{{ category_name }}</h3>
    <a name="{{ category_name | slugize }}"></a>
    {% for post in site.categories[category_name] %}
    <article class="archive-item">
      <h4><a href="{{ site.baseurl }}{{ post.url }}">{{post.title}}</a></h4>
    </article>
    {% endfor %}
  </div>
{% endfor %}
</div>

<main role="main" class="cf">

    <p>Reviews be here</p>

    <article class="archive">
        <article role="article">

            <header>
                <ul class="tag-cloud">
                    {% capture site_tags %}{% for tag in site.tags %}{{tag | first}}{% unless forloop.last %},{% endunless %}{% endfor %}{% endcapture %}
                    {% assign sortedTags=site_tags | split:',' | sort %}

                    {% for tag in sortedTags %}
                        <li><a href="#{{tag | cgi_escape}}">{{tag}} [{{site.tags[tag].size}}]</a></li>
                    {% endfor %}
                </ul>
            </header>

            {% for tag in sortedTags %}
                <h3 id="{{tag | cgi_escape}}">{{tag}}</h3>
                <ul class="taglist">
                    {% for post in site.tags[tag] %}
                        <li>
                            <time itemprop="dateCreated" datetime="{{post.date}}">
                                {{ post.date | date: "%b %d, %Y" }}</time> | <a href="{{site.baseurl}}{{post.url}}" rel="bookmark" title="Permanent Link to {{site.baseurl}}{{post.url}}">
                                {{post.title}}</a>
                        </li>
                    {% endfor %}
                <li class="return"><a href="#top" title="return to top">return to top</a></li>
                </ul>
            {% endfor %}

        </article>
    </article>
</main>
