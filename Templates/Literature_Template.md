# 📖 `{{title}}`

## 📝 Summary
> `{{abstractNote | truncate(500, "...")}}`

---

## ✏️ Annotations
{% for annotation in annotations %}
> [!quote] **📄 Page {{annotation.page}}**  
> **🖍 Highlight:** {{annotation.annotatedText}}  
> {% if annotation.comment %}💬 _{{annotation.comment}}_{% endif %}
> ⏳ _Created on: {{annotation.date | format("YYYY-MM-DD HH:mm")}}_
{% endfor %}

---

## 🧐 Personal Notes
### 🔍 **Key Takeaways**
- _你的见解和反思_

### 📌 **Important Concepts**
- _概念 A_
- _概念 B_

### ❓ **Questions for Further Research**
- _需要进一步探索的问题_

---

## 📚 References
```dataview
table title, authors, year, DOI
from "Literature Notes"
where contains(tags, "AI") or contains(tags, "NLP")
sort year desc
```