---
layout: people
title: Invited Speakers
permalink: /speakers/
---

<div class="row">
    <div class="col-sm-12">
        <h2 class="section-heading">Keynote</h2>
    </div>
</div>

{% for person in site.speakers %}
{% if person.keynote %}
<div class="row" id="speakers">
    <div class="col-sm-10 speakers-item">
        <div class="row">
            {% if person.pic %}
            <div class="col-sm-2">
                <img src="{{ person.pic | relative_url }}" class="img-responsive img-centered" alt="">
            </div>
            <div class="col-sm-10 speakers-info">
            {% else %}
            <div class="col-sm-12 speakers-info">
            {% endif %}
                <h4 class="speakers-name">{{ person.topic }}</h4>
                <p><b>Speaker:</b>
                    {% if person.webpage %}<a href="{{ person.webpage }}">{{ person.name }}</a>{% else %}{{ person.name }}{% endif %}
                </p>
                <p><b>Affiliation:</b> {{ person.affiliation }}</p>
                {% if person.abstract %}
                <p><b>Abstract:</b></p>
                {{ person.abstract | markdownify | strip_newlines }}
                {% endif %}
                <p><b>Bio:</b> {{ person.bio }}</p>
            </div>
        </div>
    </div>
    <div class="col-sm-2"></div>
</div>
{% endif %}
{% endfor %}

{% assign invited = site.speakers | where_exp: "p", "p.keynote != true" %}
{% if invited.size > 0 %}
<div class="row">
    <div class="col-sm-12">
        <h2 class="section-heading">{{ page.title }}</h2>
    </div>
</div>
{% endif %}

{% for person in invited %}
<div class="row" id="speakers">
    <div class="col-sm-10 speakers-item">
        <div class="row">
            {% if person.pic %}
            <div class="col-sm-2">
                <img src="{{ person.pic | relative_url }}" class="img-responsive img-centered" alt="">
            </div>
            <div class="col-sm-10 speakers-info">
            {% else %}
            <div class="col-sm-12 speakers-info">
            {% endif %}
                <p><b>Name:</b>
                    {% if person.webpage %}<a href="{{ person.webpage }}">{{ person.name }}</a>{% else %}{{ person.name }}{% endif %}
                </p>
                <p><b>Affiliation:</b> {{ person.affiliation }}</p>
                <p><b>Topic:</b> {{ person.topic }}</p>
                <p><b>Bio:</b> {{ person.bio }}</p>
            </div>
        </div>
    </div>
    <div class="col-sm-2"></div>
</div>
{% endfor %}
