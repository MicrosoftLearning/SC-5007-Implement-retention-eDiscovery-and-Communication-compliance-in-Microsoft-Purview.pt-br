---
title: Instruções online hospedadas
permalink: index.html
layout: home
---

# Diretório de conteúdo

Hiperlinks para cada um dos exercícios de laboratório e demonstrações estão listados abaixo.

## Laboratórios

{% assign labs = site.pages | where_exp:"page", "page.url contains '/Instructions/Labs'" %}
| Exercício | Tarefa |
| --- | --- |
{% for activity in labs  %}| {{ activity.lab.exercise }} | [{{ activity.lab.task }}{% if activity.lab.type %} - {{ activity.lab.type }}{% endif %}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}
