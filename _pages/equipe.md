---
layout: page
date: 2020-04-18
title: Quem Somos
permalink: /equipe/
tags: [equipe, professor]
permalink: "/equipe.html"
---
{% assign coordenadores = site.equipe  | where_exp:"p", "p.type contains 'Coordenador'"  %}

{% assign professores = site.equipe | where_exp:"p", "p.type contains 'Professor'" | compact  %}

{% assign profNCoord = "" | split:"/" %}
{% for p in professores %}
	{% unless p.type contains 'Coordenador'  %}
		{% assign profNCoord = profNCoord | push: p %}
	{% endunless %}
{% endfor %}

{% capture texto %}Coordenação ({{coordenadores.size}}){% endcapture %}
{% include linha_user_cards.html dados=coordenadores titulo=texto %}

{% capture texto %}Professores ({{profNCoord.size}}){% endcapture %}
{% include linha_user_cards.html dados=profNCoord titulo=texto %}
