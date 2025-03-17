# {{title}}

<!-- Collapsible Metadata -->
<details>
  <summary>🌐 Source Information</summary>
  
  - **Source Title:** {{title}}
  - **Source Type:** Web / Snapshot / Other  
  - **URL:** {% if url %}[{{url}}]({{url}}){% else %}N/A{% endif %}
  - **Date Captured:** {{date | format("YYYY-MM-DD")}}
  - **Tags:** {{tags}}
  - **Zotero Link:** {{zoteroSelectURI}}

</details>

---

## 🖍️ Annotation Review
{% for annotation in annotations %}
> [!quote] 📌 **Captured Insight**
> ✨ **Excerpt:** {{annotation.annotatedText}}  

> {% if annotation.comment %}🗒️ **Note:** {{annotation.comment}}{% endif %}
{% endfor %}
---

