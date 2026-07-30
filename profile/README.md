## Wordpress premium plugins

This repository contains all WordPress plugins that require a licence and cannot be installed via Composer.

* Formidable PRO + addons
* WPML + addons

## Pré-requis

Pouvoir pouvoir connecter un site Wordpress à ce repo privé, il faut impérativement créer un Access Token en [cliquant ici](https://github.com/settings/personal-access-tokens)

Il faut donner un accès aux repos souhaités et donner l'autorisation suivante uniquement : "Contents" > Read-only

Github va générer un Token qu'il faudra ajouter dans un fichier auth.json à la racine du projet:
```json
{
  "github-oauth": {
    "github.com": "copier-coller-la-cle-ici"
  }
}
```

### Mise à jour d'un plugin existant

1/ Télécharger le zip du plugin à mettre à jour.

2/ Mettre à jour le repo du plugin avec le contenu du zip

3/ Il faut inclure dans le commit le fichier composer.json adapté avec le numéro de version du plugin (voir exemple ci-dessous : "version": "X.X")

```json
{
  "name": "paf-agency/nom-du-plugin",
  "description": "Plugin Premium pour WordPress",
  "type": "wordpress-plugin",
  "version": "X.X",
  "require": {
    "composer/installers": "^1.0 || ^2.0"
  }
}
```

4/ Il faut également toujours créer une nouvelle release avec le numéro de version du plugin.

5/ Ensuite sur le site Wordpress où l'on souhaite mettre à jour le plugin, il faudra mettre à jour en faisant un `composer update`


### Ajout d'un nouveau plugin premium

1/ Télécharger le zip du plugin à installer

2/ Créer un nouveau repo privé portant le nom du plugin

3/ Inclure dans le commit le fichier composer.json à la racine, contenenant les paramètres suivants:
```json
{
  "name": "paf-agency/nom-du-plugin",
  "description": "Plugin Premium pour WordPress",
  "type": "wordpress-plugin",
  "version": "X.X",
  "require": {
    "composer/installers": "^1.0 || ^2.0"
  }
}
```
En prenant soin d'adapter les paramètres "name" avec le nom du plugin (précédé de paf-agency/) et "version" avec le numéro de version du plugin.

4/ Il faut ensuite créer une release avec le même numéro de version que le plugin.

5/ Pour installer le plugin sur le site Wordpress, il faut aller dans le fichier composer.json du projet et y ajouter les lignes suivantes:

Sous le noeud "repositories":
```
{
  "type": "vcs",
  "url": "git@github.com:paf-agency/nom-du-plugin.git"
}
```

Sous le noeud "web/app/mu-plugins/{$name}/":
```
"paf-agency/nom-du-plugin"
```

Et pour finir exécuter la commande `composer require paf-agency/nom-du-plugin`

