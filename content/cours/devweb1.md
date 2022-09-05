---
title: "DevWeb: Introduction"
date: 2022-09-02T09:43:48+02:00
tags: ["Ressource R03.0 Développement Web"]
---

# Langages 

* php -> server side
* js -> client side
  - JQuery
  - ReactNative
* web assembly -> client side

# Interactions avec l'utilisateur en Js

## Relation etre balises et données de script 

Correspondance directe entre une balise et un objet

Balise -> Objet
* attributs -> propriétés
* contenu -> objet fils
* gestionnaires d'événements -> méthodes

## Hiérarchisation d'objets pour une page html 

La page html est représenté par une hierarchie en arbre similaire à l'encapsulation des balises html.
Un objet parent a des références sur ses enfants et inversement. 

```Yaml
ex:
  body:
    tagName: body
    id: doc
    innerHTML: raw text
    children : h3 et div
    style: objet style
```

Le style d'un objet est encore un objet.

Pour change le background de body on peut donc faire 
```Javascript
body.style.background = red
```

On peut donner à l'attribut onclick (qui gère l'évènement du clique) directement du js : 

```Html
<p onclick="alert('T'as cliqué);">

Texte

</p>
```
