---
layout: page
date: 2020-04-18
title: Quem Somos
permalink: /equipe/
tags: [equipe, professor]
permalink: "/equipe.html"
---


{% assign coordenadores = site.equipe  | where: 'type', 'Coordenador' | compact  %}


{% include linha_user_cards.html dados=coordenadores titulo="Coordenação" %}


{% assign professores = site.equipe 
	| where_exp:"p", "p.type contains 'Professor'" | compact | order: name  %}


{% assign profNCoord = "" | split:"/" %}
{% for p in professores %}
	{% unless p.type contains 'Coordenador'  %}
		{% assign profNCoord = profNCoord | push: p %}
	{% else %}
		{% assign professores = professores | pop %}
	{% endunless %}

{% endfor %}



{% include linha_user_cards.html dados=profNCoord titulo="Professores" %}
