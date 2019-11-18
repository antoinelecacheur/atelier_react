# Ressources utiles

Si vous envisagez de vous autoformer, si vous cherchez quelques ressources ou encore si vous voulez vous assurer que vous maîtrisez les bases, cette page recense quelques ressources utiles du web pour apprendre React.

## Étape préliminaire

Bien connaître le langage JavaScript et les spécificités introduites par **ES6** (conférence EcmaScript 2015) et au-delà.
Les principaux ajouts sont présentés ici [ES6 for beginners](https://hackernoon.com/es6-for-beginners-f98120b57414) en 3 parties.
Avoir compris le principe de `Promises` en JavaScript, essentielles notamment pour l'utilisation d'API.

## Initiation à React

React fonctionne à partir de composants définis à l'aide d'une syntaxe JSX qui permet l'injection de HTML dans du JavaScript. Des méthodes permettent de gérer les propriétés de ses composants de manière statique et dynamique. Pour comprendre les fondamentaux de React, je recommande de passer par les tutoriels suivants :

1. [Scrimba](https://scrimba.com/g/glearnreact) Excellent tutoriel vidéo anglophone, le code est accessible, modifiable et enregistrable à n'importe quel moment de la vidéo.
2. [Codecademy](https://www.codecademy.com/learn/react-101) Création d'un compte pour 7 jours premium gratuit, Learn React part I et II assez complet.
3. [OpenClassroom](https://openclassrooms.com/fr/courses/4664381-realisez-une-application-web-avec-react-js) Donne une vision d'ensemble de React.
4. [React tutorial](https://reactjs.org/tutorial/tutorial.html) A faire après l'un des tutoriels précédents, ou en ayant bien assimilé la documentation officielle (sur le même site).
5. [L'intérêt de youtube à l'insee](https://www.youtube.com/watch?v=40pWMVMnftc) Un tutoriel très complet (avec une partie redux : #40, #42)

## Liens essentiels

* Pour initialiser une application avec React, utiliser la commande globale [create-react-app](https://openclassrooms.com/fr/courses/4664381-realisez-une-application-web-avec-react-js/4664801-demarrez-facilement-avec-create-react-app) disponible via npm.



* Un bon récapitulatif des étapes du *cycle de vie*, et leur utilisation : [Lifecycle](https://blog.bitsrc.io/react-16-lifecycle-methods-how-and-when-to-use-them-f4ad31fb2282)

* Les bases de la navigation avec React : [React Router](https://reacttraining.com/react-router/web/guides/quick-start). Voir en particulier l'exemple d'une Sidebar pour comprendre la force des composants au service de la navigation.

## Exemples de fonctionnement avec __Spring Boot__ (avec une API Rest)

* [Spring tutorial](https://spring.io/guides/tutorials/react-and-spring-data-rest/) Guide spring pour l'utilisation de React et Rest

* [Spring Boot et React](https://developer.okta.com/blog/2018/07/19/simple-crud-react-and-spring-boot) et [Bières en image](https://developer.okta.com/blog/2017/12/06/bootiful-development-with-spring-boot-and-react) deux tutoriels proposés par un développeur de chez Okta (API de gestion d'authentification).

## Style et composants

* __Ajouter du style__ :

Il est nécessaire d'ajouter des feuilles de style css pour styliser les composants. Il est donc possible d'utiliser du [Bootstrap](https://getbootstrap.com/) avec React.

* __Composants fonctionnels__ :

De nombreuses librairies proposent des composants stylisés et fonctionnels en React ([React Bootstrap](https://react-bootstrap.github.io/), [ReactStrap](https://reactstrap.github.io/)) mais la plus utilisée (notamment pour Nautile) reste [Material UI](https://material-ui.com/).

* __Datatables en React ?__ :

"On reconnaît un framework complet à son implémentation des [datatables](https://github.com/gregnb/mui-datatables), des [formulaires](https://jaredpalmer.com/formik/docs/overview) et de [l'autocomplétion](https://material-ui.com/components/autocomplete/)." aurait dit un grand sage à l'Insee.


## Du typage en __JavaScript__ ?

React supporte l'utilisation de [TypeScript](https://facebook.github.io/create-react-app/docs/adding-typescript) pour pouvoir typer ses variables (et quelques autres fonctionnalités).

## Fonctionnement avancé : utilisation de __Redux__

La gestion des états avec React peut s'avérer compliqué dès qu'on multiplie les composants et les fonctionnalités. On se retrouve parfois à devoir envoyer des informations (`props`) des éléments enfants vers les éléments parents, ce qui n'est pas prévu initialement dans le flux des données React.

* Pour pallier à ce genre de problèmes, et pour avoir une meilleure maîtrise du flux des données, une traçabilité des changements d'états, il existe une solution : [__Redux__](https://redux.js.org/) qui peut s'appliquer de manière générale pour toute application JavaScript.

* La logique de __Redux__ fonctionne particulièrement bien avec React, c'est pourquoi une librairie permet une [utilisation spécifique à React](https://redux.js.org/basics/usage-with-react).

* Pour mieux comprendre les bases de Redux en lien avec React, un excellent [tutoriel](https://www.valentinog.com/blog/redux/) explique pas à pas les étapes à réaliser.

* [Redux Form](https://redux-form.com/8.2.2/docs/gettingstarted.md/) propose une implémentation très pratique pour manipuler des formulaires en React, connectés au store très simplement.

## Nouveauté : les hooks

* Une fonctionnalité récemment ajoutée permet également une manipulation différente des `state` dans React : les [Hooks](https://reactjs.org/docs/hooks-intro.html). Ils permettent d'introduire un `state` au sein d'un _function component_. Ils ne remplacent pas définitivement les classes, mais assurent un fonctionnement similaire et simplifié pour certains aspects. Un autre [tutoriel](https://www.valentinog.com/blog/hooks/) reprend les explications de React et propose quelques ouvertures.


## « Tester, c'est douter. »

* __Vision globale__ : Toujours [Valentino](https://www.valentinog.com/blog/testing-react/).

* __Jest__ : Tests via snapshot ou via le DOM [en react](https://jestjs.io/docs/en/tutorial-react).

* __Librairie de tests__ : Toujours plus de moyens de [TESTER](https://github.com/testing-library/react-testing-library)

## Ressources supplémentaires

* __Glossaire__ : Github regroupant de nombreuses ressources React [awesome-react](https://github.com/enaqx/awesome-react)


