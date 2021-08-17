---
layout: schedule
permalink: /meeting/
title: Meeting
---

{% for item in site.data.meeting %}
    {% if item.date %}
    {% assign lecture = item %}
        <tr>
            <th scope="row">{{ lecture.date }}</th>
            <td>
                {% if lecture.title %}
                    <br />{{ lecture.title }}<br />
                {% endif %}
                [
                    {% if lecture.slides %}
                    <a href="{{ lecture.slides }}" target="_blank">slides</a>
                    {% else %}
                    slides
                    {% endif %}
                    {% if lecture.slides2 %}
                    | <a href="{{ lecture.slides2 }}" target="_blank">slides 2</a>
                    {% endif %}
                ]
            </td>
            <td>
                {% if lecture.readings %}
                <ul>
                {% for reading in lecture.readings %}
                    <li>{{ reading }}</li>
                {% endfor %}
                </ul>
                {% endif %}
            </td>
        </tr>
    {% endif %}
{% endfor %}


<!-- {% if site.talks %}
{% assign talks = site.talks | reverse %}
{% for item in talks %}
    <tr>
    <td><strong>{{item.date | date: "%b %-d, %Y"}}</strong></td>
    <td>{{item.speaker}}</td>
    <td><a href="{{item.url | relative_url}}">{{item.title}}</a>
    </td>
    </tr>
{% endfor %}
{% endif %}
<tr class="past">
    <td colspan="3" align="center"><strong>End of the table</strong></td>
</tr> -->
