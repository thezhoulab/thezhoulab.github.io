---
layout: black
title: Patents
permalink: /patents
---

# Patents

{%- assign all_pubs   = site.data.patents | sort: 'year' -%}
{%- assign patents    = all_pubs | where: "type", "patent" | sort: 'year' | reverse -%}
{%- assign patent_num = patents.size -%}

{%- comment -%}
Build highlight-author list from `_data/team.yml`.
- `l_authors`: non-undergraduate team members (format: "F Last")
{%- endcomment -%}
{% assign l_authors_str = "" %}
{%- for role in site.data.team -%}
  {% assign role_name = role[0] %}
  {% assign role_name_lc = role_name | downcase %}
  {% assign people = role[1] %}
  {%- if people -%}
    {%- for person in people -%}
      {%- if person.name -%}
        {% assign parts = person.name | split: " " %}
        {% assign first = parts | first %}
        {% assign last = parts | last %}
        {% assign initial = first | slice: 0, 1 %}
        {% assign author = initial | append: " " | append: last %}
        {%- unless role_name_lc contains "undergraduate" -%}
          {% assign l_authors_str = l_authors_str | append: author | append: "|" %}
        {%- endunless -%}
      {%- endif -%}
    {%- endfor -%}
  {%- endif -%}
{%- endfor -%}
{% assign author_list = l_authors_str | append: "R Zhou|" | split: "|" %}

{% include publications/patents.html patents=patents author_list=author_list patent_num=patent_num %}
