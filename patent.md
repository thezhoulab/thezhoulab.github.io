---
layout: black
title: Patents
permalink: /patents
---

# Patents

{%- assign all_pubs   = site.data.patents | sort: 'year' -%}
{%- assign patents    = all_pubs | where: "type", "patent" | sort: 'year' | reverse -%}
{%- assign patent_num = patents.size -%}
{% assign author_list = "R Zhou|H Zhang" | split:"|" %}

{% include publications/patents.html 
     patents=patents 
     author_list=author_list 
     patent_num=patent_num %}
