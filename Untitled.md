---
title: {{title}}
authors: {% for author in creators %}{{author.lastName}}, {{author.firstName}}{% if not loop.last %}; {% endif %}{% endfor %}
date: {{date | format("YYYY-MM-DD")}}
tags: {{tags}}
---

## 摘要
{{abstractNote}}

## 注释
{% for annotation in annotations %}
- **页面 {{annotation.page}}**: {{annotation.annotatedText}}
  - 评论: {{annotation.comment}}
{% endfor %}