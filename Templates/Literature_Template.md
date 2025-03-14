# {{title}}

<!-- Collapsible Basic Information -->
<details>
  <summary>📌 Basic Information</summary>
  
  - **Authors:** {% for author in creators %}{{author.firstName}} {{author.lastName}}{% if not loop.last %}, {% endif %}{% endfor %}
  - **Publication Date:** {{date | format("YYYY-MM-DD")}}
  {% if DOI %}
  - **DOI:** [{{DOI}}](https://doi.org/{{DOI}})
  {% endif %}
  - **Tags:** {{tags}}
  
</details>

---

## 📝 Summary
> {{abstractNote | truncate(500, "...")}}

---

## ✏️ Annotations
{% for annotation in annotations %}
> [!quote] **Page {{annotation.page}}**
> **Highlight:** {{annotation.annotatedText}}
> {% if annotation.comment %}💬 _{{annotation.comment}}_{% endif %}
{% endfor %}

---

## 🧐 Personal Notes

### 🔍 Key Takeaways  
- *Write your insights and reflections here.*

### 📌 Important Concepts  
- *Concept 1*  
- *Concept 2*

### ❓ Questions for Further Research  
- *List questions or points you need to explore further.*

---

## 📚 References
{{bibliography}}