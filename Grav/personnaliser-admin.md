# Personnaliser le plugin d'administration 

## Ajouter un champs de texte

Dans mon cas d'utilisation, j'ai besoin d'ajouter un sous-titre dans mon modèle "item".  
Mes fichiers de contenu sont donc de types `item.md`  

On va utiliser la possibilité de Grav d'étendre les formulaires. 
La gestion des formulaires est faites dans des fichiers appelés "blueprints"

- À la racine du dossier de mon thème, je crée un dossier `blueprints/`
- Dedans je crée un fichier `item.yaml`

### Le code

Voilà le code que j'ai mis pour ajouter mes sous-titres
```
title: Item
'@extends':
    type: blog
    context: blueprints://pages

form:
  fields:
    tabs:
      type: tabs
      active: 1

      fields:
        content:
          type: tab

          fields:

            subTitle:
              parrent.parent.classes: vertical
              ordering@: 1
              type: text
              label: Sous titre
              validate:
                required: true
                type: text
              placeholder: "Ex. : Par … / Le …"
```

### Explications 

On commence donc par étendre l'existant du plugin.
```
'@extends':
    type: blog
    context: blueprints://pages
```

On spécifie la tabulation dans laquelle on veut ajouter le champs, ici `content`
```
  fields:
        content:
          type: tab
```

On crée ensuite notre champs. 

- `subTitle:` son petit nom
- `ordering@: 1` spécifie que l'on veut qu'il s'affiche à la 2è position
- `type: text` ça sera un champ texte
- `label: Sous titre` le label qui s'affichera à côté du champ
- `validate:
        required: true
        type: text`
   on veut que le champs soit obligatoire, et vérifie que c'est bien du texte
- `placeholder: "Ex. : Par … / Le …"` et enfin on spécifie le texte affiché par défaut

Ensuite dans mon modèle `item.html.twig`, j'appelle `{{ page.subTitle }}` partout où j'en ai besoin
