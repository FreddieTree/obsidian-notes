---
title: {{reference.title}}
authors: {{reference.authors}}
year: {{reference.year}}
tags: [zotero, {{reference.type}}, {{reference.year}}]
citation_key: {{reference.citationKey}}
---
{% for annotation in annotations %}

> [!quote] 📌 **Captured Insight**

> ✨ **Excerpt:** {{annotation.annotatedText}}  
> {% if annotation.comment %}🗒️ **Note:** {{annotation.comment}}{% endif %}

{% endfor %}