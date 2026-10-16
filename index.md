---
layout: default
title: Presentations
---

Slides and handouts from presentations by UNL Libraries Acquisitions, Cataloging, Metadata and E-Resources (ACME) faculty and staff. Unless otherwise noted, content is licensed [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/).

{% assign talks = site.data.presentations | sort: "date" | reverse %}
{% assign years = talks | group_by_exp: "t", "t.date | date: '%Y'" %}
{% for year in years %}
## {{ year.name }}
{% for t in year.items %}
### {{ t.title }}

{{ t.presenters }} · {{ t.event }} · {{ t.date | date: "%B %-d, %Y" }}

{% if t.abstract %}> {{ t.abstract }}{% endif %}

{% if t.slides %}- [Slides (PDF)]({{ t.folder | append: "/" | append: t.slides | relative_url }}){% endif %}
{% if t.slides_notes %}- [Slides with speaker notes (PDF)]({{ t.folder | append: "/" | append: t.slides_notes | relative_url }}){% endif %}
{% if t.handout %}- [Handout (PDF)]({{ t.folder | append: "/" | append: t.handout | relative_url }}){% endif %}
- [All files on GitHub](https://github.com/unl-libraries-acme/presentations/tree/main/{{ t.folder }})

{% if t.links %}
**Related resources**

{% for link in t.links %}
{% if link.url contains "://" %}- [{{ link.label }}]({{ link.url }}){% else %}- [{{ link.label }}]({{ link.url | relative_url }}){% endif %}
{% endfor %}
{% endif %}

{% endfor %}
{% endfor %}
