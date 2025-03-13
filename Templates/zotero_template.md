---
title: {{title}}
authors: 
{% for author in creators %}
- **{{author.firstName}} {{author.lastName}}**
{% endfor %}
date: {{date | format("YYYY-MM-DD")}}
tags: {{tags}}
---

## 📖 摘要
{{abstractNote}}

## ✏️ 批注
{% for annotation in annotations %}
### 📌 批注
- **页面 [{{annotation.page}}]**: {{annotation.annotatedText}}
  - 💬 {{annotation.comment}}
{% endfor %}