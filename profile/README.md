## Wordpress premium plugins

This repository contains all WordPress plugins that require a licence and cannot be installed via Composer.

* Formidable PRO + addons
* WPML + addons

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
