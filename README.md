# Déploiement de la partie client d'une DApp
Exercice réalisé dans le cadre de la formation Alyra.

## Heroku
**Pré-requis**
1. Créer un compte sur [Heroku](https://www.heroku.com/)
2. Installer le CLI de Heroku
```console
$ sudo npm install -g heroku

# Vérification
$ heroku --version
```

**Ensuite**
1. Créer un projet DApp (pour l'exercice, j'ai forké [ce projet](https://github.com/Alyra-school/whitelist-system-with-heroku/tree/master/client/src)
2. Se logger via Heroku CLI:
```console
$ heroku login
```
3. Ajouter une branche remote appelée `heroku` à notre repo actuelle (en se basant sur un projet de type create-react-app):
```console
$ heroku create --buildpack mars/create-react-app <nom>
Creating ⬢ simple-storage-deploy... done
Setting buildpack to mars/create-react-app... done
https://simple-storage-deploy.herokuapp.com/ | https://git.heroku.com/simple-storage-deploy.git
```
4. Déployer:
``` console
$ git subtree push --prefix client/ heroku master

[...]
remote: -----> Launching...
remote:        Released v3
remote:        https://simple-storage-deploy.herokuapp.com/ deployed to Heroku
remote: 
remote: Verifying deploy... done.
To https://git.heroku.com/simple-storage-deploy.git
 * [new branch]      226f7dd408c095c3b465c97c7f1ddcdfc6c51ce9 -> master

```

[Résultat sur Heroku (utiliser un compte sur Ropsten)](https://pacific-fortress-09484.herokuapp.com/)

## Github Pages
**Pré-requis**
1. Créer un compte sur [Github](https://www.github.com//)

**Ensuite**
1. Aller dans le répertoire `client/`, et:
```console
$ npm install --save gh-pages
```
2. Dans `package.json`, ajouter les scripts pour déployer et l'URL d'accès:
```json
  "scripts": {
    "predeploy": "npm run build",
    "deploy": "gh-pages -d build",
    "clean": "gh-pages-clean"
  },
  "homepage": "https://USERNAME.github.io/REPO/"
```
où USERNAME est le nom d'utilisateur Github et REPO le nom du repository Github

3. Déployer
```console
$ npm run deploy
```

[Résultat sur Github Pages (utiliser un compte sur Ropsten)](https://oumod.github.io/simple-storage-deploy/)

4. Besoin de modifier, puis de redéployer ?
```console
# Pour redéployer, il faut d'abord supprimer le cache, autrement le déploiement ne tiendra pas compte des modifications:
$ npm run clean
$ npm run deploy
```
