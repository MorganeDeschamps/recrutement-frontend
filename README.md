# Exercice de recrutement Front-End

Nous souhaitons mettre en place un endroit d'échanges simple et rapide à destination de nos collaborateurs.

## Fonctionnalités

Chacun est libre d'utiliser le pseudonyme de son choix au moment de publier.

### Publications

- Publier un message texte
- Modifier le titre d'une publication
- Supprimer une publication (optionnel)
- Afficher les publications les une à la suite des autres

### Commentaires

L'ajout d'un commentaire reprend le même style que celui de la publication. Il n'y a pas de pseudo ni de titre pour un commentaire.

- Répondre à une publication par un message texte
- Supprimer un commentaire (optionnel)
- Afficher les commentaires d'une publication

## Maquette

https://xd.adobe.com/view/d9f2d0e4-ae2a-4ea2-9d90-abcd4bd08c37-8ca1/specs/

## Développement

Merci de fork le projet sur votre compte GitHub.

### API

- Démarrer l'API: `yarn run api`
- Documentation: https://github.com/typicode/json-server

## Interface

- Démarrer l'interface: `yarn run dev`
- Documentation: https://nuxtjs.org/docs/features/file-system-routing
- Extension VSCode: https://vuejs.github.io/vetur/guide/
- Extension Chrome: https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd

## FAQ

- Comment récupérer les commentaires des publications ?
```js
await $nuxt.$axios.$get('/posts?_embed=comments')
```
