# {{reference.title}}

## Metadata
- **Authors**: {{reference.authors}}
- **Year**: {{reference.year}}
- **Citation**: {{reference.citationKey}}

---

## 🟡 Key Points
{% for annotation in annotations %}
{% if annotation.color == "yellow" %}
> [!quote]- 📌 **Key Point**
> ✨ **Excerpt:** {{annotation.annotatedText}}  
> {% if annotation.comment %}🗒️ **Note:** {{annotation.comment}}{% endif %}
{% endif %}
{% endfor %}

## 🔴 Questions & Critiques
{% for annotation in annotations %}
{% if annotation.color == "red" %}
> [!quote]- ❓ **Question or Critique**
> ✨ **Excerpt:** {{annotation.annotatedText}}  
> {% if annotation.comment %}🗒️ **Note:** {{annotation.comment}}{% endif %}
{% endif %}
{% endfor %}

## 🔵 Definitions / APIs
{% for annotation in annotations %}
{% if annotation.color == "blue" %}
> [!quote]- 🧩 **Definition / API**
> ✨ **Excerpt:** {{annotation.annotatedText}}  
> {% if annotation.comment %}🗒️ **Note:** {{annotation.comment}}{% endif %}
{% endif %}
{% endfor %}

## 🟢 How-To / Code Snippets
{% for annotation in annotations %}
{% if annotation.color == "green" %}
> [!quote]- 💻 **How-To / Code**
> ✨ **Excerpt:** {{annotation.annotatedText}}  
> {% if annotation.comment %}🗒️ **Note:** {{annotation.comment}}{% endif %}
{% endif %}
{% endfor %}

## 🟣 Ideas / Applications
{% for annotation in annotations %}
{% if annotation.color == "purple" %}
> [!quote]- 💡 **Idea / Application**
> ✨ **Excerpt:** {{annotation.annotatedText}}  
> {% if annotation.comment %}🗒️ **Note:** {{annotation.comment}}{% endif %}
{% endif %}
{% endfor %}