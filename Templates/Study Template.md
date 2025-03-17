---
title: {{reference.title}}
authors: {{reference.authors}}
year: {{reference.year}}
tags: [zotero, {{reference.type}}, {{reference.year}}]
citation_key: {{reference.citationKey}}
---

# {{reference.title}}

## Metadata
- **Authors**: {{reference.authors}}
- **Year**: {{reference.year}}
- **Citation**: {{reference.citationKey}}

---

{% set yellow = annotations | filter(attribute='color', value='yellow') %}
{% if yellow %}
## 🟡 Key Points
{% for annotation in yellow %}
> [!quote]- 📌 **Key Point**
> ✨ **Excerpt:** {{annotation.annotatedText}}  
> {% if annotation.comment %}🗒️ **Note:** {{annotation.comment}}{% endif %}
{% endfor %}
{% endif %}

{% set red = annotations | filter(attribute='color', value='red') %}
{% if red %}
## 🔴 Questions & Critiques
{% for annotation in red %}
> [!quote]- ❓ **Question or Critique**
> ✨ **Excerpt:** {{annotation.annotatedText}}  
> {% if annotation.comment %}🗒️ **Note:** {{annotation.comment}}{% endif %}
{% endfor %}
{% endif %}

{% set blue = annotations | filter(attribute='color', value='blue') %}
{% if blue %}
## 🔵 Definitions / APIs
{% for annotation in blue %}
> [!quote]- 🧩 **Definition / API**
> ✨ **Excerpt:** {{annotation.annotatedText}}  
> {% if annotation.comment %}🗒️ **Note:** {{annotation.comment}}{% endif %}
{% endfor %}
{% endif %}

{% set green = annotations | filter(attribute='color', value='green') %}
{% if green %}
## 🟢 How-To / Code Snippets
{% for annotation in green %}
> [!quote]- 💻 **How-To / Code**
> ✨ **Excerpt:** {{annotation.annotatedText}}  
> {% if annotation.comment %}🗒️ **Note:** {{annotation.comment}}{% endif %}
{% endfor %}
{% endif %}

{% set purple = annotations | filter(attribute='color', value='purple') %}
{% if purple %}
## 🟣 Ideas / Applications
{% for annotation in purple %}
> [!quote]- 💡 **Idea / Application**
> ✨ **Excerpt:** {{annotation.annotatedText}}  
> {% if annotation.comment %}🗒️ **Note:** {{annotation.comment}}{% endif %}
{% endfor %}
{% endif %}