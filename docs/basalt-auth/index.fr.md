# **[Basalt Auth](https://www.npmjs.com/package/@basalt-lab/basalt-auth)**

!!! warning

    Basalt est actuellement à ses débuts, s'il vous plaît soyez indulgent et n'hesitez pas à faire un retour sur votre expérience par mail à [basalt-lab@proton.me](mailto:basalt-lab@proton.me).

## **Introduction**

**Basalt Auth** fait partie de l'écosystème Basalt, offrant une méthode pratique pour gérer l'authentification via des tokens.

Au cœur de ce module se trouve la classe BasaltToken, dont la fonction principale est la génération et la vérification des tokens.

La particularité de **Basalt Auth** réside dans son système de paire de clés : chaque token est associé à sa propre paire, une caractéristique qui le différencie des [JWT](https://jwt.io/) standards.

## **Pourquoi Basalt Auth ?**

L'objectif derrière **Basalt Auth** était de développer un système d'authentification personnalisé qui s'inspire de la structure des [JWT](https://jwt.io/), mais avec une touche distinctive: chaque token dispose de sa propre paire de clés.

Cette approche n'est pas nécessairement supérieure aux méthodes conventionnelles; c'est plutôt une exploration personnelle dans la conception de systèmes d'authentification.

Il est important de noter que la sécurité est une discipline évolutive, et les mérites de cette structure par rapport aux standards établis n'ont pas été pleinement évalués.

!!! warning

    **Basalt Auth** ne cherche pas à remplacer les solutions existantes, mais plutôt à offrir une alternative pour des cas d'utilisation spécifiques.

## **Caractéristiques Principales**

Au-delà de sa méthode de gestion des tokens, **Basalt Auth** est assez simple, avec quelques fonctionnalités clés :

  - **Paires de clés uniques par token :** Cette caractéristique peut offrir des aspects intéressants en termes de gestion des sessions.
  - **Processus de génération et de vérification :** Ces fonctions suivent une logique simplifiée, rendant leur utilisation assez directe.

Il n'est pas question de prétendre rivaliser ou remplacer les solutions existantes, mais plutôt de proposer une alternative pour des scénarios spécifiques.


## **Polyvalence et Compatibilité**

**Basalt Auth** est conçu pour être utilisé dans des contextes variés, que ce soit backend ou frontend.  
Sa nature indépendante facilite son incorporation dans différents projets, sans nécessiter de composants externes spécifiques.

## **Conclusion**

**Basalt Auth** propose une approche différente de l'authentification tokenisée.  
Sans chercher à révolutionner le domaine, ce module offre des fonctionnalités supplémentaires qui pourraient être d'intérêt pour des cas d'utilisation spécifiques.

Son parcours sera dicté par les retours d'expérience et les besoins émergents, et il reste un outil à considérer pour des projets recherchant une méthode d'authentification légèrement différente de la norme.
