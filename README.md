<<<<<<< HEAD
# Todo-backend
=======
<p align="center">
  <a href="http://nestjs.com/" target="blank"><img src="https://nestjs.com/img/logo-small.svg" width="200" alt="Nest Logo" /></a>
</p>

[circleci-image]: https://img.shields.io/circleci/build/github/nestjs/nest/master?token=abc123def456
[circleci-url]: https://circleci.com/gh/nestjs/nest

  <p align="center">A progressive <a href="http://nodejs.org" target="_blank">Node.js</a> framework for building efficient and scalable server-side applications.</p>
    <p align="center">
<a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/v/@nestjs/core.svg" alt="NPM Version" /></a>
<a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/l/@nestjs/core.svg" alt="Package License" /></a>
<a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/dm/@nestjs/common.svg" alt="NPM Downloads" /></a>
<a href="https://circleci.com/gh/nestjs/nest" target="_blank"><img src="https://img.shields.io/circleci/build/github/nestjs/nest/master" alt="CircleCI" /></a>
<a href="https://coveralls.io/github/nestjs/nest?branch=master" target="_blank"><img src="https://coveralls.io/repos/github/nestjs/nest/badge.svg?branch=master#9" alt="Coverage" /></a>
<a href="https://discord.gg/G7Qnnhy" target="_blank"><img src="https://img.shields.io/badge/discord-online-brightgreen.svg" alt="Discord"/></a>
<a href="https://opencollective.com/nest#backer" target="_blank"><img src="https://opencollective.com/nest/backers/badge.svg" alt="Backers on Open Collective" /></a>
<a href="https://opencollective.com/nest#sponsor" target="_blank"><img src="https://opencollective.com/nest/sponsors/badge.svg" alt="Sponsors on Open Collective" /></a>
  <a href="https://paypal.me/kamilmysliwiec" target="_blank"><img src="https://img.shields.io/badge/Donate-PayPal-ff3f59.svg"/></a>
    <a href="https://opencollective.com/nest#sponsor"  target="_blank"><img src="https://img.shields.io/badge/Support%20us-Open%20Collective-41B883.svg" alt="Support us"></a>
  <a href="https://twitter.com/nestframework" target="_blank"><img src="https://img.shields.io/twitter/follow/nestframework.svg?style=social&label=Follow"></a>
</p>
  <!--[![Backers on Open Collective](https://opencollective.com/nest/backers/badge.svg)](https://opencollective.com/nest#backer)
  [![Sponsors on Open Collective](https://opencollective.com/nest/sponsors/badge.svg)](https://opencollective.com/nest#sponsor)-->

## Description

[Nest](https://github.com/nestjs/nest) framework TypeScript starter repository.

## Installation

```bash
$ yarn install
```

## Running the app

```bash
# development
$ yarn run start

# watch mode
$ yarn run start:dev

# production mode
$ yarn run start:prod
```

## Test

```bash
# unit tests
$ yarn run test

# e2e tests
$ yarn run test:e2e

# test coverage
$ yarn run test:cov
```

## Support

Nest is an MIT-licensed open source project. It can grow thanks to the sponsors and support by the amazing backers. If you'd like to join them, please [read more here](https://docs.nestjs.com/support).

## Stay in touch

- Author - [Kamil Myśliwiec](https://kamilmysliwiec.com)
- Website - [https://nestjs.com](https://nestjs.com/)
- Twitter - [@nestframework](https://twitter.com/nestframework)

## License

Nest is [MIT licensed](LICENSE).
>>>>>>> ea5fae7 (Initial commit)

# 📝 README.md

## 🎯 Objectif du projet

Dans ce projet, j’ai dû mettre en place une application de gestion de tâches (Todo List) avec un backend en NestJS et un frontend React. L'objectif principal était de permettre la création, l'édition, la suppression et la recherche de tâches.

---

## 🧠 Mes choix techniques et organisation du code

### 1. Architecture

J’ai choisi de structurer le backend en plusieurs couches :
- **Controller** : pour gérer les routes.
- **UseCase** : pour séparer la logique métier.
- **Repository** : pour interagir avec la base de données via Prisma.

Cette séparation permet une meilleure lisibilité, une maintenance facilitée, et une bonne testabilité du code.

### 2. UseCaseFactory

J’ai utilisé une `UseCaseFactory` pour instancier dynamiquement les use cases. Cela évite d’avoir à injecter manuellement chaque service dans les contrôleurs et respecte le principe d'inversion des dépendances.

---

## ⚙️ Fonctionnalités implémentées

- Récupération de toutes les tâches (`GET /tasks`)
- Création d’une tâche (`POST /tasks`)
- Mise à jour d’une tâche (`PATCH /tasks/:id`)
- Suppression d’une tâche (`DELETE /tasks/:id`)
- Recherche côté frontend avec filtre dynamique
- Désactivation du bouton de mise à jour si le nom de la tâche n’a pas changé

---

## ⚠️ Points d’arrêt / Problèmes rencontrés

### 🛑 Erreur TypeScript dans UseCaseFactory
J’ai rencontré une erreur lors de l’appel de la méthode `create()` :
```ts
Argument of type 'typeof SaveTaskUseCase' is not assignable to parameter of type 'Type<UseCases>'.
```
J’ai corrigé cela en m’assurant que tous les use cases partagent bien la même structure typée, notamment au niveau des constructeurs et des dépendances attendues.

### 🔁 Méthode save dans le repository

Dans `TaskRepository`, j’ai dû adapter la méthode `save()` pour qu’elle différencie la création (`create`) de la mise à jour (`update`) en fonction de la présence ou non de `data.id`.

### 🧪 Validation dans SaveTaskUseCase

J’ai ajouté une vérification dans le `SaveTaskUseCase` pour m’assurer que le champ `name` est bien présent. Sinon, une `BadRequestException` est levée.

### 🖱️ Frontend – Bouton de sauvegarde

Pour répondre à la consigne "*une tâche ne peut être mise à jour si le nom n’a pas changé*", j’ai ajouté une condition dans le frontend pour désactiver le bouton de sauvegarde dans ce cas-là.

---

## 💻 Stack technique utilisée

- **Backend** : NestJS, Prisma, SQLite
- **Frontend** : React, Vite, Material UI
- **Langage** : TypeScript

---

## ✅ Résultat final

L’application permet de gérer une liste de tâches de façon fluide avec toutes les fonctionnalités attendues. L’architecture mise en place est claire, modulaire et facilement maintenable.
