# Ce que j'ai découvert

## Taxonomies

### Créer des nouvelles taxonomies

### Afficher la liste des taxonomies

Je n'ai pas trouvé de solution qui ne nécessite pas l'installation du plugin [Taxonomy List](https://github.com/getgrav/grav-plugin-taxonomylist)

```
{% set taxlist = taxonomylist.get() %}
{% if taxlist %}
    {% set category = grav.uri.params("Themes", true) %} /* Themes est la taxonomy que l'on veut lister */
    {% for tax,value in taxlist['Themes'] %}
        {% set current_page = (tax == category) ? 'active' : '' %}
        <li class="{{ current_page }}">
            <a href="{{ base_url }}/themes/{{ tax |replace({'é': 'e', 'â': 'a', 'ï': 'i'})|hyphenize }}">{{ tax|capitalize }}</a>
        </li>
    {% endfor %}
{% endif %}
```


### Twig

