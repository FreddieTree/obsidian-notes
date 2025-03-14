---
title: {{title}}
authors: {% for author in creators %}{{author.firstName}} {{author.lastName}}{% if not loop.last %}, {% endif %}{% endfor %}
date: {{date | format("YYYY-MM-DD")}}
tags: {{tags}}
{% if DOI %}DOI: [{{DOI}}](https://doi.org/{{DOI}}){% endif %}
---

# 📖 {{title}}

### 📌 Basic Information
- **Authors**: {% for author in creators %}{{author.firstName}} {{author.lastName}}{% if not loop.last %}, {% endif %}{% endfor %}
- **Publication Date**: {{date | format("YYYY-MM-DD")}}
{% if DOI %}- **DOI**: [{{DOI}}](https://doi.org/{{DOI}}){% endif %}
- **Tags**: {{tags}}

---

## 📝 Summary
> {{abstractNote}}

---

## ✏️ Annotations
{% for annotation in annotations %}
> **📄 Page {{annotation.page}}**
> - {{annotation.annotatedText}}
> {% if annotation.comment %}💬 _{{annotation.comment}}_{% endif %}
{% endfor %}

---

## 🧐 Personal Notes
🔍 **Key Takeaways**  
- _Write your insights and reflections here._

📌 **Important Concepts**  
- _Concept 1_  
- _Concept 2_

❓ **Questions for Further Research**  
- _List questions or points you need to explore further._

---

## 📚 References
{{bibliography}}