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
> [!quote] **Location:** {{annotation.page | default("N/A")}}  
> **Highlight:** {{annotation.annotatedText}}  

{% if annotation.comment %}💬 _Note:_ {{annotation.comment}}{% endif %}
{% endfor %}

---

