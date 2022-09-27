---
layout: default
---

<main id="page" role="main">
{% for category in site.categories %}
    {% assign counter=0 %}
    {% for posts in category %}
        {% for post in posts %}
            {% if post.tags contains page.tag %}
                {% assign counter=counter | plus:1 %}
            {% endif %}
        {% endfor %}
    {% endfor %}

{% if counter != 0 %}

<div class="col pane ui-layout-{% assign counter=counter | plus:1 %}" id="{{ page.id }}">
    <div class="colheader">
        <div class="bar"></div>
        <p class="lead">Leadin text</p>
        <h1>{{ category | first }}</h1>
    </div>
    <div class="colscroll unlock">
{% for posts in category %}
{% for post in posts %}
{% if post.tags contains page.tag %}
    <div class="colblock" itemscope itemtype="http://schema.org/BlogPosting">
        <div class="excerpt">
            <time class="date" datetime="{{ page.date | '%Y-%m-%dT%H:%i:%S-08:00' }}" itemprop="datePublished">
                {{ page.date | date: '%B %d, %Y' }}
            </time>
        <h1>
            <a itemprop="url" href="{{ post.url }}" target="_blank" title="{{ post.title }}">
                <span itemprop="name" itemprop=name>{{ post.title }}</span>
            </a>
        </h1>
        <p itemprop="description">
            {{ post.excerpt }}..
        </p>
        <p class="link_tags">{{ page.tags }}</p>
        </div>
    </div>
{% endif %}
{% endfor %}
{% endfor %}
    </div>
</div>
{% endif %}
{% endfor %}
</main>
